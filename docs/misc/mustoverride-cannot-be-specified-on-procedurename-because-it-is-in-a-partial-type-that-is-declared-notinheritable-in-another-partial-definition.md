---
title: "&#39;MustOverride&#39; kann f&#252;r &#39;&lt;prozedurname&gt;&#39; nicht angegeben werden, da es sich um einen partiellen Typ handelt, der in einer anderen partiellen Definition als &#39;NotInheritable&#39; deklariert ist. | Microsoft Docs"
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
  - "vbc30927"
  - "BC30927"
helpviewer_keywords: 
  - "BC30927"
ms.assetid: 5798dfda-3d7b-4f30-9715-40cbf52d6dc4
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;MustOverride&#39; kann f&#252;r &#39;&lt;prozedurname&gt;&#39; nicht angegeben werden, da es sich um einen partiellen Typ handelt, der in einer anderen partiellen Definition als &#39;NotInheritable&#39; deklariert ist.
Eine Prozedur oder Eigenschaft ist in einer Klasse, die in mehreren partiellen Deklarationen definiert ist, als `MustOverride` deklariert, aber eine der partiellen Definitionen legt für die Klasse `NotInheritable` fest.  
  
 Wenn Sie die Definition einer Klasse auf mehrere partielle Deklarationen aufteilen, behandelt der Compiler die Klasse als die Vereinigungsmenge ihrer sämtlichen partiellen Deklarationen. Dies gilt nicht nur für die Member, sondern auch für die Implementierung, Vererbung und Zugriffsebene.  
  
 Um eine Prozedur oder Eigenschaft zu überschreiben, muss eine Klasse sie von ihrer Basisklasse erben. Wenn Sie daher `MustOverride` für eine Prozedur oder Eigenschaft in einer Basisklasse angegeben möchten, müssen Sie für die Klasse `MustInherit` angeben. Da sie sich gegenseitig ausschließen, können Sie nicht zugleich `MustInherit` und `NotInheritable` für die gleiche Klasse angeben.  
  
 **Fehler\-ID:** BC30927  
  
### So beheben Sie diesen Fehler  
  
-   Wenn die Eigenschaft oder Prozedur überschrieben werden muss, entfernen Sie das Schlüsselwort `NotInheritable` aus der partiellen Deklaration, in der es auftritt.  
  
-   Wenn die Klasse `NotInheritable` sein muss, entfernen Sie das Schlüsselwort `MustOverride` aus der Prozedur oder Eigenschaft. Sie können sie nicht überschreiben, da sie die Klasse nicht erben können.  
  
## Siehe auch  
 [Partial](/dotnet/visual-basic/language-reference/modifiers/partial)   
 [MustOverride](/dotnet/visual-basic/language-reference/modifiers/mustoverride)   
 [MustInherit](/dotnet/visual-basic/language-reference/modifiers/mustinherit)   
 [NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)   
 [Inheritance Basics](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)