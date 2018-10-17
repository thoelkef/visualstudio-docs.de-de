---
title: 'CA2222: Sichtbarkeit für geerbte Member nicht verringern'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 9dcf92e2a5cdfb7f83a84c55b222aabf415fcfe0
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/13/2018
ms.locfileid: "45545660"
---
# <a name="ca2222-do-not-decrease-inherited-member-visibility"></a>CA2222: Sichtbarkeit für geerbte Member nicht verringern

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