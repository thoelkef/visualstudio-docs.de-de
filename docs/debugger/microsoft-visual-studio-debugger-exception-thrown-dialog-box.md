---
title: "Dialogfeld &quot;Microsoft Visual&#160;Studio Debugger (Ausnahme ausgel&#246;st)&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.exceptions.thrown"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Microsoft Visual Studio Debugger (Ausnahmeverweis) (Dialogfeld)"
  - "Ausnahmebehandlung, beim Debuggen"
  - "Debugger, Ausnahmen"
  - "Auslösen von Ausnahmen, beim Debuggen"
ms.assetid: 1fe98d10-c8f9-4b39-a920-99169bfd542e
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Dialogfeld &quot;Microsoft Visual&#160;Studio Debugger (Ausnahme ausgel&#246;st)&quot;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Im Programm ist eine Ausnahme aufgetreten.  In diesem Dialogfeld wird die Art der ausgelösten Ausnahme angezeigt.  Die Ausnahme muss durch den Code behandelt werden.  Folgende Optionen stehen für das Behandeln der Ausnahme zur Verfügung:  
  
 **Break**  
 Die Ausführung wird im Debugger unterbrochen.  Der Ausnahmehandler wird vor der Unterbrechung nicht aufgerufen.  Wenn Sie ab der Unterbrechung fortsetzen, wird der Ausnahmehandler aufgerufen.  
  
 **Continue**  
 Die Ausführung wird fortgesetzt, sodass der die Ausnahme vom Ausnahmehandler behandelt werden kann.  Diese Option ist für bestimmte Ausnahmetypen nicht verfügbar.  Mit **Weiter** kann die Anwendung fortgesetzt werden.  In einer systemeigenen Anwendung wird die Ausnahme bei dieser Option erneut ausgelöst.  In einer verwalteten Anwendung wird dadurch entweder das Programm beendet oder die Ausnahme wird von einer Hostanwendung behandelt.  
  
> [!NOTE]
>  In verwaltetem Code können Sie die Ausführung nach einem Ausnahmefehler nicht fortsetzen.  Wenn Sie nach einem Ausnahmefehler in verwaltetem Code auf **Weiter** klicken, wird das Debuggen beendet.  
  
 **Ignorieren**  
 Diese Option ermöglicht das Fortsetzen der Ausführung ohne Aufrufen des Ausnahmehandlers.  Dies kann sich weiter auswirken und beispielsweise zu weiteren Ausnahmen und Fehlern führen.  Diese Option ist für bestimmte Ausnahmetypen nicht verfügbar.  
  
## Siehe auch  
 [Verwalten von Ausnahmen mit dem Debugger](../debugger/managing-exceptions-with-the-debugger.md)   
 [Best Practices für Ausnahmen](../Topic/Best%20Practices%20for%20Exceptions.md)   
 [Exception Handling](/visual-cpp/windows/exception-handling-cpp-component-extensions)