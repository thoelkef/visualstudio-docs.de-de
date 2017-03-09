---
title: "Typparameter oder mit Typparametern konstruierte Typen sind in Attributargumenten nicht zul&#228;ssig | Microsoft Docs"
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
  - "BC32079"
  - "vbc32079"
helpviewer_keywords: 
  - "BC32079"
ms.assetid: 93eb59bd-e7db-4f73-a37f-405a83df48c1
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Typparameter oder mit Typparametern konstruierte Typen sind in Attributargumenten nicht zul&#228;ssig
Ein Attribut wird mit einem Argument angewendet, das einen Typparameter darstellt oder mithilfe eines Typparameters erstellt wird.  
  
 Visual Basic und .NET Framework unterstützen derzeit keine Kombination von Attributen und generischen Typen. Daher gelten die folgenden Einschränkungen:  
  
-   Ein Attribut kann kein generischer Typ sein und nicht in einem generischen Typ deklariert werden.  
  
-   Ein Attribut kann nicht von einer generischen Klasse erben, und eine generische Klasse kann nicht von einem Attribut erben.  
  
-   Wenn Sie ein Attribut anwenden, können Sie kein Argument angeben, auf das Folgendes zutrifft:  
  
    -   Ein generischer Typ  
  
    -   Aus einem generischen Typ erstellter Typ  
  
    -   Ein Typparameter eines enthaltenden Typs oder:  
  
    -   Aus einem Typparameter eines enthaltenden Typs erstellter Typ  
  
 **Fehler\-ID:** BC32079  
  
### So beheben Sie diesen Fehler  
  
-   Konstruieren Sie die für das Attribut angegebenen Argumente erneut so, dass sie keine Typparameter oder mithilfe von Typparametern konstruierte Typen enthalten.  
  
## Siehe auch  
 <xref:System.Attribute>   
 [NICHT IM BUILD: Übersicht über Attribute in Visual Basic](http://msdn.microsoft.com/de-de/0d0cff64-892d-4f57-83bd-bef388553d4f)   
 [Generische Typen in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)