---
title: "Benutzeroberfl&#228;chenverarbeitungszeit | Microsoft Docs"
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
  - "vs.cv.threads.timeline.uiprocessing"
helpviewer_keywords: 
  - "Parallelitätsschnellansicht, Benutzeroberflächenverarbeitungszeit"
ms.assetid: 0ddb05a3-8c6b-448b-8488-2751c1e5abcc
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Benutzeroberfl&#228;chenverarbeitungszeit
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese Segmente in der Zeitachse sind Blockierungszeiten zugeordnet, die als Benutzeroberflächenverarbeitung kategorisiert werden.  Dies bedeutet, dass ein Thread Windows\-Meldungen weiterleitet oder andere Aktionen für die Benutzeroberfläche ausführt.  Währenddessen wurde ein Thread in einer API blockiert, der von der Parallelitätsschnellansicht als Benutzeroberflächenverarbeitung angesehen wird.  Zu dieser Gruppe gehören APIs wie `GetMessage()` und `MsgWaitForMultipleObjects()`.  
  
 Überprüfen Sie die Aufruflisten und Profilberichte, um die zugrunde liegenden Ursachen der Verzögerung zu bestimmen, wenn keine vordefinierte blockierende API identifiziert wird.  
  
 Die Kategorie "Benutzeroberflächenverarbeitung" ist wichtig, um die Reaktionsgeschwindigkeit von GUI\-Anwendungen zu verstehen. Sie ist wünschenswert für Anwendungen, die von der Reaktionsgeschwindigkeit der Benutzeroberfläche abhängig sind.  Wenn beispielsweise der UI\-Thread in einer Anwendung bei der Benutzeroberflächenverarbeitung den Wert 100 % erreicht, ist wahrscheinlich eine hohe Reaktionsfähigkeit gegeben.  Wenn der UI\-Thread jedoch beträchtliche Zeit für andere Kategorien aufwendet, sollten Sie nach den Ursachen suchen und Optionen zur Verringerung von Kategorien prüfen, die keinen Bezug zur Benutzeroberfläche haben.  
  
## Siehe auch  
 [Threadansicht](../profiling/threads-view-parallel-performance.md)