---
title: 'CA1811: Nicht aufgerufenen privaten Code vermeiden.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidUncalledPrivateCode
- CA1811
helpviewer_keywords:
- CA1811
- AvoidUncalledPrivateCode
ms.assetid: aadbba74-7821-475f-8980-34d17c0a0a8b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 92a7542499eceeccbd62ce327b386dc099b726b2
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233623"
---
# <a name="ca1811-avoid-uncalled-private-code"></a>CA1811: Nicht aufgerufenen privaten Code vermeiden.

|||
|-|-|
|TypeName|AvoidUncalledPrivateCode|
|CheckId|CA1811|
|Kategorie|Microsoft.Performance|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
Ein privater oder interner Member (auf Assemblyebene) besitzt keine Aufrufer in der Assembly, wird nicht vom Common Language Runtime aufgerufen und wird nicht von einem Delegaten aufgerufen. Folgende Mitglieder werden von dieser Regel nicht geprüft:

- Explizite Schnittstellenmember.

- Statische Konstruktoren.

- Serialisierungskonstruktoren.

- Mit <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> oder<xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>gekennzeichnete Methoden.

- Member, die außer Kraft gesetzt werden.

## <a name="rule-description"></a>Regelbeschreibung
Diese Regel kann falsch positive Ergebnisse melden, wenn Einstiegspunkte auftreten, die derzeit nicht durch die Regellogik identifiziert werden. Außerdem kann ein Compiler nicht Aufruf baren Code in eine Assembly ausgeben.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie den nicht Aufruf baren Code, oder fügen Sie Code hinzu, der ihn aufruft.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken.

## <a name="related-rules"></a>Verwandte Regeln
[CA1812: Nicht instanziierte interne Klassen vermeiden](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

[CA1801: Nicht verwendete Parameter überprüfen](../code-quality/ca1801-review-unused-parameters.md)

[CA1804: Nicht verwendete lokale Variablen entfernen](../code-quality/ca1804-remove-unused-locals.md)