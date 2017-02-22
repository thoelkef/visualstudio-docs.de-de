---
title: "Gewusst wie: Sammeln von Windows-Indikatordaten | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.property.syscounter"
  - "vs.performance.property.wincounter"
helpviewer_keywords: 
  - "Windows-Indikatoren"
  - "Leistungstools, Verwenden von Windows-Indikatoren"
  - "Profilerstellungtools, Verwenden von Windows-Indikatoren"
ms.assetid: db4fbac2-bea5-4558-aa8b-160fcccf4b33
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Sammeln von Windows-Indikatordaten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Windows\-Indikatoren sind Systemleistungsindikatoren, die bei festgelegten Intervallen während der Profilerstellung gesammelt werden können.  In der Markierungsansicht des Berichts für Profilerstellungstools finden Sie für jedes Sammlungsintervall eine Zeile mit der Bezeichnung **AutoMark**.  Die Zeile enthält Spalten, in denen die Leistungsindikatorwerte für dieses Intervall beschrieben werden.  Um die Analyse auf einen bestimmten Zeitraum zwischen zwei Markierungen einzugrenzen, wählen Sie die Markierungen aus, klicken Sie mit der rechten Maustaste und wählen Sie dann \-\> auf  **Markierungen** im Kontextmenü **Filtern nach** aus.  
  
 **Voraussetzungen**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
> [!NOTE]
>  Verbesserte Sicherheitsfeatures in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio\-Profilers auf diesen Plattformen.  Außerdem benötigen Windows Store\-Apps neue Erfassungsmethoden.  Siehe [Profilerstellung für Windows 8\- und Windows Server 2012\-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
### So erfassen Sie Windows\-Indikatordaten  
  
1.  Klicken Sie im Leistungs\-Explorer mit der rechten Maustaste auf die Sitzung, für die Sie Windows\-Indikatoren konfigurieren möchten, und wählen Sie **Eigenschaften** aus.  
  
2.  Klicken Sie in den **Eigenschaftenseiten** auf **Windows\-Indikatoren**.  
  
3.  Aktivieren Sie das Kontrollkästchen **Windows\-Indikatoren erfassen**.  
  
4.  Geben Sie im Textfeld **Erfassungsintervall \(ms\)** ein Zeitintervall ein.  
  
5.  Wählen Sie in der Dropdownliste **Indikatorenkategorie** eine Kategorie aus.  
  
6.  Wählen Sie aus der Dropdownliste **Instanz** eine Instanz aus.  
  
7.  Wählen Sie die gewünschten Indikatoren für die Profilerstellung für Ihre Anwendung aus.  
  
8.  Klicken Sie auf **Übernehmen**.  
  
## Siehe auch  
 [Konfigurieren von Leistungssitzungen](../profiling/configuring-performance-sessions.md)   
 [Eigenschaften von Leistungssitzungen](../profiling/performance-session-properties.md)   
 [CPU\- und Windows\-Indikatoren](../profiling/cpu-and-windows-counters.md)