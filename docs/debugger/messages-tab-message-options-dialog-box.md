---
title: Registerkarte "Meldungen", Optionsdialogfeld | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
helpviewer_keywords:
- message options, Messages
ms.assetid: fb9fa211-e82c-40a5-9e4b-ba8de07313c0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f19da533d2ab13e7493eae53af8dea3af4e520df
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
---
# <a name="messages-tab-message-options-dialog-box"></a>Registerkarte "Meldungen", Dialogfeld "Meldungsoptionen"
Verwenden der **Nachrichten** Registerkarte auswählen, welche Nachrichtentypen Liste in [Ansicht "Nachrichten"](../debugger/messages-view.md), und geben Sie Suchkriterien für die Nachricht an. Zum Anzeigen der [Nachricht Optionen (Dialogfeld)](../debugger/message-options-dialog-box.md), wählen Sie **Protokollmeldungen** aus der **Spy++** Menü.  
  
 In der Regel zunächst wählen **Nachrichtengruppen**, und klicken Sie dann die Auswahl optimieren, indem Sie einzelne auswählen **Nachrichten anzuzeigende**. Die **alle** Schaltfläche wählt alle Nachrichtentypen und **keine** Schaltfläche löscht alle Typen.  
  
 Die folgenden Einstellungen sind verfügbar, auf die **Nachrichten** Registerkarte:  
  
 **Nachrichten zur Ansicht**  
 Wählen Sie bestimmte Nachrichten für die Anzeige. Wenn Sie ein neues Fenster erstellen, können sie alle Nachrichten anzeigen. Wenn Sie Nachrichten von Filtern die **Nachrichten** Registerkarte diesen Filter gilt nur für neue Nachrichten, nicht für Nachrichten, die bereits in der Ansicht angezeigt wurden.  
  
 **Nachrichtengruppen**  
 Wählen Sie für die Anzeige Nachrichtengruppen. Die verfügbaren Gruppen enthalten:  
  
-   WM_USER: mit einem Code größer als oder gleich WM_USER  
  
-   : Registriert mit der **RegisterWindowMessage registriert** aufrufen  
  
-   Unbekannt: Unbekannte Nachrichten im Bereich von 0 WM_USER (- 1)  
  
 Beachten Sie, dass diese **Nachrichtengruppen** nicht auf bestimmte Einträge unter zuordnen **zu Meldungsansicht**. Wenn Sie eine Gruppe auswählen, wird die Auswahl direkt in den Meldungsstream angewendet.  
  
 Das Kontrollkästchen abgeblendet innerhalb **Nachrichtengruppen** gibt an, dass die **Meldungsansicht zu** im Listenfeld für Nachrichten in dieser Gruppe geändert wurde, nicht alle Nachrichtentypen in dieser Gruppe werden ausgewählt.  
  
 **Einstellungen als Standard speichern**  
 Speichern Sie die aktuellen Einstellungen für die spätere Verwendung als Nachricht Suchoptionen. Diese Einstellungen werden beim Beenden von Spy++-ebenfalls gespeichert.