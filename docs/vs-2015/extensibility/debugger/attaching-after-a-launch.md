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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841309"
---
# <a name="attaching-after-a-launch"></a>Anfügen nach einem Start
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Nachdem ein Programm gestartet wurde, ist die Debugsitzung bereit, die Debug-Engine (de) an das angefügte Programm anzufügen.  
  
## <a name="design-decisions"></a>Entwurfsentscheidungen  
 Da die Kommunikation innerhalb eines freigegebenen Adressraums einfacher ist, müssen Sie entscheiden, ob es sinnvoller ist, die Kommunikation zwischen der Debugsitzung und der de oder zwischen dem Programm de und dem Programm zu vereinfachen. Wählen Sie eine der folgenden Optionen aus:  
  
- Wenn es sinnvoller ist, die Kommunikation zwischen der Debugsitzung und der de zu vereinfachen, erstellt die Debugsitzung die de und fordert die de auf, das Programm anzufügen. Dadurch bleiben die Debuggingsitzung und die Deaktivierung in einem Adressraum und die Laufzeitumgebung und das Programm in einem anderen.  
  
- Wenn es sinnvoller ist, die Kommunikation zwischen der de und dem Programm zu vereinfachen, erstellt die Laufzeitumgebung die de. Dadurch bleibt die SDM in einem Adressraum und der de-, Laufzeitumgebung sowie das Programm in einem anderen Adressraum. Dies ist typisch für ein de-, das mit einem Interpreter zum Ausführen von Skriptsprachen implementiert wird.  
  
    > [!NOTE]
    > Wie der de an das Programm angefügt wird, hängt von der Implementierung ab. Die Kommunikation zwischen der de und dem Programm ist ebenfalls implementierungsabhängig.  
  
## <a name="implementation"></a>Implementierung  
 Programm gesteuert, wenn der Sitzungs-Debug-Manager (SDM) zuerst das [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) -Objekt empfängt, das das zu startende Programm darstellt, ruft es die [Attach](../../extensibility/debugger/reference/idebugprogram2-attach.md) -Methode auf und übergibt ihm ein [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) -Objekt, das später verwendet wird, um Debugereignisse an die SDM zurückzuleiten. Die `IDebugProgram2::Attach` Methode ruft dann die [onattach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) -Methode auf. Weitere Informationen zur Art und Weise, in der die SDM die `IDebugProgram2` Schnittstelle empfängt, finden Sie unter [Benachrichtigen des Ports](../../extensibility/debugger/notifying-the-port.md).  
  
 Wenn Ihre de im gleichen Adressraum wie das zu debuggende Programm ausgeführt werden muss, in der Regel, weil die de Teil eines interpreters ist, der ein Skript ausgeführt, `IDebugProgramNodeAttach2::OnAttach` gibt die Methode zurück `S_FALSE` , was darauf hinweist, dass der Anfüge Vorgang abgeschlossen wurde.  
  
 Wenn andererseits der de im Adressraum des SDM ausgeführt wird, `IDebugProgramNodeAttach2::OnAttach` gibt die Methode zurück, `S_OK` oder die [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) -Schnittstelle wird nicht für das [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) -Objekt implementiert, das dem gedebenen Programm zugeordnet ist. In diesem Fall wird die [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) -Methode schließlich aufgerufen, um den Anfüge Vorgang abzuschließen.  
  
 Im letzteren Fall müssen Sie die [getProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) -Methode für das- `IDebugProgram2` Objekt aufrufen, das an die-Methode weitergegeben wurde `IDebugEngine2::Attach` , die `GUID` im lokalen Programmobjekt speichern und diese zurückgeben, `GUID` Wenn die- `IDebugProgram2::GetProgramId` Methode anschließend für dieses Objekt aufgerufen wird. `GUID`Wird verwendet, um das Programm in den verschiedenen Debugkomponenten eindeutig zu identifizieren.  
  
 Beachten Sie, dass im Fall der `IDebugProgramNodeAttach2::OnAttach` Rückgabe der-Methode `S_FALSE` der `GUID` für das Programm zu verwendende-Objekt an diese Methode weitergegeben wird und es sich um die Methode handelt, die für `IDebugProgramNodeAttach2::OnAttach` `GUID` das lokale Programmobjekt festlegt.  
  
 DE ist nun an das Programm angefügt und kann alle Start Ereignisse senden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Direktes Anfügen an ein Programm](../../extensibility/debugger/attaching-directly-to-a-program.md)   
 [Benachrichtigen des Ports](../../extensibility/debugger/notifying-the-port.md)   
 [Debugtasks](../../extensibility/debugger/debugging-tasks.md)   
 [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [An](../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [Onattach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Anfügen](../../extensibility/debugger/reference/idebugengine2-attach.md)
