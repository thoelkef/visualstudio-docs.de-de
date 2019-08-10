---
title: 'CA1809: Übermäßige lokale Variablen vermeiden.'
ms.date: 11/04/2016
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
ms.openlocfilehash: 8d1c2f76258be3b0be6409bffd002fd916883ab2
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921537"
---
# <a name="ca1809-avoid-excessive-locals"></a>CA1809: Übermäßige lokale Variablen vermeiden.

|||
|-|-|
|TypeName|AvoidExcessiveLocals|
|CheckId|CA1809|
|Kategorie|Microsoft.Performance|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
Ein Member enthält mehr als 64 lokale Variablen, von denen einige möglicherweise vom Compiler generiert werden.

## <a name="rule-description"></a>Regelbeschreibung
Eine häufige Leistungsoptimierung besteht darin, einen Wert in einem Prozessor Register anstelle von im Arbeitsspeicher zu speichern. Dies wird als *registrieren* des Werts bezeichnet. Der Common Language Runtime berücksichtigt bis zu 64 lokale Variablen für die Registrierung. Variablen, die nicht registriert werden, werden auf dem Stapel abgelegt und müssen vor der Bearbeitung in ein Register verschoben werden. Um die Wahrscheinlichkeit zuzulassen, dass alle lokalen Variablen registriert werden, begrenzen Sie die Anzahl der lokalen Variablen auf 64.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, müssen Sie die Implementierung so umgestalten, dass nicht mehr als 64 lokale Variablen verwendet werden.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken oder die Regel zu deaktivieren, wenn die Leistung kein Problem ist.

## <a name="related-rules"></a>Verwandte Regeln
[CA1804: Nicht verwendete lokale Variablen entfernen](../code-quality/ca1804-remove-unused-locals.md)