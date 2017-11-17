---
title: "Inline temporäre Variable - Umgestaltung (c#) | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0182179f-f74f-47a2-a1dc-b60c86f9abaf
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e6e9ed28a42aa3d7521a059b668eed8ae1d28b8e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="inline-a-temporary-variable-with-c"></a>Inline eine temporäre Variable mit c# #
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
[Refactoring (C#)](../refactoring-csharp.md)