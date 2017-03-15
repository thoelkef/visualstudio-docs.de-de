---
title: "F&#252;r den &#39;&lt;Operatorsymbol&gt;&#39;-Operator werden Operanden vom Typ „Object“ verwendet. Dies kann Laufzeitfehler verursachen. | Microsoft Docs"
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
  - "BC42019"
  - "vbc42019"
helpviewer_keywords: 
  - "BC42019"
ms.assetid: f61944ba-863b-4a82-aae4-249bda52ec8d
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# F&#252;r den &#39;&lt;Operatorsymbol&gt;&#39;-Operator werden Operanden vom Typ „Object“ verwendet. Dies kann Laufzeitfehler verursachen.
Ein Ausdruck verwendet einen Operator, für den ein oder beide Operanden vom [Object Data Type](/dotnet/visual-basic/language-reference/data-types/object-data-type) sind.  
  
 Wenn eine Variable oder ein Ausdruck `Object` ergibt, muss der Compiler die *späte Bindung* durchführen, die zur Laufzeit zusätzliche Vorgänge verursacht. Sie setzt die Anwendung zudem möglichen Laufzeitfehlern aus. Angenommen, Sie weisen ein <xref:System.Windows.Forms.Form> zu einer `Object`\-Variable zu und versuchen dann, sie mit dem [\/ Operator](/dotnet/visual-basic/language-reference/operators/floating-point-division-operator) zu verwenden. In diesem Fall löst die Laufzeit eine <xref:System.InvalidCastException> aus, da Visual Basic ein <xref:System.Windows.Forms.Form>\-Objekt nicht in einen numerischen Wert konvertieren kann.  
  
 Standardmäßig ist diese Meldung eine Warnung. Informationen zum Ausblenden von Warnungen oder zum Behandeln von Warnungen als Fehler finden Sie unter [Konfigurieren von Warnungen in Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Fehler\-ID:** BC42019  
  
### So beheben Sie diesen Fehler  
  
-   Ordnen Sie nach Möglichkeit alle auszuwertenden Operanden zu Datentypen zu, für die der Operator definiert ist.  
  
## Siehe auch  
 [Arithmetic Operators in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators)