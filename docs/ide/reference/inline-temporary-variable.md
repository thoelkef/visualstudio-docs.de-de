---
title: "Ersetzen einer temporären Variablen durch ihren Wert in Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 01/26/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: b66236847e597aeddb4e6f09c27e64e717fdb7d9
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="inline-a-temporary-variable-refactoring"></a>Inlinesetzen eines temporären Variablenrefactorings

Dieses Refactoring gilt für:

- C#

- Visual Basic

**Beschreibung**: Hiermit können Sie eine temporäre Variable entfernen und diese stattdessen durch ihren Wert ersetzen.

**Hintergrund**: Durch die Verwendung der temporären Variable ist der Code schwieriger zu verstehen.

**Vorteile**: Durch das Entfernen einer temporären Variablen kann die Lesbarkeit des Codes verbessert werden.

## <a name="how-to"></a>Vorgehensweise

1. Markieren Sie die inline zu setzende temporäre Variable, oder platzieren Sie den Textcursor in die Variable:

   - C#:

    ![Hervorgehobener Code – C#](media/inline-highlight-cs.png)

   - Visual Basic:

    ![Hervorgehobener Code – Visual Basic](media/inline-highlight-vb.png)

1. Führen Sie dann eine der folgenden Aktionen aus:

   - **Tastatur**
     - Drücken Sie **STRG+.**, um das Menü **Schnellaktionen und Refactorings** aufzurufen.
   - **Maus**
     - Klicken Sie mit der rechten Maustaste auf den Code, und wählen Sie das Menü **Schnellaktionen und Refactorings** aus.

1. Wählen Sie im Popupvorschaufenster **Inline temporär variabel** aus.

   Die Variable wird entfernt und sofort durch ihren Wert ersetzt.

   - C#:

    ![Ergebnis des Inlinevorgangs in C#](media/inline-result-cs.png)

   - Visual Basic:

    ![Ergebnis des Inlinevorgangs in Visual Basic](media/inline-result-vb.png)

## <a name="see-also"></a>Siehe auch

[Refactoring](../refactoring-in-visual-studio.md)