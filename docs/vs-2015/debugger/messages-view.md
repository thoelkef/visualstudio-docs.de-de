---
title: Meldungsansicht | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.externaltools.spyplus.messagesview
helpviewer_keywords:
- Messages view
ms.assetid: 14c2a786-c23a-4b2d-acad-8c32a856c70d
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3765b9804224549c98b57cd1b0a44f0330d278b5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157497"
---
# <a name="messages-view"></a>Meldungsansicht
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jedes Fenster verfügt über einen zugehörigen Meldungsdatenstrom. In einem Meldungsansichtsfenster wird dieser Meldungsdatenstrom angezeigt. Angezeigt werden das Fensterhandle, der Meldungscode und die Meldung. Sie können eine Meldungsansicht auch für einen Thread oder einen Prozess erstellen. Dadurch können Sie Meldungen anzeigen, die an alle Fenster gesendet werden, die sich im Besitz eines bestimmten Prozesses oder Threads befinden. Dies ist besonders hilfreich für die Erfassung von Fensterinitialisierungsmeldungen.  
  
 Die folgende Abbildung zeigt ein typisches Meldungsansichtsfenster. Beachten Sie, dass die erste Spalte das Fensterhandle und die zweite Spalte einen Meldungscode (erläutert unter [Meldungscodes](../debugger/message-codes.md)) enthält. Rechts befinden sich die decodierten Meldungsparameter und die Rückgabewerte.  
  
 ![Spy&#43;&#43; Messages-Ansicht](../debugger/media/spy-messagesview.png "Spy + +-_MessagesView")  
Spy++-Meldungsansicht  
  
## <a name="procedures"></a>Verfahren  
  
#### <a name="to-open-a-messages-view-for-a-window-process-or-thread"></a>So öffnen Sie eine Meldungsansicht für ein Fenster, einen Prozess oder einen Thread  
  
1. Verschieben Sie den Fokus in ein [Fensteransichts](../debugger/windows-view.md)-, [Prozessansichts](../debugger/processes-view.md)- oder [Threadansichts](../debugger/threads-view.md)-Fenster.  
  
2. Suchen Sie nach dem Knoten für das Element, dessen Meldungen Sie untersuchen möchten, und wählen Sie ihn aus.  
  
3. Wählen Sie im Menü **Spy** die Option **Meldungen protokollieren** aus.  
  
     Das Dialogfeld [Meldungsoptionen](../debugger/message-options-dialog-box.md) wird geöffnet.  
  
4. Wählen Sie die Optionen für die Meldung aus, die Sie anzeigen möchten.  
  
5. Drücken Sie **OK**, um mit der Protokollierung von Meldungen zu beginnen.  
  
     Ein Meldungsansichtsfenster wird geöffnet, und der Spy++-Symbolleiste wird ein Menü **Meldungen** hinzugefügt. Abhängig von den ausgewählten Optionen wird der Meldungsdatenstrom in das aktive Meldungsansichtsfenster gestartet.  
  
6. Wenn genügend Meldungen eingegangen sind, wählen Sie **Protokollierung beenden** im Menü **Meldungen** aus.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Steuern der Meldungs Ansicht](../debugger/how-to-control-messages-view.md)  
 Erläutert die Verwaltung der Nachrichtenansicht.  
  
 [Suchen nach einer Meldung in der Meldungs Ansicht](../debugger/how-to-search-for-a-message-in-messages-view.md)  
 Erläutert, wie Sie eine bestimmte Nachricht in der Meldungs Ansicht suchen.  
  
 [Starten und Beenden der Meldungs Protokoll Anzeige](../debugger/how-to-start-and-stop-the-message-log-display.md)  
 Erläutert, wie die Nachrichten Protokollierung gestartet und beendet wird.  
  
 [Meldungscodes](../debugger/message-codes.md)  
 Definiert die Codes für Meldungen, die in der Meldungs Ansicht aufgelistet sind.  
  
 [Anzeigen von Nachrichten Eigenschaften](../debugger/how-to-display-message-properties.md)  
 Erfahren Sie, wie Sie weitere Informationen zu einer Nachricht anzeigen.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Spy++-Ansichten](../debugger/spy-increment-views.md)  
 Erläutert die Spy + +-Struktur Ansichten von Fenstern, Meldungen, Prozessen und Threads.  
  
 [Verwenden von Spy++](../debugger/using-spy-increment.md)  
 Stellt das Spy + +-Tool vor und erläutert, wie es verwendet werden kann.  
  
 [Dialogfeld "Meldungsoptionen"](../debugger/message-options-dialog-box.md)  
 Wird verwendet, um auszuwählen, welche Meldungen in der Ansicht aktive Meldungen aufgeführt sind.  
  
 [Meldungssuche (Dialogfeld)](../debugger/message-search-dialog-box.md)  
 Wird verwendet, um nach dem Knoten für eine bestimmte Nachricht in der Meldungs Ansicht zu suchen.  
  
 [Dialogfeld "Meldungseigenschaften"](../debugger/message-properties-dialog-box.md)  
 Wird verwendet, um die Eigenschaften einer in der Meldungs Ansicht ausgewählten Nachricht anzuzeigen.  
  
 [Spy++-Referenz](../debugger/spy-increment-reference.md)  
 Enthält Abschnitte, in denen jedes Spy + +-Menü und Dialogfeld beschrieben werden.
