---
title: Codeanalyse-Regelsätze CA2153 für Corrupted State Exceptions
ms.date: 02/19/2019
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4b75e45b8a199265eaefe3a2b3c37ed62039e0eb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62542156"
---
# <a name="ca2153-avoid-handling-corrupted-state-exceptions"></a>CA2153: Verhindern, dass Corrupted State Exceptions

|||
|-|-|
|TypeName|AvoidHandlingCorruptedStateExceptions|
|CheckId|CA2153|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

[Ausnahmen (CSEs) aufgrund von](https://msdn.microsoft.com/magazine/dd419661.aspx) anzugeben, dass der Speicher Speicherbeschädigung innerhalb des Prozesses. Diese abzufangen, statt einen Absturz des Prozesses zuzulassen, führt zu Sicherheitsrisiken, falls ein Angreifer einen Exploit in den beschädigten Speicherbereich einschleusen kann.

## <a name="rule-description"></a>Regelbeschreibung

CSE gibt an, dass der Zustand eines Prozesses beschädigt wurde und nicht vom System abgefangen wurde. In diesem Szenario beschädigten Zustand ein allgemeiner Handler nur fängt die Ausnahme ab, wenn Sie die Methode mit kennzeichnen die <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=fullName> Attribut. In der Standardeinstellung die [Common Language Runtime (CLR)](/dotnet/standard/clr) ist keine Catch-Handler für CSEs aufgerufen.

Die sicherste Methode ist, um den Prozess abstürzen zu ermöglichen, ohne diese Arten von Ausnahmen abfangen. Selbst das Protokollieren von Code können Angreifer speicherbeschädigungen auszunutzen.

Diese Warnung wird ausgelöst, wenn CSEs mit einem allgemeinen Handler abgefangen werden, der alle Ausnahmen, z. B. abfängt `catch (System.Exception e)` oder `catch` ohne Ausnahme-Parameter.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Führen Sie eine der folgenden Schritte aus, um diese Warnung zu beheben:

- Entfernen Sie das <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>-Attribut. Dadurch wird wieder das Standardverhalten der Laufzeit hergestellt, bei dem CSEs nicht an Catch-Handler übergeben werden.

- Entfernen Sie den allgemeinen Catch-Handler zugunsten von Handlern, die bestimmte Ausnahmetypen abfangen. Dies kann auch CSEs, vorausgesetzt, dass vom Handlercode sicher behandelt werden kann (selten vorkommenden) gehören.

- Erneut die CSE im Catch-Handler, übergibt die Ausnahme an dem Aufrufer und führt zum Beenden des ausgeführten Prozesses aus.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Unterdrücken Sie keine Warnung dieser Regel.

## <a name="pseudo-code-example"></a>Pseudocodebeispiel

### <a name="violation"></a>Verletzung

Der folgende Pseudocode veranschaulicht das von dieser Regel erkannte Muster.

```csharp
[HandleProcessCorruptedStateExceptions]
// Method that handles CSE exceptions.
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle exception.
    }
}
```

### <a name="solution-1---remove-the-attribute"></a>Lösung 1: Entfernen Sie das Attribut

Entfernen der <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> Attribut wird sichergestellt, dass Corrupted State Exceptions nicht von der Methode behandelt werden.

```csharp
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle exception.
    }
}
```

### <a name="solution-2---catch-specific-exceptions"></a>Lösung 2: bestimmte Ausnahmen abfangen

Entfernen Sie den allgemeinen Catch-Handler, und fangen Sie nur bestimmte Ausnahmetypen ab.

```csharp
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (IOException e)
    {
        // Handle IOException.
    }
    catch (UnauthorizedAccessException e)
    {
        // Handle UnauthorizedAccessException.
    }
}
```

### <a name="solution-3---rethrow"></a>Lösung 3: Lösen Sie erneut aus

Ausnahme erneut auslösen.

```csharp
[HandleProcessCorruptedStateExceptions]
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Rethrow the exception.
        throw;
    }
}
```