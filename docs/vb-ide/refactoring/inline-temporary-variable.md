---
title: "Temporäre Variable für Inline - Umgestaltung (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a63d6407-5acb-4d5f-8c0e-ecedddc07177
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 574a1a41464ede08571e1c0201618d666fa7ad92
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="inline-a-temporary-variable-in-visual-basic"></a>Inline einer temporären Variablen in Visual Basic
**Was:** können Sie die Verwendung einer temporären Variablen zu entfernen und Ersetzen Sie es stattdessen mit den eigentlichen Code.

**Wann:** durch die Verwendung der temporären Variable wird den Code, die schwieriger zu verstehen.  

**Grund:** eine temporäre Variable entfernen möglicherweise Lesbarkeit des Codes in bestimmten Situationen

**Vorgehensweise:**

1. Markieren Sie, oder platzieren Sie den Textcursor innerhalb der temporären Variablen Inline zu setzen:

   ![Hervorgehobene code](media/inline_highlight.png)

1. Als Nächstes führen Sie eine der folgenden:
   * **Tastatur**
     * Drücken Sie **STRG +.** Trigger die **Schnellaktionen und Refactorings** Menü **temporären Variablen Inline** im Popupmenü Fenster Vorschau.
   * **Maus**
     * Mit der rechten Maustaste in des Codes, wählen Sie die **Schnellaktionen und Refactorings** , und wählen Sie im Menü **temporären Variablen Inline** im Popupmenü Fenster Vorschau.

   Die Variable wird entfernt, und ihre Verwendungen sofort durch den Wert der Variablen ersetzt.

   ![Inline-Ergebnis](media/inline_result.png)

## <a name="see-also"></a>Siehe auch
[Refactoring (Visual Basic)](../refactoring-vb.md)