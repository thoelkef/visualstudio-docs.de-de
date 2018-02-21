---
title: Refactoring des Entfernens von nicht erreichbarem Code in Visual Studio | Microsoft-Dokumentation
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
ms.openlocfilehash: 1048458eb41a5c1f9842c3cfea1b3c8a553fbf20
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="remove-unreachable-code-refactoring"></a>Refactoring des Entfernens von nicht erreichbarem Code

Dieses Refactoring gilt für:

- C#

**Beschreibung**: Es wird Code entfernt, der nie ausgeführt wird.

**Hintergrund**: Ihr Programm enthält keinen Pfad zu einem bestimmten Codeausschnitt, weshalb dieser Codeausschnitt nicht benötigt wird.

**Vorteile**: Die Lesbarkeit und Verwaltbarkeit werden durch das Entfernen eines überflüssigen, nie ausgeführten Code verbessert.

## <a name="how-to"></a>Vorgehensweise

1. Platzieren Sie den Cursor an eine beliebige Stelle im ausgeblendeten, nicht erreichbaren Code:

![Ausgeblendeter nicht erreichbarer Code](media/unreachablecode-faded-cs.png)

1. Führen Sie dann eine der folgenden Aktionen aus:

   - **Tastatur**
     - Drücken Sie **STRG+.**, um das Menü **Schnellaktionen und Refactorings** aufzurufen, und wählen Sie im Popupvorschaufenster **Nicht erreichbaren Code entfernen** aus.
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

[Refactoring](../refactoring-in-visual-studio.md)  
[Vorschau der Änderungen](../../ide/preview-changes.md)