---
title: "CA1309: Ordinal-StringComparison verwenden | Microsoft Docs"
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
  - "UseOrdinalStringComparison"
  - "CA1309"
helpviewer_keywords: 
  - "UseOrdinalStringComparison"
  - "CA1309"
ms.assetid: 19be0854-cb6e-4efd-a4c8-a5c1fc6f7a71
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1309: Ordinal-StringComparison verwenden
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseOrdinalStringComparison|  
|CheckId|CA1309|  
|Kategorie \(Category\)|Microsoft.Globalization|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Durch einen nicht linguistischen Zeichenfolgenvergleich wird der <xref:System.StringComparison>\-Parameter weder auf **Ordinal** noch auf **OrdinalIgnoreCase** festgelegt.  
  
## Regelbeschreibung  
 Viele Zeichenfolgenoperationen, vor allem die <xref:System.String.Compare%2A?displayProperty=fullName>\-Methode und die <xref:System.String.Equals%2A?displayProperty=fullName>\-Methode, bieten jetzt eine Überladung, durch die ein <xref:System.StringComparision?displayProperty=fullName>\-Enumerationswert als Parameter akzeptiert wird.  
  
 Wenn Sie **StringComparison.Ordinal** oder **StringComparison.OrdinalIgnoreCase** festlegen, ist der Zeichenfolgenvergleich nicht linguistisch.  Die für die natürliche Sprache spezifischen Features werden also ignoriert, wenn Vergleichsentscheidungen getroffen werden.  Die Entscheidungen basieren folglich auf einfachen Bytevergleichen, wobei Groß\-\/Kleinschreibung oder nach Kultur parametrisierte Entsprechungstabellen ignoriert werden.  Wenn der Parameter explizit auf **StringComparison.Ordinal** oder **StringComparison.OrdinalIgnoreCase** festgelegt wird, werden die Codeausführung beschleunigt sowie Richtigkeit und Zuverlässigkeit gesteigert.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie die Zeichenfolgenvergleichsmethode in eine Überladung, die die <xref:System.StringComparison?displayProperty=fullName>\-Enumeration als Parameter akzeptiert, und geben entweder **Ordinal** oder **OrdinalIgnoreCase** an.  Ändern Sie beispielsweise `String.Compare(str1, str2)` zu `String.Compare(str1, str2, StringComparison.Ordinal)`.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann gefahrlos unterdrückt werden, wenn die Bibliothek oder Anwendung für eine begrenzte lokale Zielgruppe bestimmt ist bzw. die Semantik der aktuellen Kultur verwendet werden sollte.  
  
## Siehe auch  
 [Globalisierungswarnungen](../code-quality/globalization-warnings.md)   
 [CA1307: StringComparison angeben](../code-quality/ca1307-specify-stringcomparison.md)