---
title: "Nach einem starten Anf&#252;gen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Debugmodule, Anhängen an Programme"
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Nach einem starten Anf&#252;gen
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Nachdem ein Programm gestartet wurde, ist die Debugsitzung bereit, das Debugmodul \(DE\) besagtem Programm anzufügen.  
  
## Entwurfs\-Entscheidungen  
 Da die Kommunikation innerhalb eines freigegebenen Adressbereichs einfacher ist, müssen Sie sich, ob sie mehr von Bedeutung, ist die Kommunikation zwischen der Debugsitzung und DE zu erleichtern, oder zwischen DE und dem Programm ermitteln.  Wählen Sie zwischen dem folgenden aus:  
  
-   Wenn es mehr sinnvoll ist, die Kommunikation zwischen der Debugsitzung und DE zu erleichtern, erstellt die Debugsitzung DE und fordert DE, um auf das Programm anzufügen.  Auf diese Weise können die Debugsitzung und DE in einem Adressraum und die Laufzeitumgebung und das Programm in einen anderen.  
  
-   Wenn es mehr sinnvoll ist, die Kommunikation zwischen DE und dem Programm zu erleichtern, erstellt die Laufzeitumgebung. DE  Dies ermöglicht das SDM in einem Adressraum und DE, die Laufzeitumgebung und das Programm in einen anderen.  Dies ist der DE typisch, das mit einem Interpreter implementiert wird, damit vorbereitete Sprachen auszuführen.  
  
    > [!NOTE]
    >  Wie DE Programmieren anfügt, ist Implementierung abhängige Datei.  Kommunikation zwischen DE und dem Programm kann auch Implementierung abhängige Datei.  
  
## Implementierung  
 Programmgesteuert, wenn der Debug\- Manager der Sitzung \(SDM\) zuerst das [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)\-Objekt empfängt, das das Programm gestartet werden darstellt, ruft es die [Anfügen](../../extensibility/debugger/reference/idebugprogram2-attach.md)\-Methode auf und übergibt es ein [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)\-Objekt, das zum Debuggen von Ereignissen zurück an den SDM verwendetes neueres zu übergeben.  Die `IDebugProgram2::Attach`\-Methode ruft anschließend die [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)\-Methode auf.  Weitere Informationen darüber, wie sich das SDM die `IDebugProgram2`\-Schnittstelle erhält, finden Sie unter [Benachrichtigen den Port](../../extensibility/debugger/notifying-the-port.md).  
  
 Wenn in den gleichen DE den Adressbereich ausgeführt werden muss das Programm, das gedebuggt wird. In der Regel werden, da DE Teil eines Interpreters handelt, der ein Skript ausgeführt wird, gibt die Methode `IDebugProgramNodeAttach2::OnAttach``S_FALSE`zurück, um anzugeben, dass sie den Anfügen Prozess abgeschlossen wurde.  
  
 Wenn andererseits DE im Adressbereich des SDM ausgeführt wird, gibt die Methode `IDebugProgramNodeAttach2::OnAttach``S_OK` zurück, oder [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)\-Schnittstelle wird nicht an allen auf dem [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)\-Objekt implementiert, das mit dem Programm verknüpft ist, das gedebuggt wird.  In diesem Fall wird die [Anfügen](../../extensibility/debugger/reference/idebugengine2-attach.md) schließlich Methode aufgerufen, um den Anfügevorgang zu vervollständigen.  
  
 In letzterem Fall müssen Sie die [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)`IDebugProgram2`\-Methode für das Objekt aufrufen, das an die Methode übergeben, `IDebugEngine2::Attach` im lokalen `GUID` gespeichert wurde. Dieses Programm Objekt `GUID` zurückgibt, wenn die `IDebugProgram2::GetProgramId`\-Methode danach für dieses Objekt aufgerufen wird.  `GUID` wird verwendet, um das Programm zu den verschiedenen Komponenten Debuggen eindeutig zu identifizieren.  
  
 Beachten Sie, dass im Falle der `IDebugProgramNodeAttach2::OnAttach`\-Methode, die `S_FALSE`zurückgibt, wird für das Programm zu verwenden `GUID` , an diese Methode übergeben und die `IDebugProgramNodeAttach2::OnAttach`\-Methode, die auf dem lokalen `GUID` Programm Objekt festgelegt werden soll.  
  
 DE wird jetzt in das Programm angefügt und vorbereitet, um alle Start von Ereignissen zu senden.  
  
## Siehe auch  
 [Anfügen an ein Programm direkt](../../extensibility/debugger/attaching-directly-to-a-program.md)   
 [Benachrichtigen den Port](../../extensibility/debugger/notifying-the-port.md)   
 [Debugging\-Aufgaben](../../extensibility/debugger/debugging-tasks.md)   
 [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [Anfügen](../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Anfügen](../../extensibility/debugger/reference/idebugengine2-attach.md)