---
title: 'CA1819: Eigenschaften sollten keine Arrays zurückgeben.'
ms.date: 03/11/2019
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
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 2824be0ecc29965abb68519aaa8eb8a83af8e688
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65841382"
---
# <a name="ca1819-properties-should-not-return-arrays"></a>CA1819: Eigenschaften sollten keine Arrays zurückgeben.

|||
|-|-|
|TypeName|PropertiesShouldNotReturnArrays|
|CheckId|CA1819|
|Kategorie|Microsoft.Performance|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Eine Eigenschaft gibt ein Array zurück.

Diese Regel nur sucht standardmäßig an extern sichtbare Eigenschaften und Typen. Dies ist jedoch [konfigurierbare](#configurability).

## <a name="rule-description"></a>Regelbeschreibung

Von Eigenschaften zurückgegebene Arrays sind nicht schreibgeschützt, selbst wenn die Eigenschaft schreibgeschützt ist. Damit das Array gegen Manipulationen geschützt bleibt, muss die Eigenschaft eine Kopie des Arrays zurückgeben. In der Regel werden Benutzer nicht negativen Leistungseinbußen bei der Aufruf einer solchen Eigenschaft verstehen. Insbesondere können sie die Eigenschaft als eine indizierte Eigenschaft.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, stellen Sie der Eigenschaft eine Methode oder ändern Sie die Eigenschaft zum Zurückgeben einer Auflistung.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Sie können eine Warnung, die für eine Eigenschaft eines Attributs ausgelöst wird, das von abgeleitet ist Unterdrücken der <xref:System.Attribute> Klasse. Attribute können Eigenschaften enthalten, die Arrays zurückgeben, aber Sie können keine Eigenschaften enthalten, die Auflistungen zurückgeben.

Sie können die Warnung unterdrücken, wenn die Eigenschaft Teil ist eine [Data Transfer Object (DTO)](/previous-versions/msp-n-p/ff649585(v=pandp.10)) Klasse.

Unterdrücken Sie andernfalls keine Warnung dieser Regel.

## <a name="configurability"></a>Konfigurierbarkeit

Wenn Sie diese Regel aus ausführen, [FxCop-Analysen](install-fxcop-analyzers.md) (und nicht über die Analyse von statischem Code), können Sie konfigurieren, welche Teile Ihrer Codebasis, um die Ausführung dieser Regel auf, um basierend auf deren Barrierefreiheit. Z. B. um anzugeben, dass die Regel nur für die nicht öffentlichen API-Oberfläche ausgeführt werden soll, fügen Sie die folgenden Schlüssel-Wert-Paar in einer editorconfig-Datei in Ihrem Projekt:

```ini
dotnet_code_quality.ca1819.api_surface = private, internal
```

Sie können diese Option, die für diese eine Regel, für alle Regeln oder für alle Regeln in dieser Kategorie (Leistung) konfigurieren. Weitere Informationen finden Sie unter [konfigurieren FxCop-Analysetools](configure-fxcop-analyzers.md).

## <a name="example-violation"></a>Beispiel für einen Verstoß

Das folgende Beispiel zeigt eine Eigenschaft, die gegen diese Regel verstößt:

[!code-csharp[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_1.cs)]
[!code-vb[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_1.vb)]

Um einen Verstoß gegen diese Regel zu beheben, stellen Sie der Eigenschaft eine Methode oder ändern Sie die Eigenschaft zum Zurückgeben einer Auflistung anstelle eines Arrays zu.

### <a name="change-the-property-to-a-method"></a>Ändern Sie die Eigenschaft an eine Methode

Im folgende Beispiel wird der Verstoß durch Ändern der Eigenschaft an eine Methode korrigiert:

[!code-vb[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_2.vb)]
[!code-csharp[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_2.cs)]

### <a name="change-the-property-to-return-a-collection"></a>Ändern Sie die Eigenschaft zum Zurückgeben einer Auflistung

Im folgenden Beispiel wird der Verstoß korrigiert, durch Ändern der Eigenschaft zum Zurückgeben einer <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>:

[!code-csharp[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_3.cs)]
[!code-vb[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_3.vb)]

## <a name="allow-users-to-modify-a-property"></a>Ermöglichen Sie Benutzern das Ändern einer Eigenschaft

Sie möchten die Consumer der-Klasse zum Ändern einer Eigenschaft zu ermöglichen. Das folgende Beispiel zeigt eine Lese-/Schreibeigenschaft, die gegen diese Regel verstößt:

[!code-csharp[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_4.cs)]
[!code-vb[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_4.vb)]

Im folgenden Beispiel wird der Verstoß korrigiert, durch Ändern der Eigenschaft zum Zurückgeben einer <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>:

[!code-vb[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_5.vb)]
[!code-csharp[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_5.cs)]

## <a name="related-rules"></a>Verwandte Regeln

- [CA1024: Verwenden Sie Eigenschaften](../code-quality/ca1024-use-properties-where-appropriate.md)