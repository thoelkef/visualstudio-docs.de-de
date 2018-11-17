---
title: Kernansicht | Microsoft-Dokumentation
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
- vs.performance.view.cores
helpviewer_keywords:
- Concurrency Visualizer, Cores View
ms.assetid: e47af672-9785-4899-bd45-4d9dda3c396f
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6c609745e0df5ece6d3de9be718851b45110d4fb
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51746315"
---
# <a name="cores-view"></a>Kernansicht
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Kernansicht zeigt, wie die Ausführung der Threads den logischen Prozessorkernen zugeordnet wurde. Beim Schreiben von Serveranwendungen kann diese Ansicht nützlich sein: Optimieren Sie die Cacheleistung, indem Sie Threadaffinität oder Threadpoolverwaltung einsetzen. Manchmal kann sich auch die Prüfung von Fällen als hilfreich erweisen, in denen die Verwendung von Threadaffinität das Problem kernübergreifender Migration noch verstärkt hat. Die Kernansicht verfügt über zwei Komponenten: ein Diagramm und eine Legende.  
  
 Das Diagramm bildet logische Kerne auf der y-Achse und die Zeit auf der x-Achse ab. Jeder Thread im Diagramm hat eine eindeutige Farbe, damit Sie seine Bewegung durch Kerne im zeitlichen Verlauf verfolgen können. Sie können die Threads in diesem Diagramm filtern, indem Sie sie im Legendenbereich auswählen.  
  
 Der Legendenbereich enthält einen Eintrag für jede Farbe im Diagramm. Jeder Eintrag zeigt die Threadfarbe und den Threadnamen, die Anzahl der kernübergreifenden Kontextwechsel, die Gesamtzahl der Kontextwechsel und den Prozentsatz der Kontextwechsel, die durch Kerne verlaufen. Die Legende ist nach der Anzahl der kernübergreifenden Kontextwechsel in absteigender Reihenfolge angeordnet. Sie enthält nur jene Threads, die während des angezeigten Zeitraums ausgeführt wurden.  Die Liste wird aktualisiert, wenn Sie zoomen oder schwenken.  
  
## <a name="see-also"></a>Siehe auch  
 [Nebenläufigkeitsschnellansicht](../profiling/concurrency-visualizer.md)   
 [Auslastungsansicht](../profiling/utilization-view.md)   
 [Threads View (Threadansicht)](../profiling/threads-view-parallel-performance.md)



