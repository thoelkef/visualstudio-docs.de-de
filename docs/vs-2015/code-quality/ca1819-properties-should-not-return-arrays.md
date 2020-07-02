---
title: 'CA1819: Eigenschaften sollten keine Arrays zurückgeben | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PropertiesShouldNotReturnArrays
- CA1819
helpviewer_keywords:
- PropertiesShouldNotReturnArrays
- CA1819
ms.assetid: 85fcf312-57f8-438a-8b10-34441fe0bdeb
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a96d2164cbd6c03cb0d191b2d0c3c4607468209c
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545326"
---
# <a name="ca1819-properties-should-not-return-arrays"></a>CA1819: Eigenschaften sollten keine Arrays zurückgeben.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|PropertiesShouldNotReturnArrays|
|CheckId|CA1819|
|Kategorie|Microsoft. Performance|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine öffentliche oder geschützte Eigenschaft in einem öffentlichen Typ gibt ein Array zurück.

## <a name="rule-description"></a>Beschreibung der Regel
 Arrays, die von Eigenschaften zurückgegeben werden, sind nicht schreibgeschützt, auch wenn die Eigenschaft schreibgeschützt ist. Damit das Array gegen Manipulationen geschützt bleibt, muss die Eigenschaft eine Kopie des Arrays zurückgeben. Normalerweise verstehen die Benutzer nicht, welche negativen Auswirkungen der Aufruf einer solchen Eigenschaft auf die Leistung hat. Insbesondere kann die-Eigenschaft als indizierte Eigenschaft verwendet werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, stellen Sie entweder die-Eigenschaft als Methode dar, oder ändern Sie die-Eigenschaft, um eine Auflistung zurückzugeben.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Attribute können Eigenschaften enthalten, die Arrays zurückgeben, aber keine Eigenschaften enthalten, die Auflistungen zurückgeben. Sie können eine Warnung unterdrücken, die für eine Eigenschaft eines Attributs ausgelöst wird, das von [System. Attribute] abgeleitet ist (<!-- TODO: review code entity reference <xref:assetId:///System.Attribute?qualifyHint=False&amp;autoUpgrade=True>  -->klassi. Andernfalls sollten Sie keine Warnung aus dieser Regel unterdrücken.

## <a name="example-violation"></a>Beispiel Verstoß

### <a name="description"></a>Beschreibung
 Das folgende Beispiel zeigt eine Eigenschaft, die gegen diese Regel verstößt.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Performance.PropertyArrayViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayViolation/cs/FxCop.Performance.PropertyArrayViolation.cs#1)]
 [!code-vb[FxCop.Performance.PropertyArrayViolation#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayViolation/vb/FxCop.Performance.PropertyArrayViolation.vb#1)]

### <a name="comments"></a>Kommentare
 Um einen Verstoß gegen diese Regel zu beheben, machen Sie die Eigenschaft zu einer Methode, oder ändern Sie die Eigenschaft so, dass eine Auflistung anstelle eines Arrays zurückgegeben wird.

## <a name="change-the-property-to-a-method-example"></a>Ändern der-Eigenschaft in ein Methoden Beispiel

### <a name="description"></a>Beschreibung
 Im folgenden Beispiel wird die Verletzung behoben, indem die-Eigenschaft in eine-Methode geändert wird.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Performance.PropertyArrayFixedMethod#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayFixedMethod/cs/FxCop.Performance.PropertyArrayFixedMethod.cs#1)]
 [!code-vb[FxCop.Performance.PropertyArrayFixedMethod#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayFixedMethod/vb/FxCop.Performance.PropertyArrayFixedMethod.vb#1)]

## <a name="return-a-collection-example"></a>Beispiel für eine Auflistung zurückgeben

### <a name="description"></a>Beschreibung
 Im folgenden Beispiel wird die Verletzung behoben, indem die-Eigenschaft geändert wird, um eine

 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Performance.PropertyArrayFixedCollection#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayFixedCollection/cs/FxCop.Performance.PropertyArrayFixedCollection.cs#1)]
 [!code-vb[FxCop.Performance.PropertyArrayFixedCollection#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayFixedCollection/vb/FxCop.Performance.PropertyArrayFixedCollection.vb#1)]

## <a name="allowing-users-to-modify-a-property"></a>Benutzern das Ändern einer Eigenschaft gestatten

### <a name="description"></a>Beschreibung
 Möglicherweise möchten Sie dem Consumer der-Klasse gestatten, eine Eigenschaft zu ändern. Das folgende Beispiel zeigt eine Lese-/Schreibeigenschaft, die gegen diese Regel verstößt.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Performance.PropertyModifyViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyModifyViolation/cs/FxCop.Performance.PropertyModifyViolation.cs#1)]
 [!code-vb[FxCop.Performance.PropertyModifyViolation#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyModifyViolation/vb/FxCop.Performance.PropertyModifyViolation.vb#1)]

### <a name="comments"></a>Kommentare
 Im folgenden Beispiel wird die Verletzung behoben, indem die-Eigenschaft geändert wird, um einen zurückzugeben <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName> .

### <a name="code"></a>Code
 [!code-csharp[FxCop.Performance.PropertyModifyFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyModifyFixed/cs/FxCop.Performance.PropertyModifyFixed.cs#1)]
 [!code-vb[FxCop.Performance.PropertyModifyFixed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyModifyFixed/vb/FxCop.Performance.PropertyModifyFixed.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1024: Nach Möglichkeit Eigenschaften verwenden.](../code-quality/ca1024-use-properties-where-appropriate.md)
