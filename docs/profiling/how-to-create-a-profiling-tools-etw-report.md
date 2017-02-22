---
title: "Gewusst wie: Erstellen eines ETW-Berichts mit den Profilerstellungstools | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bf5547b3-f6c7-4989-9d47-2fe4f1261444
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Erstellen eines ETW-Berichts mit den Profilerstellungstools
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Im Bericht der Ereignisablaufverfolgung für Windows \(ETW\) werden die ETW\-Ereignisse aufgeführt, die in einer Leistungssitzung der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Profilerstellungstools aufgezeichnet werden.  ETW\-Daten werden in einer Binärdatei \(.etl\) erfasst.  Weitere Informationen über diesen Bericht finden Sie unter [Bericht der Ereignisablaufverfolgung für Windows \(ETW\)](../profiling/event-tracing-for-windows-etw-report.md).  
  
> [!NOTE]
>  Sie können keine ETW\-Berichte in der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Oberfläche anzeigen.  
  
-   Informationen zum Sammeln von ETW\-Daten mit der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Benutzeroberfläche finden Sie unter [Gewusst wie: Sammeln von Daten der Ereignisablaufverfolgung für Windows \(ETW\)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).  
  
-   Informationen zum Erfassen von ETW\-Daten über eine Eingabeaufforderung finden Sie unter [VSPerfCmd](../profiling/vsperfcmd.md) und [Ereignisse](../profiling/events-vsperfcmd.md).  
  
 Der ETW\-Bericht wird mit dem **VSReport \/summary:etw**\-Befehl generiert.  Die ETL\-Dateien mit den ETW\-Daten muss sich im selben Verzeichnis wie die Profilerstellungs\-Datendatei \(.vsp oder .vsps\) befinden.  Standardmäßig wird der Bericht als CSV\-Datei \(.csv\) generiert.  Weitere Informationen finden Sie unter [VSPerfReport](../profiling/vsperfreport.md).  
  
### So generieren Sie einen ETW\-Bericht  
  
-   Geben Sie in einem Eingabeaufforderungsfenster die folgende Befehlszeile ein:  
  
     *ToolsPath* **VSPerfReport** *VSPFile* **\/Summary:ETW \[\/Xml\]**  
  
    |||  
    |-|-|  
    |*ToolsPath*|Der Pfad der Profilerstellungstools.  Weitere Informationen finden Sie unter [Angeben des Pfads zu Tools für die Befehlszeile](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|  
    |*VSPFile*|Die Profilerstellungs\-Datendatei \(.vsp oder .vsps\).  Es werden vollständige und partielle Pfade angenommen.|  
    |Xml|Generiert einen Bericht, der in XML formatiert wird.|