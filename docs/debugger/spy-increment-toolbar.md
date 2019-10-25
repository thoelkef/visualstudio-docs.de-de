---
title: Spy + +-Symbolleiste | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Spy++ toolbar
ms.assetid: 949c18fb-bb25-42ed-9130-c4a47869f24d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4fa1dfe0917fece3c814678295c5abd6013b426b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72729739"
---
# <a name="spy-toolbar"></a>Spy++-Symbolleiste
Die Symbolleiste wird in Spy + + in der Menüleiste angezeigt. Klicken Sie im Menü **Ansicht** auf **Symbolleiste**, um die Symbolleiste anzuzeigen oder auszublenden.

 Die folgenden Steuerelemente sind auf der Symbolleiste verfügbar.

## <a name="uielement-list"></a>UIElement-Liste

|Schaltfläche|Effekt|
|------------|------------|
|![Spy&#43; &#43; Windows-Schaltfläche](../debugger/media/icon_spy--_windows.gif "Icon_Spy + + _Windows")|Zeigt eine Strukturansicht der Fenster und Steuerelemente im System an. Weitere Informationen finden Sie in der [Windows-Ansicht](../debugger/windows-view.md).|
|![Spy&#43; &#43; -Prozesse](../debugger/media/icon_spy--_processes.gif "Icon_Spy + + _Processes")|Zeigt eine Strukturansicht der Prozesse im System an. Weitere Informationen finden Sie in der [Ansicht "Prozesse](../debugger/processes-view.md)".|
|![Schalt&#43; &#43; Fläche Spy-Threads](../debugger/media/icon_spy--_threads.gif "Icon_Spy + + _Threads")|Zeigt eine Strukturansicht der Threads im System an. Weitere Informationen finden Sie in der [Thread Ansicht](../debugger/threads-view.md).|
|![Spy&#43; &#43; Messages-Schaltfläche](../debugger/media/icon_spy--_messages.gif "Icon_Spy + + _Messages")|Erstellt ein Fenster zum Anzeigen von Fenster Meldungen und öffnet das Dialogfeld **Nachrichten Optionen** , sodass Sie das Fenster, dessen Meldungen angezeigt werden, und andere Optionen auswählen können. Weitere Informationen finden Sie in der [Ansicht Meldungen](../debugger/messages-view.md).|
|![Schalt&#43; &#43; Fläche "Spy Start log"](../debugger/media/icon_spy--_startlog.gif "Icon_Spy + + _StartLog")|Startet die Nachrichten Protokollierung und zeigt den Nachrichten Datenstrom an. Dieses Steuerelement ist nur verfügbar, wenn ein **Nachrichten** Fenster das aktive Fenster ist. Weitere Informationen finden Sie unter Gewusst [wie: starten und Abbrechen der Nachrichtenprotokoll Anzeige](../debugger/how-to-start-and-stop-the-message-log-display.md).|
|![Spy&#43; &#43; -Schaltfläche "Abbrechen"](../debugger/media/icon_spy--_stoplog.gif "Icon_Spy + + _StopLog")|Beendet die Nachrichten Protokollierung und die Anzeige des Nachrichten Datenstroms. Dieses Steuerelement ist nur verfügbar, wenn ein **Nachrichten** Fenster das aktive Fenster ist. Weitere Informationen finden Sie unter Gewusst [wie: starten und Abbrechen der Nachrichtenprotokoll Anzeige](../debugger/how-to-start-and-stop-the-message-log-display.md).|
|![Schalt&#43; &#43; Fläche "Spy Log Options"](../debugger/media/icon_spy--_logoptions.gif "Icon_Spy + + _LogOptions")|Zeigt das Dialogfeld [Nachrichten Optionen](../debugger/message-options-dialog-box.md) an. Mithilfe dieses Dialog Felds können Sie Windows-und Nachrichten Typen für die Anzeige auswählen. Dieses Steuerelement ist nur verfügbar, wenn ein **Nachrichten** Fenster das aktive Fenster ist.|
|![Spy&#43; &#43; Clear log-Schaltfläche](../debugger/media/spy--_clearlog.gif "Spy + + _ClearLog")|Löscht den Inhalt des Fensters aktive **Nachrichten** . Dieses Steuerelement ist nur verfügbar, wenn ein **Nachrichten** Fenster das aktive Fenster ist.|
|![Spy&#43; &#43; -Schaltflächen Fenster](../debugger/media/icon_spy--_findwindow.gif "Icon_Spy + + _FindWindow")|Öffnet das Dialogfeld " [Fenster](../debugger/find-window-dialog-box.md) suchen", in dem Sie Suchkriterien für Fenster festlegen und Eigenschaften oder Meldungen anzeigen können. Weitere Informationen finden Sie unter Gewusst [wie: Verwenden des Suchtools](../debugger/how-to-use-the-finder-tool.md).|
|![Spy&#43; &#43; -Schaltfläche "erste Suche"](../debugger/media/icon_spy--_window.gif "Icon_Spy + + _Window")|Durchsucht die aktuelle Ansicht nach einem passenden Fenster, Prozess, Thread oder einer Nachricht.|
|![Spy&#43; &#43; -Schaltfläche "Nächstes suchen"](../debugger/media/icon_spy--_nextwindow.gif "Icon_Spy + + _NextWindow")|Durchsucht die aktuelle Ansicht nach dem nächsten übereinstimmenden Fenster, Prozess, Thread oder der Nachricht. Dieses Steuerelement (und der zugehörige Menübefehl) ist nur verfügbar, wenn ein gültiges Suchergebnis vorliegt, das nicht eindeutig ist. Wenn Sie z. b. ein Fenster Handle als Suchkriterium in der Fenster Struktur verwenden, werden eindeutige Ergebnisse erzeugt, da in der Fenster Struktur nur ein Fenster mit diesem Handle vorhanden ist. in dieser Instanz ist " **weiter suchen** " nicht verfügbar.|
|![Spy&#43; &#43; -Schaltfläche zum Suchen vorheriger Fenster](../debugger/media/icon_spy--_prevwindow.gif "Icon_Spy + + _PrevWindow")|Durchsucht die aktuelle Ansicht nach dem vorherigen übereinstimmenden Fenster, Prozess, Thread oder Nachricht. Dieses Steuerelement (und der zugehörige Menübefehl) ist nur verfügbar, wenn ein gültiges Suchergebnis vorliegt, das nicht eindeutig ist. Wenn Sie z. b. ein Fenster Handle als Suchkriterium in der Fenster Struktur verwenden, werden eindeutige Ergebnisse erzeugt, da in der Fenster Struktur nur ein Fenster mit diesem Handle vorhanden ist. in dieser Instanz ist die **Suche nach vorheriger** nicht verfügbar.|
|![Spy&#43; &#43; -Eigenschaften-Explorer](../debugger/media/icon_spy--_propexp.gif "Icon_Spy + + _PropExp")|Zeigt die Eigenschaften des Fensters an, das in der Windows-Ansicht ausgewählt ist.|
|![Spy&#43; &#43; Refresh-Schaltfläche](../debugger/media/icon_spy--_refresh.gif "Icon_Spy + + _Refresh")|Aktualisiert die System Sichten.|

## <a name="see-also"></a>Siehe auch
- [Verwenden von Spy++](../debugger/using-spy-increment.md)
- [Spy++-Ansichten](../debugger/spy-increment-views.md)
- [Spy++-Referenz](../debugger/spy-increment-reference.md)