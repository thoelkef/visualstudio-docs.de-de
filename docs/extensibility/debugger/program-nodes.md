---
title: "Programm-Knoten | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Programm-Knoten Debugkontext"
  - "Debuggen [Debugging-SDK] Knoten Programm"
  - "Programm-Knoten hinzufügen"
  - "Programm-Knoten, die ersetzende"
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Programm-Knoten
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Im Hinblick auf die Architektur der Debugger **Knoten**eines **Programms**:  
  
-   Ist eine einfache Beschreibung eines Programms.  
  
-   Kann sich selbst und den Prozess identifizieren, die er ausgeführt wird und kann angefügt werden, getrennt sind, und das Debugmodul DE \(sofern vorhanden\) beschreiben das den Fehler erstellt hat.  
  
-   Wird von einer [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)\-Schnittstelle dargestellt, in der Regel durch DE oder einen Port erstellt.  Knoten werden in einen Anschluss Programm hinzugefügt, indem [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)aufruft.  Wenn ein Programm an einen Anschluss Knoten hinzugefügt wird, wird er dem Prozess hinzugefügt, der das Programm, das dieser Knoten Programm darstellt.  
  
 Einmal, nachdem eine Debugsitzung, abhängig von der Implementierung des Pakets Knoten Debuggen, Programm gestartet wurde, werden entsprechende Anwendungen zu erstellen.  Wenn ein Prozess für die Programme abgefragt wird, werden die Programme, und zwar jeweils eines für jeden Knoten Programm aufgelistet.  
  
 Bevor ein Programm angefügt wird, erfordert nur die IDE eine einfache Beschreibung des Programms.  Diese Informationen können Knoten vom Programm abgerufen werden.  Nachdem das Programm angefügt wird, muss die IDE ausführlichere Informationen, z. B. eine Liste aller Threads anzeigen, die in das Programm aus.  Diese Informationen werden vom Programm selbst abgerufen.  
  
## Siehe auch  
 [Programs](../../extensibility/debugger/programs.md)   
 [Prozesse](../../extensibility/debugger/processes.md)   
 [Debug\-Modul](../../extensibility/debugger/debug-engine.md)   
 [Debugger\-Konzepte](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)