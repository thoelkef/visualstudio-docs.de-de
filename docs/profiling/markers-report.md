---
title: Markerbericht | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.cv.threads.report.markers
ms.assetid: 829ce099-172e-4c7e-bbd0-578b110c59bd
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1d9d546e96d92c26725bc8a169c413bc7b96feb7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="markers-report"></a>Markerbericht
Der Markerbericht führt die Marker im angezeigten Zeitrahmen auf.  Das Schwenken, Zoomen oder Ausblenden von Bereichen führt, möglicherweise dazu, das Marker angezeigt werden oder wieder ausgeblendet werden. Der Bericht enthält folgende Informationen über jeden Marker:  
  
-   Die Startzeit, relativ zum Beginn der Ablaufverfolgung.  
  
-   Die Dauer. Die Dauer beträgt 0 (null) für Flags und Nachrichten, da sie einen Zeitpunkt darstellen.  
  
-   Die ID des Threads, der sie generiert hat.  
  
-   Die Ereignisablaufverfolgung (ETW) für den Windows-Anbieter, der diese generiert hat.  
  
-   Die Markerreihe aus die er geschrieben wurde.  
  
-   Die Kategorie der Ereignisse, denen er angehört.  
  
-   Die Wichtigkeitsstufe.  
  
-   Der Typ (span, flag oder message).  
  
-   Eine allgemeine Beschreibung der Bedeutung.  
  
 Wählen Sie die Schaltfläche **Exportieren** aus, um den Markerbericht als CSV-Datei zu speichern. Sie können die Daten in der CSV-Datei mit anderen Apps oder Tools verwenden.  
  
> [!NOTE]
>  Der Markerbericht kann 1.000 Marker anzeigen. Um alle Marker anzuzeigen, exportieren Sie den vollständigen Bericht in eine CSV-Datei.