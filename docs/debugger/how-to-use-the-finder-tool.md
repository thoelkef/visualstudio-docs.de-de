---
title: 'Vorgehensweise: Verwenden des Suchtools | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Window Finder Tool
ms.assetid: 5841926b-08c3-4e43-88bd-4223d04f9aef
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5bf3fcf00486ebb8ec54f2d692d483a7f9cf18d7
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63387653"
---
# <a name="how-to-use-the-finder-tool"></a>Vorgehensweise: Verwenden des Suchtools
Können Sie das Suchtool im der **Fenster Suchen** Dialogfeld zum Anzeigen von Eigenschaften oder Meldungen. Das Suchtool können auch deaktivierte untergeordnete Fenster Suchen und erkennen, welches Fenster zum Hervorheben, deaktivierte untergeordnete Fenster überlappen.

 ![Spy++&#43; &#43; Dialogfeld Fenster Suchen](../debugger/media/icon_spy--_find.png "Icon_Spy ++ _Find") Suchtool im Dialogfeld "Fenster Suchen"

 Die obige Abbildung zeigt das Dialogfeld "Fenster Suchen" nach Schritt 3 weiter unten.

### <a name="to-display-window-properties-or-messages"></a>Zum Anzeigen von Eigenschaften oder Meldungen

1. Ordnen Sie die Fenster, sodass Spy++ und das Zielfenster angezeigt werden.

2. Von der **Spy** Menü wählen **Fenster Suchen**.

    Die [Dialogfeld Fenster Suchen](../debugger/find-window-dialog-box.md) wird geöffnet.

3. Ziehen Sie die **Suchtool** über das Zielfenster.

    Wie Sie das Tool, ziehen Sie die **Fenster Suchen** Dialogfeld zeigt die Details für das ausgewählte Fenster.

   - ODER

     Wenn Sie das Handle des Fensters haben (z. B. aus dem Debugger kopiert) überprüfen möchten, geben Sie ihn in das **behandeln** Textfeld.

   > [!TIP]
   > Um die Übersichtlichkeit des Bildschirms, wählen Sie die **Spy++ ausblenden** Option. Diese Option verbirgt die Spy++-Hauptfenster, sondern nur die **Fenster Suchen** Dialogfeld sichtbar ist, zusätzlich zu anderen Anwendungen. Spy++-Hauptfenster wird wiederhergestellt, wenn Sie auf **OK** oder **Abbrechen**, oder wenn Sie das Kontrollkästchen der **Spy++ ausblenden** Option.

4. Klicken Sie unter **anzeigen**, wählen Sie entweder **Eigenschaften** oder **Nachrichten**.

5. Klicken Sie auf **OK**.

    Wenn Sie ausgewählt haben **Eigenschaften**, [Dialogfeld "Fenstereigenschaften"](../debugger/window-properties-dialog-box.md) wird geöffnet. Wenn Sie ausgewählt haben **Nachrichten**, [Meldungsansicht](../debugger/messages-view.md) Fenster wird geöffnet.

## <a name="see-also"></a>Siehe auch
- [Spy++-Ansichten](../debugger/spy-increment-views.md)
- [Verwenden von Spy++](../debugger/using-spy-increment.md)
- [Spy++-Referenz](../debugger/spy-increment-reference.md)