---
title: Im Dialogfeld Eigenschaften von Nachrichten | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- message options
- message options, General
ms.assetid: 58e9dc24-baf6-4ab8-916c-aea28b72e3b0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1f590f40e4e3361f4dbeb46a3a9b8758b8ab5075
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62846114"
---
# <a name="message-properties-dialog-box"></a>Dialogfeld "Meldungseigenschaften"
Verwenden Sie das Dialogfeld zu öffnen, um weitere Informationen zu einer bestimmten Nachricht. Um das Dialogfeld anzuzeigen, den Fokus auf ein [Meldungsansicht](../debugger/messages-view.md) Fenster. Wählen Sie einen in der Struktur aus, und wählen Sie dann **Eigenschaften** aus der **Ansicht** Menü.

 Die **allgemeine** Registerkarte ist die einzige Registerkarte angezeigt. Die folgenden Einstellungen sind verfügbar:

 **Das Fensterhandle** die eindeutige ID des in diesem Fenster. Die Nummern der Ziehpunkte Fenster werden wiederverwendet. Identifizieren sie ein Fenster, nur für die Lebensdauer dieses Fensters. Klicken Sie auf diesen Wert, um die Eigenschaften dieses Fenster anzuzeigen.

 **Schachtelungsebene** Tiefe der Schachtelung, 0, in denen keine Schachtelung ist dieser Nachricht.

 **Nachricht** Anzahl, Status und Namen der ausgewählten Windows-Meldung.

 **lResult** den Wert des der *lResult* Parameters, sofern vorhanden.

 **wParam** den Wert des der *wParam* Parameters, sofern vorhanden.

 **lParam** den Wert des der *lParam* Parameters, sofern vorhanden. Dieser Wert wird decodiert, wenn es sich um einen Zeiger auf eine Zeichenfolge oder eine Struktur ist.

## <a name="related-sections"></a>Verwandte Abschnitte
 [Optionen (Dialogfeld) Nachricht](../debugger/message-options-dialog-box.md) verwendet, um auszuwählen, welche Nachrichten in der aktiven Ansicht "Nachrichten" aufgeführt sind.

 [Meldungssuche (Dialogfeld) Nachricht](../debugger/message-search-dialog-box.md) verwendet, um den Knoten für eine bestimmte Nachricht in der Ansicht "Nachrichten" suchen.

 [Spy++-Referenz](../debugger/spy-increment-reference.md) enthält Abschnitte, die jedes Spy++ Menü- und Dialogfeldressourcen Feld beschreibt.

 [Öffnen der Meldungsansicht aus "Fenster Suchen"](../debugger/how-to-open-messages-view-from-find-window.md) wird erläutert, wie im Dialogfeld "Fenster Suchen" Ansicht "Nachrichten" zu öffnen.

 [Suchen nach einer Nachricht in der Meldungsansicht](../debugger/how-to-search-for-a-message-in-messages-view.md) wird erläutert, wie Sie eine bestimmte Nachricht in der Ansicht "Nachrichten".

 [Meldungsansicht](../debugger/messages-view.md) zeigt den Nachrichtenstream, der ein Fenster, Prozess oder Thread zugeordnet.

 [Spy++-Ansichten](../debugger/spy-increment-views.md) wird erläutert, die Spy++-Strukturansichten von Windows, Nachrichten, Prozesse und Threads.

 [Verwenden von Spy++](../debugger/using-spy-increment.md) stellt die Spy++-Tools vor und erläutert, wie sie verwendet werden kann.