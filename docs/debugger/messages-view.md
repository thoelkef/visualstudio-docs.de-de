---
title: "Messages View | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.externaltools.spyplus.messagesview"
helpviewer_keywords: 
  - "Messages view"
ms.assetid: 14c2a786-c23a-4b2d-acad-8c32a856c70d
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Messages View
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Jedem Fenster ist ein Meldungsstream zugeordnet.  Der Meldungsstream wird in einem Meldungsansichtsfenster angezeigt.  Das Fensterhandle, der Meldungscode und die Meldung werden angezeigt.  Sie können auch eine Meldungsansicht für einen Thread oder Prozess erstellen.  Dies ermöglicht Ihnen das Anzeigen von Meldungen, die an alle Fenster im Besitz eines bestimmten Prozesses oder Threads gesendet wurden. Dies ist insbesondere zum Aufzeichnen von Fensterinitialisierungsmeldungen hilfreich.  
  
 Ein typisches Meldungsansichtsfenster wird unten dargestellt.  Beachten Sie, dass die erste Spalte das Fensterhandle enthält, und die zweite Spalte enthält einen Meldungscode \(in [Meldungscodes](../debugger/message-codes.md) erläutert\).  Decodierte Meldungsparameter und Rückgabewerte werden rechts dargestellt.  
  
 ![Spy&#43;&#43;&#45;Meldungsansicht](../debugger/media/spy--_messagesview.png "Spy\+\+\_MessagesView")  
Spy\+\+\-Meldungsansicht  
  
## Arbeitsschritte  
  
#### So öffnen Sie eine Meldungsansicht für ein Fenster, einen Prozess oder einen Thread  
  
1.  Verschieben Sie den Fokus auf ein [Fensteransichtsfenster](../debugger/windows-view.md), [Prozessansichtsfenster](../debugger/processes-view.md) oder [Threadansichtsfenster](../debugger/threads-view.md).  
  
2.  Suchen Sie den Knoten für das Element, dessen Meldungen Sie untersuchen möchten, und wählen Sie ihn aus.  
  
3.  Klicken Sie im Menü **Spy** auf **Meldungen protokollieren**.  
  
     Das Dialogfeld [Meldungsoptionen](../debugger/message-options-dialog-box.md) wird geöffnet.  
  
4.  Wählen Sie die Optionen für die Meldung aus, die Sie anzeigen möchten.  
  
5.  Klicken Sie auf **OK**, um mit dem Protokollieren von Meldungen zu beginnen.  
  
     Ein Meldungsansichtsfenster wird geöffnet, und der Spy\+\+\-Symbolleiste wird das Menü **Meldungen** hinzugefügt.  Je nach den ausgewählten Optionen wird der Stream von Meldungen in das aktive Meldungsansichtsfenster gestartet.  
  
6.  Wenn genügend Meldungen vorhanden sind, klicken Sie im Menü **Meldungen** auf **Protokollierung beenden**.  
  
## In diesem Abschnitt  
 [Steuern der Meldungsansicht](../debugger/how-to-control-messages-view.md)  
 Erklärt, wie die Meldungsansicht verwaltet wird.  
  
 [Öffnen der Meldungsansicht aus "Fenster suchen"](_asug_choosing_message_options)  
 Erklärt, wie Sie die Meldungsansicht im Dialogfeld "Fenster suchen" öffnen.  
  
 [Suchen nach einer Meldung in der Meldungsansicht](../debugger/how-to-search-for-a-message-in-messages-view.md)  
 Erklärt, wie Sie eine bestimmte Meldung in der Meldungsansicht finden.  
  
 [Starten und Beenden der Meldungsprotokollanzeige](../debugger/how-to-start-and-stop-the-message-log-display.md)  
 Erklärt, wie die Meldungsprotokollierung gestartet und beendet wird.  
  
 [Meldungscodes](../debugger/message-codes.md)  
 Definiert die Codes für in der Meldungsansicht aufgeführte Meldungen.  
  
 [Anzeigen von Meldungseigenschaften](../debugger/how-to-display-message-properties.md)  
 Erläutert, wie weitere Informationen zu einer Meldung angezeigt werden.  
  
## Verwandte Abschnitte  
 [Spy\+\+\-Ansichten](../debugger/spy-increment-views.md)  
 Erklärt die Spy\+\+\-Strukturansichten von Fenstern, Meldungen, Prozessen und Threads.  
  
 [Verwenden von Spy\+\+](../debugger/using-spy-increment.md)  
 Stellt das Tool Spy\+\+ vor und erläutert die Verwendung.  
  
 [Dialogfeld "Meldungsoptionen"](../debugger/message-options-dialog-box.md)  
 Wird verwendet, um auszuwählen, welche Meldungen in der aktiven Meldungsansicht aufgeführt werden.  
  
 [Dialogfeld "Meldungssuche"](../debugger/message-search-dialog-box.md)  
 Wird verwendet, um in der Meldungsansicht den Knoten für eine bestimmte Meldung zu suchen.  
  
 [Dialogfeld "Meldungseigenschaften"](../debugger/message-properties-dialog-box.md)  
 Wird verwendet, um die Eigenschaften einer in der Meldungsansicht ausgewählten Meldung anzuzeigen.  
  
 [Spy\+\+\-Referenz](../debugger/spy-increment-reference.md)  
 Enthält Abschnitte mit Beschreibungen der einzelnen Spy\+\+\-Menüs und \-Dialogfelder.