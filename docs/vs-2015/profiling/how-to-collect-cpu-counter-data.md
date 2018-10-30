---
title: 'Vorgehensweise: Sammeln von CPU-Indikatordaten | Microsoft-Dokumentation'
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
- vs.performance.property.cpucounters
helpviewer_keywords:
- profiling tools, using portable CPU counters
- performance tools, portable CPU counters
ms.assetid: 102fb6ca-5fbf-4b05-925f-56912ce3f44b
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 89750ad7ee47f1238d75d3c51ae0b6ee291944fe
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49940943"
---
# <a name="how-to-collect-cpu-counter-data"></a>Gewusst wie: Sammeln von CPU-Indikatordaten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ein CPU-Ereignisindikator wird zum Sammeln von hardwarespezifischen Leistungsdaten verwendet. In diesem Thema erfahren Sie, wie Sie Ereignisindikatordaten sammeln, wenn Sie die Instrumentierungs-Profilerstellungs-Methode verwenden.  
  
 **Anforderungen**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  Es treten zwei Typen von CPU-Indikatorereignissen auf:  
  
- Portable Ereignisse: CPU-Ereignisse, die unabhängig des bestimmten CPUs gesammelt werden.  
  
- Plattformereignisse: CPU-Ereignisse, die mit einem bestimmten CPU verbunden sind.  
  
  Portable Ereignisse enthalten allgemeine Ereignisse, z.B. zurückgezogene Anweisungen und nicht angehaltene Zyklen, CPU-Pufferereignisse, verzweigte Ereignisse sowie L2-Cache-Ereignisse. Die verfügbaren Plattformereignisindikatoren werden durch den Hersteller des Prozessors bestimmt.  
  
  Ereigniskategorien können von portablen und Plattfomindikatoren gemeinsam genutzt werden. Die folgenden Datenkategorien gelten z.B. häufig für beide Typen:  
  
- Speicherereignisse  
  
- Front-End-Ereignisse  
  
- Verzweigungsereignisse  
  
  Sie können die Leistungsindikatordaten auf Zwei Arten im Profiler sammeln:  
  
- Sammeln Sie Daten aus einem oder mehrere Leistungsindikatoren, wenn Sie ein Profil durch Instrumentation erstellen.  
  
- Geben Sie ein Leistungsindikatorereignis als Samplingintervall an, wenn Sie das Profil durch Sampling erstellen. Weitere Informationen finden Sie unter [Vorgehensweise: Auswählen von Samplingereignissen](../profiling/how-to-choose-sampling-events.md)  
  
### <a name="to-collect-cpu-performance-counter-data-when-you-profile-by-instrumentation"></a>So sammeln Sie CPU-Leistungsindikatordaten, wenn Sie ein Profil durch Instrumentation erstellen.  
  
1.  Klicken Sie auf der Leistungssitzung **Eigenschaftenseiten** auf **CPU-Indikatoren.**  
  
2.  Wählen Sie das Kontrollkästchen **CPU-Indikatoren auflisten** aus.  
  
3.  Erweitern Sie die Struktur **Verfügbaren Leistungsindikatoren**, bis Sie die Beispielereignisse finden, die Sie sammeln möchten.  
  
4.  Wählen Sie für jedes Ereignis, das Sie erfassen möchten, das Ereignis aus, und klicken Sie dann auf den Pfeil nach rechts, um das Ereignis zur Liste **Ausgewählte Indikatoren** hinzuzufügen.  
  
    > [!NOTE]
    >  **Verfügbare Leistungsindikatoren** ist nur aktiviert, wenn Sie das Kontrollkästchen **CPU-Indikatoren auflisten** auswählen.  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren von Leistungssitzungen](../profiling/configuring-performance-sessions.md)   
 [Eigenschaften von Leistungssitzungen](../profiling/performance-session-properties.md)   
 [CPU- und Windows-Indikatoren](../profiling/cpu-and-windows-counters.md)   
 [Vorgehensweise: Auswählen von Samplingereignissen](../profiling/how-to-choose-sampling-events.md)



