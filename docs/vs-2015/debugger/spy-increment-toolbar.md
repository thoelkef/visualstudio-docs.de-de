---
title: Spy++-Symbolleiste | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Spy++ toolbar
ms.assetid: 949c18fb-bb25-42ed-9130-c4a47869f24d
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 05dc7dd74af20c76a3b673d5960cd88331ad7d51
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51763331"
---
# <a name="spy-toolbar"></a>Spy++-Symbolleiste
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Symbolleiste wird in der Menüleiste in Spy++ angezeigt. Zum Anzeigen oder Ausblenden der Symbolleiste auf die **Ansicht** Menü klicken Sie auf **Symbolleiste**.  
  
 Die folgenden Steuerelemente sind auf der Symbolleiste verfügbar.  
  
## <a name="uielement-list"></a>UIElement-Liste  
  
|Schaltfläche|Effekt|  
|------------|------------|  
|![Spy++&#43; &#43; Windows-Schaltfläche](../debugger/media/icon-spy-windows.gif "Icon_Spy ++ _Windows")|Zeigt eine Strukturansicht der Steuerelemente für Windows und im System an. Weitere Informationen finden Sie unter [Windows-Ansicht](../debugger/windows-view.md).|  
|![Spy++&#43; &#43; verarbeitet Schaltfläche](../debugger/media/icon-spy-processes.gif "Icon_Spy ++ _Processes")|Zeigt eine Strukturansicht der Prozesse im System an. Weitere Informationen finden Sie unter [Prozessansicht](../debugger/processes-view.md).|  
|![Spy++&#43; &#43; Threads Schaltfläche](../debugger/media/icon-spy-threads.gif "Icon_Spy ++ _Threads")|Zeigt eine Strukturansicht der Threads im System an. Weitere Informationen finden Sie unter [Ansicht "Threads"](../debugger/threads-view.md).|  
|![Spy++&#43; &#43; Nachrichten Schaltfläche](../debugger/media/icon-spy-messages.gif "Icon_Spy ++ _Messages")|Erstellt ein Fenster zum Anzeigen von Windows-Meldungen und öffnet die **Meldungsoptionen** Dialogfeld, sodass Sie das Fenster, deren Meldungen werden angezeigt, und wählen Sie auch andere Optionen, auswählen können. Weitere Informationen finden Sie unter [Meldungsansicht](../debugger/messages-view.md).|  
|![Spy++&#43; &#43; starten Sie die Schaltfläche "Protokoll"](../debugger/media/icon-spy-startlog.gif "Icon_Spy ++ _StartLog")|Startet die nachrichtenprotokollierung und zeigt den Nachrichtenstream. Dieses Steuerelement ist nur verfügbar, wenn eine **Nachrichten** Fenster ist das aktive Fenster. Weitere Informationen finden Sie unter [Vorgehensweise: Starten und Beenden der Meldungsprotokollanzeige](../debugger/how-to-start-and-stop-the-message-log-display.md).|  
|![Spy++&#43; &#43; beenden Sie die Schaltfläche "Protokoll"](../debugger/media/icon-spy-stoplog.gif "Icon_Spy ++ _StopLog")|Beendet den Nachrichteneigenschaften Protokollierung und die Anzeige des nachrichtendatenstroms. Dieses Steuerelement ist nur verfügbar, wenn eine **Nachrichten** Fenster ist das aktive Fenster. Weitere Informationen finden Sie unter [Vorgehensweise: Starten und Beenden der Meldungsprotokollanzeige](../debugger/how-to-start-and-stop-the-message-log-display.md).|  
|![Spy++&#43; &#43; protokollieren Sie die Schaltfläche "Optionen"](../debugger/media/icon-spy-logoptions.gif "Icon_Spy ++ _LogOptions")|Zeigt die [Meldungsoptionen](../debugger/message-options-dialog-box.md) Dialogfeld. Verwenden Sie das Dialogfeld zum Auswählen von Windows und Nachrichtentypen für die Anzeige. Dieses Steuerelement ist nur verfügbar, wenn eine **Nachrichten** Fenster ist das aktive Fenster.|  
|![Spy++&#43; &#43; deaktivieren Sie die Schaltfläche "Protokoll"](../debugger/media/spy-clearlog.gif "Spy-_ClearLog")|Löscht den Inhalt des aktiven **Nachrichten** Fenster. Dieses Steuerelement ist nur verfügbar, wenn eine **Nachrichten** Fenster ist das aktive Fenster.|  
|![Spy++&#43; &#43; finden Sie die Schaltfläche "Fenster"](../debugger/media/icon-spy-findwindow.gif "Icon_Spy ++ _FindWindow")|Öffnet die [Fenster Suchen](../debugger/find-window-dialog-box.md) Dialogfeld können Sie Kriterien für die Fenstersuche festlegen und Anzeigen von Eigenschaften oder Meldungen. Weitere Informationen finden Sie unter [Vorgehensweise: Verwenden des Suchtools](../debugger/how-to-use-the-finder-tool.md).|  
|![Spy++&#43; &#43; finden Sie erste Fensterschaltfläche](../debugger/media/icon-spy-window.gif "Icon_Spy ++ _Window")|Durchsucht die aktuelle Ansicht nach übereinstimmenden Fenster, Prozesses, Threads, oder einer Nachricht an.|  
|![Spy++&#43; &#43; finden Sie weiter Fensterschaltfläche](../debugger/media/icon-spy-nextwindow.gif "Icon_Spy ++ _NextWindow")|Durchsucht die aktuelle Ansicht nach dem nächsten übereinstimmenden Fenster, Prozess, Thread oder Nachricht. Dieses Steuerelement (und den entsprechenden Menübefehl) ist verfügbar, nur, wenn ein gültiges Suchergebnis, das nicht eindeutig ist. Z. B. Wenn Sie ein Fensterhandle als Suchkriterium in der Fensterstruktur im verwenden, eindeutige Ergebnisse erzeugt, da es nur ein Fenster, in dem Fenster dieses Handle hat ist; In diesem Fall **Weitersuchen** ist nicht verfügbar.|  
|![Spy++&#43; &#43; finden Sie die Schaltfläche "Vorheriges Fenster"](../debugger/media/icon-spy-prevwindow.gif "Icon_Spy ++ _PrevWindow")|Durchsucht die aktuelle Ansicht nach dem vorherigen übereinstimmenden Fenster, Prozess, Thread oder Nachricht. Dieses Steuerelement (und den entsprechenden Menübefehl) ist verfügbar, nur, wenn ein gültiges Suchergebnis, das nicht eindeutig ist. Z. B. Wenn Sie ein Fensterhandle als Suchkriterium in der Fensterstruktur im verwenden, eindeutige Ergebnisse erzeugt, da es nur ein Fenster, in dem Fenster dieses Handle hat ist; In diesem Fall **Vorheriges suchen** ist nicht verfügbar.|  
|![Spy++&#43; &#43; Eigenschaft Schaltfläche "Explorer"](../debugger/media/icon-spy-propexp.gif "Icon_Spy ++ _PropExp")|Zeigt die Eigenschaften des Fensters, das in der Windows-Ansicht ausgewählt ist.|  
|![Spy++&#43; &#43; Schaltfläche "Aktualisieren"](../debugger/media/icon-spy-refresh.gif "Icon_Spy ++ _Refresh")|Aktualisiert die Systemsichten.|  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von Spy++](../debugger/using-spy-increment.md)   
 [Spy++-Ansichten](../debugger/spy-increment-views.md)   
 [Spy++-Referenz](../debugger/spy-increment-reference.md)



