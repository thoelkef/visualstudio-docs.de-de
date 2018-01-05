---
title: Entfernen von Unerreichbarer Code - Umgestaltung (c#) | Microsoft Docs
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
author: kuhlenh
ms.author: kaseyu
manager: ghogen
dev_langs: csharp
ms.workload: dotnet
ms.openlocfilehash: e57db74ea431d9090df1dc34fd3cff3cf03dd475
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="remove-unreachable-code-in-c"></a>Entfernen von unerreichbarer Code in c# #
**Was:** entfernt Code, der nie ausgeführt wird.

**Wann:** das Programm muss kein Pfad zu einem Codeausschnitt, der dieser Codeausschnitt unnötig zu machen.

**Grund:** Lesbarkeit und verwaltbarkeit verbessern, indem Sie Code, der überflüssig ist entfernt und wird nie ausgeführt.

**Vorgehensweise:**

1. Platzieren Sie den Cursor an einer beliebigen Stelle in den verblasst, Code, der nicht erreichbar ist:

![Insgesamt unerreichbarer code](media/unreachablecode_faded.png)  

1. Als Nächstes führen Sie eine der folgenden:
   * **Tastatur**
     * Drücken Sie **STRG +.** Trigger die **Schnellaktionen und Refactorings** Menü **unerreichbarer Code entfernen** im Popupmenü Fenster Vorschau.
   * **Maus**
     * Mit der rechten Maustaste in des Codes, wählen Sie die **Schnellaktionen und Refactorings** Menü **unerreichbarer Code entfernen** im Popupmenü Fenster Vorschau.

1. Wenn Sie mit der Änderung zufrieden sind, drücken Sie die **EINGABETASTE** oder klicken Sie auf das Update im Menü und die Änderungen werden ein Commit ausgeführt werden.

Beispiel:
```csharp
// Before
private void Method()
{
    throw new Exception(nameof(Method));
    Console.WriteLine($"Exception for method {nameof(Method)}");
}

// Remove unreachable code

// After
private void Method()
{
    throw new Exception(nameof(Method));
}
```

## <a name="see-also"></a>Siehe auch  
[Refactoring (C#)](../refactoring-csharp.md)  
[Vorschau der Änderungen](../../ide/preview-changes.md)