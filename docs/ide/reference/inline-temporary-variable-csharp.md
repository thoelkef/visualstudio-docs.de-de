---
title: "Ersetzen einer temporären Variable durch ihren Wert in C# | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 626224e8ed90196294f7b3ded245bb5272f70595
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/06/2018
---
# <a name="inline-a-temporary-variable-with-c"></a>Inlinesetzen einer temporären Variable mit C# #

**Beschreibung**: Hiermit können Sie eine temporäre Variable entfernen und diese stattdessen durch ihren Wert ersetzen.

**Hintergrund**: Durch die Verwendung der temporären Variable ist der Code schwieriger zu verstehen.

**Vorteile**: Durch das Entfernen einer temporären Variablen kann die Lesbarkeit des Codes verbessert werden.

**Vorgehensweise**:

1. Markieren Sie die inline zu setzende temporäre Variable, oder platzieren Sie den Textcursor in die Variable:

   ![Markierter Code](media/inline-highlight-cs.png)

1. Führen Sie dann eine der folgenden Aktionen aus:
   * **Tastatur**
     * Drücken Sie **STRG+.**, um das Menü **Schnellaktionen und Refactorings** aufzurufen.
   * **Maus**
     * Klicken Sie mit der rechten Maustaste auf den Code, und wählen Sie das Menü **Schnellaktionen und Refactorings** aus.

1. Wählen Sie im Popupvorschaufenster **Inline temporär variabel** aus.

   Die Variable wird entfernt, und ihre Vorkommen werden sofort durch den Wert der Variable ersetzt.

   ![Ergebnis des Inlinevorgangs](media/inline-result-cs.png)

## <a name="see-also"></a>Siehe auch

[Refactoring](../refactoring-in-visual-studio.md)