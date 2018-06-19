---
title: Nach einem Start Anfügen | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 69f9f9cde76c5fa66294fd2cdbdc5252169e0183
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31104705"
---
# <a name="attaching-after-a-launch"></a>Nach einem Start Anfügen
Nachdem ein Programm gestartet wurde, kann die Debugsitzung besagten Programm Debugging-Modul (DE) zuordnen.  
  
## <a name="design-decisions"></a>Entwurfsentscheidungen  
 Da die Kommunikation in einen freigegebenen Adressenbereich einfacher ist, müssen Sie entscheiden, ob es sinnvoller zur Erleichterung der Kommunikation zwischen der Debugsitzung und die DE oder zwischen dem Code und die Anwendung ist. Wählen Sie zwischen den folgenden:  
  
-   Wenn es zum Vereinfachen der Kommunikation zwischen der Debugsitzung und die DE sinnvoller, klicken Sie dann die Debugsitzung zusammen erstellt die DE, und fordert die DE an die Anwendung angefügt. Dadurch wird die Debugsitzung und "DE" zusammen einen Adressraum und der Laufzeitumgebung und Programm in einer anderen zusammen.  
  
-   Wenn sie weitere zum Vereinfachen der Kommunikation zwischen dem Code und die Anwendung sinnvoll ist, erstellt zusammen dann die Laufzeitumgebung DE. Dadurch verbleibt die SDM in einem Adressraum, und die DE, Laufzeitumgebung und Programm in einer anderen zusammen. Dies ist typisch für die einer bereitgestellten Kompatibilitätsrichtlinie, die ein Interpreter auszuführende skriptgesteuerte Sprachen implementiert sind.  
  
    > [!NOTE]
    >  Wie die DE an das Programm angefügt wird, ist implementierungsabhängig. Kommunikation zwischen dem Code und das Programm ist auch abhängig von der Implementierung.  
  
## <a name="implementation"></a>Implementierung  
 Programmgesteuert, wenn die Sitzung Debug-Manager (SDM) zuerst empfängt die [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) Objekt, das die Anwendung gestartet werden, ruft der [Anfügen](../../extensibility/debugger/reference/idebugprogram2-attach.md) -Methode, und übergeben sie ein [ IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) -Objekt, das später verwendet, um Debug-Ereignisse an die SDM zu übergeben. Die `IDebugProgram2::Attach` -Methode ruft dann die [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) Methode. Weitere Informationen zu den SDM wie empfängt die `IDebugProgram2` Benutzeroberfläche, siehe [benachrichtigen den Port](../../extensibility/debugger/notifying-the-port.md).  
  
 Wenn Ihre DE ausgeführt wird, in der gleichen Adressbereich wie der zu debuggenden Programms in der Regel ist die DE Teil ein Interpreter Ausführen eines Skripts, muss die `IDebugProgramNodeAttach2::OnAttach` -Methode zurückkehrt `S_FALSE`, gibt an, dass er den Prozess anhängen abgeschlossen.  
  
 Wenn andererseits, DE im Adressraum der SDM ausgeführt wird die `IDebugProgramNodeAttach2::OnAttach` -Methode zurückkehrt `S_OK` oder [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) Schnittstelle wird nicht auf alle implementiert die [IDebugProgramNode2 ](../../extensibility/debugger/reference/idebugprogramnode2.md) Objekt, das derzeit debuggte Programm zugeordnet. In diesem Fall die [Anfügen](../../extensibility/debugger/reference/idebugengine2-attach.md) -Methode schließlich aufgerufen, um der Anfügevorgang abgeschlossen.  
  
 In letzterem Fall, rufen Sie die [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) Methode auf der `IDebugProgram2` -Objekt, das übergeben wurde der `IDebugEngine2::Attach` -Methode, Speicher der `GUID` in der lokalen Anwendung Objekt, und dies zurückgeben `GUID` bei der `IDebugProgram2::GetProgramId` -Methode für dieses Objekt anschließend aufgerufen wird. Die `GUID` wird verwendet, um das Programm in die verschiedenen Komponenten der Debug eindeutig zu identifizieren.  
  
 Beachten Sie, dass im Fall von der `IDebugProgramNodeAttach2::OnAttach` Methode zurückgeben `S_FALSE`, die `GUID` für das Programm an diese Methode übergeben wird, und es wird die `IDebugProgramNodeAttach2::OnAttach` Methode, die festlegt der `GUID` für das lokale Programme-Objekt.  
  
 Die DE ist jetzt an das Programm und alle Startereignisse senden angefügt.  
  
## <a name="see-also"></a>Siehe auch  
 [Anhängen an ein Programm direkt](../../extensibility/debugger/attaching-directly-to-a-program.md)   
 [Benachrichtigen den Port](../../extensibility/debugger/notifying-the-port.md)   
 [Debugging-Aufgaben](../../extensibility/debugger/debugging-tasks.md)   
 [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [Anfügen](../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Anfügen](../../extensibility/debugger/reference/idebugengine2-attach.md)