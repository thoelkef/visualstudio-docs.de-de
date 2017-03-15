---
title: "Debuggen von F# | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Debuggen [F#]"
  - "F#, Debuggen"
ms.assetid: 20bcd51c-2d06-4281-9a1e-ef2b91d1a779
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Debuggen von F# #
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Das Debuggen von F\# entspricht mit wenigen Ausnahmen dem Debuggen einer verwalteten Sprache:  
  
-   Das Fenster **Auto** zeigt keine F\#\-Variablen an.  
  
-   Bearbeiten und Fortfahren wird für F\# nicht unterstützt.  Das Bearbeiten von F\#\-Code während einer Debugsitzung ist möglich, sollte aber vermieden werden.  Da Codeänderungen während der Debugsitzung nicht übernommen werden, verursacht das Bearbeiten von F\#\-Code während des Debuggens einen Konflikt zwischen dem Quellcode und dem gedebuggten Code.  
  
-   Der Debugger erkennt keine F\#\-Ausdrücke.  Übersetzen Sie den Ausdruck in C\#\-Syntax, um während des F\#\-Debuggings einen Ausdruck in ein Debuggerfenster oder Dialogfeld einzugeben.  Beachten Sie beim Übersetzen eines F\#\-Ausdrucks in C\#, dass C\# \=\= als Vergleichsoperator für Gleichheit und F\# ein einzelnes \= verwendet.  
  
## Siehe auch  
 [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)