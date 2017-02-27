---
title: "Programs | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Programme Debuggen [SDK-Debuggen]"
  - "Debuggen von Programmen"
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Programs
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Im Hinblick auf die Architektur der Debugger ein **Programm**:  
  
-   Ist ein Container für eine Gruppe von Threads und einen Satz von Modulen.  Ein Programm verfügt über keine Analogie im Windows\-Betriebssystem.  
  
     Ein Programm ist eine Art Unterprozess.  Wenn Sie beispielsweise eine Website debuggen, kann ein Skript als Programm angezeigt werden.  Während ein Skript im Skriptmodul Prozess ausgeführt wird, unabhängig von anderen Skripts, verfügt es auch über einen eigenen Satz von Threads.  Ein Modul \(Debug\) DE und nicht mit einem Programm fügt den Debugger an einen Prozess oder einen Thread an.  
  
-   Kann sich selbst und den Prozess identifizieren, die er ausgeführt wird und kann angefügt werden, getrennt sind, und beschreiben ggf. DE, das sie erstellt hat.  Ein Programm kann ausgeführt werden, anzuhalten, fährt fort und wird beendet.  
  
-   Es können alle Threads auflisten.  Ein Programm kann auch einen eigenen Disassemblys datenstrom angeben und kann alle Code kontexte einer bestimmten Position des Dokuments auflisten.  
  
-   Wird von einer Schnittstelle dargestellt [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) erstellt, bevor das Programm angefügt wird oder Anfügen als Teil des Prozesses, abhängig von der Implementierung.  Wenn ein Anschluss Programme eines Prozesses auflistet, wird jedes Programm in Übereinstimmung mit einer entsprechenden [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)\-Schnittstelle erstellt, die als Argument an [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)übergeben wird.  Beim Debuggen von Modulen `IDebugProgram2` auch Schnittstellen erstellen, um Programme zu zeigen, werden diese Programmen nicht in Übereinstimmung mit einem Knoten Programm erstellt.  Die Schnittstellen, die von `IDebugProgramNode2` DE erstellt wurden, sind für das Debuggen verwendet, während die tatsächlich von einem Port erstellt werden, nur zum Ermitteln von Programmen verwendet werden, die in einem Prozess ausgeführt werden.  
  
## Siehe auch  
 [Prozesse](../../extensibility/debugger/processes.md)   
 [Programm\-Knoten](../../extensibility/debugger/program-nodes.md)   
 [Module](../../extensibility/debugger/modules.md)   
 [Debugger\-Konzepte](../../extensibility/debugger/debugger-concepts.md)   
 [Debug\-Modul](../../extensibility/debugger/debug-engine.md)   
 [Dokumentposition](../../extensibility/debugger/document-position.md)   
 [Codekontext](../../extensibility/debugger/code-context.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)