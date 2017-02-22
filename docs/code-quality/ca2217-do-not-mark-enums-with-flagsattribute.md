---
title: "CA2217: Enumerationen nicht mit FlagsAttribute markieren | Microsoft Docs"
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
  - "DoNotMarkEnumsWithFlags"
  - "CA2217"
helpviewer_keywords: 
  - "CA2217"
  - "DoNotMarkEnumsWithFlags"
ms.assetid: 1b6f626c-66bf-45b0-a3e2-7c41ee9ceda7
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2217: Enumerationen nicht mit FlagsAttribute markieren
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotMarkEnumsWithFlags|  
|CheckId|CA2217|  
|Kategorie \(Category\)|Microsoft.Usage|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Eine extern sichtbare Enumeration wird mit <xref:System.FlagsAttribute> gekennzeichnet und weist einen oder mehrere Werte auf, die keine Potenzen von 2 oder keine Kombination von anderen in der Enumeration definierten Werten sind.  
  
## Regelbeschreibung  
 In einer Enumeration sollte <xref:System.FlagsAttribute> nur vorhanden sein, wenn jeder in der Enumeration definierte Wert eine Potenz von 2 oder eine Kombination definierter Werte ist.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie <xref:System.FlagsAttribute> aus der Enumeration.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## Beispiel  
 Das folgende Beispiel zeigt eine Enumeration Color, die den Wert 3 enthält, der weder eine Potenz von 2 noch eine Kombination aus den anderen definierten Werten ist.  Die Color\-Enumeration sollte nicht mit dem <xref:System.FlagsAttribute> gekennzeichnet werden.  
  
 [!code-cpp[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_1.cpp)]
 [!code-cs[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_1.cs)]
 [!code-vb[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_1.vb)]  
  
## Beispiel  
 Im folgenden Beispiel wird eine Enumeration Days veranschaulicht, die die Anforderungen zur Kennzeichnung mit dem System.FlagsAttribute erfüllt.  
  
 [!code-cpp[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_2.cpp)]
 [!code-cs[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_2.cs)]
 [!code-vb[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_2.vb)]  
  
## Verwandte Regeln  
 [CA1027: Enumerationen mit FlagsAttribute markieren](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
## Siehe auch  
 <xref:System.FlagsAttribute?displayProperty=fullName>