---
title: "CA2101: Marshalling f&#252;r P/Invoke-Zeichenfolgenargumente festlegen | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SpecifyMarshalingForPInvokeStringArguments"
  - "CA2101"
helpviewer_keywords: 
  - "CA2101"
  - "SpecifyMarshalingForPInvokeStringArguments"
ms.assetid: 9d1abfc3-d320-41e0-9f6e-60cefe6ffe1b
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2101: Marshalling f&#252;r P/Invoke-Zeichenfolgenargumente festlegen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SpecifyMarshalingForPInvokeStringArguments|  
|CheckId|CA2101|  
|Kategorie \(Category\)|Microsoft.Globalization|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Ein Plattformaufrufmember lässt teilweise vertrauenswürdige Aufrufer zu, enthält einen Zeichenfolgenparameter und führt kein explizites Marshalling der Zeichenfolge durch.  
  
## Regelbeschreibung  
 Bei der Konvertierung von Unicode in ANSI können eventuell nicht alle Unicode\-Zeichen mit einer bestimmten ANSI\-Codepage dargestellt werden.  Dieses Problem soll durch die *optimale Zuordnung* gelöst werden, bei der das nicht darstellbare Zeichen durch ein Zeichen ersetzt wird.  Die Verwendung dieses Features stellt unter Umständen eine Sicherheitslücke dar, da Sie nicht bestimmen können, welches Zeichen ausgewählt wird.  Durch böswilligen Code könnte z. B. absichtlich eine Unicode\-Zeichenfolge mit Zeichen erstellt werden, die auf einer bestimmten Codepage nicht enthalten sind und die in dateisystemspezifische Zeichen wie '..' oder '\/' konvertiert werden.  Beachten Sie auch, dass Sicherheitsüberprüfungen bei Sonderzeichen häufig vor der Konvertierung der Zeichenfolge in ANSI erfolgen.  
  
 Die optimale Zuordnung ist die Standardeinstellung für die nicht verwaltete Konvertierung von WChar in MByte.  Wenn Sie die optimale Zuordnung nicht explizit deaktivieren, kann der Code aufgrund dieses Problems eine ausnutzbare Sicherheitslücke enthalten.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, führen Sie ein explizites Marshalling von Zeichenfolgendatentypen aus.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## Beispiel  
 Das folgende Beispiel zeigt eine Methode, die gegen diese Regel verstößt. Danach wird dargestellt, wie der Verstoß behoben wird.  
  
 [!code-cs[FxCop.Security.PinvokeAnsiUnicode#1](../code-quality/codesnippet/CSharp/ca2101-specify-marshaling-for-p-invoke-string-arguments_1.cs)]