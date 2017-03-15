---
title: "Registerkarte &quot;Meldungen&quot;, Dialogfeld &quot;Meldungsoptionen&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Meldungsoptionen, Meldungen"
ms.assetid: fb9fa211-e82c-40a5-9e4b-ba8de07313c0
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Registerkarte &quot;Meldungen&quot;, Dialogfeld &quot;Meldungsoptionen&quot;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Verwenden Sie die Registerkarte **Meldungen**, um auszuwählen, welche Meldungstypen in der [Meldungsansicht](../debugger/messages-view.md) aufgeführt werden sollen, und um Meldungssuchkriterien anzugeben.  Klicken Sie im Menü **Spy** auf **Meldungen protokollieren**, um das Dialogfeld [Meldungsoptionen](../debugger/message-options-dialog-box.md) anzuzeigen.  
  
 In der Regel wählen Sie zuerst **Meldungsgruppen** aus und grenzen dann die Auswahl ein, indem Sie einzelne **Anzuzeigende Meldungen** auswählen.  Mit der Schaltfläche **Alle** werden alle Meldungstypen ausgewählt, und mit der Schaltfläche **Keine** werden alle Typen gelöscht.  
  
 Auf der Registerkarte **Meldungen** sind die folgenden Einstellungen verfügbar:  
  
 **Anzuzeigende Meldungen**  
 Wählen Sie bestimmte Meldungen zum Anzeigen aus.  Wenn Sie ein neues Meldungsfenster erstellen, können in ihm alle Meldungen angezeigt werden.  Wenn Sie Meldungen auf der Registerkarte **Meldungen** filtern, wird dieser Filter nur auf neue Meldungen angewendet, nicht auf Meldungen, die bereits in der Fensteransicht angezeigt wurden.  
  
 **Meldungsgruppen**  
 Wählen Sie Meldungsgruppen zum Anzeigen aus.  Folgende Gruppen sind verfügbar:  
  
-   WM\_USER: mit einem Code größer oder gleich WM\_USER  
  
-   Registriert: mit dem Aufruf von **RegisterWindowMessage** registriert  
  
-   Unbekannt: unbekannte Meldungen im Bereich 0 bis \(WM\_USER \- 1\)  
  
 Beachten Sie, dass die **Meldungsgruppen** nicht bestimmten Einträgen unter **Anzuzeigende Meldungen** zugeordnet sind.  Wenn Sie eine Gruppe auswählen, wird die Auswahl direkt auf den Meldungsstream angewendet.  
  
 Ein abgeblendetes Kontrollkästchen in **Meldungsgruppen** gibt an, dass das Listenfeld **Anzuzeigende Meldungen** für Meldungen in der betreffenden Gruppe geändert wurde. Es werden nicht alle Meldungstypen in dieser Gruppe ausgewählt.  
  
 **Als Voreinstellung speichern**  
 Speichert die aktuellen Einstellungen zur späteren Verwendung als Meldungssuchoptionen.  Diese Einstellungen werden auch beim Beenden von Spy\+\+ gespeichert.