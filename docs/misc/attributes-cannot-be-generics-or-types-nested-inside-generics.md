---
title: "Attribute k&#246;nnen keine Generika oder in Generika geschachtelte Typen sein | Microsoft Docs"
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
  - "bc32067"
  - "vbc32067"
helpviewer_keywords: 
  - "BC32067"
ms.assetid: 93ae2848-0a72-4ae5-82a3-32e0a49bb7cd
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Attribute k&#246;nnen keine Generika oder in Generika geschachtelte Typen sein
Ein Attribut ist als generischer Typ oder innerhalb eines generischen Typs deklariert.  
  
 Visual Basic und .NET Framework unterstützen derzeit keine Kombination von Attributen und generischen Typen. Daher gelten die folgenden Einschränkungen:  
  
-   Ein Attribut kann kein generischer Typ sein und nicht in einem generischen Typ deklariert werden.  
  
-   Ein Attribut kann nicht von einer generischen Klasse erben, und eine generische Klasse kann nicht von einem Attribut erben.  
  
-   Wenn Sie ein Attribut anwenden, können Sie kein Argument angeben, auf das Folgendes zutrifft:  
  
    -   Ein generischer Typ  
  
    -   Aus einem generischen Typ erstellter Typ  
  
    -   Ein Typparameter eines enthaltenden Typs oder:  
  
    -   Aus einem Typparameter eines enthaltenden Typs erstellter Typ  
  
 **Fehler\-ID:** BC32067  
  
### So beheben Sie diesen Fehler  
  
-   Wenn die Attributdeklaration das Schlüsselwort `Of` und eine Typparameterliste enthält, entfernen Sie beide.  
  
-   Wenn die Attributdeklaration innerhalb eines generischen Typs auftritt, verschieben Sie sie an eine Position außerhalb von generischen Typen.  
  
## Siehe auch  
 <xref:System.Attribute>   
 [NICHT IM BUILD: Übersicht über Attribute in Visual Basic](http://msdn.microsoft.com/de-de/0d0cff64-892d-4f57-83bd-bef388553d4f)   
 [Generische Typen in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)