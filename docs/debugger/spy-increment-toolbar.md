---
title: Spy++-Symbolleiste | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Spy++ toolbar
ms.assetid: 949c18fb-bb25-42ed-9130-c4a47869f24d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 7a9d9331e8767c4d815a6f62b7952414ced966d0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="spy-toolbar"></a>Spy++-Symbolleiste
Die Symbolleiste wird unterhalb der Menüleiste in Spy++ angezeigt. Zum Anzeigen oder Ausblenden der Symbolleiste auf die **Ansicht** Menü klicken Sie auf **Symbolleiste**.  
  
 Die folgenden Steuerelemente werden auf der Symbolleiste verfügbar.  
  
## <a name="uielement-list"></a>UIElement-Liste  
  
|Schaltfläche|Effekt|  
|------------|------------|  
|![Spy++ &#43; &#43; Windows-Taste](../debugger/media/icon_spy--_windows.gif "Icon_Spy ++ _Windows")|Zeigt eine Strukturansicht der Steuerelemente für Windows und im System an. Weitere Informationen finden Sie unter [Fensteransicht](../debugger/windows-view.md).|  
|![Spy++ &#43; &#43; Schaltfläche verarbeitet](../debugger/media/icon_spy--_processes.gif "Icon_Spy ++ _Processes")|Zeigt eine Strukturansicht der Prozesse im System an. Weitere Informationen finden Sie unter [Prozessansicht](../debugger/processes-view.md).|  
|![Spy++ &#43; &#43; Schaltfläche Threads](../debugger/media/icon_spy--_threads.gif "Icon_Spy ++ _Threads")|Zeigt eine Strukturansicht der Threads im System an. Weitere Informationen finden Sie unter [Threadansicht](../debugger/threads-view.md).|  
|![Spy++ &#43; &#43; Schaltfläche Nachrichten](../debugger/media/icon_spy--_messages.gif "Icon_Spy ++ _Messages")|Erstellt ein Fenster zum Anzeigen von fenstermeldungen und öffnet die **Meldungsoptionen** Dialogfeld, sodass Sie das Fenster auswählen können, deren Meldungen werden angezeigt, und wählen Sie auch andere Optionen. Weitere Informationen finden Sie unter [Ansicht "Nachrichten"](../debugger/messages-view.md).|  
|![Spy++ &#43; &#43; Starten Sie die Schaltfläche "Protokoll"](../debugger/media/icon_spy--_startlog.gif "Icon_Spy ++ _StartLog")|Startet die nachrichtenprotokollierung und zeigt den Nachrichtenstream an. Dieses Steuerelement ist nur verfügbar, wenn eine **Nachrichten** Fenster das aktive Fenster ist. Weitere Informationen finden Sie unter [Vorgehensweise: Starten und Beenden der Meldungsprotokollanzeige](../debugger/how-to-start-and-stop-the-message-log-display.md).|  
|![Spy++ &#43; &#43; Beenden Sie die Schaltfläche "Protokoll"](../debugger/media/icon_spy--_stoplog.gif "Icon_Spy ++ _StopLog")|Beendet Nachricht protokollieren und die Anzeige des nachrichtendatenstroms. Dieses Steuerelement ist nur verfügbar, wenn eine **Nachrichten** Fenster das aktive Fenster ist. Weitere Informationen finden Sie unter [Vorgehensweise: Starten und Beenden der Meldungsprotokollanzeige](../debugger/how-to-start-and-stop-the-message-log-display.md).|  
|![Spy++ &#43; &#43; Protokollieren Sie die Schaltfläche "Optionen"](../debugger/media/icon_spy--_logoptions.gif "Icon_Spy ++ _LogOptions")|Zeigt die [Meldungsoptionen](../debugger/message-options-dialog-box.md) (Dialogfeld). Verwenden Sie dieses Dialogfeld zum Auswählen von Windows und Nachrichtentypen für die Anzeige. Dieses Steuerelement ist nur verfügbar, wenn eine **Nachrichten** Fenster das aktive Fenster ist.|  
|![Spy++ &#43; &#43; Deaktivieren Sie die Schaltfläche "Protokoll"](../debugger/media/spy--_clearlog.gif "Spy++ ++ _ClearLog")|Löscht den Inhalt des aktiven **Nachrichten** Fenster. Dieses Steuerelement ist nur verfügbar, wenn eine **Nachrichten** Fenster das aktive Fenster ist.|  
|![Spy++ &#43; &#43; Fensterschaltfläche "Suchen"](../debugger/media/icon_spy--_findwindow.gif "Icon_Spy ++ _FindWindow")|Öffnet die ["Fenster Suchen"](../debugger/find-window-dialog-box.md) (Dialogfeld), können Sie die Fenster Suchkriterien festlegen und Anzeigen von Eigenschaften oder Nachrichten. Weitere Informationen finden Sie unter [wie: Verwenden des Suchtools](../debugger/how-to-use-the-finder-tool.md).|  
|![Spy++ &#43; &#43; Erste Fensterschaltfläche "Suchen"](../debugger/media/icon_spy--_window.gif "Icon_Spy ++ _Window")|Durchsucht die aktuelle Ansicht für eine entsprechendes Fenster, Prozess, Thread oder Nachricht.|  
|![Spy++ &#43; &#43; Nächste Fensterschaltfläche "Suchen"](../debugger/media/icon_spy--_nextwindow.gif "Icon_Spy ++ _NextWindow")|Durchsucht die aktuelle Ansicht für den nächsten übereinstimmenden Fenster, Prozess, Thread oder Nachricht. Dieses Steuerelement (und der zugehörige Menübefehl) ist verfügbar, nur, wenn ein gültiges Suchergebnis, das nicht eindeutig ist. Beispielsweise bei Verwendung von ein Fensterhandle als Suchkriterium in der Fensterstruktur im eindeutige Ergebnisse erzeugt, da nur ein Fenster, in dem Fenster dieses Handle hat vorhanden ist; in dieser Instanz **Weitersuchen** ist nicht verfügbar.|  
|![Spy++ &#43; &#43; Vorherigen Fensterschaltfläche "Suchen"](../debugger/media/icon_spy--_prevwindow.gif "Icon_Spy ++ _PrevWindow")|Durchsucht die aktuelle Ansicht für die vorherigen übereinstimmenden Fenster, Prozess, Thread oder Nachricht. Dieses Steuerelement (und der zugehörige Menübefehl) ist verfügbar, nur, wenn ein gültiges Suchergebnis, das nicht eindeutig ist. Beispielsweise bei Verwendung von ein Fensterhandle als Suchkriterium in der Fensterstruktur im eindeutige Ergebnisse erzeugt, da nur ein Fenster, in dem Fenster dieses Handle hat vorhanden ist; in dieser Instanz **Vorheriges suchen** ist nicht verfügbar.|  
|![Spy++ &#43; &#43; Schaltfläche "Explorer"-Eigenschaft](../debugger/media/icon_spy--_propexp.gif "Icon_Spy ++ _PropExp")|Zeigt die Eigenschaften des Fensters, das in der Ansicht ausgewählt ist.|  
|![Spy++ &#43; &#43; Schaltfläche "Aktualisieren"](../debugger/media/icon_spy--_refresh.gif "Icon_Spy ++ _Refresh")|Aktualisiert die Systemsichten.|  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von Spy++](../debugger/using-spy-increment.md)   
 [Spy++-Ansichten](../debugger/spy-increment-views.md)   
 [Spy++-Referenz](../debugger/spy-increment-reference.md)