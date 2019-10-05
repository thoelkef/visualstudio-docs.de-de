---
title: 'CA1804: Nicht verwendete lokale Variablen entfernen.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1804
- RemoveUnusedLocals
helpviewer_keywords:
- RemoveUnusedLocals
- CA1804
ms.assetid: cc332e67-6543-4813-bd8a-6f6fc75bf22a
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 0a83d0afffc50c7697fad98c4dc49e31770d63d4
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233750"
---
# <a name="ca1804-remove-unused-locals"></a>CA1804: Nicht verwendete lokale Variablen entfernen.

|||
|-|-|
|TypeName|RemoveUnusedLocals|
|CheckId|CA1804|
|Kategorie|Microsoft.Performance|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
Eine Methode deklariert eine lokale Variable, verwendet jedoch nicht die Variable, außer möglicherweise als Empfänger einer Zuweisungsanweisung. Zur Analyse durch diese Regel muss die getestete Assembly mit Debuginformationen erstellt werden, und die zugehörige Programm Datenbankdatei (. pdb) muss verfügbar sein.

## <a name="rule-description"></a>Regelbeschreibung
Nicht verwendete lokale Variablen und unnötige Zuweisungen vergrößern die Assembly unnötig und beeinträchtigen die Leistung.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie die lokale Variable, oder verwenden Sie Sie.

> [!NOTE]
> Der C# Compiler entfernt nicht verwendete lokale Variablen, `optimize` wenn die Option aktiviert ist.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Unterdrückt eine Warnung aus dieser Regel, wenn die Variable vom Compiler ausgegeben wurde. Es ist auch sicher, eine Warnung aus dieser Regel zu unterdrücken oder die Regel zu deaktivieren, wenn die Leistung und die Codewartung keine Haupt Bedenken darstellen.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt mehrere nicht verwendete lokale Variablen.

[!code-vb[FxCop.Performance.UnusedLocals#1](../code-quality/codesnippet/VisualBasic/ca1804-remove-unused-locals_1.vb)]
[!code-csharp[FxCop.Performance.UnusedLocals#1](../code-quality/codesnippet/CSharp/ca1804-remove-unused-locals_1.cs)]

## <a name="related-rules"></a>Verwandte Regeln
[CA1809: Übermäßige lokale Variablen vermeiden](../code-quality/ca1809-avoid-excessive-locals.md)

[CA1811: Nicht aufgerufenen privaten Code vermeiden](../code-quality/ca1811-avoid-uncalled-private-code.md)

[CA1812: Nicht instanziierte interne Klassen vermeiden](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

[CA1801: Nicht verwendete Parameter überprüfen](../code-quality/ca1801-review-unused-parameters.md)