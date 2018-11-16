---
title: Registerkarte "Meldungen", Optionsdialogfeld | Microsoft-Dokumentation
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
- message options, Messages
ms.assetid: fb9fa211-e82c-40a5-9e4b-ba8de07313c0
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b44a5932d178fe8432273038d677f5831d568146
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51793944"
---
# <a name="messages-tab-message-options-dialog-box"></a>Registerkarte "Meldungen", Dialogfeld "Meldungsoptionen"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Verwenden der **Nachrichten** Tab, um auszuwählen, welche Nachrichtentypen zur Liste in [Meldungsansicht](../debugger/messages-view.md), und Angeben von Suchkriterien für die Nachricht. Zum Anzeigen der [im Dialogfeld "Optionen" Nachricht](../debugger/message-options-dialog-box.md), wählen Sie **Protokollmeldungen** aus der **Spy** Menü.  
  
 In der Regel zuerst auswählen **Nachrichtengruppen**, und der anschließenden Optimierung die Auswahl durch Auswahl eines einzelnen **Nachrichten an die Ansicht**. Die **alle** Schaltfläche auswählt, alle Nachrichtentypen, und die **keine** Schaltfläche löscht alle Typen.  
  
 Die folgenden Einstellungen stehen auf der **Nachrichten** Registerkarte:  
  
 **Nachrichten anzeigen**  
 Wählen Sie bestimmte Nachrichten für die Anzeige. Wenn Sie ein neues Fenster für die Nachrichten erstellen, können sie alle Meldungen anzuzeigen. Wenn Sie Nachrichten von Filtern die **Nachrichten** Registerkarte, dass der Filter gilt nur für neue Nachrichten, nicht die Nachrichten, die bereits in der Windows-Ansicht angezeigt wurden.  
  
 **Nachrichtengruppen**  
 Wählen Sie für die Anzeige. Die verfügbaren Gruppen enthalten:  
  
- WM_USER: Klicken Sie mit einem Code, die größer als oder gleich WM_USER  
  
- : Registriert mit der **RegisterWindowMessage registriert** aufrufen  
  
- Unbekannt: Unbekannte Nachrichten im Bereich von 0 WM_USER (– 1)  
  
  Beachten Sie, dass diese **Nachrichtengruppen** lassen sich bestimmte Einträge unter nicht zuordnen **Nachrichten zu Ansicht**. Wenn Sie eine Gruppe auswählen, wird die Auswahl direkt auf den Nachrichtenstream angewendet.  
  
  In das Kontrollkästchen grau **Nachrichtengruppen** gibt an, dass die **Nachrichten zu Ansicht** Listenfeld für Nachrichten in dieser Gruppe geändert wurde, nicht alle die Nachrichtentypen in der Gruppe ausgewählt werden.  
  
  **Einstellungen als Standard speichern**  
  Speichern Sie die aktuellen Einstellungen für die spätere Verwendung als Nachricht Suchoptionen an. Diese Einstellungen werden ebenfalls gespeichert, wenn Spy++ beendet wird.



