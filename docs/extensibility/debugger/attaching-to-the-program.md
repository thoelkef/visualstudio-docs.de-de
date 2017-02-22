---
title: "Anf&#252;gen an das Programm | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Debugmodule, Anhängen an Programme"
ms.assetid: 9a3f5b83-60b5-4ef0-91fe-a432105bd066
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Anf&#252;gen an das Programm
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Nachdem Sie die Programme mit dem geeigneten Anschluss registriert haben, müssen Sie den Debugger an das Programm anhängen, das Sie debuggen möchten.  
  
## Auswählen, wie anhängt  
 Es gibt drei Möglichkeiten, in denen der Debug\- Manager der Sitzung \(SDM\) versucht, auf das Programm anzufügen, das gedebuggt wird.  
  
1.  Für Programme, die durch das Debugmodul von der [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)\-Methode gestartet werden \(typisch von interpretierten Sprachen, z\), erhält das SDM die [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)\-Schnittstelle aus dem [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)\-Objekt, das mit dem Programm verknüpft ist, das angefügt wird.  Wenn das SDM erhalten kann die `IDebugProgramNodeAttach2`\-Schnittstelle, ruft das SDM dann die [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)\-Methode auf.  Die `IDebugProgramNodeAttach2::OnAttach`\-Methode gibt `S_OK` zurück, um anzugeben, dass sie nicht auf das Programm angefügt haben und dass andere Tests ausgeführt werden können, um dem Programm anzufügen.  
  
2.  Wenn das SDM die [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)\-Schnittstelle vom Programm abgerufen werden können, das angefügt wird, ruft das SDM die [Anfügen](../../extensibility/debugger/reference/idebugprogramex2-attach.md)\-Methode auf.  Dieser Ansatz ist typisch für Programme, die remote des Anschlusslieferanten gestartet wurden.  
  
3.  Wenn das Programm nicht von der `IDebugProgramNodeAttach2::OnAttach` oder `IDebugProgramEx2::Attach`\-Methode angefügt werden kann, wird die Auslastung SDM das Debugmodul \(sofern dies nicht bereits geladen wurde\), indem sie die `CoCreateInstance`\-Funktion aufrufen und dann die [Anfügen](../../extensibility/debugger/reference/idebugengine2-attach.md)\-Methode auf.  Dieser Ansatz ist für Programme, die lokal durch einen Anschlusslieferanten typisch.  
  
     Es ist auch möglich, für einen benutzerdefinierten Anschlusslieferanten, die `IDebugEngine2::Attach`\-Methode in der benutzerdefinierten Implementierung des Anschlusslieferanten der `IDebugProgramEx2::Attach`\-Methode aufzurufen.  In der Regel in diesem Fall löst der benutzerdefinierten Port lieferant das Debugmodul auf dem Remotecomputer.  
  
 Anlage wird erreicht, wenn der Debug\- Manager der Sitzung \(SDM\), die [Anfügen](../../extensibility/debugger/reference/idebugengine2-attach.md)\-Methode aufruft.  
  
 Wenn Sie DE im gleichen Prozess der die Anwendung gedebuggt werden soll, dann müssen Sie die folgenden Methoden ausführen: Implementieren von [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)  
  
-   [GetHostName](../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md),  
  
-   [GetHostPid](../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)  
  
-   [GetProgramName](../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)  
  
 Nachdem die `IDebugEngine2::Attach`\-Methode aufgerufen wird, führen Sie die folgenden Schritte in der Implementierung der `IDebugEngine2::Attach`\-Methode:  
  
1.  Senden Sie ein [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) SDM auf das Ereignisobjekt.  Weitere Informationen finden Sie unter [Senden von Ereignissen](../../extensibility/debugger/sending-events.md).  
  
2.  Rufen Sie die [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)\-Methode für das [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)\-Objekt an, das zur `IDebugEngine2::Attach`\-Methode übergeben wurde.  
  
     Dies gibt `GUID` zurück, das verwendet wird, um das Programm zu identifizieren.  `GUID` muss im Objekt gespeichert, das das lokale Programm DE darstellt, und es muss zurückgegeben werden, wenn die von der `IDebugProgram2`\-Schnittstelle `IDebugProgram2::GetProgramId`\-Methode aufgerufen wird.  
  
    > [!NOTE]
    >  Wenn Sie die `IDebugProgramNodeAttach2`\-Schnittstelle implementieren, wird `GUID` des Programms zur `IDebugProgramNodeAttach2::OnAttach`\-Methode übergeben.  Dieses `GUID` wird für `GUID` des Programms verwendet, das von der `IDebugProgram2::GetProgramId`\-Methode zurückgegeben wird.  
  
3.  Senden Sie ein [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)\-Ereignisobjekt, um das SDM zu benachrichtigen, dass das lokale `IDebugProgram2`\-Objekt erstellt wurde, um das Programm zu präsentieren. DE  Ausführlichere Informationen finden Sie unter [Senden von Ereignissen](../../extensibility/debugger/sending-events.md).  
  
    > [!NOTE]
    >  Dies ist nicht dasselbe `IDebugProgram2`\-Objekt, das in die `IDebugEngine2::Attach`\-Methode übergeben wurde.  Das zuvor erfolgreich `IDebugProgram2`\-Objekt wird nur durch den Anschluss erkannt und stellt ein separates Objekt.  
  
## Siehe auch  
 [Launch\-basierte Anlage](../../extensibility/debugger/launch-based-attachment.md)   
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