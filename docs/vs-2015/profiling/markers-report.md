---
title: Markerbericht | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.cv.threads.report.markers
ms.assetid: 829ce099-172e-4c7e-bbd0-578b110c59bd
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a1777f2f9fbd63ba659e74d0ce471962b29b15fd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49811068"
---
# <a name="markers-report"></a>Markerbericht
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der Markerbericht führt die Marker im angezeigten Zeitrahmen auf.  Das Schwenken, Zoomen oder Ausblenden von Bereichen führt, möglicherweise dazu, das Marker angezeigt werden oder wieder ausgeblendet werden. Der Bericht enthält folgende Informationen über jeden Marker:  
  
- Die Startzeit, relativ zum Beginn der Ablaufverfolgung.  
  
- Die Dauer. Die Dauer beträgt 0 (null) für Flags und Nachrichten, da sie einen Zeitpunkt darstellen.  
  
- Die ID des Threads, der sie generiert hat.  
  
- Die Ereignisablaufverfolgung (ETW) für den Windows-Anbieter, der diese generiert hat.  
  
- Die Markerreihe aus die er geschrieben wurde.  
  
- Die Kategorie der Ereignisse, denen er angehört.  
  
- Die Wichtigkeitsstufe.  
  
- Der Typ (span, flag oder message).  
  
- Eine allgemeine Beschreibung der Bedeutung.  
  
  Wählen Sie die Schaltfläche **Exportieren** aus, um den Markerbericht als CSV-Datei zu speichern. Sie können die Daten in der CSV-Datei mit anderen Apps oder Tools verwenden.  
  
> [!NOTE]
>  Der Markerbericht kann 1.000 Marker anzeigen. Um alle Marker anzuzeigen, exportieren Sie den vollständigen Bericht in eine CSV-Datei.



