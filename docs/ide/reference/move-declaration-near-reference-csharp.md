---
title: "Verschieben einer Variablendeklaration in Verweisnähe in C# | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: reference
author: kuhlenh
ms.author: kaseyu
manager: ghogen
dev_langs: csharp
ms.workload: dotnet
ms.openlocfilehash: f61fbdc8dd24bb07082081557c875e9149c1c398
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2018
---
# <a name="move-declaration-near-reference-in-c"></a>Verschieben einer Deklaration in Verweisnähe in C# #

**Beschreibung**: Hiermit können Sie Variablendeklarationen näher an deren Verwendung verschieben.

**Hintergrund**: Sie verwenden Variablendeklarationen, die in einem engeren Bereich definiert werden können.

**Vorteile**: Sie könnten die Deklaration in ihrem jeweiligen Zustand belassen, dies könnte jedoch Probleme mit der Lesbarkeit verursachen oder zum Ausblenden von Informationen führen. Mit diesem Feature erhalten Sie die Möglichkeit zur Umgestaltung, um die Lesbarkeit zu verbessern.

**Vorgehensweise**:

1. Platzieren Sie den Cursor in die Variablendeklaration.

1. Führen Sie dann eine der folgenden Aktionen aus:
   * **Tastatur**
     * Drücken Sie **STRG+.**, um das Menü **Schnellaktionen und Refactorings** aufzurufen, und wählen Sie im Popupvorschaufenster **Deklaration nahe Referenz verschieben** aus.
   * **Maus**
     * Klicken Sie mit der rechten Maustaste auf den Code, und wählen Sie das Menü **Schnellaktionen und Refactorings** sowie im Popupvorschaufenster **Deklaration nahe Referenz verschieben** aus.

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