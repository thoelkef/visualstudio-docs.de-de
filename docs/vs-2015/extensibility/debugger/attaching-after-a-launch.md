---
title: Anfügen nach einem Start | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 693cf6d746f51862415f2f30e46d48a998047f14
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63437434"
---
# <a name="attaching-after-a-launch"></a>Anfügen nach einem Start
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Nachdem ein Programm gestartet wurde, kann die Debugsitzung die Debug-Engine (DE) um genannte Anwendung anfügen.  
  
## <a name="design-decisions"></a>Entwurfsentscheidungen  
 Da die Kommunikation innerhalb einer gemeinsam genutzten Adressraums einfacher ist, müssen Sie entscheiden, ob die Kommunikation zwischen der Debugsitzung und die DE oder zwischen den Code und die Anwendung ermöglicht Weitere sinnvoll ist. Wählen Sie zwischen den folgenden:  
  
- Wenn sie zum Vereinfachen der Kommunikation zwischen der Debugsitzung und die DE sinnvoller, klicken Sie dann die Debugsitzung zusammen erstellt die DE, und fordert die DE zum Anfügen an die Anwendung. Dies bewirkt, dass die Debugsitzung und DE zusammen einen Adressraum, und das Runtime-Umgebung und das Programm in einem anderen zusammen.  
  
- Wenn es zum Vereinfachen der Kommunikation zwischen dem Code und das Programm sinnvoller, erstellt gemeinsam die Runtime-Umgebung die DE. Dies bewirkt, dass das SDM in einem Adressraum, und die DE-Laufzeitumgebung und Programm zusammen in einer anderen. Dies ist typisch für einer bereitgestellten Kompatibilitätsrichtlinie, die mit einem Interpreter zum Ausführen von Skripts Sprachen implementiert wird.  
  
    > [!NOTE]
    > Wie die DE für das Programm angefügt wird, ist implementierungsabhängig. Kommunikation zwischen dem Code und das Programm ist auch abhängig von der Implementierung.  
  
## <a name="implementation"></a>Implementierung  
 Programmgesteuert, wenn der Sitzungs-Manager (SDM) zuerst empfängt die [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) Objekt, das das Programm gestartet wird, ruft der [Anfügen](../../extensibility/debugger/reference/idebugprogram2-attach.md) Methode auf und übergibt es ein [ IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) -Objekt, das später verwendet, um Debugereignisse zurück, das SDM zu übergeben. Die `IDebugProgram2::Attach` -Methode ruft dann die [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) Methode. Weitere Informationen zu den SDM wie empfängt die `IDebugProgram2` Benutzeroberfläche, siehe [Benachrichtigen des Ports](../../extensibility/debugger/notifying-the-port.md).  
  
 Wenn Ihre DE ausgeführt wird, in der gleichen Adressbereich wie das derzeit debuggte Programm, in der Regel da das DE einem Interpreter gehört, Ausführen eines Skripts, muss die `IDebugProgramNodeAttach2::OnAttach` Methodenrückgabe `S_FALSE`, gibt an, dass er den anfügungsprozess abgeschlossen.  
  
 Wenn Sie auf der anderen Seite der DE in den Adressraum, der die SDM ausgeführt wird die `IDebugProgramNodeAttach2::OnAttach` Methodenrückgabe `S_OK` oder [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) Schnittstelle wird nicht an alle implementiert die [IDebugProgramNode2 ](../../extensibility/debugger/reference/idebugprogramnode2.md) Objekt, das derzeit debuggte Programm zugeordnet. In diesem Fall die [Anfügen](../../extensibility/debugger/reference/idebugengine2-attach.md) schließlich aufgerufen, um der Anfügevorgang abgeschlossen.  
  
 In letzterem Fall müssen Sie Aufrufen der [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) Methode für die `IDebugProgram2` -Objekt, das übergeben wurde die `IDebugEngine2::Attach` -Methode, Store die `GUID` in der lokalen Anwendung Objekt aus, und dies zurückzugeben `GUID` bei der `IDebugProgram2::GetProgramId` Methode für dieses Objekt anschließend aufgerufen wird. Die `GUID` wird verwendet, um die Anwendung in den verschiedenen Komponenten von Debug eindeutig zu identifizieren.  
  
 Beachten Sie, dass im Fall von der `IDebugProgramNodeAttach2::OnAttach` Methode zurückgeben `S_FALSE`, `GUID` für das Programm die Verwendung dieser Methode übergeben wird, und es ist die `IDebugProgramNodeAttach2::OnAttach` Methode, die festlegt der `GUID` für das Objekt für die lokale Anwendung.  
  
 Die DE ist jetzt für das Programm und bereit ist, senden alle Startereignisse angefügt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Direktes Anfügen an ein Programm](../../extensibility/debugger/attaching-directly-to-a-program.md)   
 [Benachrichtigen des Ports](../../extensibility/debugger/notifying-the-port.md)   
 [Debuggingaufgaben](../../extensibility/debugger/debugging-tasks.md)   
 [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [Anfügen](../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Anfügen](../../extensibility/debugger/reference/idebugengine2-attach.md)
