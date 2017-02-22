---
title: "Markerbericht | Microsoft Docs"
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
  - "vs.cv.threads.report.markers"
ms.assetid: 829ce099-172e-4c7e-bbd0-578b110c59bd
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Markerbericht
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Marker\-Listendateien die Markierung im angezeigten Zeitraum.  Das Schwenken oder Zoomen oder das Ausblenden von Aufgrund, bewirken Markierung angezeigt oder verschwänden werden.  Der Bericht enthält diese Informationen über jeden Markierung:  
  
-   Die Zeit, als er gestartet, relativ zum Anfang der Ablaufverfolgung.  
  
-   Die Dauer.  Die Dauer beträgt für Flags und Meldungen null, da sie einen Zeitpunkt darstellen.  
  
-   Die ID des Threads, der sie generiert.  
  
-   Die Anbieter Ereignisüberwachung für Windows \(ETW\), der sie generiert.  
  
-   Die Marker\-Reihe, aus denen er erstellt wurde.  
  
-   Die Kategorie von Ereignissen er gehört.  
  
-   Die Wichtigkeitsstufe.  
  
-   Sein Typ \(Spanne, Flag oder Meldung\).  
  
-   Eine allgemeine Beschreibung von, was es darstellt  
  
 Wählen Sie die Schaltfläche **Exportieren**, um die Markierung zu speichern Bericht als CSV\-Datei.  Sie können die Daten in der CSV\-Datei mit anderen Apps oder Tools verwenden.  
  
> [!NOTE]
>  Der Marker\-Bericht kann 1.000 Markierungen anzeigen.  Um alle Markierung anzuzeigen, exportieren Sie den Gesamtbericht in eine CSV\-Datei.