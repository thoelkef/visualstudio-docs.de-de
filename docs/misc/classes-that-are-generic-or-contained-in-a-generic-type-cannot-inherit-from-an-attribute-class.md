---
title: "Generische oder in einem generischen Typ enthaltene Klassen k&#246;nnen nicht von einer Attributklasse erben | Microsoft Docs"
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
  - "vbc32074"
  - "BC32074"
helpviewer_keywords: 
  - "BC32074"
ms.assetid: 3552ac98-d86a-4962-9d51-b9a8acc38ea1
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Generische oder in einem generischen Typ enthaltene Klassen k&#246;nnen nicht von einer Attributklasse erben
Eine Klasse, bei der es sich um eine generische Klasse handelt oder die in einem generischen Typ geschachtelt ist, gibt an, dass sie von einer Attributklasse erbt.  
  
 Visual Basic und .NET Framework unterstützen derzeit keine Kombination von Attributen und generischen Typen. Daher gelten die folgenden Einschränkungen:  
  
-   Ein Attribut kann kein generischer Typ sein und nicht in einem generischen Typ deklariert werden.  
  
-   Ein Attribut kann nicht von einer generischen Klasse erben, und eine generische Klasse kann nicht von einem Attribut erben.  
  
-   Wenn Sie ein Attribut anwenden, können Sie kein Attribut angeben, auf das Folgendes zutrifft:  
  
    -   Ein generischer Typ  
  
    -   Aus einem generischen Typ erstellter Typ  
  
    -   Ein Typparameter eines enthaltenden Typs oder:  
  
    -   Aus einem Typparameter eines enthaltenden Typs erstellter Typ  
  
 **Fehler\-ID:** BC32074  
  
### So beheben Sie diesen Fehler  
  
-   Ändern Sie die Basisklasse in eine andere Klasse als eine Attributklasse, oder entfernen Sie die `Inherits`\-Anweisung vollständig.  
  
## Siehe auch  
 <xref:System.Attribute>   
 [NICHT IM BUILD: Übersicht über Attribute in Visual Basic](http://msdn.microsoft.com/de-de/0d0cff64-892d-4f57-83bd-bef388553d4f)   
 [Generische Typen in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Inheritance Basics](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)   
 [Inherits Statement](/dotnet/visual-basic/language-reference/statements/inherits-statement)