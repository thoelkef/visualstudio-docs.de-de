---
title: "Die erste Anweisung dieser &quot;Sub New&quot; muss ein Aufruf an &quot;MyBase.New&quot; oder &quot;MyClass.New&quot; sein (mehrere aufrufbare Konstruktoren ohne Parameter) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32038"
  - "bc32038"
helpviewer_keywords: 
  - "BC32038"
ms.assetid: 52e4e9df-a85b-46ae-a0cc-7d8fa377fe95
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die erste Anweisung dieser &quot;Sub New&quot; muss ein Aufruf an &quot;MyBase.New&quot; oder &quot;MyClass.New&quot; sein (mehrere aufrufbare Konstruktoren ohne Parameter)
Die erste Anweisung dieser "Sub New" muss ein Aufruf an "MyBase.New" oder "MyClass.New" sein, da die Basisklasse "Basis" von "\<Abgeleitet\>" mehr als eine zugreifbare "Sub New" hat, die ohne Argumente aufgerufen werden kann.  
  
 Ein Klassenkonstruktor stellt keinen Aufruf an einen Basisklassenkonstruktor bereit, und [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] kann keinen impliziten Aufruf bereitstellen, weil es nicht ermitteln kann, welcher Basisklassenkonstruktor aufgerufen werden soll.  
  
 **Fehler\-ID:** BC32038  
  
### So beheben Sie diesen Fehler  
  
-   Fügen Sie einen Aufruf an einen Basisklassenkonstruktor `MyBase.New()` oder einen anderen Konstruktor dieser Klasse hinzu, indem Sie `MyClass.New()` oder `Me.New()` als erste Zeile dieses Konstruktors verwenden.  
  
## Siehe auch  
 [Object Lifetime: How Objects Are Created and Destroyed](../Topic/Object%20Lifetime:%20How%20Objects%20Are%20Created%20and%20Destroyed%20\(Visual%20Basic\).md)   
 [NICHT IM BUILD: Verwenden von Konstruktoren und Destruktoren](http://msdn.microsoft.com/de-de/548eebe1-86c4-4377-b2f5-447cb8be3d90)   
 [MyBase \- löschen](http://msdn.microsoft.com/de-de/52491d06-6451-4f6f-9aa6-8fab59bbc2b9)