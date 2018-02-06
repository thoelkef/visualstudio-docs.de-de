---
title: "Ersetzen einer temporären Variable durch ihren Wert in Visual Basic | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7553a67892322a1acb2db33d7a16b399b6f0b23a
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2018
---
# <a name="inline-a-temporary-variable-in-visual-basic"></a>Inlinesetzen einer temporären Variable in Visual Basic

**Beschreibung**: Hiermit können Sie eine temporäre Variable entfernen und diese stattdessen durch ihren Wert ersetzen.

**Hintergrund**: Durch die Verwendung der temporären Variable ist der Code schwieriger zu verstehen.

**Vorteile**: Durch das Entfernen einer temporären Variablen kann die Lesbarkeit des Codes verbessert werden.

**Vorgehensweise**:

1. Markieren Sie die inline zu setzende temporäre Variable, oder platzieren Sie den Textcursor in die Variable:

   ![Markierter Code](media/inline-highlight-vb.png)

1. Führen Sie dann eine der folgenden Aktionen aus:
   * **Tastatur**
     * Drücken Sie **STRG+.**, um das Menü **Schnellaktionen und Refactorings** aufzurufen.
   * **Maus**
     * Klicken Sie mit der rechten Maustaste auf den Code, und wählen Sie das Menü **Schnellaktionen und Refactorings** aus.

1. Wählen Sie im Popupvorschaufenster **Inline temporär variabel** aus.

   Die Variable wird entfernt, und ihre Vorkommen werden sofort durch den Wert der Variable ersetzt.

   ![Ergebnis des Inlinevorgangs](media/inline-result-vb.png)

## <a name="see-also"></a>Siehe auch

[Refactoring](../refactoring-in-visual-studio.md)