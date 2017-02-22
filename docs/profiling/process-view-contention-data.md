---
title: "Prozessansicht - Profiler-Konfliktdaten | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Prozessansicht"
ms.assetid: 8821d98c-0771-43b2-a38b-e9039a3abd75
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Prozessansicht - Profiler-Konfliktdaten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Prozessansicht zeigt Konfliktdaten für die Prozesse und Threads an, die während der Profilerstellung ausgeführt wurden.  
  
 Wenn Symbole verfügbar sind, werden Prozesse nach Name aufgelistet.  Wenn keine Symbole verfügbar sind, werden Prozesse nach zugewiesener Speicheradresse im Hexadezimalformat aufgelistet.  Threads werden als untergeordnete Elemente des Prozesses aufgeführt, der sie erstellt hat.  
  
 In der folgenden Tabelle werden die Werte der Spalten in der Prozessansichtstabelle erläutert.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Anfangszeit**|Die Zeit in Millisekunden oder Prozessorzyklen vom Start der Profilerstellung bis zum Start des Prozesses oder Threads.|  
|**Blockierte Zeit**|Die Gesamtzeit, während der die Ausführung von Funktionen des Prozesses oder Threads blockiert wurde.|  
|**Blockierte Zeit %**|Der Prozentsatz der Lebensdauer des Prozesses oder Threads, in dem die Ausführung von Funktionen des Prozesses oder Threads blockiert wurde.|  
|**Konflikte**|Die Häufigkeit, mit der die Ausführung von Funktionen des Prozesses oder Threads blockiert wurde.|  
|**Konflikte %**|Der Prozentsatz aller Konflikte in der Profilerstellung, bei denen es sich um Konflikte des Prozesses oder Threads handelte.|  
|**Endzeit**|Die Zeit in Millisekunden oder Prozessorzyklen vom Start der Profilerstellung bis zum Ende des Prozesses oder Threads.|  
|**ID**|Der vom System generierte Bezeichner für den Prozess oder Thread.|  
|**Lebensdauer**|Die Zeit in Millisekunden oder Prozessorzyklen vom Start des Prozesses oder Threads bis zum Ende des Prozesses oder Threads oder bis zum Ende der Profilausstellung.|  
|**Typ**|Der Typ der Zeile, entweder Prozess oder Thread.<br /><br /> Nur in **VSReport**\-Befehlszeilenberichten.  Weitere Informationen finden Sie unter [VSPerfReport](../profiling/vsperfreport.md).|  
|**Name**|Der Name des Prozesses oder Threads.|  
|**Unique ID**|Ein vom Profiler generierter eindeutiger Bezeichner für den Prozess oder Thread.|  
  
## Siehe auch  
 [Gewusst wie: Anpassen von Spalten in Berichtsansichten](../profiling/how-to-customize-report-view-columns.md)   
 [Prozessansicht](../profiling/process-view.md)