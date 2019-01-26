---
title: 'CA2222: Sichtbarkeit für geerbte Member nicht verringern.'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
helpviewer_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
ms.assetid: 066c8675-381f-43cc-956c-d757cc494028
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: bdae21ec1a95cdc12cb6511a39f45e610e09b329
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55031785"
---
# <a name="ca2222-do-not-decrease-inherited-member-visibility"></a>CA2222: Sichtbarkeit für geerbte Member nicht verringern.

|||
|-|-|
|TypeName|DoNotDecreaseInheritedMemberVisibility|
|CheckId|CA2222|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

Eine private Methode in einem nicht versiegelten Typ verfügt über eine Signatur, die an eine öffentliche Methode, die in einem Basistyp deklariert identisch ist. Die private Methode ist nicht endgültig.

## <a name="rule-description"></a>Regelbeschreibung

Ändern Sie den Zugriffsmodifizierer für geerbte Member nicht. Wenn Sie einen geerbten Member in private ändern, werden Aufrufer nicht am Zugriff auf die Implementierung der Basisklasse der Methode gehindert. Wenn das Element ist privat, und der Typ nicht versiegelten ist, kann durch das erbende Typen die letzte öffentliche Implementierung der Methode in der Vererbungshierarchie aufrufen. Wenn Sie den Zugriffsmodifizierer ändern müssen, die Methode sollte als final gekennzeichnet werden, oder sein Typ muss versiegelt werden, um zu verhindern, dass die Methode überschrieben wird.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Zugriff auf nicht privat sein. Auch wenn Ihre bevorzugte Programmiersprache unterstützt wird, können Sie die Methode endgültige vornehmen.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt einen Typ, der gegen diese Regel verstößt.

[!code-vb[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/VisualBasic/ca2222-do-not-decrease-inherited-member-visibility_1.vb)]
[!code-csharp[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/CSharp/ca2222-do-not-decrease-inherited-member-visibility_1.cs)]