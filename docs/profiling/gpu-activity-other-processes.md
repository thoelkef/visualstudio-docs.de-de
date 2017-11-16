---
title: "GPU-Aktivität (andere Prozesse) | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.cv.threads.timeline.gpuother
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 8a68df65-eb63-452f-9285-fb4ffc92f2b2
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3b32ee2967ccc4a7cf1f02935a58cfff5c9e8a33
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="gpu-activity-other-processes"></a>GPU-Aktivität (andere Prozesse)
Die Segmente der **GPU-Aktivität (andere Prozesse)** in der Threads-Ansicht von Concurrency Visualizer stellen Zeiten dar, in denen die GPU Anforderungen im Auftrag von anderen Prozessen im System verarbeitet hat. Diese Anforderungen werden an die GPU als DMA-Pakete (direkter Speicherzugriff) gesendet.  Die Länge eines Segments stellt die Zeitspanne dar, in der das Paket von der GPU verarbeitet wurde.  
  
 Wenn Sie diese Segmentart auswählen, zeigt der Bericht in der Registerkarte **Aktuell** Informationen über das verarbeitete Paket an.  Die Information umfasst die Zeitspanne, in der das Paket in der Hardware-Warteschlange gewartet hat, die mit dem DirectX-Modul – der Prozess, der das Paket gesendet hat – und der Zeit, die zum Verarbeiten des Pakets benötigt wurde, verbunden wird.