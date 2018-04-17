---
title: 'CA1027: Enumerationen mit FlagsAttribute markieren | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- MarkEnumsWithFlags
- CA1027
helpviewer_keywords:
- CA1027
- MarkEnumsWithFlags
ms.assetid: 249e882c-8cd1-4c00-a2de-7b6bdc1849ff
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 702bc45001f1d545fab6e6a3d54d58b552408402
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="ca1027-mark-enums-with-flagsattribute"></a>CA1027: Enumerationen mit FlagsAttribute markieren
|||  
|-|-|  
|TypeName|MarkEnumsWithFlags|  
|CheckId|CA1027|  
|Kategorie|Microsoft.Design|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## <a name="cause"></a>Ursache  
 Die Werte für eine öffentliche Enumeration sind Potenzen von 2 oder Kombinationen aus anderen Werten, die in der Enumeration definiert sind und die <xref:System.FlagsAttribute?displayProperty=fullName> -Attribut nicht vorhanden ist. Um falsch positive Ergebnisse zu reduzieren, meldet diese Regel keinen Verstoß bei Enumerationen, die zusammenhängende Werte aufweisen.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Eine Enumeration ist ein Werttyp, der einen Satz verwandter benannter Konstanten definiert. Anwenden <xref:System.FlagsAttribute> auf eine Enumeration, wenn deren benannten Konstanten sinnvoll kombiniert werden können. Betrachten Sie beispielsweise eine Enumeration der Tage der Woche in einer Anwendung, die überwacht die Tag-Ressourcen verfügbar sind. Wenn die Verfügbarkeit von jeder Ressource codiert ist, indem Sie die Enumeration mit ab <xref:System.FlagsAttribute> vorhanden, eine beliebige Kombination von Tagen dargestellt werden kann. Ohne das Attribut kann nur einen Tag der Woche dargestellt werden.  
  
 Für Felder, in denen kombinierbare Enumerationen gespeichert werden, werden die einzelnen Enumerationswerte als Gruppen von Bits in das Feld behandelt. Aus diesem Grund diese Felder werden manchmal als bezeichnet *Bitfelder*. Enumerationswerte für die Speicherung in einem Bitfeld zu kombinieren, verwenden Sie die bedingten booleschen Operatoren. Testen ein Bitfeld, um zu bestimmen, ob ein bestimmte Enumerationswert vorhanden ist, verwenden Sie die booleschen logischen Operatoren. Für ein Bitfeld zum Speichern und Abrufen von kombinierten Enumerationswerte ordnungsgemäß muss jeder Wert, der in der Enumeration definiert ist, eine Potenz von zwei sein. Wenn dies zutrifft, werden die booleschen logischen Operatoren werden nicht zum Extrahieren von einzelnen Enumerationswerte, die in das Feld gespeichert werden.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, fügen <xref:System.FlagsAttribute> der Enumeration.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie eine Warnung dieser Regel, wenn Sie nicht, dass die Enumerationswerte kombinierbar sein möchten.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel `DaysEnumNeedsFlags` ist eine Enumeration, die die Anforderungen für die Verwendung von erfüllt <xref:System.FlagsAttribute>, jedoch verfügt nicht über. Die `ColorEnumShouldNotHaveFlag` -Enumeration weist keine Werte, die Potenzen von 2 sind, jedoch gibt fälschlicherweise an <xref:System.FlagsAttribute>. Dies verstößt gegen die Regel [CA2217: Enumerationen mit FlagsAttribute markieren](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md).  
  
 [!code-csharp[FxCop.Design.EnumFlags#1](../code-quality/codesnippet/CSharp/ca1027-mark-enums-with-flagsattribute_1.cs)]  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA2217: Enumerationen nicht mit FlagsAttribute markieren](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.FlagsAttribute?displayProperty=fullName>