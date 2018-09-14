---
title: 'CA1819: Eigenschaften sollten keine Arrays zurückgeben'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PropertiesShouldNotReturnArrays
- CA1819
helpviewer_keywords:
- PropertiesShouldNotReturnArrays
- CA1819
ms.assetid: 85fcf312-57f8-438a-8b10-34441fe0bdeb
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 68f64d37a7616f095a86452353edc498d2d27f28
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/13/2018
ms.locfileid: "45549416"
---
# <a name="ca1819-properties-should-not-return-arrays"></a>CA1819: Eigenschaften sollten keine Arrays zurückgeben

|||
|-|-|
|TypeName|PropertiesShouldNotReturnArrays|
|CheckId|CA1819|
|Kategorie|Microsoft.Performance|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine öffentliche oder geschützte Eigenschaft in einem öffentlichen Typ zurückgegeben ein Array.

## <a name="rule-description"></a>Regelbeschreibung
 Von Eigenschaften zurückgegebene Arrays sind nicht schreibgeschützt, selbst wenn die Eigenschaft schreibgeschützt ist. Damit das Array gegen Manipulationen geschützt bleibt, muss die Eigenschaft eine Kopie des Arrays zurückgeben. Normalerweise verstehen die Benutzer nicht, welche negativen Auswirkungen der Aufruf einer solchen Eigenschaft auf die Leistung hat. Insbesondere können sie die Eigenschaft als eine indizierte Eigenschaft.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, stellen Sie der Eigenschaft eine Methode oder ändern Sie die Eigenschaft zum Zurückgeben einer Auflistung.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Attribute können Eigenschaften enthalten, die Arrays zurückgeben, aber Sie können keine Eigenschaften enthalten, die Auflistungen zurückgeben. Sie können eine Warnung, die für eine Eigenschaft eines Attributs ausgelöst wird, das von abgeleitet ist Unterdrücken der <xref:System.Attribute> Klasse. Unterdrücken Sie andernfalls keine Warnung dieser Regel.

## <a name="example-violation"></a>Beispiel für einen Verstoß

### <a name="description"></a>Beschreibung
 Das folgende Beispiel zeigt eine Eigenschaft, die gegen diese Regel verstößt.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_1.cs)]
 [!code-vb[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_1.vb)]

### <a name="comments"></a>Kommentare
 Um einen Verstoß gegen diese Regel zu beheben, stellen Sie der Eigenschaft eine Methode oder ändern Sie die Eigenschaft zum Zurückgeben einer Auflistung anstelle eines Arrays zu.

## <a name="change-the-property-to-a-method-example"></a>Ändern Sie die Eigenschaft in einer Methode – Beispiel

### <a name="description"></a>Beschreibung
 Im folgende Beispiel wird der Verstoß durch Ändern der Eigenschaft an eine Methode korrigiert.

### <a name="code"></a>Code
 [!code-vb[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_2.vb)]
 [!code-csharp[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_2.cs)]

## <a name="return-a-collection-example"></a>Ein Beispiel für die Sammlung zurück

### <a name="description"></a>Beschreibung
 Im folgenden Beispiel wird der Verstoß korrigiert, durch Ändern der Eigenschaft zum Zurückgeben einer

 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>

### <a name="code"></a>Code
 [!code-csharp[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_3.cs)]
 [!code-vb[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_3.vb)]

## <a name="allowing-users-to-modify-a-property"></a>Benutzer zum Ändern einer Eigenschaft

### <a name="description"></a>Beschreibung
 Sie möchten die Consumer der-Klasse zum Ändern einer Eigenschaft zu ermöglichen. Das folgende Beispiel zeigt eine Lese-/Schreibeigenschaft, die gegen diese Regel verstößt.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_4.cs)]
 [!code-vb[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_4.vb)]

### <a name="comments"></a>Kommentare
 Im folgenden Beispiel wird der Verstoß korrigiert, durch Ändern der Eigenschaft zum Zurückgeben einer <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>.

### <a name="code"></a>Code
 [!code-vb[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_5.vb)]
 [!code-csharp[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_5.cs)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1024: Nach Möglichkeit Eigenschaften verwenden](../code-quality/ca1024-use-properties-where-appropriate.md)