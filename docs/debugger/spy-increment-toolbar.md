---
title: "Spy++ Toolbar | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Spy++ toolbar"
ms.assetid: 949c18fb-bb25-42ed-9130-c4a47869f24d
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Spy++ Toolbar
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Symbolleiste wird unter der Menüleiste in Spy\+\+ angezeigt.  Um die Symbolleiste zu deaktivieren oder auszublenden, klicken Sie im Menü **Ansicht** auf **Symbolleiste**.  
  
 Die folgenden Steuerelemente sind auf der Symbolleiste verfügbar.  
  
## UIElement-Liste  
  
|Button|Effect|  
|------------|------------|  
|![Spy&#43;&#43;&#45;Schaltfläche "Fenster"](../debugger/media/icon_spy--_windows.png "Icon\_Spy\+\+\_Windows")|Zeigt eine Strukturansicht der Fenster und Steuerelemente im System an.  Weitere Informationen finden Sie unter [Windows View](../debugger/windows-view.md).|  
|![Spy&#43;&#43;&#45;Schaltfläche "Prozesse"](../debugger/media/icon_spy--_processes.png "Icon\_Spy\+\+\_Processes")|Zeigt eine Strukturansicht der Prozesse im System an.  Weitere Informationen finden Sie unter [Processes View](../debugger/processes-view.md).|  
|![Spy&#43;&#43;&#45;Schaltfläche "Threads"](../debugger/media/icon_spy--_threads.png "Icon\_Spy\+\+\_Threads")|Zeigt eine Strukturansicht der Threads im System an.  Weitere Informationen finden Sie unter [Threads View](../debugger/threads-view.md).|  
|![Spy&#43;&#43;&#45;Schaltfläche "Meldungen"](../debugger/media/icon_spy--_messages.png "Icon\_Spy\+\+\_Messages")|Erstellt ein Fenster zum Anzeigen von Fenstermeldungen und öffnet das Dialogfeld **Meldungsoptionen**, sodass das Fenster, dessen Meldungen angezeigt werden, und weitere Optionen ausgewählt werden können.  Weitere Informationen finden Sie unter [Messages View](../debugger/messages-view.md).|  
|![Spy&#43;&#43;&#45;Schaltfläche „Protokollierung starten“](../debugger/media/icon_spy--_startlog.png "Icon\_Spy\+\+\_StartLog")|Startet die Meldungsprotokollierung und zeigt den Meldungsstream an.  Dieses Steuerelement ist nur verfügbar, wenn das Fenster **Meldungen** das aktive Fenster ist.  Weitere Informationen finden Sie unter [How to: Start and Stop the Message Log Display](../debugger/how-to-start-and-stop-the-message-log-display.md).|  
|![Spy&#43;&#43;&#45;Schaltfläche „Protokollierung beenden“](../debugger/media/icon_spy--_stoplog.png "Icon\_Spy\+\+\_StopLog")|Beendet die Meldungsprotokollierung und die Anzeige des Meldungsstreams.  Dieses Steuerelement ist nur verfügbar, wenn das Fenster **Meldungen** das aktive Fenster ist.  Weitere Informationen finden Sie unter [How to: Start and Stop the Message Log Display](../debugger/how-to-start-and-stop-the-message-log-display.md).|  
|![Spy&#43;&#43;&#45;Schaltfläche „Protokolloptionen“](../debugger/media/icon_spy--_logoptions.png "Icon\_Spy\+\+\_LogOptions")|Zeigt das Dialogfeld [Meldungsoptionen](../debugger/message-options-dialog-box.md) an.  Verwenden Sie dieses Dialogfeld, um Fenster und Meldungstypen zum Anzeigen auszuwählen.  Dieses Steuerelement ist nur verfügbar, wenn das Fenster **Meldungen** das aktive Fenster ist.|  
|![Spy&#43;&#43;&#45;Schaltfläche "Protokoll löschen"](../debugger/media/spy--_clearlog.png "Spy\+\+\_ClearLog")|Löscht den Inhalt des aktiven Fensters **Meldungen**.  Dieses Steuerelement ist nur verfügbar, wenn das Fenster **Meldungen** das aktive Fenster ist.|  
|![Spy&#43;&#43;&#45;Schaltfläche "Fenster suchen"](../debugger/media/icon_spy--_findwindow.png "Icon\_Spy\+\+\_FindWindow")|Öffnet das Dialogfeld [Fenster suchen](../debugger/find-window-dialog-box.md), in dem Sie Fenstersuchkriterien festlegen und Eigenschaften oder Meldungen anzeigen können.  Weitere Informationen finden Sie unter [How to: Use the Finder Tool](../debugger/how-to-use-the-finder-tool.md).|  
|![Spy&#43;&#43;&#45;Schaltfläche "Erstes Fenster suchen"](../debugger/media/icon_spy--_window.png "Icon\_Spy\+\+\_Window")|Sucht in der aktuellen Ansicht ein entsprechendes Fenster, einen entsprechenden Prozess, einen entsprechenden Thread oder eine entsprechende Meldung.|  
|![Spy&#43;&#43;&#45;Schaltfläche "Nächstes Fenster suchen"](../debugger/media/icon_spy--_nextwindow.png "Icon\_Spy\+\+\_NextWindow")|Sucht in der aktuellen Ansicht das nächste entsprechende Fenster, den nächsten entsprechenden Prozess, den nächsten entsprechenden Thread bzw. die nächste entsprechende Meldung.  Dieses Steuerelement \(und der zugehörige Menübefehl\) ist nur verfügbar, wenn ein gültiges Suchergebnis nicht eindeutig ist.  Wenn Sie beispielsweise ein Fensterhandle als Suchkriterium in der Fensterstruktur verwenden, erzeugt es eindeutige Ergebnisse, da nur ein Fenster in der Fensterstruktur über ein Handle verfügt. In dieser Instanz ist **Weitersuchen** nicht verfügbar.|  
|![Spy&#43;&#43; Schaltfläche "Vorheriges Fenster suchen"](../debugger/media/icon_spy--_prevwindow.png "Icon\_Spy\+\+\_PrevWindow")|Sucht in der aktuellen Ansicht das vorherige entsprechende Fenster, den vorherigen entsprechenden Prozess, den vorherigen entsprechenden Thread bzw. die vorherige entsprechende Meldung.  Dieses Steuerelement \(und der zugehörige Menübefehl\) ist nur verfügbar, wenn ein gültiges Suchergebnis nicht eindeutig ist.  Wenn Sie beispielsweise ein Fensterhandle als Suchkriterium in der Fensterstruktur verwenden, erzeugt es eindeutige Ergebnisse, da nur ein Fenster in der Fensterstruktur über ein Handle verfügt. In dieser Instanz ist **Vorheriges suchen** nicht verfügbar.|  
|![Spy&#43;&#43;&#45;Schaltfläche "Eigenschaften&#45;Explorer"](../debugger/media/icon_spy--_propexp.png "Icon\_Spy\+\+\_PropExp")|Zeigt die Eigenschaften des Fensters an, das in der Fensteransicht ausgewählt ist.|  
|![Spy&#43;&#43;&#45;Schaltfläche „Aktualisieren“](../debugger/media/icon_spy--_refresh.png "Icon\_Spy\+\+\_Refresh")|Aktualisiert die Systemansichten.|  
  
## Siehe auch  
 [Using Spy\+\+](../debugger/using-spy-increment.md)   
 [Spy\+\+ Views](../debugger/spy-increment-views.md)   
 [Spy\+\+ Reference](../debugger/spy-increment-reference.md)