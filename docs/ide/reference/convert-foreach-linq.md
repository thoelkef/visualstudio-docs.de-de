---
title: Konvertieren einer ForEach-Schleife in LINQ
descritpion: Convert any foreach loop that uses an IEnumerable to a LINQ query or a LINQ call form (also known as a LINQ method).
ms.date: 02/20/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: baa1f32bb981e6d244555baef2a00d03933cdd6c
ms.sourcegitcommit: 0f5f7955076238742f2071d286ad8e896f3a6cad
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "68483719"
---
# <a name="convert-a-foreach-loop-to-linq"></a>Konvertieren einer ForEach-Schleife in LINQ

Dieses Refactoring gilt für:

- C#

**Beschreibung:** Hiermit können Sie Ihre *ForEach*-Schleife, die eine IEnumerable verwendet, in das Format von LINQ-Abfragen oder -Aufrufen (auch bekannt als LINQ-Methode) konvertieren.

**Hintergrund:** Sie verfügen über eine ForEach-Schleife, die eine IEnumerable-Schnittstelle nutzt, und diese Schleife soll als LINQ-Abfrage gelesen werden.

**Vorteile**: Es soll eine LINQ-Syntax anstelle einer ForEach-Schleife verwendet werden. Durch [LINQ](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq) wird eine Abfrage zu einem erstklassigen Sprachkonstrukt in C#. Mit LINQ kann die Menge an Code in einer Datei reduziert werden, wodurch dieser Code einfacher zu lesen ist und verschiedene Datenquellen mit ähnlichen Abfrageausdrucksmustern zugelassen werden.

> [!NOTE]
> Die LINQ-Syntax ist in der Regel weniger effizient als ForEach-Schleifen. Es ist gut, sich über alle Leistungseinbußen im Klaren zu sein, die auftreten können, wenn Sie LINQ zur Verbesserung der Lesbarkeit Ihres Codes verwenden.

## <a name="convert-a-foreach-loop-to-linq-refactoring"></a>Refactoring: Konvertieren einer ForEach-Schleife in LINQ

1. Platzieren Sie Ihren Cursor im Schlüsselwort `foreach`.

    ![ForEach-Schleife mit IEnumerable – Beispiel](media/convert-foreach-to-LINQ.png)

2. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen.

   ![Menü zum Konvertieren in LINQ – Beispiel](media/convert-foreach-to-LINQ-codefix.png)

3. Wählen Sie **In LINQ konvertieren** oder **In LINQ konvertieren (Aufrufformat)** aus.

   ![Ergebnis der LINQ-Abfrage – Beispiel](media/convert-foreach-to-LINQ-result.png)

   ![Resultierendes LINQ-Aufrufformat – Beispiel](media/convert-foreach-to-LINQ-callform-result.png)

### <a name="sample-code"></a>Beispielcode

```csharp
using System.Collections.Generic;

public class Class1
{
    public void MyMethod()
    {
        var greetings = new List<string>()
            { "hi", "yo", "hello", "howdy" };

        IEnumerable<string> enumerable()
        {
            foreach (var greet in greetings)
            {
                if (greet.Length < 3)
                {
                    yield return greet;
                }
            }

            yield break;
        }
    }
}
```

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)
- [Fenster „Vorschau der Änderungen“](../../ide/preview-changes.md)
- [Tipps für .NET-Entwickler](../csharp-developer-productivity.md)
