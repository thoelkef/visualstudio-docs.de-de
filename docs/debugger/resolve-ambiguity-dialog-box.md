---
title: "Dialogfeld &quot;Mehrdeutigkeit aufl&#246;sen&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.Disambig"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Mehrdeutigkeit auflösen (Dialogfeld)"
  - "Debugger, Mehrdeutigkeit auflösen (Dialogfeld)"
  - "Debuggen [C++], Auflösen von Mehrdeutigkeiten"
ms.assetid: d9f47455-a116-4c84-8bad-2dfbf4d77f74
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Dialogfeld &quot;Mehrdeutigkeit aufl&#246;sen&quot;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Das Dialogfeld `Resolve Ambiguity` wird angezeigt, wenn die anzuzeigende Position vom Debugger nicht ausgewählt werden kann.  Wenn Sie beispielsweise C\+\+\-Vorlagen verwenden, können Sie aus einer einzigen Funktionsvorlage mehrere Funktionen erstellen.  Wenn der Debugger an einer Quellcodeposition in der Vorlage anhält und Sie auf `Go To Disassembly` klicken, bietet der Debugger mehrere Möglichkeiten.  Jede aus der Vorlage erstellte Funktion hat einen eigenen Disassemblycode, und der Debugger weiß nicht, welcher Code angezeigt werden soll.  Im Dialogfeld `Resolve Ambiguity` können Sie die gewünschte Position aus einer Liste aller entsprechenden Positionen auswählen.  
  
 `Choose the specific location`  
 Es werden alle dem Befehl entsprechenden Positionen aufgeführt.  
  
 `Address`  
 Die Speicheradressen für die einzelnen Funktionen werden angezeigt.  
  
 `Function`  
 Der Name der jeweiligen Funktion wird angezeigt.  
  
 `Module`  
 Das Modul \(EXE oder DLL\), das den Objektcode für die Funktion enthält, wird angezeigt.  
  
## Siehe auch  
 [Ausdrücke im Debugger](../debugger/expressions-in-the-debugger.md)