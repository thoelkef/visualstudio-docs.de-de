---
title: Registerkarte "Meldungen", Optionsdialogfeld | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- message options, Messages
ms.assetid: fb9fa211-e82c-40a5-9e4b-ba8de07313c0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: de50e6fe997ce10266cbb51f2fd91c318ab2bd1f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62905530"
---
# <a name="messages-tab-message-options-dialog-box"></a>Registerkarte "Meldungen", Dialogfeld "Meldungsoptionen"
Verwenden der **Nachrichten** Tab, um auszuwählen, welche Nachrichtentypen zur Liste in [Meldungsansicht](../debugger/messages-view.md), und Angeben von Suchkriterien für die Nachricht. Zum Anzeigen der [im Dialogfeld "Optionen" Nachricht](../debugger/message-options-dialog-box.md), wählen Sie **Protokollmeldungen** aus der **Spy** Menü.

 In der Regel zuerst auswählen **Nachrichtengruppen**, und der anschließenden Optimierung die Auswahl durch Auswahl eines einzelnen **Nachrichten an die Ansicht**. Die **alle** Schaltfläche auswählt, alle Nachrichtentypen, und die **keine** Schaltfläche löscht alle Typen.

 Die folgenden Einstellungen stehen auf der **Nachrichten** Registerkarte:

 **Nachrichten zur Ansicht** bestimmte Nachrichten für die Anzeige auswählen. Wenn Sie ein neues Fenster für die Nachrichten erstellen, können sie alle Meldungen anzuzeigen. Wenn Sie Nachrichten von Filtern die **Nachrichten** Registerkarte, dass der Filter gilt nur für neue Nachrichten, nicht die Nachrichten, die bereits in der Windows-Ansicht angezeigt wurden.

 **Nachricht Gruppen** wählen Sie für die Anzeige. Die verfügbaren Gruppen enthalten:

- WM_USER: Klicken Sie mit einem Code, die größer als oder gleich WM_USER

- : Registriert mit der **RegisterWindowMessage registriert** aufrufen

- Unbekannt: Unbekannte Nachrichten im Bereich von 0 WM_USER (- 1)

  Beachten Sie, dass diese **Nachrichtengruppen** lassen sich bestimmte Einträge unter nicht zuordnen **Nachrichten zu Ansicht**. Wenn Sie eine Gruppe auswählen, wird die Auswahl direkt auf den Nachrichtenstream angewendet.

  In das Kontrollkästchen grau **Nachrichtengruppen** gibt an, dass die **Nachrichten zu Ansicht** Listenfeld für Nachrichten in dieser Gruppe geändert wurde, nicht alle die Nachrichtentypen in der Gruppe ausgewählt werden.

  **Speichern Sie die Einstellungen als Standard** speichern Sie die aktuellen Einstellungen für die spätere Verwendung als Nachricht Suchoptionen. Diese Einstellungen werden ebenfalls gespeichert, wenn Spy++ beendet wird.