---
title: 'CA1809: Übermäßige lokale Variablen vermeiden.'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5adce9ea32cb29154d88538d7b142e29b3e29761
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54957675"
---
# <a name="ca1809-avoid-excessive-locals"></a>CA1809: Übermäßige lokale Variablen vermeiden.

|||
|-|-|
|TypeName|AvoidExcessiveLocals|
|CheckId|CA1809|
|Kategorie|Microsoft.Performance|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein Element enthält mehr als 64 lokale Variablen, von die einige Compiler generiert werden kann.

## <a name="rule-description"></a>Regelbeschreibung
 Zur Optimierung der allgemeinen Leistung ist zum Speichern eines Werts in einem Prozessorregister statt im Speicher, der als bezeichnet wird *Ablaufanalyse* den Wert. Die common Language Runtime betrachtet, bis zu 64 lokale Variablen für die Registrierung in Betracht. Variablen, die nicht registriert werden, die auf dem Stapel abgelegt werden und müssen vor der Bearbeitung in ein Register verschoben werden. Um die Möglichkeit, dass alle lokale Variablen registriert werden, die Anzahl der lokalen Variablen auf 64 beschränken.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Umgestalten Sie, um einen Verstoß gegen diese Regel zu beheben, die Implementierung, um nicht mehr als 64 lokale Variablen verwenden.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Es ist sicher, um eine Warnung dieser Regel zu unterdrücken, oder um die Regel zu deaktivieren, wenn die Leistung kein Problem darstellt.

## <a name="related-rules"></a>Verwandte Regeln
 [CA1804: Nicht verwendete lokale Variablen entfernen](../code-quality/ca1804-remove-unused-locals.md)