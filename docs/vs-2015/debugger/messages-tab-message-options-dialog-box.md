---
title: Meldungen-Registerkarte und Meldungsoptionen-Dialogfeld | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- message options, Messages
ms.assetid: fb9fa211-e82c-40a5-9e4b-ba8de07313c0
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a9eb1c88d935fa307e8b86a9a75da423bc08111c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149434"
---
# <a name="messages-tab-message-options-dialog-box"></a>Registerkarte "Meldungen", Dialogfeld "Meldungsoptionen"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Verwenden Sie die Registerkarte **Meldungen**, um auszuwählen, welche Meldungstypen in der [Meldungsansicht](../debugger/messages-view.md) angezeigt werden sollen, und um Suchkriterien für Meldungen anzugeben. Um das [Dialogfeld „Meldungsoptionen](../debugger/message-options-dialog-box.md) anzuzeigen, wählen Sie im Menü **Spy** die Option **Meldungen protokollieren** aus.  
  
 In der Regel wählen Sie zunächst **Meldungsgruppen** aus und optimieren dann die Auswahl, indem Sie einzelne **anzuzeigende Meldungen** auswählen. Mit der Schaltfläche **Alle** können Sie alle Meldungstypen auswählen und mit der Schaltfläche **Keine** werden alle Typen gelöscht.  
  
 Auf der Registerkarte **Meldungen** sind folgende Einstellungen verfügbar:  
  
 **Anzuzeigende Meldungen**  
 Wählen Sie bestimmte Nachrichten für die Anzeige aus. Wenn Sie ein neues Meldungsfenster erstellen, können alle Meldungen angezeigt werden. Wenn Sie Meldungen über die Registerkarte **Meldungen** filtern, gilt dieser Filter nur für neue Meldungen und nicht für Meldungen, die bereits in der Fensteransicht angezeigt wurden.  
  
 **Nachrichten Gruppen**  
 Wählen Sie Nachrichten Gruppen zum Anzeigen aus. Zu den verfügbaren Gruppen gehören:  
  
- WM_USER: Meldungen mit einem Code größer als oder gleich WM_USER  
  
- Registered (Registriert): Meldungen die mit dem Aufruf **RegisterWindowMessage** registriert wurden  
  
- Unbekannt: Unbekannte Nachrichten im Bereich von 0 bis (WM_USER – 1)  
  
  Beachten Sie, dass diese **Meldungsgruppen** nicht bestimmten Einträgen unter **Anzuzeigende Meldungen** zugeordnet werden. Wenn Sie eine Gruppe auswählen, wird diese Auswahl direkt auf den Meldungsdatenstrom angewendet.  
  
  Ein ausgegrautes Kontrollkästchen in **Meldungsgruppen** gibt an, dass das Listenfeld **Anzuzeigende Meldungen** für Meldungen in dieser Gruppe geändert wurde. Nicht alle Meldungstypen in dieser Gruppe wurden ausgewählt.  
  
  **Als Voreinstellung speichern**  
  Speichern Sie die aktuellen Einstellungen für die spätere Verwendung als Nachrichten Suchoptionen. Diese Einstellungen werden ebenfalls beim Beenden von Spy++ gespeichert.
