---
title: 'CA1900: Werttypfelder sollten portabel sein.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1900
- ValueTypeFieldsShouldBePortable
helpviewer_keywords:
- ValueTypeFieldsShouldBePortable
- CA1900
ms.assetid: 1787d371-389f-4d39-b305-12b53bc0dfb9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e823a58d7a2be45c43305320bd32175de7a3fad6
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55953723"
---
# <a name="ca1900-value-type-fields-should-be-portable"></a>CA1900: Werttypfelder sollten portabel sein.

|||
|-|-|
|TypeName|ValueTypeFieldsShouldBePortable|
|CheckId|CA1900|
|Kategorie|Microsoft.Portability|
|Unterbrechende Änderung|Unterbrechend – Wenn das Feld außerhalb der Assembly angezeigt werden.<br /><br /> Nicht unterbrechend – Wenn das Feld nicht außerhalb der Assembly sichtbar ist.|

## <a name="cause"></a>Ursache
 Diese Regel überprüft, dass mit explizitem Layout deklarierten Strukturen korrekt, beim Marshallen an nicht verwalteten Code auf 64-Bit-Betriebssystemen ausgerichtet werden. IA-64 lässt nicht korrekt ausgerichteten Speicher zugreift und der Prozess stürzt ab, wenn diese Verletzung nicht behoben wurde.

## <a name="rule-description"></a>Regelbeschreibung
 Strukturen mit explizitem Layout, das falsch ausgerichtete Felder verursachen auf 64-Bit-Betriebssystemen Systemabstürze enthält.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Müssen alle Felder, die kleiner als 8 Bytes, Offsets, die ein Vielfaches von ihrer Größe und Felder, die 8 Bytes sind, oder benötigen mehr Offsets, die ein Vielfaches von 8 sind. Eine andere Lösung ist die Verwendung `LayoutKind.Sequential` anstelle von `LayoutKind.Explicit`, bei Bedarf.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Nur, wenn Fehler auftreten, sollte diese Warnung unterdrückt werden.