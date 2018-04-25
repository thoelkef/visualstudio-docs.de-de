---
title: 'CA1809: Übermäßige lokale Variablen vermeiden'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1809
- AvoidExcessiveLocals
helpviewer_keywords:
- AvoidExcessiveLocals
- CA1809
ms.assetid: 5c81ea43-cb49-448f-980f-a1dd9764043c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a4790d78ae1050a2c5443a8f048416f5f4de078e
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="ca1809-avoid-excessive-locals"></a>CA1809: Übermäßige lokale Variablen vermeiden
|||
|-|-|
|TypeName|AvoidExcessiveLocals|
|CheckId|CA1809|
|Kategorie|Microsoft.Performance|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein Element enthält mehr als 64 lokale Variablen, von die einige Compiler generiert werden kann.

## <a name="rule-description"></a>Regelbeschreibung
 Zur leistungsoptimierung wird zum Speichern eines Werts in einem Prozessorregister statt im Arbeitsspeicher, die so genannte *Ablaufanalyse* den Wert. Die common Language Runtime betrachtet, bis zu 64 lokale Variablen können. Variablen, die nicht registriert werden, die auf dem Stapel abgelegt werden und müssen vor der Bearbeitung in ein Register verschoben werden. Um die Möglichkeit, dass alle lokale Variablen registriert werden, die Anzahl der lokalen Variablen auf 64 beschränken.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, gestalten Sie die Implementierung, um nicht mehr als 64 lokale Variablen verwenden.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Sie können ruhig zum Unterdrücken einer Warnung dieser Regel, oder um die Regel deaktivieren, wenn Leistung kein Problem darstellt.

## <a name="related-rules"></a>Verwandte Regeln
 [CA1804: Nicht verwendete lokale Variablen entfernen](../code-quality/ca1804-remove-unused-locals.md)