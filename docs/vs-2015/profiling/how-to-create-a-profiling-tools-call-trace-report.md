---
title: 'Vorgehensweise: Erstellen eines Aufrufablaufverfolgungsberichts für Profilerstellungstools | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, viewing ETW data
- ETW [Visual Studio ALM], viewing data
ms.assetid: 7640520a-7d3c-456c-b184-872a5d2f82f3
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fbf92b38f9408455e10048fbd4a5e84fdf822ea2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547991"
---
# <a name="how-to-create-a-profiling-tools-call-trace-report"></a>Gewusst wie: Erstellen eines Aufrufablaufverfolgungsberichts für Profilerstellungstools
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Im *Aufrufablaufverfolgungsbericht* für die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Profilerstellungstools werden Zeitsteuerungsinformationen für jeden Einstiegs- und Endpunkt der Funktionen Ihrer Anwendung sowie jeder Aufruf anderer Funktionen durch die Funktion aufgeführt. Aufrufablaufverfolgungsberichte sind nur für Profilerstellungsdaten verfügbar, wenn diese mit der Instrumentationsmethode gesammelt wurden.  
  
> [!NOTE]
> Sie können keine Aufrufablaufverfolgungsberichte in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] anzeigen. Sie müssen das Befehlszeilen Tool **VSPerfReport** verwenden, um einen durch Trennzeichen getrennten Wert (. CSV) oder eine XML-Datei zu generieren. Weitere Informationen zu diesem Tool finden Sie unter [VSPerfReport](../profiling/vsperfreport.md).  
  
### <a name="to-create-a-call-trace-report"></a>So erstellen Sie einen Aufrufablaufverfolgungsbericht  
  
1. Öffnen Sie ein **Eingabeaufforderungsfenster**.  
  
2. Geben Sie an der Eingabeaufforderung folgenden Befehl ein:  
  
     *ToolsPath* **VSPerfReport** *VSPFile*  **/CallTrace [/Xml]**  
  
    |Command-Element|Beschreibung|
    |-|-|  
    |*ToolsPath*|Der Pfad für die Befehlszeilentools der Profilerstellungstools. Weitere Informationen finden Sie unter [Angeben des Pfads zu Tools für die Befehlszeile](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|  
    |*VSPFile*|Die Profilerstellungs-Datendatei (.vsp oder .vsps). Es werden vollständige und partielle Pfade angenommen.|  
    |Xml|Generiert einen Bericht im XML-Format.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gewusst wie: Erfassen von Daten der Ereignis Ablauf Verfolgung für Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)   
 [Profilerstellungstools-APIs](../profiling/profiling-tools-apis.md)
