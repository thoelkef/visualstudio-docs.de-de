---
title: 'CA1819: Eigenschaften sollten keine Arrays zurückgeben | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- PropertiesShouldNotReturnArrays
- CA1819
helpviewer_keywords:
- PropertiesShouldNotReturnArrays
- CA1819
ms.assetid: 85fcf312-57f8-438a-8b10-34441fe0bdeb
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6591431edf7ca6de84bbf18d431ad7350308a172
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49881721"
---
# <a name="ca1819-properties-should-not-return-arrays"></a>CA1819: Eigenschaften sollten keine Arrays zurückgeben
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Attribute können Eigenschaften enthalten, die Arrays zurückgeben, aber Sie können keine Eigenschaften enthalten, die Auflistungen zurückgeben. Sie können eine Warnung, die für eine Eigenschaft eines Attributs ausgelöst wird, die von der [System.Attribute] abgeleitet ist unterdrücken (<!-- TODO: review code entity reference <xref:assetId:///System.Attribute?qualifyHint=False&amp;autoUpgrade=True>  -->) Klasse. Unterdrücken Sie andernfalls keine Warnung dieser Regel.

## <a name="example-violation"></a>Beispiel für einen Verstoß

### <a name="description"></a>Beschreibung
 Das folgende Beispiel zeigt eine Eigenschaft, die gegen diese Regel verstößt.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Performance.PropertyArrayViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayViolation/cs/FxCop.Performance.PropertyArrayViolation.cs#1)]
 [!code-vb[FxCop.Performance.PropertyArrayViolation#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayViolation/vb/FxCop.Performance.PropertyArrayViolation.vb#1)]

### <a name="comments"></a>Kommentare
 Um einen Verstoß gegen diese Regel zu beheben, stellen Sie der Eigenschaft eine Methode oder ändern Sie die Eigenschaft zum Zurückgeben einer Auflistung anstelle eines Arrays zu.

## <a name="change-the-property-to-a-method-example"></a>Ändern Sie die Eigenschaft in einer Methode – Beispiel

### <a name="description"></a>Beschreibung
 Im folgende Beispiel wird der Verstoß durch Ändern der Eigenschaft an eine Methode korrigiert.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Performance.PropertyArrayFixedMethod#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayFixedMethod/cs/FxCop.Performance.PropertyArrayFixedMethod.cs#1)]
 [!code-vb[FxCop.Performance.PropertyArrayFixedMethod#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayFixedMethod/vb/FxCop.Performance.PropertyArrayFixedMethod.vb#1)]

## <a name="return-a-collection-example"></a>Ein Beispiel für die Sammlung zurück

### <a name="description"></a>Beschreibung
 Im folgenden Beispiel wird der Verstoß korrigiert, durch Ändern der Eigenschaft zum Zurückgeben einer

 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Performance.PropertyArrayFixedCollection#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayFixedCollection/cs/FxCop.Performance.PropertyArrayFixedCollection.cs#1)]
 [!code-vb[FxCop.Performance.PropertyArrayFixedCollection#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayFixedCollection/vb/FxCop.Performance.PropertyArrayFixedCollection.vb#1)]

## <a name="allowing-users-to-modify-a-property"></a>Benutzer zum Ändern einer Eigenschaft

### <a name="description"></a>Beschreibung
 Sie möchten die Consumer der-Klasse zum Ändern einer Eigenschaft zu ermöglichen. Das folgende Beispiel zeigt eine Lese-/Schreibeigenschaft, die gegen diese Regel verstößt.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Performance.PropertyModifyViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyModifyViolation/cs/FxCop.Performance.PropertyModifyViolation.cs#1)]
 [!code-vb[FxCop.Performance.PropertyModifyViolation#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyModifyViolation/vb/FxCop.Performance.PropertyModifyViolation.vb#1)]

### <a name="comments"></a>Kommentare
 Im folgenden Beispiel wird der Verstoß korrigiert, durch Ändern der Eigenschaft zum Zurückgeben einer <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Performance.PropertyModifyFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyModifyFixed/cs/FxCop.Performance.PropertyModifyFixed.cs#1)]
 [!code-vb[FxCop.Performance.PropertyModifyFixed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyModifyFixed/vb/FxCop.Performance.PropertyModifyFixed.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1024: Nach Möglichkeit Eigenschaften verwenden](../code-quality/ca1024-use-properties-where-appropriate.md)



