---
title: "Entfernen eines Refactorings für nicht erreichbaren Code für C# in Visual Studio | Microsoft-Dokumentation"
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
ms.openlocfilehash: 12b6910aad6399b72b3e4bc10e6b857cc98c09bb
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2018
---
# <a name="remove-unreachable-code-in-c"></a>Entfernen von nicht erreichbarem Code in C# #

**Beschreibung**: Es wird Code entfernt, der nie ausgeführt wird.

**Hintergrund**: Ihr Programm enthält keinen Pfad zu einem bestimmten Codeausschnitt, weshalb dieser Codeausschnitt nicht benötigt wird.

**Vorteile**: Die Lesbarkeit und Verwaltbarkeit werden durch das Entfernen eines überflüssigen, nie ausgeführten Code verbessert.

**Vorgehensweise**:

1. Platzieren Sie den Cursor an eine beliebige Stelle im ausgeblendeten, nicht erreichbaren Code:

![Ausgeblendeter nicht erreichbarer Code](media/unreachablecode-faded-cs.png)

1. Führen Sie dann eine der folgenden Aktionen aus:
   * **Tastatur**
     * Drücken Sie **STRG+.**, um das Menü **Schnellaktionen und Refactorings** aufzurufen, und wählen Sie im Popupvorschaufenster **Nicht erreichbaren Code entfernen** aus.
   * **Maus**
     * Klicken Sie mit der rechten Maustaste auf den Code, und wählen Sie das Menü **Schnellaktionen und Refactorings** sowie im Popupvorschaufenster **Nicht erreichbaren Code entfernen** aus.

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