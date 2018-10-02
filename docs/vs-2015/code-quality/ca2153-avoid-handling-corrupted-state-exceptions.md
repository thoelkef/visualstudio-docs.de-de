---
title: 'CA2153: Verhindern, dass Ausnahmen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 418cc9cb-68ad-47e9-a6c8-a48b9c35db45
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ff16046a115a7a21939ef33fa06f6a81ec56921c
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "47590027"
---
# <a name="ca2153-avoid-handling-corrupted-state-exceptions"></a>CA2153: Verhindern, dass Ausnahmen bei Beschädigungen verarbeitet werden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [CA2153: vermeiden Sie Handling Corrupted State Exceptions](https://docs.microsoft.com/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions).

|||
|-|-|
|TypeName|AvoidHandlingCorruptedStateExceptions|
|CheckId|CA2153|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 [(State Exceptions, CSE) beschädigt](https://msdn.microsoft.com/magazine/dd419661.aspx) anzugeben, dass der Speicher Speicherbeschädigung innerhalb des Prozesses. Diese abzufangen, statt einen Absturz des Prozesses zuzulassen, führt zu Sicherheitsrisiken, falls ein Angreifer einen Exploit in den beschädigten Speicherbereich einschleusen kann.

## <a name="rule-description"></a>Regelbeschreibung
 CSE gibt an, dass der Zustand eines Prozesses beschädigt wurde und nicht vom System abgefangen wurde. Im Szenario, das sich auf einen beschädigten Zustand bezieht, wird die Ausnahme von einem allgemeinen Handler nur abgefangen, wenn Sie die Methode mit dem richtigen `HandleProcessCorruptedStateExceptions` -Attribut markieren. In der Standardeinstellung die [Common Language Runtime (CLR)](https://msdn.microsoft.com/library/8bs2ecf4.aspx) wird kein Catch-Handler für CSEs aufgerufen.

 Die sicherste Option besteht darin, den Prozess abstürzen zu lassen, ohne diese Ausnahmetypen abzufangen, da selbst das Protokollieren von Code Angreifer in die Lage versetzen kann, Schwachstellen durch Speicherbeschädigungen auszunutzen.

 Diese Warnung wird ausgelöst, wenn CSEs mit einem allgemeinen Handler abgefangen werden, der alle Ausnahmen abfängt, wie z. B. "catch(Ausnahme)" oder "catch(keine Ausnahmespezifikation)".

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Zur Behebung des Problems sollten Sie eine der folgenden Aktionen ausführen:

 1. Entfernen Sie die `HandleProcessCorruptedStateExceptions` Attribut. Dadurch wird wieder das Standardverhalten der Laufzeit hergestellt, bei dem CSEs nicht an Catch-Handler übergeben werden.

 2. Entfernen Sie den allgemeinen Catch-Handler zugunsten von Handlern, die bestimmte Ausnahmetypen abfangen.  Dazu können auch CSEs gehören, vorausgesetzt, dass sie vom Handlercode sicher behandelt werden können (sehr selten).

 3. Lösen Sie die CSE im Catch-Handler erneut aus. So wird sichergestellt, dass die Ausnahme an den Aufrufer übergeben wird, wodurch der laufende Prozess beendet wird.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="pseudo-code-example"></a>Pseudocodebeispiel

### <a name="violation"></a>Verletzung
 Der folgende Pseudocode veranschaulicht das von dieser Regel erkannte Muster.

```
[HandleProcessCorruptedStateExceptions]
//method to handle and log CSE exceptions
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle error
    }
}
```

### <a name="solution-1"></a>Lösung 1
 Durch das Entfernen des HandleProcessCorruptedExceptions-Attributs wird sichergestellt, dass Ausnahmen nicht behandelt werden.

```
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (IOException e)
    {
        // Handle error
    }
    catch (UnauthorizedAccessException e)
    {
        // Handle error
    }
}
```

### <a name="solution-2"></a>Lösung 2
 Entfernen Sie den allgemeinen Catch-Handler, und fangen Sie nur bestimmte Ausnahmetypen ab.

```
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (IOException e)
    {
        // Handle error
    }
    catch (UnauthorizedAccessException e)
    {
        // Handle error
    }
}
```

### <a name="solution-3"></a>Lösung 3
 Lösen Sie die Ausnahme erneut aus.

```
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle error
        throw;
    }
}
```



