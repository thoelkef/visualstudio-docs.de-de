---
title: "Verschieben Sie die Deklaration in der Nähe von Verweis - Umgestaltung (c#) | Microsoft Docs"
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: d79d55ae-f6bb-4902-8db2-e7fe01bdb0bf
author: kuhlenh
ms.author: kaseyu
manager: ghogen
dev_langs: csharp
ms.openlocfilehash: f784ac9fec1dce1f21ba4b9f1f0e83b4b7deb001
ms.sourcegitcommit: 5f5587a1bcf4aae995c80d54a67b4b461f8695f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/29/2017
---
# <a name="move-declaration-near-reference-in-c"></a>Verschieben Sie die Deklaration in der Nähe von Verweis in c# #
**Was:** können Sie näher Variablendeklarationen zu ihrer Verwendung zu verschieben.

**Wann:** stehen Ihnen Variablendeklarationen, die in einen engeren Bereich definiert werden können.

**Grund:** können ist, jedoch verursachen, die Lesbarkeit Probleme oder Ausblenden von Informationen bestehen. Dies ist eine Möglichkeit für die Umgestaltung, die Lesbarkeit zu verbessern.

**Vorgehensweise:**

1. Platzieren Sie den Cursor in der Variablendeklaration.

1. Als Nächstes führen Sie eine der folgenden:
   * **Tastatur**
     * Drücken Sie **STRG +.** Trigger die **Schnellaktionen und Refactorings** Menü **verschieben Sie die Deklaration in der Nähe von Verweis** im Popupmenü Fenster Vorschau.
   * **Maus**
     * Mit der rechten Maustaste in des Codes, wählen Sie die **Schnellaktionen und Refactorings** , und wählen Sie im Menü **verschieben Sie die Deklaration in der Nähe von Verweis** im Popupmenü Fenster Vorschau.

1. Wenn Sie mit der Änderung zufrieden sind, drücken Sie die **EINGABETASTE** oder klicken Sie auf das Update im Menü und die Änderungen werden ein Commit ausgeführt werden.

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
[Refactoring (C#)](../refactoring-csharp.md)  
[Vorschau der Änderungen](../../ide/preview-changes.md)