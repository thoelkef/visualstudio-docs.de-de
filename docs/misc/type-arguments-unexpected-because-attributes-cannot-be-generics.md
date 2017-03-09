---
title: "Unerwartete Typargumente, da Attribute nicht generisch sein k&#246;nnen. | Microsoft Docs"
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
  - "bc32066"
  - "vbc32066"
helpviewer_keywords: 
  - "BC32066"
ms.assetid: cd43a92c-33fb-4def-bbf7-527d21bff93c
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Unerwartete Typargumente, da Attribute nicht generisch sein k&#246;nnen.
Ein Attribut wird mithilfe einer Liste der Argumenttypen angewendet.  
  
 Visual Basic und .NET Framework unterstützen derzeit keine Kombination von Attributen und generischen Typen. Daher gelten die folgenden Einschränkungen:  
  
-   Ein Attribut kann kein generischer Typ sein und nicht in einem generischen Typ deklariert werden.  
  
-   Ein Attribut kann nicht von einer generischen Klasse erben, und eine generische Klasse kann nicht von einem Attribut erben.  
  
-   Wenn Sie ein Attribut anwenden, können Sie kein Argument angeben, auf das Folgendes zutrifft:  
  
    -   Ein generischer Typ  
  
    -   Aus einem generischen Typ erstellter Typ  
  
    -   Ein Typparameter eines enthaltenden Typs oder:  
  
    -   Aus einem Typparameter eines enthaltenden Typs erstellter Typ  
  
 **Fehler\-ID:** BC32066  
  
### So beheben Sie diesen Fehler  
  
-   Wenn die Typargumente normale Argumente sein sollen, entfernen Sie das `Of`\-Schlüsselwort. Hierdurch wird die Typargumentliste in eine normale Argumentliste umgewandelt.  
  
-   Wenn die Typargumente für Typparameter angegeben werden sollen, entfernen Sie das `Of`\-Schlüsselwort und alle Typargumente. Ein Attribut kann keine Typargumente akzeptieren.  
  
## Siehe auch  
 <xref:System.Attribute>   
 [NICHT IM BUILD: Übersicht über Attribute in Visual Basic](http://msdn.microsoft.com/de-de/0d0cff64-892d-4f57-83bd-bef388553d4f)   
 [Generische Typen in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)