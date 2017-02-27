---
title: "Zusammenfassungsansicht - Profiler-Ansicht f&#252;r Ressourcenkonflikte | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Zusammenfassungsansicht"
ms.assetid: 6da57b83-7b42-4d7c-9aea-8e0a830faf6b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Zusammenfassungsansicht - Profiler-Ansicht f&#252;r Ressourcenkonflikte
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In der Zusammenfassungsansicht werden Informationen zu den Ereignissen in der Anwendung angezeigt, in der ein Thread oder ein Prozess angehalten wurde, während er auf Zugriff auf eine Ressource gewartet hat.  
  
 Weitere Informationen, einschließlich einer Beschreibung der Benachrichtigungslinks und Berichtslisten, finden Sie unter [Zusammenfassungsansicht](../profiling/summary-view.md).  
  
## Zeitachsendiagramm  
 Das Zeitachsendiagramm in der Zusammenfassungsansicht zeigt die Anzahl von Konfliktereignissen der profilierten Anwendung über den Zeitraum der Profilerstellung an.  Sie können die Ansicht mithilfe des Zeitachsendiagramms nach einem ausgewählten Zeitraum filtern.  Weitere Informationen finden Sie unter [Gewusst wie: Filtern von Berichtsansichten aus der Zeitachsenübersicht](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).  
  
## Ressourcen mit den meisten Konflikten  
 Unter **Ressourcen mit den meisten Konflikten** sind die Ressourcen in der Anwendung aufgeführt, die die meisten Konfliktereignisse verursachten.  Sie können auf einen Ressourcennamen klicken, um die Konfliktansicht anzuzeigen.  Die Konfliktansicht stellt eine detaillierte Zeitachse der Ressourcenkonflikte nach Thread bereit.  
  
 **Ressourcen mit den meisten Konflikten** umfasst die folgenden Daten für die einzelnen Ressourcen:  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Name**|Der Name der Ressource.|  
|**Konflikte %**|Der Prozentsatz aller Konfliktereignisse in den Profilerstellungsdaten, die Konflikte über dieser Ressource waren.|  
  
## Threads mit den meisten Konflikten  
 Unter **Threads mit den meisten Konflikten** sind die Threads in der Anwendung mit der größten Anzahl von Konfliktereignissen aufgeführt.  Sie können auf einen Threadnamen klicken, um die Konfliktansicht anzuzeigen, die eine detaillierte Zeitachse der Ressourcenkonflikte nach Thread bereitstellt.  
  
 **Threads mit den meisten Konflikten** umfasst die folgenden Daten für die einzelnen Threads:  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**ID**|Der Threadbezeichner.|  
|**Name**|Der Name des Prozesses, der den Thread besitzt.|  
|**Konflikte %**|Der Prozentsatz aller Konfliktereignisse in den Profilerstellungsdaten, die Konflikte über dieser Ressource waren.|