---
title: 'CA1008: Enumerationen müssen aufweisen Nullwert | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1008
- EnumsShouldHaveZeroValue
helpviewer_keywords:
- CA1008
- EnumsShouldHaveZeroValue
ms.assetid: 3503a73c-360c-416d-8ee4-c2aa44365a05
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: af0b742c42dae829c0e066babf77494f612e8908
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="ca1008-enums-should-have-zero-value"></a>CA1008: Enumerationen müssen einen Wert von 0 (null) aufweisen
|||  
|-|-|  
|TypeName|EnumsShouldHaveZeroValue|  
|CheckId|CA1008|  
|Kategorie|Microsoft.Design|  
|Unterbrechende Änderung|Nicht unterbrechend – Wenn Sie, zum Hinzufügen aufgefordert werden einer **keine** Wert, der eine Flagenumeration. Unterbrechend – Wenn Sie aufgefordert werden, umbenennen oder entfernen alle Enumerationswerte.|  
  
## <a name="cause"></a>Ursache  
 Eine Enumeration angewendet <xref:System.FlagsAttribute?displayProperty=fullName> definiert einen Member mit dem Wert 0 (null); oder eine Enumeration, die eine angewendet wurde keine <xref:System.FlagsAttribute> definiert ein Element mit dem Wert 0 (null), aber der Name ist nicht "None" oder die Enumeration definiert mehrere NULL-Werten Elemente.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Der Standardwert einer nicht initialisierten Enumeration ist wie der anderer Werttypen ist 0 (null). Eine Enumeration nicht Flags-Attribut sollte einen Member definieren, mit dem Wert 0 (null), damit der Standardwert ein gültiger Wert der Enumeration ist. Bei Bedarf, benennen Sie das Element "None". Ordnen Sie andernfalls 0 (null), auf die am häufigsten verwendeten Member. Beachten Sie, dass, standardmäßig, wenn der Wert des ersten Elements der Enumeration in der Deklaration nicht festgelegt ist der Wert 0 (null).  
  
 Wenn eine Enumeration, wird die <xref:System.FlagsAttribute> angewendet definiert ein NULL-Werten-Element, seinen Namen muss 'None', um anzugeben, in der Enumeration keine Werte festgelegt wurden. Verwenden einen NULL-Member für andere Zwecke entgegen die Verwendung von ist das <xref:System.FlagsAttribute> , den AND-Operator und bitweise Operatoren sind nutzlos, mit dem Element. Dies bedeutet, dass nur ein Member den Wert 0 (null) zugewiesen werden soll. Beachten Sie, dass mehrere Elemente haben, die der Wert 0 (null) in einer Enumeration Flags-Attribut auftreten `Enum.ToString()` gibt falsche Ergebnisse für Elemente, die nicht 0 (null) zurück.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel für nicht-Enumerationen zu beheben, definieren Sie ein Element mit dem Wert 0 (null); Dies ist eine nicht unterbrechende Änderung. Namen Sie für Enumerationen, die einen NULL-Member definieren dieser Member den "None", und löschen Sie anderer Elemente, die den Wert Null aufweisen; Dies ist eine unterbrechende Änderung.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel, mit Ausnahme von Enumerationen, die zuvor versendet habe.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt zwei Enumerationen, die die Regel erfüllen, und eine Enumeration `BadTraceOptions`, die die Regel verletzt.  
  
 [!code-cpp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CPP/ca1008-enums-should-have-zero-value_1.cpp)]
 [!code-csharp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CSharp/ca1008-enums-should-have-zero-value_1.cs)]
 [!code-vb[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/VisualBasic/ca1008-enums-should-have-zero-value_1.vb)]  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA2217: Enumerationen nicht mit FlagsAttribute markieren](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
 [CA1700: Enumerationswerte nicht mit "Reserviert" benennen](../code-quality/ca1700-do-not-name-enum-values-reserved.md)  
  
 [CA1712: Keine Typnamen als Präfixe für Enumerationswerte verwenden](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)  
  
 [CA1028: Der Enumerationsspeicher sollte Int32 sein.](../code-quality/ca1028-enum-storage-should-be-int32.md)  
  
 [CA1027: Enumerationen mit FlagsAttribute markieren](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Enum?displayProperty=fullName>