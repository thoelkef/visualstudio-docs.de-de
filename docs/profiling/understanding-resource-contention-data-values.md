---
title: "Grundlagen zu Ressourcenkonflikt-Datenwerten in Profilerstellungstools | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Parallelitätsmethode zur Profilerstellung"
  - "Profilerstellungstools, Parallelitätsmethode"
ms.assetid: 071c0f0f-1eba-4dc8-ae87-0810e4086dd0
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Grundlagen zu Ressourcenkonflikt-Datenwerten in Profilerstellungstools
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ressourcenkonflikt\-Profilerstellung werden ausführliche konkurrierende Threads der Ressourcenkonflikt\-Profilerstellung werden immer dann in einer Anwendung werden erzwungen, auf Zugriff auf eine freigegebene Ressource gewartet.  
  
 **Voraussetzungen**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 Ressourcenkonfliktberichte enthalten für die Module, Funktionen, Quellcodezeilen und Anweisungen, in denen die Verzögerung aufgetreten ist, die Gesamtanzahl von Konflikten sowie die Gesamtwartezeit für eine Ressource.  
  
-   Inklusive Werte geben Aufschluss über die Gesamtanzahl von Konflikten \(sortiert nach Ressourcenkonflikten\), aufgrund derer die Verzögerung für die Funktion aufgetreten ist, sowie über die Gesamtwartezeit der Funktion.  In den inklusiven Werten sind auch durch untergeordnete, von der Funktion aufgerufene Funktionen verursachte Konflikte enthalten.  
  
-   Exklusive Werte geben nur Aufschluss über die Anzahl von Konflikten, die die Verzögerung einer Funktion zur Folge hatten und durch Code im Text der Funktion verursacht wurden.  Von untergeordneten Funktionen verursachte Konflikte werden nicht berücksichtigt.  Die exklusive Zeit für die Funktion umfasst ebenfalls nur die Wartezeiten, die durch Anweisungen im Funktionstext verursacht wurden.  
  
 Die Ansichten des Ressourcenkonfliktberichts enthalten auch Zeitachsendiagramme mit den einzelnen Konfliktereignissen im Zeitverlauf und die Aufruflisten, von denen das Ereignis erstellt wurde.  Weitere Informationen finden Sie in einem der folgenden Themen:  
  
-   [Threaddetailansicht](../profiling/thread-details-view-contention-data.md)  
  
-   [Ressourcendetailansicht](../profiling/resource-details-view-contention-data.md)  
  
 Weitere Informationen zum zweiten Modus der Parallelitätsprofilerstellung finden Sie unter [Parallelitätsschnellansicht](../profiling/concurrency-visualizer.md).