---
title: "Die Datentypen der Typparameter k&#246;nnen nicht von diesen Argumenten abgeleitet werden, da mehrere Typen m&#246;glich sind | Microsoft Docs"
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
  - "vbc36653"
  - "bc36653"
  - "vbc36650"
  - "bc36650"
helpviewer_keywords: 
  - "BC36650"
  - "BC36650"
ms.assetid: 79287e1f-7070-4a71-96d2-aee0a0c9d8bd
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die Datentypen der Typparameter k&#246;nnen nicht von diesen Argumenten abgeleitet werden, da mehrere Typen m&#246;glich sind
Die Datentypen der Typparameter können nicht von diesen Argumenten abgeleitet werden, da mehrere Typen möglich sind. Sie können diesen Fehler möglicherweise beheben, indem Sie die Datentypen explizit angeben.  
  
 Dieser Fehler tritt auf, wenn bei der Überladungsauflösung ein Fehler auftritt. Er wird als untergeordnete Meldung angezeigt, die den Grund für die Entfernung eines bestimmten Überladungskandidaten angibt. Der Fehler erläutert, dass der Compiler bei Anwendung von Typrückschluss zur Bestimmung des Datentyps der Typparameter der aufgerufenen generischen Prozedur mehr als einen möglichen Datentyp für mindestens einen davon findet.  
  
> [!NOTE]
>  Wenn die Angabe von Argumenten keine Option ist \(z. B. für Abfrageoperatoren in Abfrageausdrücken\), wird nur der erste Satz der Fehlermeldung angezeigt.  
  
 Weitere Informationen und Beispiele finden Sie unter [Die Datentypen der Typparameter in der Methode \<Methodenname\> können nicht von diesen Argumenten abgeleitet werden, da mehrere Typen möglich sind.](../misc/data-type-s-of-the-type-parameter-s-in-method-methodname-cannot-be-inferred-from-these-arguments-because-more-than-one-type-is-possible.md).  
  
 **Fehler\-ID:** BC36653 und BC36650  
  
## Siehe auch  
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Overload Resolution](/dotnet/visual-basic/programming-guide/language-features/procedures/overload-resolution)