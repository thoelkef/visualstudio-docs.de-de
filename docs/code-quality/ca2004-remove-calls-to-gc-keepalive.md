---
title: 'CA2004: Aufrufe an GC.KeepAlive entfernen.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
helpviewer_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
ms.assetid: bc543b5b-23eb-4b45-abc2-9325cd254ac2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c495357b837c4ae10d4dfe1e25237d6caaefcc4c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233116"
---
# <a name="ca2004-remove-calls-to-gckeepalive"></a>CA2004: Aufrufe an GC.KeepAlive entfernen.

|||
|-|-|
|TypeName|RemoveCallsToGCKeepAlive|
|CheckId|CA2004|
|Kategorie|Microsoft.Reliability|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
Klassen verwenden `SafeHandle` , aber enthalten weiterhin Aufrufe `GC.KeepAlive`von.

## <a name="rule-description"></a>Regelbeschreibung
Wenn Sie in die Verwendung `SafeHandle` von umrechnen, entfernen Sie `GC.KeepAlive` alle Aufrufe von (-Objekt). In diesem Fall dürfen Klassen nicht aufzurufen `GC.KeepAlive`, wenn Sie keinen Finalizer haben, sondern `SafeHandle` sich darauf verlassen, das Betriebssystem Handle für Sie abzuschließen.  Obwohl die Kosten für die Durchführung eines Aufrufes `GC.KeepAlive` durch die Leistung vernachlässigbar sein können, `GC.KeepAlive` ist der Eindruck, dass ein aufrufbedarf entweder notwendig oder ausreichend ist, um ein Lebensdauer Problem zu lösen, das möglicherweise nicht mehr vorhanden ist, den Code schwerer zu machen. Verwalten.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Entfernen Sie Aufrufe `GC.KeepAlive`von.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Sie können diese Warnung nur unterdrücken, wenn die Konvertierung `SafeHandle` in die Verwendung in ihrer Klasse nicht technisch korrekt ist.