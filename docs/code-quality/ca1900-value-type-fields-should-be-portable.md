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
ms.openlocfilehash: 4bef51c547d4a1614137e0691343bef635aed50d
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233280"
---
# <a name="ca1900-value-type-fields-should-be-portable"></a>CA1900: Werttypfelder sollten portabel sein.

|||
|-|-|
|TypeName|ValueTypeFieldsShouldBePortable|
|CheckId|CA1900|
|Kategorie|Microsoft.Portability|
|Unterbrechende Änderung|Unterbrechung: Wenn das Feld außerhalb der Assembly sichtbar ist.<br /><br /> Nicht unterbrechend: Wenn das Feld außerhalb der Assembly nicht sichtbar ist.|

## <a name="cause"></a>Ursache
Mit dieser Regel wird überprüft, ob Strukturen, die mit expliziten Layouts deklariert werden, beim Marshalling an nicht verwalteten Code auf 64-Bit-Betriebssystemen korrekt ausgerichtet werden. IA-64 lässt keine nicht ausgerichteten Speicherzugriffe zu, und der Prozess stürzt ab, wenn diese Verletzung nicht korrigiert wird.

## <a name="rule-description"></a>Regelbeschreibung
Strukturen mit expliziten Layouts, die falsch ausgerichtete Felder enthalten, verursachen Abstürze bei 64-Bit-Betriebssystemen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Alle Felder, die kleiner als 8 Bytes sind, müssen Offsets aufweisen, die ein Vielfaches ihrer Größe aufweisen, und Felder, die 8 Bytes oder mehr umfassen, müssen Offsets aufweisen, die ein Vielfaches von 8 sind. Eine andere Lösung ist, `LayoutKind.Sequential` wenn vernünftig `LayoutKind.Explicit`, anstelle von zu verwenden.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Diese Warnung sollte nur unterdrückt werden, wenn Sie fehlerhaft auftritt.