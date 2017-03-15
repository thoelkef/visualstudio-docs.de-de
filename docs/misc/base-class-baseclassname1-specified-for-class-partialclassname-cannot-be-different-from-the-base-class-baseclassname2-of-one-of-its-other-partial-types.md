---
title: "Die f&#252;r die Klasse &lt;Name der partiellen Klasse&gt; angegebene Basisklasse &lt;Basisklassenname1&gt; muss mit der Basisklasse &lt;Basisklassenname2&gt; eines der anderen partiellen Typen identisch sein. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BC30928"
  - "vbc30928"
helpviewer_keywords: 
  - "BC30928"
ms.assetid: da464f09-1016-4dec-beb7-3202cacd8e1e
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die f&#252;r die Klasse &lt;Name der partiellen Klasse&gt; angegebene Basisklasse &lt;Basisklassenname1&gt; muss mit der Basisklasse &lt;Basisklassenname2&gt; eines der anderen partiellen Typen identisch sein.
Eine Klasse wird in zwei oder mehr partiellen Deklarationen definiert, die mehr als eine [Inherits Statement](/dotnet/visual-basic/language-reference/statements/inherits-statement) enthalten, die mehr als eine Basisklasse angeben.  
  
 Wenn Sie die Definition einer Klasse zwischen mehreren partiellen Deklarationen aufteilen, behandelt der Compiler die Klasse als die Union all seiner partiellen Deklarationen. Dies gilt nicht nur für die Member, sondern auch für die Implementierung, Vererbung und Zugriffsebene.  
  
 Eine Klasse kann mehr als eine Schnittstelle implementieren, aber sie kann nur von einer Basisklasse erben. Aus diesem Grund müssen alle `Inherits`\-Anweisungen dieselbe Basisklasse angeben.  
  
 **Fehler\-ID:** BC30928  
  
### So beheben Sie diesen Fehler  
  
-   Entscheiden Sie, welche Klasse als Basisklasse der partiellen Klasse verwendet werden soll, und entfernen Sie alle `Inherits`\-Anweisungen, die andere Basisklassen angegeben, aus den partiellen Deklarationen.  
  
## Siehe auch  
 [Partial](/dotnet/visual-basic/language-reference/modifiers/partial)   
 [Inherits Statement](/dotnet/visual-basic/language-reference/statements/inherits-statement)   
 [Inheritance Basics](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)