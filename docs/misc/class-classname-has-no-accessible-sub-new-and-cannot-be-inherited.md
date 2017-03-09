---
title: "Die &lt;Klassenname&gt;-Klasse hat kein zugreifbares &quot;Sub New&quot; und kann nicht geerbt werden. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31399"
  - "BC31399"
helpviewer_keywords: 
  - "BC31399"
ms.assetid: 035b333f-ff6a-4fc4-bd36-82f40b1d8bab
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die &lt;Klassenname&gt;-Klasse hat kein zugreifbares &quot;Sub New&quot; und kann nicht geerbt werden.
Eine Klasse verwendet eine [Inherits Statement](/dotnet/visual-basic/language-reference/statements/inherits-statement), um eine Basisklasse anzugeben, kann jedoch auf keinen Konstruktor in der beabsichtigten Basisklasse zugreifen.  
  
 Dies kann geschehen, wenn die beabsichtigte Basisklasse keine Konstruktoren oder Konstruktoren mit Zugriffsebenen aufweist, die den Zugriff von einer anderen Klasse verhindern.  
  
 Wenn Sie eine Klasse erben, sollte Ihr Konstruktor den Basisklassenkonstruktor mit [MyBase \- delete](http://msdn.microsoft.com/de-de/52491d06-6451-4f6f-9aa6-8fab59bbc2b9) aufrufen. Wenn Sie diesen Aufruf nicht ausführen oder auch keinen expliziten Konstruktor schreiben, generiert Visual Basic einen impliziten Konstruktor, der `MyBase.New()` aufruft.  
  
 **Fehler\-ID:** BC31399  
  
### So beheben Sie diesen Fehler  
  
1.  Wenn die beabsichtigte Basisklasse der Quellcodeverwaltung unterliegt, ändern Sie die Zugriffsebene mindestens eines ihrer Konstruktoren, damit eine andere Klasse darauf zugreifen kann.  
  
2.  Wenn Sie die Zugriffsebenen der Konstruktoren der beabsichtigten Basisklasse nicht ändern können, sollte die Vererbung von einer anderen Klasse oder gar nicht erfolgen.  
  
## Siehe auch  
 [Inherits Statement](/dotnet/visual-basic/language-reference/statements/inherits-statement)   
 [Inheritance Basics](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)   
 [MyBase \- delete](http://msdn.microsoft.com/de-de/52491d06-6451-4f6f-9aa6-8fab59bbc2b9)   
 [New Operator](/dotnet/visual-basic/language-reference/operators/new-operator)   
 [Access Levels in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/access-levels)