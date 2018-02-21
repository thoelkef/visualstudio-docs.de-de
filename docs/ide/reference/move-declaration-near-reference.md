---
title: "Refactoring zum Verschieben einer Variablendeklaration in Verweisnähe in Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 01/26/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: kuhlenh
ms.author: kaseyu
manager: ghogen
dev_langs:
- csharp
ms.workload:
- dotnet
ms.openlocfilehash: d19a348ff21abce181f971c798d61cde393f4689
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="move-declaration-near-reference-refactoring"></a>Refactoring zum Verschieben einer Deklaration in Verweisnähe

Dieses Refactoring gilt für:

- C#

**Beschreibung**: Hiermit können Sie Variablendeklarationen näher an deren Verwendung verschieben.

**Hintergrund**: Sie verwenden Variablendeklarationen, die in einem engeren Bereich definiert werden können.

**Vorteile**: Sie könnten die Deklaration in ihrem jeweiligen Zustand belassen, dies könnte jedoch Probleme mit der Lesbarkeit verursachen oder zum Ausblenden von Informationen führen. Mit diesem Feature erhalten Sie die Möglichkeit zur Umgestaltung, um die Lesbarkeit zu verbessern.

## <a name="how-to"></a>Vorgehensweise

1. Platzieren Sie den Cursor in die Variablendeklaration.

1. Führen Sie dann eine der folgenden Aktionen aus:

   - **Tastatur**
     - Drücken Sie **STRG+.**, um das Menü **Schnellaktionen und Refactorings** aufzurufen, und wählen Sie im Popupvorschaufenster **Deklaration nahe Referenz verschieben** aus.
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

[Refactoring](../refactoring-in-visual-studio.md)  
[Vorschau der Änderungen](../../ide/preview-changes.md)