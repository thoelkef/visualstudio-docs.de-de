---
title: 'CA2153: Behandlung von Ausnahmen zu vermeiden'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e6b789a4580c3787a4504d730e694308341657eb
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53821859"
---
# <a name="ca2153-avoid-handling-corrupted-state-exceptions"></a>CA2153: Behandlung von Ausnahmen zu vermeiden

|||
|-|-|
|TypeName|AvoidHandlingCorruptedStateExceptions|
|CheckId|CA2153|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

[Ausnahmen bei Beschädigungen (Corrupted State Exceptions, CSE)](https://msdn.microsoft.com/magazine/dd419661.aspx) weisen auf eine Speicherbeschädigung innerhalb des Prozesses hin. Diese abzufangen, statt einen Absturz des Prozesses zuzulassen, führt zu Sicherheitsrisiken, falls ein Angreifer einen Exploit in den beschädigten Speicherbereich einschleusen kann.

## <a name="rule-description"></a>Regelbeschreibung

CSE gibt an, dass der Zustand eines Prozesses beschädigt wurde und nicht vom System abgefangen wurde. Im Szenario, das sich auf einen beschädigten Zustand bezieht, wird die Ausnahme von einem allgemeinen Handler nur abgefangen, wenn Sie die Methode mit dem richtigen `HandleProcessCorruptedStateExceptions` -Attribut markieren. Von der [Common Language Runtime (CLR)](/dotnet/standard/clr) werden standardmäßig keine Catch-Handler für CSEs aufgerufen.

Die sicherste Option besteht darin, den Prozess abstürzen zu lassen, ohne diese Ausnahmetypen abzufangen, da selbst das Protokollieren von Code Angreifer in die Lage versetzen kann, Schwachstellen durch Speicherbeschädigungen auszunutzen.

Diese Warnung wird ausgelöst, wenn CSEs mit einem allgemeinen Handler abgefangen werden, der alle Ausnahmen abfängt, wie z. B. "catch(Ausnahme)" oder "catch(keine Ausnahmespezifikation)".

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Führen Sie eine der folgenden Schritte aus, um diese Warnung zu beheben:

- Entfernen Sie das `HandleProcessCorruptedStateExceptions`-Attribut. Dadurch wird wieder das Standardverhalten der Laufzeit hergestellt, bei dem CSEs nicht an Catch-Handler übergeben werden.

- Entfernen Sie den allgemeinen Catch-Handler zugunsten von Handlern, die bestimmte Ausnahmetypen abfangen. Dies kann auch CSEs gehören, vorausgesetzt, dass vom Handlercode sicher behandelt werden kann (selten vorkommenden).

- Erneut die CSE im Catch-Handler, wodurch sichergestellt wird, die Ausnahme, die an den Aufrufer übergeben wird, und führt dazu, beenden den laufenden Prozess aus.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Unterdrücken Sie keine Warnung dieser Regel.

## <a name="pseudo-code-example"></a>Pseudocodebeispiel

### <a name="violation"></a>Verletzung

Der folgende Pseudocode veranschaulicht das von dieser Regel erkannte Muster.

```csharp
[HandleProcessCorruptedStateExceptions]
// Method to handle and log CSE exceptions.
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle error.
    }
}
```

### <a name="solution-1"></a>Lösung 1

Durch das Entfernen des HandleProcessCorruptedExceptions-Attributs wird sichergestellt, dass Ausnahmen nicht behandelt werden.

```csharp
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (IOException e)
    {
        // Handle error.
    }
    catch (UnauthorizedAccessException e)
    {
        // Handle error.
    }
}
```

### <a name="solution-2"></a>Lösung 2

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
        // Handle error.
    }
    catch (UnauthorizedAccessException e)
    {
        // Handle error.
    }
}
```

### <a name="solution-3"></a>Lösung 3

Ausnahme erneut auslösen.

```csharp
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle error.
        throw;
    }
}
```