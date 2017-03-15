---
title: "Threaddetailansicht - Profiler-Konfliktdaten | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.threaddetails"
helpviewer_keywords: 
  - "Threaddetailansicht"
ms.assetid: 874c3b1c-88d8-479a-bb35-1291d9aa8e67
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Threaddetailansicht - Profiler-Konfliktdaten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Ansicht "Threaddetails" enthält ein Zeitachsendiagramm der blockierenden Ereignisse im ausgewählten Thread einer Profilerstellung, die von Ressourcenkonflikten ausgelöst wurden.  Ein blockierendes Ereignis tritt auf, wenn der Thread gezwungen wird, die Ausführung anzuhalten, da ein anderer Thread den Zugriff auf eine Ressource gesperrt hat.  
  
 Diese Ansicht stellt die Ausführungszeitachse des Threads als horizontalen Balken und die blockierenden Ereignisse als senkrechten Balken auf einer horizontalen Zeitachse für den Thread dar.  Bei Bedarf können Sie die Ansicht eines Zeitachsenbereichs vergrößern, um die einzelnen Ereignisse anzuzeigen.  Um den Ausführungspfad der Funktionen anzuzeigen, die zum Ereignis geführt haben, klicken Sie auf die Ereignisleiste.  Die Funktionen werden im Fenster "Aufrufliste" angezeigt.  Wenn der Quellcode für eine Funktion verfügbar ist, können Sie auf den Funktionsnamen klicken, um die Quelldatei in der Visual Studio IDE zu bearbeiten.  
  
## Navigieren in der Zeitachse  
  
#### So vergrößern Sie die Ansicht eines Zeitachsensegments  
  
-   Wählen Sie mit gedrückter Maustaste einen Bereich auf der Zeitachse aus.  
  
     Wenn Sie die Maustaste loslassen, wird die Ansicht des ausgewählten Zeitsegments vergrößert.  Sie können den Vorgang wiederholen, um größeres Detail zu vergrößern.  Das Bildlauffeld auf der Zeitbildlaufleiste stellt die relative Größe des Zeitsegments dar, das in der Ansicht angezeigt wird.  
  
#### So verkleinern Sie die Ansicht einer Zeitachse  
  
-   Klicken Sie auf **Verkleinern**, um zur vorherigen Zoomstufe zurückzukehren.  
  
-   Klicken Sie auf **Zurücksetzen des Zooms**, um die ganze Zeitachse in der Ansicht anzuzeigen.  
  
#### So zeigen Sie die Aufrufliste eines Ereignisses an  
  
-   Klicken Sie im Zeitachsendiagramm auf den senkrechten Balken, der das Ereignis darstellt.  
  
#### So zeigen Sie den Quellcode für eine Funktion in der Aufrufliste an oder bearbeiten diesen  
  
-   Klicken Sie im Fenster "Aufrufliste" auf den Funktionsnamen.  
  
 Der Funktionsquellcode muss Teil des aktuellen Projekts sein.  
  
#### So zeigen Sie die Konfliktereignisse einer Ressource in allen Threads bei der Profilerstellung an  
  
-   Klicken Sie im Zeitachsendiagramm auf den Namen oder die ID der Ressource.  
  
     Die [Ressourcendetailansicht](../profiling/resource-details-view-contention-data.md) wird für die ausgewählte Ressource angezeigt.  
  
#### So zeigen Sie die Threadkonfliktdaten im Fenster "Prozesse" an  
  
-   Klicken Sie im Zeitachsendiagramm auf **Gesamt**.  
  
     Die [Prozessansicht](../profiling/process-view-contention-data.md) werden für den ausgewählten Thread angezeigt.