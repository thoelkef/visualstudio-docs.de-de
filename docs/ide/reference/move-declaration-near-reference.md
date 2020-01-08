---
title: Verschieben einer Variablendeklaration in die Nähe eines Verweises
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 35735009a5b813ca29159f276fe2d5abb734be0e
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75585283"
---
# <a name="move-declaration-near-reference-refactoring"></a>Refactoring zum Verschieben einer Deklaration in Verweisnähe

Dieses Refactoring gilt für:

- C#

**Beschreibung:** Hiermit können Sie Variablendeklarationen in die Nähe des Codes verschieben, der sie verwendet.

**Hintergrund:** Sie verwenden Variablendeklarationen, die für eine engeren Bereich definiert werden können.

**Vorteile**: Sie könnten die Deklaration in ihrem jeweiligen Zustand belassen, dies könnte jedoch Probleme mit der Lesbarkeit verursachen oder zum Ausblenden von Informationen führen. Mit diesem Feature erhalten Sie die Möglichkeit zur Umgestaltung, um die Lesbarkeit zu verbessern.

## <a name="how-to"></a>Vorgehensweise

1. Platzieren Sie den Cursor in die Variablendeklaration.

1. Führen Sie dann eine der folgenden Aktionen aus:

   - **Tastatur**
      - Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+ **.** , um das Menü **Schnellaktionen und Refactorings** aufzurufen, und wählen Sie im Popupvorschaufenster **Deklaration nahe Referenz verschieben** aus.
   - **Maus**
      - Klicken Sie mit der rechten Maustaste auf den Code, und wählen Sie das Menü **Schnellaktionen und Refactorings** sowie im Popupvorschaufenster **Deklaration nahe Referenz verschieben** aus.

1. Wenn Sie mit der Änderung zufrieden sind, drücken Sie die **EINGABETASTE**, oder klicken Sie im Menü auf die Korrektur. Die Änderungen werden angewendet.

Beispiel:

```csharp
// Before
int x;
if (condition)
{
    x = 1;
    Console.WriteLine(x);
}

// Move declaration near reference

// After
if (condition)
{
    int x = 1;
    Console.WriteLine(x);
}
```

## <a name="see-also"></a>Siehe auch

- [Refactoring](../refactoring-in-visual-studio.md)
- [Vorschau der Änderungen](../../ide/preview-changes.md)
