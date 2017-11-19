---
title: 'CA1307: StringComparison angeben | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1307
- SpecifyStringComparison
helpviewer_keywords:
- CA1307
- SpecifyStringComparison
ms.assetid: 9b0d5e71-1683-4a0d-bc4a-68b2fbd8af71
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 61d8ca557bfc55e3488a35e82f0242f931c51ed4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ca1307-specify-stringcomparison"></a>CA1307: StringComparison angeben
|||  
|-|-|  
|TypeName|SpecifyStringComparison|  
|CheckId|CA1307|  
|Kategorie|Microsoft.Globalization|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## <a name="cause"></a>Ursache  
 Ein Zeichenfolgenvergleich verwendet eine methodenüberladung, die nicht festgelegt, wird eine <xref:System.StringComparison> Parameter.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Viele Zeichenfolgenoperationen, vor allem die <xref:System.String.Compare%2A> und <xref:System.String.Equals%2A> dienen, eine Überladung, akzeptiert eine <xref:System.StringComparison> -Enumerationswert als Parameter.  
  
 Wenn eine Überladung vorhanden ist, nimmt ein <xref:System.StringComparison> Parameter, es sollte verwendet werden, anstatt eine Überladung, die keine dieser Parameter akzeptiert. Durch diesen Parameter explizit festlegen, ist der Code häufig verständlicher und einfacher zu verwalten.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie Methoden zum Zeichenfolgenvergleich für Überladungen, die akzeptieren der <xref:System.StringComparison> -Enumeration als Parameter. Zum Beispiel: Ändern Sie `String.Compare(str1, str2)` auf `String.Compare(str1, str2, StringComparison.Ordinal)`.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Sie können ruhig auf eine Warnung dieser Regel zu unterdrücken, wenn die Bibliothek oder Anwendung für eine begrenzte lokale Zielgruppe bestimmt ist, und daher nicht lokalisiert werden wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Globalisierungswarnungen](../code-quality/globalization-warnings.md)   
 [CA1309: Ordinal-StringComparison verwenden](../code-quality/ca1309-use-ordinal-stringcomparison.md)