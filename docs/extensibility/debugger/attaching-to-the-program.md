---
title: "Anfügen an das Programm | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debug engines, attaching to programs
ms.assetid: 9a3f5b83-60b5-4ef0-91fe-a432105bd066
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 75b532005bf4aeb471aa16ecfc6ac8ff508e3c7f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="attaching-to-the-program"></a>Anfügen an die Anwendung
Nachdem Sie Ihre Programme mit den entsprechenden Port registriert haben, müssen Sie den Debugger an das Programm anfügen, die Sie debuggen möchten.  
  
## <a name="choosing-how-to-attach"></a>Auswählen des Verfahrens zum Anfügen  
 Es gibt drei Möglichkeiten, die in denen Sitzung Debug-Manager (SDM) versucht, das derzeit debuggte Programm an.  
  
1.  Für Programme, die durch die Debugging-Modul über gestartet sind die [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) -Methode (typisch für interpretierte Sprachen, z. B.), das SDM erhält die [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) -Schnittstelle aus die [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) Objekt zugewiesen ist, mit dem Programm, die daran angefügt werden. Wenn die SDM abrufen kann die `IDebugProgramNodeAttach2` -Schnittstelle, die SDM ruft dann die [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) Methode. Die `IDebugProgramNodeAttach2::OnAttach` -Methode zurückkehrt `S_OK` , um anzugeben, dass es nicht an das Programm angefügt und andere Versuche unternommen werden können, an die Anwendung angefügt.  
  
2.  Wenn die SDM abrufen kann die [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md) Schnittstelle aus dem Programm, die daran angefügt werden, die SDM-Aufrufe der [Anfügen](../../extensibility/debugger/reference/idebugprogramex2-attach.md) Methode. Dieser Ansatz ist typisch für Programme, die durch den Port Lieferanten Remote gestartet wurden.  
  
3.  Wenn das Programm nicht werden, über angefügt kann die `IDebugProgramNodeAttach2::OnAttach` oder `IDebugProgramEx2::Attach` Methoden, die SDM lädt die Debugging-Modul (sofern noch nicht geladen) durch Aufrufen der `CoCreateInstance` -Funktion und ruft dann die [Anfügen](../../extensibility/debugger/reference/idebugengine2-attach.md) Methode. Dieser Ansatz ist typisch für Programme, die lokal ein Lieferant Port gestartet.  
  
     Es ist auch möglich, für einen benutzerdefinierten Port Lieferanten zum Aufrufen der `IDebugEngine2::Attach` in den benutzerdefinierten Port Lieferanten Implementierung der Methode der `IDebugProgramEx2::Attach` Methode. In diesem Fall startet der benutzerdefinierten Port Lieferanten in der Regel die Debugging-Modul auf dem Remotecomputer.  
  
 Anlage wird erzielt, wenn die Sitzung Debug-Manager (SDM) Ruft die [Anfügen](../../extensibility/debugger/reference/idebugengine2-attach.md) Methode.  
  
 Wenn Sie Ihre DE in demselben Prozess wie die Anwendung, die debuggt werden ausgeführt, müssen Sie die folgenden Methoden implementieren [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md):  
  
-   [GetHostName](../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md),  
  
-   [GetHostPid](../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)  
  
-   [GetProgramName](../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)  
  
 Nach der `IDebugEngine2::Attach` -Methode aufgerufen wird, befolgen Sie diese Schritte in der Implementierung von der `IDebugEngine2::Attach` Methode:  
  
1.  Senden einer [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) Ereignisobjekt, das SDM. Weitere Informationen finden Sie unter [Ereignisse senden](../../extensibility/debugger/sending-events.md).  
  
2.  Rufen Sie die [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) Methode auf die [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) -Objekt, das übergeben wurde die `IDebugEngine2::Attach` Methode.  
  
     Dies gibt eine `GUID` dient außerdem zur Identifizierung des Programms. Die `GUID` müssen gespeichert werden, in dem Objekt, stellt die lokale Programm, de, und es werden, wenn zurückgegeben muss die `IDebugProgram2::GetProgramId` Methode wird aufgerufen, auf die `IDebugProgram2` Schnittstelle.  
  
    > [!NOTE]
    >  Bei Implementierung die `IDebugProgramNodeAttach2` Netzwerkschnittstelle, die des Programms `GUID` übergeben wird, um die `IDebugProgramNodeAttach2::OnAttach` Methode. Dies `GUID` wird verwendet, für des Programms `GUID` zurückgegebenes die `IDebugProgram2::GetProgramId` Methode.  
  
3.  Senden einer [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) Ereignisobjekt, das SDM benachrichtigen, die der lokalen `IDebugProgram2` Objekt, das Sie erstellt wurde, um das Programm de darstellen. Weitere Informationen finden Sie unter [Ereignisse senden](../../extensibility/debugger/sending-events.md).  
  
    > [!NOTE]
    >  Dies entspricht nicht dem `IDebugProgram2` -Objekt, das übergeben wurde, die `IDebugEngine2::Attach` Methode. Die zuvor übergebene `IDebugProgram2` Objekt wird von den Port nur erkannt, und ist ein separates Objekt.  
  
## <a name="see-also"></a>Siehe auch  
 [Start-basierte Anlage](../../extensibility/debugger/launch-based-attachment.md)   
 [Senden von Ereignissen](../../extensibility/debugger/sending-events.md)   
 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)   
 [Anfügen](../../extensibility/debugger/reference/idebugprogramex2-attach.md)   
 [Anfügen](../../extensibility/debugger/reference/idebugengine2-attach.md)