---
title: 'Vorgehensweise: Sammeln von Windows-Indikatordaten | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.syscounter
- vs.performance.property.wincounter
helpviewer_keywords:
- windows counters
- performance tools, using windows counters
- profiling tools, using windows counters
ms.assetid: db4fbac2-bea5-4558-aa8b-160fcccf4b33
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9743fa7defbbf3321636d2ba4799454713a647db
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432783"
---
# <a name="how-to-collect-windows-counter-data"></a>Gewusst wie: Sammeln von Windows-Indikatordaten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows-Indikatoren sind Systemleistungsindikatoren, die während der Profilerstellung in festgelegten Intervallen gesammelt werden können In der Markierungsansicht des Berichts „Profilerstellungstools“, wird eine Zeile für jedes Sammlungsintervall als **AutoMark** bezeichnet. Die Zeile enthält Spalten, die die Leistungsindikatorwerte in diesem Intervall beschreibt. Klicken Sie zum Beschränken der Analyse auf eine Zeitraum zwischen zwei bestimmten Markierungen auf die Markierungen, anschließend auf die rechte Maustaste, und wählen Sie dann im Kontextmenü **Filtern nach** ->  **Markierungen** aus  
  
 **Anforderungen**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
> [!NOTE]
> Verbesserte Sicherheitsfunktionen in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio-Profilers auf diesen Plattformen. Außerdem benötigen Windows Store-Apps neue Erfassungsmethoden. Siehe [Profilerstellungstools für Windows 8- und Windows Server 2012-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
### <a name="to-collect-windows-counter-data"></a>So sammeln Sie Windows-Indikatordaten  
  
1. Klicken Sie im Leistungs-Explorer mit der rechten Maustaste auf die Sitzung, für die Sie Windows-Indikatoren konfigurieren möchten, und wählen Sie **Eigenschaften** aus.  
  
2. Klicken Sie in den **Eigenschaftenseiten** auf **Windows-Indikatoren**.  
  
3. Wählen Sie das Kontrollkästchen **Windows-Indikatoren auflisten** aus.  
  
4. Geben Sie im Textfeld **Sammlungsintervall (ms)** ein Zeitintervall ein.  
  
5. Wählen Sie eine Kategorie aus der Dropdownliste **Indikatorkategorie** aus.  
  
6. Wählen Sie eine Instanz aus der Dropdownliste **Instanz** aus.  
  
7. Wählen Sie die Indikatoren aus, die Sie bei der Profilerstellung Ihrer Anwendung verwenden möchten.  
  
8. Klicken Sie auf **Übernehmen**.  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren von Leistungssitzungen](../profiling/configuring-performance-sessions.md)   
 [Eigenschaften von Leistungssitzungen](../profiling/performance-session-properties.md)   
 [CPU- und Windows-Indikatoren](../profiling/cpu-and-windows-counters.md)
