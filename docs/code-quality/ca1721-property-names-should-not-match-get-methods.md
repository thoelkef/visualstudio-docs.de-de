---
title: 'CA1721: Eigenschaftennamen sollten nicht mit dem Get-Methoden übereinstimmen.'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
helpviewer_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
ms.assetid: 45a0e853-1f06-4688-af1b-cc634409e295
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: e0b9c348fc9131ede355c58408b517d20ed2500b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53920977"
---
# <a name="ca1721-property-names-should-not-match-get-methods"></a>CA1721: Eigenschaftennamen sollten nicht mit dem Get-Methoden übereinstimmen.

|||
|-|-|
|TypeName|PropertyNamesShouldNotMatchGetMethods|
|CheckId|CA1721|
|Kategorie|Microsoft.Naming|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Der Name eines öffentlichen oder geschützten Members beginnt mit "Get" und entspricht andernfalls den Namen einer öffentlichen oder geschützten Eigenschaft. Ein Typ, der eine Methode, mit dem Namen enthält "GetColor" und eine Eigenschaft mit dem Namen "Farbe" z. B. verletzt diese Regel.

## <a name="rule-description"></a>Regelbeschreibung
 Get-Methoden und Eigenschaften sollten Namen aufweisen, die ihre Funktionen deutlich erkennbar.

 Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild. Diese Konsistenz reduziert die Zeit, die ist erforderlich, um eine neue Softwarebibliothek zu erhalten und zudem wird das Kundenvertrauen, dass die Bibliothek von einer Person entwickelt wurde, die Erfahrung in der Entwicklung von verwaltetem Code hat.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Ändern Sie den Namen ein, sodass sie nicht den Namen einer Methode übereinstimmt, der mit "Get" vorangestellt ist.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie keine Warnung dieser Regel.

> [!NOTE]
> Diese Warnung kann ausgeschlossen werden, wenn die Get-Methode verursacht wird, indem Sie IExtenderProvider-Schnittstelle implementieren.

## <a name="example"></a>Beispiel
 Das folgende Beispiel enthält eine Methode und eine Eigenschaft, die gegen diese Regel verstoßen.

 [!code-csharp[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/CSharp/ca1721-property-names-should-not-match-get-methods_1.cs)]
 [!code-vb[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/VisualBasic/ca1721-property-names-should-not-match-get-methods_1.vb)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1024: NACH MÖGLICHKEIT Verwenden Sie Eigenschaften](../code-quality/ca1024-use-properties-where-appropriate.md)