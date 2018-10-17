---
title: Grundlagen zu Ressourcenkonflikt-Datenwerten| Microsoft-Dokumentation
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
- concurrency profiling method
- Profiling Tools, concurrency method
ms.assetid: 071c0f0f-1eba-4dc8-ae87-0810e4086dd0
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 54f8c7a545e0517c9d27dc32b68428e078cdfd40
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49263236"
---
# <a name="understanding-resource-contention-data-values"></a>Grundlagen zu Ressourcenkonflikt-Datenwerten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bei der Profilerstellung für Ressourcenkonflikte werden immer dann ausführliche Aufruflisteninformationen gesammelt, wenn konkurrierende Threads in einer Anwendung auf den Zugriff auf eine gemeinsam genutzte Ressource warten müssen.  
  
 **Anforderungen**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
 Ressourcenkonfliktberichte enthalten für die Module, Funktionen, Quellcodezeilen und Anweisungen, in denen die Verzögerung aufgetreten ist, die Gesamtanzahl von Konflikten sowie die Gesamtwartezeit für eine Ressource.  
  
-   Inklusive Werte geben Aufschluss über die Gesamtanzahl von Konflikten (sortiert nach Ressourcenkonflikten), aufgrund derer die Verzögerung für die Funktion aufgetreten ist, sowie über die Gesamtwartezeit der Funktion.  In den inklusiven Werten sind auch Konflikte enthalten, die durch untergeordnete, von der Funktion aufgerufene Funktionen verursacht wurden.  
  
-   Exklusive Werte geben nur Aufschluss über die Anzahl von Konflikten, die die Verzögerung einer Funktion zur Folge hatten und durch Code im Funktionstext verursacht wurden. Von untergeordneten Funktionen verursachte Konflikte werden nicht berücksichtigt. Die exklusive Zeit für die Funktion enthält auch nur die Wartezeiten, die von Anweisungen im Funktionsrumpf verursacht wurden.  
  
 Die Ansichten des Ressourcenkonfliktberichts enthalten auch Zeitachsendiagramme mit den einzelnen Konfliktereignissen im Zeitverlauf und die Aufruflisten, von denen das Ereignis erstellt wurde. Weitere Informationen finden Sie in einem der folgenden Themen:  
  
-   [Threaddetailansicht](../profiling/thread-details-view-contention-data.md)  
  
-   [Ressourcendetailansicht](../profiling/resource-details-view-contention-data.md)  
  
 Weitere Informationen zum zweiten Modus der Parallelitätsprofilerstellung finden Sie unter [Parallelitätsschnellansicht](../profiling/concurrency-visualizer.md).



