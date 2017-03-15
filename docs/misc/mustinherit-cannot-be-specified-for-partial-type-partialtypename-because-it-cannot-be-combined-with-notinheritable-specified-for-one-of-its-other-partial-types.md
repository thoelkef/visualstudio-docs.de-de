---
title: "&#39;MustInherit&#39; kann nicht f&#252;r den partiellen Typ &#39;&lt;partialtypename&gt;&#39; angegeben werden, da &#39;NotInheritable&#39; f&#252;r einen der anderen partiellen Typen angegeben wurde und eine Kombination nicht m&#246;glich ist. | Microsoft Docs"
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
  - "vbc30926"
  - "BC30926"
helpviewer_keywords: 
  - "BC30926"
ms.assetid: 59a0b5d9-f53c-4234-88f4-dfc66342f143
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;MustInherit&#39; kann nicht f&#252;r den partiellen Typ &#39;&lt;partialtypename&gt;&#39; angegeben werden, da &#39;NotInheritable&#39; f&#252;r einen der anderen partiellen Typen angegeben wurde und eine Kombination nicht m&#246;glich ist.
Eine Klasse ist in mehreren partiellen Deklarationen definiert, von denen eine `MustInherit` angibt, eine andere jedoch `NotInheritable`.  
  
 Wenn Sie die Definition einer Klasse auf mehrere partielle Deklarationen aufteilen, behandelt der Compiler die Klasse als die Vereinigungsmenge ihrer sämtlichen partiellen Deklarationen. Dies gilt nicht nur für die Member, sondern auch für die Implementierung, Vererbung und Zugriffsebene.  
  
 Eine Klasse kann nicht sowohl *abstrakt* als auch *versiegelt* sein, d. h. sie kann Vererbung nicht zugleich vorschreiben als auch verbieten. Daher können Sie nicht sowohl `MustInherit` als auch `NotInheritable` für die gleiche Klasse festlegen.  
  
 **Fehler\-ID:** BC30926  
  
### So beheben Sie diesen Fehler  
  
-   Entscheiden Sie, ob die Klasse Vererbung vorschreiben, sie verbieten oder keins von beidem soll, und entfernen Sie die Schlüsselwörter, die im Widerspruch zu dieser Entscheidung stehen.  
  
## Siehe auch  
 [Partial](/dotnet/visual-basic/language-reference/modifiers/partial)   
 [MustInherit](/dotnet/visual-basic/language-reference/modifiers/mustinherit)   
 [NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)   
 [Inheritance Basics](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)