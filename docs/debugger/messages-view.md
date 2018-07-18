---
title: Der Meldungsansicht | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.externaltools.spyplus.messagesview
helpviewer_keywords:
- Messages view
ms.assetid: 14c2a786-c23a-4b2d-acad-8c32a856c70d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 31baccc88b25979dfc92fed6217bec3b0ef16a55
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
ms.locfileid: "31477078"
---
# <a name="messages-view"></a>Meldungsansicht
Jedes Fenster verfügt über einen Stream zugeordnete Meldung. Fenster mit einer Nachrichten zeigt diese Nachrichtenstream an. Das Fensterhandle, Meldungscode und Meldung werden angezeigt. Sie können eine Ansicht "Nachrichten" für einen Thread oder den Prozess sowie erstellen. Dadurch können Sie Nachrichten an alle Fenster, die einen bestimmten Prozess oder Thread besonders nützlich ist für das Erfassen von fenstermeldungen für die Initialisierung der Besitz anzuzeigen.  
  
 Fenster mit einer typischen Nachrichten wird unten angezeigt. Beachten Sie, dass die erste Spalte das Fensterhandle enthält und die zweite Spalte einen Message Authentication Code enthält (beschrieben [Meldungscodes](../debugger/message-codes.md)). Decodierte Nachrichtenparameter und Rückgabewerte werden auf der rechten Seite.  
  
 ![Spy++&#43; &#43; der Meldungsansicht](../debugger/media/spy--_messagesview.png "Spy++ ++ _MessagesView")  
Spy++-Meldungsansicht  
  
## <a name="procedures"></a>Verfahren  
  
#### <a name="to-open-a-messages-view-for-a-window-process-or-thread"></a>Öffnen Sie eine Ansicht "Nachrichten" für ein Fenster, Prozess oder thread  
  
1.  Verschieben des Fokus auf ein [Fensteransicht](../debugger/windows-view.md), [Prozessansicht](../debugger/processes-view.md), oder [Threadansicht](../debugger/threads-view.md) Fenster.  
  
2.  Suchen Sie den Knoten für das Element, dessen Nachrichten, die Sie untersuchen möchten, und wählen Sie sie.  
  
3.  Aus der **Spy++** Menü wählen **Protokollmeldungen**.  
  
     Die [Nachricht Optionen (Dialogfeld)](../debugger/message-options-dialog-box.md) wird geöffnet.  
  
4.  Wählen Sie die Optionen für die Nachricht, die Sie anzeigen möchten.  
  
5.  Drücken Sie **OK** zum Protokollieren von Nachrichten beginnen.  
  
     Einen Meldungen im Fenster wird geöffnet und ein **Nachrichten** Menü zur Spy++-Symbolleiste hinzugefügt wird. Je nach ausgewählten Optionen, beginnen Nachrichten streaming in das aktive Fenster des Nachrichten-Sicht.  
  
6.  Wenn Sie über genügend Nachrichten verfügen, wählen Sie **Protokollierung beenden** aus der **Nachrichten** Menü.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Steuern der Meldungsansicht](../debugger/how-to-control-messages-view.md)  
 Erläutert die Ansicht "Nachrichten" zu verwalten.  
  
 [Öffnen der Meldungsansicht aus "Fenster Suchen"](../debugger/how-to-open-messages-view-from-find-window.md)  
 Erläutert die Ansicht "Nachrichten" im Dialogfeld "Fenster Suchen" zu öffnen.  
  
 [Suchen nach einer Nachricht in der Ansicht "Nachrichten"](../debugger/how-to-search-for-a-message-in-messages-view.md)  
 Erläutert, wie eine bestimmte Nachricht in der Ansicht "Nachrichten" gefunden.  
  
 [Starten und Beenden der Meldungsprotokollanzeige](../debugger/how-to-start-and-stop-the-message-log-display.md)  
 Erläutert das Starten und beenden die nachrichtenprotokollierung.  
  
 [Meldungscodes](../debugger/message-codes.md)  
 Definiert die Codes für Nachrichten, die in der Ansicht "Nachrichten" aufgeführt.  
  
 [Anzeigen von Nachrichteneigenschaften](../debugger/how-to-display-message-properties.md)  
 So zeigen Sie weitere Informationen zu einer Meldung.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Spy++-Ansichten](../debugger/spy-increment-views.md)  
 Erläutert die Spy++-Strukturansichten von Windows, Nachrichten, Prozesse und Threads an.  
  
 [Verwenden von Spy++](../debugger/using-spy-increment.md)  
 Führt das Tool Spy++ und erläutert, wie sie verwendet werden kann.  
  
 [Dialogfeld "Meldungsoptionen"](../debugger/message-options-dialog-box.md)  
 Verwendet, um auszuwählen, welche Nachrichten in die aktive Ansicht "Nachrichten" aufgeführt sind.  
  
 [Meldungssuche (Dialogfeld)](../debugger/message-search-dialog-box.md)  
 So suchen Sie den Knoten für eine bestimmte Nachricht in der Ansicht "Nachrichten" verwendet.  
  
 [Dialogfeld "Meldungseigenschaften"](../debugger/message-properties-dialog-box.md)  
 Zum Anzeigen der Eigenschaften einer ausgewählten Meldung Nachricht verwendet.  
  
 [Spy++-Referenz](../debugger/spy-increment-reference.md)  
 Enthält Abschnitte beschreiben die einzelnen Spy++-Menü und das Dialogfeld.