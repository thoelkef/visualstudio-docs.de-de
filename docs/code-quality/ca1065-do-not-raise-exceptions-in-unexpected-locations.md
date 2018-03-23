---
title: 'CA1065: Keine Ausnahmen an unerwarteten Speicherorten auslösen | Microsoft Docs'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: article
f1_keywords:
- CA1065
- DoNotRaiseExceptionsInUnexpectedLocations
helpviewer_keywords:
- DoNotRaiseExceptionsInUnexpectedLocations
- CA1065
ms.assetid: 4e1bade4-4ca2-4219-abc3-c7b2d741e157
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: c81e2c7d54c8efdb1af2782c4b4937270e87d66b
ms.sourcegitcommit: 67374acb6d24019a434d96bf705efdab99d335ee
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="ca1065-do-not-raise-exceptions-in-unexpected-locations"></a>CA1065: Keine Ausnahmen an unerwarteten Speicherorten auslösen

|||
|-|-|
|TypeName|DoNotRaiseExceptionsInUnexpectedLocations|
|CheckId|CA1065|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

Eine Methode, von der das Auslösen von Ausnahmen nicht erwartet wird, löst eine Ausnahme aus.

## <a name="rule-description"></a>Regelbeschreibung

Methoden, die zum Auslösen von Ausnahmen nicht erwartet werden können wie folgt kategorisiert werden:

- Get-Eigenschaftenmethoden

- Ereigniszugriffsmethoden

- Equals-Methoden

- GetHashCode-Methoden

- ToString-Methoden

- Statische Konstruktoren

- Finalizer

- Dispose-Methoden

- Gleichheitsoperatoren

- Impliziten Umwandlungsoperatoren

In den folgenden Abschnitten werden diese Methodentypen erläutert.

### <a name="property-get-methods"></a>Get-Eigenschaftenmethoden

Eigenschaften sind im Grunde intelligente Felder. Aus diesem Grund sollten sie z. B. ein Feld so weit wie möglich Verhalten auf. Felder keine Ausnahmen auslösen und sollte weder Eigenschaften. Wenn Sie eine Eigenschaft, die eine Ausnahme auslöst verfügen, sollten Sie somit zu einer Methode.

Die folgenden Ausnahmen können von einem Property-Get-Methode ausgelöst werden:

- <xref:System.InvalidOperationException?displayProperty=fullName> und alle ableitungen (einschließlich <xref:System.ObjectDisposedException?displayProperty=fullName>)

- <xref:System.NotSupportedException?displayProperty=fullName> und alle ableitungen

- <xref:System.ArgumentException?displayProperty=fullName> (nur von Get)

- <xref:System.Collections.Generic.KeyNotFoundException> (nur von Get)

### <a name="event-accessor-methods"></a>Ereigniszugriffsmethoden

Ereignisaccessoren sollte es sich um einfache Operationen sein, die Ausnahmen auslösen, nicht. Ein Ereignis sollte keine Ausnahme auslöst, wenn Sie versuchen, hinzufügen oder entfernen einen Ereignishandler.

Die folgenden Ausnahmen können von einem Ereignisaccessor ausgelöst werden:

- <xref:System.InvalidOperationException?displayProperty=fullName> und alle ableitungen (einschließlich <xref:System.ObjectDisposedException?displayProperty=fullName>)

- <xref:System.NotSupportedException?displayProperty=fullName> und alle ableitungen

- <xref:System.ArgumentException> und ableitungen

### <a name="equals-methods"></a>Equals-Methoden

Die folgenden **gleich** Methoden sollte keine Ausnahmen auslösen:

- <xref:System.Object.Equals%2A?displayProperty=fullName>

- <xref:System.IEquatable%601.Equals%2A>

Ein **gleich** -Methode zurückgeben sollte `true` oder `false` anstatt eine Ausnahme auszulösen. Z. B. wenn gleich zwei nicht übereinstimmende Typen übergeben werden sollte nur zurückgegeben `false` statt einer <xref:System.ArgumentException>.

### <a name="gethashcode-methods"></a>GetHashCode-Methoden

Die folgenden **GetHashCode** Methoden sollten normalerweise keine Ausnahmen auslösen:

- <xref:System.Object.GetHashCode%2A>

- <xref:System.Collections.IEqualityComparer.GetHashCode%2A>

**GetHashCode** immer einen Wert zurück. Andernfalls können Sie Elemente in der Hashtabelle verloren gehen.

Die Versionen der **GetHashCode** nehmen ein Argument kann Auslösen einer <xref:System.ArgumentException>. Allerdings **Object.GetHashCode** sollten nie eine Ausnahme auslösen.

### <a name="tostring-methods"></a>ToString-Methoden

Der Debugger nutzt <xref:System.Object.ToString%2A?displayProperty=fullName> , um Informationen zu Objekten im Zeichenfolgenformat anzuzeigen. Aus diesem Grund **ToString** sollte nicht den Zustand eines Objekts ändern, und es darf keine Ausnahmen auslösen.

### <a name="static-constructors"></a>Statische Konstruktoren

Auslösen von Ausnahmen von einem statischen Konstruktor führt dazu, dass den Typ in der aktuellen Anwendungsdomäne nicht verwendet werden. Sie sollten einen guten Grund (z. B. ein Sicherheitsproblem) verfügen, für das Auslösen einer Ausnahme von einem statischen Konstruktor.

### <a name="finalizers"></a>Finalizer

Auslösen einer Ausnahme über einem Finalizer bewirkt, dass die CLR schnelle, fehl, die der Prozess beendet. Aus diesem Grund sollte das Auslösen von Ausnahmen in einem Finalizer immer vermieden werden.

### <a name="dispose-methods"></a>Dispose-Methoden

Ein <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> Methode sollte keine Ausnahme ausgelöst. Dispose wird häufig aufgerufen, als Teil der Bereinigungslogik in einer `finally` Klausel. Aus diesem Grund explizit eine Ausnahme von Dispose Benutzers Ausnahmebehandlung innerhalb hinzugefügt erzwingt die `finally` Klausel.

Die **Dispose(false)** Codepfad sollte nie Ausnahmen auslösen, da Dispose fast immer von einem Finalizer aufgerufen wird.

### <a name="equality-operators--"></a>Gleichheitsoperatoren (==,! =)

Wie Equals-Methoden sollte zurückgeben Gleichheitsoperatoren entweder `true` oder `false`, und sollte keine Ausnahmen auslösen.

### <a name="implicit-cast-operators"></a>Impliziten Umwandlungsoperatoren

Da der Benutzer oft nicht bewusst, dass ein implizite Umwandlung-Operator aufgerufen wurde, ist eine von der impliziten Umwandlungsoperator ausgelöste Ausnahme unerwartet. Aus diesem Grund sollte keine Ausnahmen aus impliziten Umwandlungsoperatoren ausgelöst werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Für den Eigenschaftengetter entweder ändern Sie die Logik, damit er nicht mehr auf eine Ausnahme auslöst, oder ändern Sie die Eigenschaft in eine Methode verfügt.

Ändern Sie die Logik für alle anderen oben aufgeführten Methodentypen, damit eine Ausnahme nicht mehr ausgelöst werden soll.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Wenn von einer Ausnahmedeklaration statt eine Ausnahme die Verletzung verursacht wurde, ist es sicher zum Unterdrücken einer Warnung dieser Regel.

## <a name="related-rules"></a>Verwandte Regeln

- [CA2219: Keine Ausnahmen in Ausnahmeklauseln auslösen](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)

## <a name="see-also"></a>Siehe auch

- [Entwurfswarnungen](../code-quality/design-warnings.md)