---
title: 'Vorgehensweise: Suchen einer Meldung in der Ansicht "Nachrichten" | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Message Search dialog box
- Messages view
- messages, searching for
ms.assetid: 732b7ccc-54ea-41db-823b-2b96e3e4083e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 368d10f2285c94f053e536da77966e9b2fb26da9
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-search-for-a-message-in-messages-view"></a>Gewusst wie: Suchen einer Meldung in der Meldungsansicht
Sie können mithilfe von dessen Handle, den Typ oder die Nachrichten-ID als Suchkriterium für eine bestimmte Nachricht in der Ansicht "Nachrichten" suchen. Eine dieser – oder eine Kombination aus – werden gültige Suchkriterien. Die anfängliche Richtung der Suche kann auch angegeben werden. Die Felder im Dialogfeld werden mit den Attributen der aktuell ausgewählten Meldung vorab geladen.  
  
### <a name="to-search-for-a-message-in-messages-view"></a>Suchen Sie für eine Nachricht in der Ansicht "Nachrichten"  
  
1.  Ordnen Sie die Fenster so, Spy++ und ein aktives [Ansicht "Nachrichten"](../debugger/messages-view.md) Fenster sichtbar sind.  
  
2.  Aus der **Suche** Menü wählen **Nachricht suchen**.  
  
     Die [Nachricht-Dialogfeld "Fenstersuche"](../debugger/message-search-dialog-box.md) wird geöffnet.  
  
3.  Ziehen Sie die **Suchtools** über das gewünschte Fenster. Wie Sie das Tool, ziehen Sie die **Meldungssuche** Dialogfeld zeigt Details für das ausgewählte Fenster.  
  
     - ODER  
  
     Wenn Sie das Handle des Fensters, deren Meldungen, die Sie untersuchen möchten verfügen, geben Sie ihn in die **behandeln** Textfeld.  
  
     - ODER  
  
     Sie kennen die Nachrichtentyp und/oder die Nachrichten-ID, die Sie möchten, wählen Sie sie aus der **Typ** und **Nachricht** Dropdownmenüs, und deaktivieren Sie die **behandeln** Textfeld.  
  
4.  Deaktivieren Sie alle Felder, die für die Sie keine Werte angeben möchten.  
  
    > [!TIP]
    >  Wählen Sie zum Bildschirm übersichtlicher gestalten möchten, die **Spy++ ausblenden** Option. Diese Option verbirgt Spy++-Hauptfenster nur verlassen der **"Fenster Suchen"** (Dialogfeld), die zusätzlich zu anderen Anwendungen sichtbar. Spy++-Hauptfenster wird wiederhergestellt, wenn Sie auf **OK** oder **"Abbrechen"**, oder wenn Sie deaktivieren die **Spy++ ausblenden** Option.  
  
5.  Wählen Sie **einrichten** oder **unten** für die anfängliche Richtung der Suche.  
  
6.  Klicken Sie auf **OK**.  
  
 Wenn eine entsprechende Meldung gefunden wird, wird es im Ansichtsfenster Meldungen hervorgehoben. Finden Sie unter [der Meldungsansicht](../debugger/messages-view.md).