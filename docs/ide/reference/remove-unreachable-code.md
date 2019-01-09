---
title: Refactoring des Entfernens von nicht erreichbarem Code
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 481c0d116eb2aee2c4f931f1ca4cb2de7927c62e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53842537"
---
# <a name="remove-unreachable-code-refactoring"></a>Refactoring des Entfernens von nicht erreichbarem Code

Dieses Refactoring gilt für:

- C#

**Beschreibung:** Es wird Code entfernt, der nie ausgeführt werden wird.

**Hintergrund:** Ihr Programm enthält keinen Pfad zu einem bestimmten Codeausschnitt, weshalb dieser Codeausschnitt nicht benötigt wird.

**Vorteile**: Die Lesbarkeit und Verwaltbarkeit werden durch das Entfernen eines überflüssigen, nie ausgeführten Code verbessert.

## <a name="how-to"></a>Vorgehensweise

1. Platzieren Sie den Cursor an eine beliebige Stelle im ausgeblendeten, nicht erreichbaren Code:

![Ausgeblendeter nicht erreichbarer Code](media/unreachablecode-faded-cs.png)

1. Führen Sie dann eine der folgenden Aktionen aus:

   - **Tastatur**
      - Drücken Sie an einer beliebigen Stelle in einer Zeile **STRG**+**.**, um das Menü **Schnellaktionen und Refactorings** aufzurufen, und wählen Sie im Popupvorschaufenster **Nicht erreichbaren Code entfernen** aus.
   - **Maus**
      - Klicken Sie mit der rechten Maustaste auf den Code, und wählen Sie das Menü **Schnellaktionen und Refactorings** sowie im Popupvorschaufenster **Nicht erreichbaren Code entfernen** aus.

1. Wenn Sie mit der Änderung zufrieden sind, drücken Sie die **EINGABETASTE**, oder klicken Sie im Menü auf die Korrektur. Die Änderungen werden angewendet.

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

- [Refactoring](../refactoring-in-visual-studio.md)
- [Vorschau der Änderungen](../../ide/preview-changes.md)