---
title: "Die Datentypen der Typparameter k&#246;nnen nicht von diesen Argumenten abgeleitet werden, da sie nicht in denselben Typ konvertiert werden | Microsoft Docs"
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
  - "vbc36659"
  - "bc36659"
  - "vbc36656"
  - "bc36656"
helpviewer_keywords: 
  - "BC36659"
  - "BC36656"
ms.assetid: 0aa809da-3b44-4d78-b3c5-0a148bdf7ce8
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die Datentypen der Typparameter k&#246;nnen nicht von diesen Argumenten abgeleitet werden, da sie nicht in denselben Typ konvertiert werden
Die Datentypen der Typparameter können nicht von diesen Argumenten abgeleitet werden, da sie nicht in denselben Typ konvertiert werden. Sie können diesen Fehler möglicherweise beheben, indem Sie die Datentypen explizit angeben.  
  
 Dieser Fehler tritt auf, wenn die Überladungsauflösung fehlgeschlagen ist. Er wird als untergeordnete Meldung angezeigt, die den Grund für die Entfernung einer bestimmten Überladung angibt. Es wird erläutert, dass der Compiler nicht mithilfe des Typrückschlusses nach Datentypen für die Typparameter suchen kann, die mit den Argumenten kompatibel sind.  
  
> [!NOTE]
>  Wenn die Angabe von Argumenten keine Option ist \(z. B. für Abfrageoperatoren in Abfrageausdrücken\), wird nur der erste Satz der Fehlermeldung angezeigt.  
  
 Weitere Informationen und Beispiele finden Sie unter [Die Datentypen der Typparameter in der '\<Methodenname\>'\-Methode können nicht von diesen Argumenten abgeleitet werden, da sie nicht in denselben Typ konvertiert werden.](../misc/data-type-s-of-the-type-parameter-s-in-method-methodname-cannot-be-inferred-from-these-arguments-because-they-do-not-convert-to-the-same-type.md).  
  
 **Fehler\-ID:** BC36659 und BC36656  
  
## Siehe auch  
 [Relaxed Delegate Conversion](/dotnet/visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion)   
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Overload Resolution](/dotnet/visual-basic/programming-guide/language-features/procedures/overload-resolution)