---
title: Verschieben einer Variablendeklaration in die Nähe eines Verweises
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 1339f4a9d151ef41d9a35c5aac0a96f220a297b3
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "79093993"
---
# <a name="move-declaration-near-reference-refactoring"></a>Refactoring zum Verschieben einer Deklaration in Verweisnähe

Dieses Refactoring gilt für:

- C#

- Visual Basic

**Beschreibung**: Hiermit können Sie Variablendeklarationen näher an deren Verwendung verschieben.

**Hintergrund**: Sie verwenden Variablendeklarationen, die in einem engeren Bereich definiert werden können.

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

## <a name="see-also"></a>Weitere Informationen

- [Refactoring](../refactoring-in-visual-studio.md)
- [Vorschau der Änderungen](../../ide/preview-changes.md)
