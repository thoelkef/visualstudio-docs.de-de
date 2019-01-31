---
title: Spy++-Symbolleiste | Microsoft-Dokumentation
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
ms.openlocfilehash: a7a3213d614caa19fb6df77a72efd05e36484c77
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54982675"
---
# <a name="spy-toolbar"></a>Spy++-Symbolleiste
Die Symbolleiste wird in der Menüleiste in Spy++ angezeigt. Zum Anzeigen oder Ausblenden der Symbolleiste auf die **Ansicht** Menü klicken Sie auf **Symbolleiste**.  
  
 Die folgenden Steuerelemente sind auf der Symbolleiste verfügbar.  
  
## <a name="uielement-list"></a>UIElement-Liste  
  
|Schaltfläche|Effekt|  
|------------|------------|  
|![Spy++&#43; &#43; Windows-Schaltfläche](../debugger/media/icon_spy--_windows.gif "Icon_Spy ++ _Windows")|Zeigt eine Strukturansicht der Steuerelemente für Windows und im System an. Weitere Informationen finden Sie unter [Windows-Ansicht](../debugger/windows-view.md).|  
|![Spy++&#43; &#43; verarbeitet Schaltfläche](../debugger/media/icon_spy--_processes.gif "Icon_Spy ++ _Processes")|Zeigt eine Strukturansicht der Prozesse im System an. Weitere Informationen finden Sie unter [Prozessansicht](../debugger/processes-view.md).|  
|![Spy++&#43; &#43; Threads Schaltfläche](../debugger/media/icon_spy--_threads.gif "Icon_Spy ++ _Threads")|Zeigt eine Strukturansicht der Threads im System an. Weitere Informationen finden Sie unter [Ansicht "Threads"](../debugger/threads-view.md).|  
|![Spy++&#43; &#43; Nachrichten Schaltfläche](../debugger/media/icon_spy--_messages.gif "Icon_Spy ++ _Messages")|Erstellt ein Fenster zum Anzeigen von Windows-Meldungen und öffnet die **Meldungsoptionen** Dialogfeld, sodass Sie das Fenster, deren Meldungen werden angezeigt, und wählen Sie auch andere Optionen, auswählen können. Weitere Informationen finden Sie unter [Meldungsansicht](../debugger/messages-view.md).|  
|![Spy++&#43; &#43; starten Sie die Schaltfläche "Protokoll"](../debugger/media/icon_spy--_startlog.gif "Icon_Spy ++ _StartLog")|Startet die nachrichtenprotokollierung und zeigt den Nachrichtenstream. Dieses Steuerelement ist nur verfügbar, wenn eine **Nachrichten** Fenster ist das aktive Fenster. Weitere Informationen finden Sie unter [Vorgehensweise: Starten und Beenden der Meldungsprotokollanzeige](../debugger/how-to-start-and-stop-the-message-log-display.md).|  
|![Spy++&#43; &#43; beenden Sie die Schaltfläche "Protokoll"](../debugger/media/icon_spy--_stoplog.gif "Icon_Spy ++ _StopLog")|Beendet den Nachrichteneigenschaften Protokollierung und die Anzeige des nachrichtendatenstroms. Dieses Steuerelement ist nur verfügbar, wenn eine **Nachrichten** Fenster ist das aktive Fenster. Weitere Informationen finden Sie unter [Vorgehensweise: Starten und Beenden der Meldungsprotokollanzeige](../debugger/how-to-start-and-stop-the-message-log-display.md).|  
|![Spy++&#43; &#43; protokollieren Sie die Schaltfläche "Optionen"](../debugger/media/icon_spy--_logoptions.gif "Icon_Spy ++ _LogOptions")|Zeigt die [Meldungsoptionen](../debugger/message-options-dialog-box.md) Dialogfeld. Verwenden Sie das Dialogfeld zum Auswählen von Windows und Nachrichtentypen für die Anzeige. Dieses Steuerelement ist nur verfügbar, wenn eine **Nachrichten** Fenster ist das aktive Fenster.|  
|![Spy++&#43; &#43; deaktivieren Sie die Schaltfläche "Protokoll"](../debugger/media/spy--_clearlog.gif "Spy-_ClearLog")|Löscht den Inhalt des aktiven **Nachrichten** Fenster. Dieses Steuerelement ist nur verfügbar, wenn eine **Nachrichten** Fenster ist das aktive Fenster.|  
|![Spy++&#43; &#43; finden Sie die Schaltfläche "Fenster"](../debugger/media/icon_spy--_findwindow.gif "Icon_Spy ++ _FindWindow")|Öffnet die [Fenster Suchen](../debugger/find-window-dialog-box.md) Dialogfeld können Sie Kriterien für die Fenstersuche festlegen und Anzeigen von Eigenschaften oder Meldungen. Weitere Informationen finden Sie unter [Vorgehensweise: Verwenden des Suchtools](../debugger/how-to-use-the-finder-tool.md).|  
|![Spy++&#43; &#43; finden Sie erste Fensterschaltfläche](../debugger/media/icon_spy--_window.gif "Icon_Spy ++ _Window")|Durchsucht die aktuelle Ansicht nach übereinstimmenden Fenster, Prozesses, Threads, oder einer Nachricht an.|  
|![Spy++&#43; &#43; finden Sie weiter Fensterschaltfläche](../debugger/media/icon_spy--_nextwindow.gif "Icon_Spy ++ _NextWindow")|Durchsucht die aktuelle Ansicht nach dem nächsten übereinstimmenden Fenster, Prozess, Thread oder Nachricht. Dieses Steuerelement (und den entsprechenden Menübefehl) ist verfügbar, nur, wenn ein gültiges Suchergebnis, das nicht eindeutig ist. Z. B. Wenn Sie ein Fensterhandle als Suchkriterium in der Fensterstruktur im verwenden, eindeutige Ergebnisse erzeugt, da es nur ein Fenster, in dem Fenster dieses Handle hat ist; In diesem Fall **Weitersuchen** ist nicht verfügbar.|  
|![Spy++&#43; &#43; finden Sie die Schaltfläche "Vorheriges Fenster"](../debugger/media/icon_spy--_prevwindow.gif "Icon_Spy ++ _PrevWindow")|Durchsucht die aktuelle Ansicht nach dem vorherigen übereinstimmenden Fenster, Prozess, Thread oder Nachricht. Dieses Steuerelement (und den entsprechenden Menübefehl) ist verfügbar, nur, wenn ein gültiges Suchergebnis, das nicht eindeutig ist. Z. B. Wenn Sie ein Fensterhandle als Suchkriterium in der Fensterstruktur im verwenden, eindeutige Ergebnisse erzeugt, da es nur ein Fenster, in dem Fenster dieses Handle hat ist; In diesem Fall **Vorheriges suchen** ist nicht verfügbar.|  
|![Spy++&#43; &#43; Eigenschaft Schaltfläche "Explorer"](../debugger/media/icon_spy--_propexp.gif "Icon_Spy ++ _PropExp")|Zeigt die Eigenschaften des Fensters, das in der Windows-Ansicht ausgewählt ist.|  
|![Spy++&#43; &#43; Schaltfläche "Aktualisieren"](../debugger/media/icon_spy--_refresh.gif "Icon_Spy ++ _Refresh")|Aktualisiert die Systemsichten.|  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von Spy++](../debugger/using-spy-increment.md)   
 [Spy++-Ansichten](../debugger/spy-increment-views.md)   
 [Spy++-Referenz](../debugger/spy-increment-reference.md)