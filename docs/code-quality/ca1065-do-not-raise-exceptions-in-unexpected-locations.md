---
title: 'CA1065: Keine Ausnahmen an unerwarteten Speicherorten auslösen.'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1065
- DoNotRaiseExceptionsInUnexpectedLocations
helpviewer_keywords:
- DoNotRaiseExceptionsInUnexpectedLocations
- CA1065
ms.assetid: 4e1bade4-4ca2-4219-abc3-c7b2d741e157
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bfdb12dfbe5bf0f0bee035e79f1b8442db0bbf71
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55031525"
---
# <a name="ca1065-do-not-raise-exceptions-in-unexpected-locations"></a>CA1065: Keine Ausnahmen an unerwarteten Speicherorten auslösen.

|||
|-|-|
|TypeName|DoNotRaiseExceptionsInUnexpectedLocations|
|CheckId|CA1065|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

Eine Methode, von der das Auslösen von Ausnahmen nicht erwartet wird, löst eine Ausnahme aus.

## <a name="rule-description"></a>Regelbeschreibung

Methoden, die keine Ausnahmen auslösen sollen, können wie folgt kategorisiert werden:

- Get-Methoden der Eigenschaften

- Ereigniszugriffsmethoden

- Equals-Methoden

- GetHashCode-Methoden

- ToString-Methoden

- Statische Konstruktoren

- Finalizer

- Dispose-Methoden

- Gleichheitsoperatoren

- Impliziten Umwandlungsoperatoren

In den folgenden Abschnitten werden die folgenden Methodentypen erläutert.

### <a name="property-get-methods"></a>Get-Methoden der Eigenschaften

Eigenschaften sind im Grunde intelligenter Felder. Aus diesem Grund sollten sie sich Verhalten wie ein Feld so weit wie möglich. Felder keine Ausnahmen auslösen und sollte weder auf Eigenschaften. Wenn Sie eine Eigenschaft, die eine Ausnahme auslöst verfügen, versuchen Sie es mit einer Methode.

Die folgenden Ausnahmen können aus einer Eigenschaft Get-Methode ausgelöst werden:

- <xref:System.InvalidOperationException?displayProperty=fullName> und alle davon abgeleiteten Klassen (einschließlich <xref:System.ObjectDisposedException?displayProperty=fullName>)

- <xref:System.NotSupportedException?displayProperty=fullName> und alle davon abgeleiteten Klassen

- <xref:System.ArgumentException?displayProperty=fullName> (nur von Get)

- <xref:System.Collections.Generic.KeyNotFoundException> (nur von Get)

### <a name="event-accessor-methods"></a>Ereigniszugriffsmethoden

Ereignisaccessoren sollte es sich um einfache Operationen sein, die keine Ausnahmen auslösen. Ein Ereignis sollte keine Ausnahme auslösen, wenn Sie versuchen, hinzufügen oder Entfernen eines ereignishandlers.

Die folgenden Ausnahmen können von einem Ereignisaccessor ausgelöst werden:

- <xref:System.InvalidOperationException?displayProperty=fullName> und alle davon abgeleiteten Klassen (einschließlich <xref:System.ObjectDisposedException?displayProperty=fullName>)

- <xref:System.NotSupportedException?displayProperty=fullName> und alle davon abgeleiteten Klassen

- <xref:System.ArgumentException> und davon abgeleiteten Klassen

### <a name="equals-methods"></a>Equals-Methoden

Die folgenden **gleich** Methoden sollte keine Ausnahmen auslösen:

- <xref:System.Object.Equals%2A?displayProperty=fullName>

- <xref:System.IEquatable%601.Equals%2A>

Ein **gleich** Methode zurückgeben soll `true` oder `false` anstatt eine Ausnahme auszulösen. Z. B. wenn gleich zwei nicht übereinstimmende Typen übergeben werden sollte nur zurückgegeben `false` statt einer <xref:System.ArgumentException>.

### <a name="gethashcode-methods"></a>GetHashCode-Methoden

Die folgenden **"GetHashCode"** sollte in der Regel Methoden keine Ausnahmen auslösen:

- <xref:System.Object.GetHashCode%2A>

- <xref:System.Collections.IEqualityComparer.GetHashCode%2A>

**GetHashCode** immer einen Wert zurück. Andernfalls können Sie Elemente in der Hashtabelle verlieren.

Die Versionen der **"GetHashCode"** , nehmen ein Argument kann Auslösen einer <xref:System.ArgumentException>. Allerdings **Object.GetHashCode** sollte nie eine Ausnahme auslösen.

### <a name="tostring-methods"></a>ToString-Methoden

Der Debugger verwendet <xref:System.Object.ToString%2A?displayProperty=fullName> , um Informationen zu Objekten in einem Format anzuzeigen. Aus diesem Grund **ToString** sollte nicht den Zustand eines Objekts ändern, und es sollte nicht Auslösen von Ausnahmen.

### <a name="static-constructors"></a>Statische Konstruktoren

Auslösen von Ausnahmen von einem statischen Konstruktor wird der Typ in der aktuellen Anwendungsdomäne nicht verwendet werden. Sie sollten einen guten Grund (z. B. ein Sicherheitsproblem) verfügen, für das Auslösen einer Ausnahme von einem statischen Konstruktor.

### <a name="finalizers"></a>Finalizer

Auslösen einer Ausnahme über einem Finalizer führt dazu, dass die CLR die fail-fast, die der Prozess beendet wird. Aus diesem Grund sollte das Auslösen von Ausnahmen in einem Finalizer immer vermieden werden.

### <a name="dispose-methods"></a>Dispose-Methoden

Ein <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> Methode sollte keine Ausnahme ausgelöst. Dispose wird häufig aufgerufen, als Teil der Bereinigungslogik in einem `finally` Klausel. Aus diesem Grund explizit eine Ausnahme von Dispose den Benutzer in die Ausnahmebehandlung hinzufügen erzwingt die `finally` Klausel.

Die **Dispose(false)** Codepfad sollte nie Ausnahmen auslösen, da Dispose fast immer von einem Finalizer aufgerufen wird.

### <a name="equality-operators--"></a>Gleichheitsoperatoren (==,! =)

Wie Equals-Methoden sollten zurückgeben Gleichheitsoperatoren entweder `true` oder `false`, und sollte keine Ausnahmen auslösen.

### <a name="implicit-cast-operators"></a>Impliziten Umwandlungsoperatoren

Da der Benutzer oft nicht bekannt ist, dass es sich bei ein impliziten Cast-Operator aufgerufen wurde, ist eine Ausnahme ausgelöst wird, durch den Operator für implizite Umwandlung unerwartet. Aus diesem Grund sollte keine Ausnahmen aus impliziten Umwandlungsoperatoren ausgelöst werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Bei der Eigenschaftengetter entweder ändern Sie die Logik aus, sodass sie nicht mehr auf eine Ausnahme auslösen, oder ändern Sie die Eigenschaft in eine Methode.

Für alle anderen Methodentypen oben aufgeführt wurden ändern Sie die Logik, damit es nicht mehr eine Ausnahme ausgelöst werden soll.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Wenn die Verletzung durch eine Ausnahmedeklaration anstelle einer ausgelösten Ausnahme verursacht wurde, ist es sicher ist, unterdrücken Sie eine Warnung dieser Regel.

## <a name="related-rules"></a>Verwandte Regeln

- [CA2219: Keine Ausnahmen in Ausnahmeklauseln auslösen](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)

## <a name="see-also"></a>Siehe auch

- [Entwurfswarnungen](../code-quality/design-warnings.md)