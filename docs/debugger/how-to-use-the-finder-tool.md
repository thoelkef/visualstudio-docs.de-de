---
title: 'Gewusst wie: Verwenden des Suchtools | Microsoft-Dokumentation'
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
ms.openlocfilehash: f96fe87137c6b14e32fb2648e93c54a1c5b094a0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72732162"
---
# <a name="how-to-use-the-finder-tool"></a>Gewusst wie: Verwenden des Suchtools
Sie können das Suchtool im Dialogfeld " **Fenster suchen** " verwenden, um Fenster Eigenschaften oder Meldungen anzuzeigen. Das Suchtool kann auch deaktivierte untergeordnete Fenster Suchen und erkennen, welches Fenster hervorgehoben werden soll, wenn sich deaktivierte untergeordnete Fenster

 ![&#43; Spy&#43; -Fenster suchen (Dialog Feld](../debugger/media/icon_spy--_find.png "Icon_Spy + + _Find") ) Finder-Tool im Dialogfeld "Fenster Suchen"

 Die obige Abbildung zeigt das Dialogfeld "Fenster Suchen" nach Schritt 3.

### <a name="to-display-window-properties-or-messages"></a>So zeigen Sie Fenster Eigenschaften oder Meldungen an

1. Ordnen Sie Ihre Fenster so an, dass sowohl Spy + + als auch das Zielfenster sichtbar sind.

2. Wählen Sie im Menü " **Spy** " die Option **Fenster suchen**aus.

    Das [Dialog Feld Fenster suchen](../debugger/find-window-dialog-box.md) wird geöffnet.

3. Ziehen Sie das **Suchtool** über das Zielfenster.

    Wenn Sie das Tool ziehen, werden im Dialogfeld " **Fenster suchen** " Details im ausgewählten Fenster angezeigt.

   - ODER

     Wenn Sie über das Handle des Fensters verfügen, das Sie untersuchen möchten (z. b. aus dem Debugger kopiert), geben Sie es in das Textfeld **handle** ein.

   > [!TIP]
   > Wählen Sie die Option **Spy ausblenden** aus, um die Bildschirm Übersichtlichkeit zu verringern. Mit dieser Option wird das Hauptfenster Spy + + verborgen, sodass nur das Dialogfeld " **Fenster suchen** " auf Ihren anderen Anwendungen angezeigt wird. Das Spy + +-Hauptfenster wird wieder hergestellt, wenn Sie auf " **OK** " oder " **Abbrechen**" klicken, oder wenn Sie die Option **Spy + + ausblenden** deaktivieren.

4. Wählen Sie unter **anzeigen**die Option **Eigenschaften** oder **Nachrichten**aus.

5. Klicken Sie auf **OK**.

    Wenn Sie **Eigenschaften**ausgewählt haben, wird das [Dialog Feld Fenster Eigenschaften](../debugger/window-properties-dialog-box.md) geöffnet. Wenn Sie **Nachrichten**ausgewählt haben, wird ein Fenster für die [Nachrichtenansicht](../debugger/messages-view.md) geöffnet.

## <a name="see-also"></a>Siehe auch
- [Spy++-Ansichten](../debugger/spy-increment-views.md)
- [Verwenden von Spy++](../debugger/using-spy-increment.md)
- [Spy++-Referenz](../debugger/spy-increment-reference.md)