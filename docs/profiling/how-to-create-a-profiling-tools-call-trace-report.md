---
title: "Gewusst wie: Erstellen eines Aufrufablaufverfolgungsberichts f&#252;r Profilerstellungstools | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ETW [Visual Studio-ALM], Anzeigen von Daten"
  - "Leistungstools, Anzeigen von ETW-Daten"
ms.assetid: 7640520a-7d3c-456c-b184-872a5d2f82f3
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# Gewusst wie: Erstellen eines Aufrufablaufverfolgungsberichts f&#252;r Profilerstellungstools
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Im *Aufrufablaufverfolgungsbericht* für die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Profilerstellungstools werden Zeitsteuerungsinformationen für jeden Einstiegs\- und Endpunkt der Funktionen Ihrer Anwendung sowie jeder Aufruf anderer Funktionen durch die Funktion aufgeführt.  Aufrufablaufverfolgungsberichte sind nur für Profilerstellungsdaten verfügbar, wenn diese mit der Instrumentationsmethode gesammelt wurden.  
  
> [!NOTE]
>  Sie können keine Aufrufablaufverfolgungsberichte in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] anzeigen.  Sie müssen das Befehlszeilentool **VSPerfReport** verwenden, um einen durch Trennzeichen getrennten Wert \(.csv\) oder eine XML\-Datei zu generieren.  Weitere Informationen zu diesem Tool finden Sie unter [VSPerfReport](../profiling/vsperfreport.md).  
  
### So erstellen Sie einen Aufrufablaufverfolgungsbericht  
  
1.  Öffnen Sie ein **Eingabeaufforderungsfenster**.  
  
2.  Geben Sie an der Eingabeaufforderung folgenden Befehl ein:  
  
     *ToolsPath* **VSPerfReport** *VSPFile* **\/CallTrace \[\/Xml\]**  
  
    |||  
    |-|-|  
    |*ToolsPath*|Der Pfad für die Befehlszeilentools der Profilerstellungstools.  Weitere Informationen finden Sie unter [Angeben des Pfads zu Tools für die Befehlszeile](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|  
    |*VSPFile*|Die Profilerstellungs\-Datendatei \(.vsp oder .vsps\).  Es werden vollständige und partielle Pfade angenommen.|  
    |Xml|Generiert einen Bericht im XML\-Format.|  
  
## Siehe auch  
 [Gewusst wie: Sammeln von Daten der Ereignisablaufverfolgung für Windows \(ETW\)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)   
 [APIs für Profilerstellungstools](../profiling/profiling-tools-apis.md)