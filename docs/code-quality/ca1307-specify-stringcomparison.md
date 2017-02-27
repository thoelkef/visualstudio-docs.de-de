---
title: "CA1307: StringComparison angeben | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1307"
  - "SpecifyStringComparison"
helpviewer_keywords: 
  - "CA1307"
  - "SpecifyStringComparison"
ms.assetid: 9b0d5e71-1683-4a0d-bc4a-68b2fbd8af71
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# CA1307: StringComparison angeben
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SpecifyStringComparison|  
|CheckId|CA1307|  
|Kategorie \(Category\)|Microsoft.Globalization|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Ein Zeichenfolgenvergleich verwendet eine Methodenüberladung, durch die kein <xref:System.StringComparison>\-Parameter festgelegt wird.  
  
## Regelbeschreibung  
 Viele Zeichenfolgenoperationen, vor allem die <xref:System.String.Compare%2A>\-Methode und die <xref:System.String.Equals%2A>\-Methode, bieten eine Überladung, durch die ein <xref:System.StringComparison>\-Enumerationswert als Parameter akzeptiert wird.  
  
 Sobald eine Überladung vorhanden ist, die einen <xref:System.StringComparison>\-Parameter akzeptiert, sollte sie anstelle einer Überladung verwendet werden, die diesen Parameter nicht akzeptiert.  Wenn Sie diesen Parameter explizit festlegen, ist der Code häufig verständlicher und leichter zu verwalten.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie die Zeichenfolgenvergleichsmethoden in Überladungen, die die <xref:System.StringComparison>\-Enumeration als Parameter akzeptieren.  Beispiel: Ändern Sie `String.Compare(str1, str2)` in `String.Compare(str1, str2, StringComparison.Ordinal)`.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann gefahrlos unterdrückt werden, wenn die Bibliothek oder Anwendung für eine begrenzte lokale Zielgruppe bestimmt ist und deshalb nicht lokalisiert wird.  
  
## Siehe auch  
 [Globalisierungswarnungen](../code-quality/globalization-warnings.md)   
 [CA1309: Ordinal\-StringComparison verwenden](../code-quality/ca1309-use-ordinal-stringcomparison.md)