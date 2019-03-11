---
title: Konvertieren von ForEach-Schleifen in LINQ
ms.date: 02/20/2019
ms.topic: reference
author: kendrahavens
ms.author: kendrahavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: dc0f94d6aa9f13ac038f1af19a1ab1c78158ea14
ms.sourcegitcommit: 11337745c1aaef450fd33e150664656d45fe5bc5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/04/2019
ms.locfileid: "57324955"
---
# <a name="convert-foreach-loop-to-linq"></a>Konvertieren von ForEach-Schleifen in LINQ

Dieses Refactoring gilt für:

- C#

**Beschreibung:** Hiermit können Sie Ihre ForEach-Schleifen mithilfe von IEnumerables in das Format von LINQ-Abfragen oder -Aufrufen (auch bekannt als LINQ-Methode) konvertieren.

**Hintergrund:** Wenn Sie über eine ForEach-Schleife verfügen, die eine IEnumerable-Schnittstelle nutzt, die als LINQ-Abfrage gelesen werden soll.

**Vorteile**: In einigen Fällen bevorzugen Benutzer die Verwendung der LINQ-Syntax anstelle einer ForEach-Schleife. Durch [LINQ](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq) wird eine Abfrage zu einem erstklassigen Sprachkonstrukt in C#. Mit LINQ kann die Menge an Code in einer Datei reduziert werden, wodurch sie einfacher zu lesen wird und verschiedene Datenquellen mit ähnlichen Abfrageausdrucksmustern zugelassen werden.

> [!NOTE]
> Die LINQ-Syntax ist in der Regel weniger leistungsfähig als ForEach-Schleifen. Es ist wichtig, dass Sie sich der möglichen Leistungseinbußen bewusst sind, wenn Sie die Lesbarkeit Ihres Codes mit LINQ verbessern.

## <a name="convert-foreach-loop-to-linq-refactoring"></a>Refactoring: Konvertieren einer ForEach-Schleife in LINQ

1. Platzieren Sie Ihren Cursor im Schlüsselwort `foreach`.

    ![ForEach-Schleife mit IEnumerable](media/convert-foreach-to-LINQ.png)

2. Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+**.**, um das Menü **Schnellaktionen und Refactorings** aufzurufen.

   ![Menü zum Konvertieren in LINQ](media/convert-foreach-to-LINQ-codefix.png)

3. Wählen Sie **Convert to LINQ** (In LINQ konvertieren) oder **Convert to Linq (call form)** (In LINQ konvertieren (Aufrufformat)) aus.

   ![Ergebnis der LINQ-Abfrage](media/convert-foreach-to-LINQ-result.png)
   
   ![Resultierendes LINQ-Aufrufformat](media/convert-foreach-to-LINQ-callform-result.png)

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)
- [Vorschau der Änderungen](../../ide/preview-changes.md)
- [Tipps für .NET-Entwickler](../../ide/visual-studio-2017-for-dotnet-developers.md)