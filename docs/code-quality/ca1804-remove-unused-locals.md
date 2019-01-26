---
title: 'CA1804: Nicht verwendete lokale Variablen entfernen.'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 4e7e82d6d631f12733e75262050afc66fb844416
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54999196"
---
# <a name="ca1804-remove-unused-locals"></a>CA1804: Nicht verwendete lokale Variablen entfernen.

|||
|-|-|
|TypeName|RemoveUnusedLocals|
|CheckId|CA1804|
|Kategorie|Microsoft.Performance|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Eine Methode deklariert eine lokale Variable verwendet jedoch nicht die Variable außer möglicherweise als Empfänger einer zuweisungsanweisung. Für die Analyse durch diese Regel muss der getestete Assembly mit Debuginformationen erstellt werden, und die zugehörigen Programmdatenbankdatei (.pdb) muss verfügbar sein.

## <a name="rule-description"></a>Regelbeschreibung
 Nicht verwendete lokale Variablen und unnötige Zuweisungen vergrößern die Assembly unnötig und beeinträchtigen die Leistung.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie, oder verwenden Sie die lokale Variable. Beachten Sie, dass der C#-Compiler, der in enthalten ist [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] entfernt nicht verwendete lokale Variablen bei der `optimize` aktiviert ist.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie eine Warnung dieser Regel, wenn die Variable vom Compiler ausgegeben wurde. Es ist auch sicher, unterdrücken Sie eine Warnung dieser Regel oder die Regel deaktivieren, wenn Leistung und Wartung des Programmcodes nicht im Vordergrund stehen.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt mehrere nicht verwendete lokale Variablen.

 [!code-vb[FxCop.Performance.UnusedLocals#1](../code-quality/codesnippet/VisualBasic/ca1804-remove-unused-locals_1.vb)]
 [!code-csharp[FxCop.Performance.UnusedLocals#1](../code-quality/codesnippet/CSharp/ca1804-remove-unused-locals_1.cs)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1809: Übermäßige lokale Variablen vermeiden](../code-quality/ca1809-avoid-excessive-locals.md)

 [CA1811: Nicht aufgerufenen privaten Code vermeiden](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812: Nicht instanziierte interne Klassen vermeiden](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801: Nicht verwendete Parameter überprüfen](../code-quality/ca1801-review-unused-parameters.md)