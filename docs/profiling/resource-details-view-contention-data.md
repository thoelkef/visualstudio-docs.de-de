---
title: "Ressourcendetailansicht - Profiler-Konfliktdaten | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.resourcedetails"
helpviewer_keywords: 
  - "Ressourcendetailansicht"
ms.assetid: a4ecfe1c-abbc-4fb3-9ab2-34de50486901
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Ressourcendetailansicht - Profiler-Konfliktdaten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Ressourcendetailansicht präsentiert ein Zeitachsendiagramm der blockierenden Ereignisse, die von Konflikten bei einer ausgewählten Ressource verursacht wurden.  Ein blockierendes Ereignis tritt auf, wenn ein Thread gezwungen wird, die Ausführung anzuhalten, da ein anderer Thread den Zugriff auf die Ressource gesperrt hat.  
  
 Diese Ansicht stellt die Ausführungszeitachse jedes Threads als horizontale Leiste dar und stellt jedes Blockierungsereignis als senkrechten Strich auf der Threadzeitachse dar.  Falls notwendig können Sie einen Abschnitt der Zeitachse vergrößern, um einzelne Ereignisse anzuzeigen.  Um den Ausführungspfad \(Aufrufliste\) der Funktionen anzuzeigen, die zum Ereignis geführt haben, klicken Sie auf die Ereignisleiste.  Die Funktionen werden im Fenster **Aufrufliste** angezeigt.  Wenn der Quellcode für eine Funktion verfügbar ist, können Sie auf den Funktionsnamen klicken, um die Quelldatei in der Schnittstelle für [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zu bearbeiten.  
  
## Prozeduren  
  
#### So vergrößern Sie ein Zeitachsensegment  
  
-   Ziehen Sie den Mauszeiger über einen Bereich der Zeitachse.  
  
     Wenn Sie die Maustaste loslassen, wird die Ansicht des ausgewählten Zeitsegments vergrößert.  Sie können den Prozess wiederholen, um das Segment weiter zu vergrößern.  Das Bildlauffeld auf der Zeitbildlaufleiste stellt die relative Größe des Zeitsegments dar, das in der Ansicht angezeigt wird.  
  
#### So verkleinern Sie die Ansicht einer Zeitachse  
  
-   Führen Sie einen der folgenden Schritte aus:  
  
    -   Klicken Sie auf **Verkleinern**, um zur vorherigen Zoomstufe zurückzukehren.  
  
    -   Klicken Sie auf **Zurücksetzen des Zooms**, um die ganze Zeitachse in der Ansicht anzuzeigen.  
  
#### So zeigen Sie die Aufrufliste eines Ereignisses an  
  
-   Klicken Sie im Zeitachsendiagramm auf die Ereignisleiste.  
  
#### So zeigen Sie den Quellcode für eine Funktion in der Aufrufliste an oder bearbeiten diesen  
  
-   Klicken Sie im Fenster **Aufrufliste** auf den Funktionsnamen.  
  
 Der Funktionsquellcode muss Teil des aktuellen Projekts sein.  
  
#### So zeigen Sie die Aufrufstruktur von Konfliktereignissen für die Ressource an  
  
-   Klicken Sie im Zeitachsendiagramm auf **Gesamt**.  
  
     Die Ansicht "Konflikte" wird für die Ressource angezeigt.  Weitere Informationen finden Sie unter [Ressourcenkonfliktansicht](../profiling/resource-contentions-view-contention-data.md)  
  
#### So zeigen Sie alle Konfliktereignisse eines Threads an  
  
-   Klicken Sie im Zeitachsendiagramm auf den Namen oder die ID des Threads.  
  
     Die Threaddetailansicht wird für den ausgewählten Thread angezeigt.  Weitere Informationen finden Sie unter [Threaddetailansicht](../profiling/thread-details-view-contention-data.md).