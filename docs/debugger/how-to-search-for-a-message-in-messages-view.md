---
title: 'Vorgehensweise: Suchen einer Meldung in der Meldungsansicht | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Message Search dialog box
- Messages view
- messages, searching for
ms.assetid: 732b7ccc-54ea-41db-823b-2b96e3e4083e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 37f99c30c23461ada406bb0650f86d45d2a4a2e9
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63388404"
---
# <a name="how-to-search-for-a-message-in-messages-view"></a>Vorgehensweise: Suchen einer Meldung in der Meldungsansicht
Sie können mithilfe der Handle, Typ oder Meldungs-ID als Suchkriterium für eine bestimmte Nachricht in der Ansicht "Nachrichten" suchen. Eine dieser – oder eine Kombination – werden gültige Suchkriterien. Die anfängliche Richtung für die Suche kann auch angegeben werden. Die Felder im Dialogfeld werden mit den Attributen der aktuell ausgewählten Nachricht vorab geladen.

### <a name="to-search-for-a-message-in-messages-view"></a>Suchen Sie für eine Nachricht in der Meldungsansicht

1. Ordnen Sie die Fenster also, Spy++ und ein aktiver [Meldungsansicht](../debugger/messages-view.md) Fenster sichtbar sind.

2. Von der **Suche** Menü wählen **Nachricht suchen**.

    Die [Nachricht Meldungssuche (Dialogfeld)](../debugger/message-search-dialog-box.md) wird geöffnet.

3. Ziehen Sie die **Suchtool** auf das gewünschte Fenster. Wie Sie das Tool, ziehen Sie die **Meldungssuche** Dialogfeld zeigt die Details für das ausgewählte Fenster.

   - ODER

     Wenn Sie das Handle des Fensters, deren Meldungen, die Sie untersuchen möchten verfügen, geben Sie ihn in das **behandeln** Textfeld.

   - ODER

     Wenn Sie wissen den Meldungstyp bzw. eine Meldungs-ID, die Sie möchten, wählen sie aus der **Typ** und **Nachricht** Dropdownmenüs, und deaktivieren Sie die **behandeln** Textfeld.

4. Deaktivieren Sie alle Felder, die für die Sie keine Werte angeben möchten.

   > [!TIP]
   > Um die Übersichtlichkeit des Bildschirms, wählen Sie die **Spy++ ausblenden** Option. Diese Option verbirgt die Spy++-Hauptfenster, sondern nur die **Fenster Suchen** Dialogfeld sichtbar ist, zusätzlich zu anderen Anwendungen. Spy++-Hauptfenster wird wiederhergestellt, wenn Sie auf **OK** oder **Abbrechen**, oder wenn Sie das Kontrollkästchen der **Spy++ ausblenden** Option.

5. Wählen Sie **einrichten** oder **unten** für die anfängliche Richtung für die Suche.

6. Klicken Sie auf **OK**.

   Wenn eine entsprechende Nachricht gefunden wird, wird es in der Nachrichten an hervorgehoben. Finden Sie unter [Meldungsansicht](../debugger/messages-view.md).