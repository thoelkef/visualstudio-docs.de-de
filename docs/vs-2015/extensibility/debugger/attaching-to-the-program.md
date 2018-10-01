---
title: Anfügen an das Programm | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 9a3f5b83-60b5-4ef0-91fe-a432105bd066
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ed9bcc02f5a17471c4679aae7ad9772a8a45f6e2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47521773"
---
# <a name="attaching-to-the-program"></a>Anfügen an das Programm
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Anfügen an das Programm](https://docs.microsoft.com/visualstudio/extensibility/debugger/attaching-to-the-program).  
  
Nachdem Sie Ihre Programme mit den entsprechenden Port registriert haben, müssen Sie den Debugger an das Programm anfügen, die Sie debuggen möchten.  
  
## <a name="choosing-how-to-attach"></a>Auswählen von Anfügen  
 Es gibt drei Möglichkeiten, die in denen die sitzungsbasierter Debug-Manager (SDM) versucht, Anfügen an die Anwendung gedebuggt wird.  
  
1.  Für Programme, die von der Debug-Engine über gestartet werden die [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) -Methode (typisch für interpretierte Sprachen, z. B.), das SDM erhält die [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) -Schnittstelle aus die [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) Objekt, das Programm daran angefügt werden, zugeordnet. Wenn das SDM abrufen kann, die `IDebugProgramNodeAttach2` -Schnittstelle, das SDM ruft dann die [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) Methode. Die `IDebugProgramNodeAttach2::OnAttach` Methodenrückgabe `S_OK` , um anzugeben, dass es nicht an das Programm angefügt und andere Versuche zum Anfügen an das Programm vorgenommen werden können.  
  
2.  Wenn, das SDM abrufen kann der [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md) Schnittstelle aus dem Programm daran angefügt werden, die SDM-Aufrufe der [Anfügen](../../extensibility/debugger/reference/idebugprogramex2-attach.md) Methode. Dieser Ansatz ist typisch für Programme, die von den Anschlusslieferanten Remote gestartet wurden.  
  
3.  Wenn das Programm nicht werden, über angefügt kann die `IDebugProgramNodeAttach2::OnAttach` oder `IDebugProgramEx2::Attach` Methoden, das SDM lädt die Debug-Engine (sofern nicht bereits geladen ist) durch Aufrufen der `CoCreateInstance` -Funktion und ruft dann die [Anfügen](../../extensibility/debugger/reference/idebugengine2-attach.md) Methode. Dieser Ansatz ist typisch für Programme, die lokal vom eines portanbieters gestartet.  
  
     Es ist auch möglich, für einen benutzerdefinierten Port Lieferanten zum Aufrufen der `IDebugEngine2::Attach` -Methode in der Implementierung des benutzerdefinierten Port Lieferanten der `IDebugProgramEx2::Attach` Methode. In diesem Fall startet der benutzerdefinierten Port Lieferanten in der Regel die Debug-Engine auf dem Remotecomputer.  
  
 Anlage wird erreicht, wenn es sich bei der sitzungsbasierter Debug-Manager (SDM) Ruft die [Anfügen](../../extensibility/debugger/reference/idebugengine2-attach.md) Methode.  
  
 Wenn Sie Ihre DE in demselben Prozess wie die zu debuggende Anwendung ausführen, müssen Sie die folgenden Methoden der implementieren [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md):  
  
-   [GetHostName](../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md),  
  
-   [GetHostPid](../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)  
  
-   [GetProgramName](../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)  
  
 Nach der `IDebugEngine2::Attach` -Methode aufgerufen wird, gehen Sie in der Implementierung von der `IDebugEngine2::Attach` Methode:  
  
1.  Senden einer [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) Event-Objekt, das SDM. Weitere Informationen finden Sie unter [Senden von Ereignissen](../../extensibility/debugger/sending-events.md).  
  
2.  Rufen Sie die [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) Methode für die [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) -Objekt, das übergeben wurde die `IDebugEngine2::Attach` Methode.  
  
     Dies gibt eine `GUID` wird, um die Anwendung zu identifizieren. Die `GUID` müssen gespeichert werden, in dem Objekt, stellt der lokalen Programm bereit, um die DE, und es muss zurückgegeben werden, wenn die `IDebugProgram2::GetProgramId` Methode wird aufgerufen, auf die `IDebugProgram2` Schnittstelle.  
  
    > [!NOTE]
    >  Wenn Sie implementieren die `IDebugProgramNodeAttach2` Schnittstelle des Programms `GUID` übergeben wird, um die `IDebugProgramNodeAttach2::OnAttach` Methode. Dies `GUID` wird verwendet, für des Programms die `GUID` zurückgegebenes der `IDebugProgram2::GetProgramId` Methode.  
  
3.  Senden einer [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) Event-Objekt, das SDM zu benachrichtigen, die der lokalen `IDebugProgram2` Objekt wurde erstellt, um die Anwendung für das DE darstellen. Weitere Informationen finden Sie unter [Senden von Ereignissen](../../extensibility/debugger/sending-events.md).  
  
    > [!NOTE]
    >  Dies ist nicht die gleiche `IDebugProgram2` -Objekt, das übergebene der `IDebugEngine2::Attach` Methode. Das zuvor übergebene `IDebugProgram2` Objekt wird von den Port nur erkannt und ein separates Objekt ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Startbasiertes](../../extensibility/debugger/launch-based-attachment.md)   
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

