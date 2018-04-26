---
title: 'CA1900: Werttypfelder sollten portabel sein'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9add21d932f7685a2dee214f396b2cbda089a5a5
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="ca1900-value-type-fields-should-be-portable"></a>CA1900: Werttypfelder sollten portabel sein
|||
|-|-|
|TypeName|ValueTypeFieldsShouldBePortable|
|CheckId|CA1900|
|Kategorie|Microsoft.Portability|
|Unterbrechende Änderung|Unterbrechend – Wenn das Feld außerhalb der Assembly sichtbar ist.<br /><br /> Nicht unterbrechend – Wenn das Feld nicht außerhalb der Assembly sichtbar ist.|

## <a name="cause"></a>Ursache
 Diese Regel überprüft, dass die mit explizitem Layout deklarierten Strukturen korrekt, beim Marshallen an nicht verwalteten Code auf 64-Bit-Betriebssystemen ausgerichtet werden. IA-64 lässt nicht zu, nicht ausgerichteten Speicherzugriffe und stürzt der Prozess, wenn der Verstoß nicht behoben wird.

## <a name="rule-description"></a>Regelbeschreibung
 Strukturen mit explizitem Layout, das falsch ausgerichtete Felder Ursache Abstürze (crashes) auf 64-Bit-Betriebssystemen enthält.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Alle Felder, die kleiner als 8 Bytes müssen Offsets, die ein Vielfaches von ihrer Größe und Felder, die 8 Bytes sind oder Offsets, die ein Vielfaches von 8 müssen aufweisen. Eine andere Lösung besteht darin, verwenden Sie `LayoutKind.Sequential` anstelle von `LayoutKind.Explicit`, sofern angemessen.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Diese Warnung unterdrückt werden sollen, nur, wenn diese Fehler auftreten.