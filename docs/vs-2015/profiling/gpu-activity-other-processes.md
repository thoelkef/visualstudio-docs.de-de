---
title: GPU-Aktivität (andere Prozesse) | Microsoft-Dokumentation
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
- vs.cv.threads.timeline.gpuother
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 8a68df65-eb63-452f-9285-fb4ffc92f2b2
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a5b38423bd629dee0f518e0f62eedcf7c55c1db0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51789836"
---
# <a name="gpu-activity-other-processes"></a>GPU-Aktivität (andere Prozesse)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Segmente der **GPU-Aktivität (andere Prozesse)** in der Threads-Ansicht von Concurrency Visualizer stellen Zeiten dar, in denen die GPU Anforderungen im Auftrag von anderen Prozessen im System verarbeitet hat. Diese Anforderungen werden an die GPU als DMA-Pakete (direkter Speicherzugriff) gesendet.  Die Länge eines Segments stellt die Zeitspanne dar, in der das Paket von der GPU verarbeitet wurde.  
  
 Wenn Sie diese Segmentart auswählen, zeigt der Bericht in der Registerkarte **Aktuell** Informationen über das verarbeitete Paket an.  Die Information umfasst die Zeitspanne, in der das Paket in der Hardware-Warteschlange gewartet hat, die mit der DirectX-Engine – der Prozess, der das Paket gesendet hat – und der Zeit, die zum Verarbeiten des Pakets benötigt wurde, verbunden wird.



