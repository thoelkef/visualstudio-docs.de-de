---
title: 'Vorgehensweise: Erstellen eines Aufrufablaufverfolgungsberichts für Profilerstellungstools | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- performance tools, viewing ETW data
- ETW [Visual Studio ALM], viewing data
ms.assetid: 7640520a-7d3c-456c-b184-872a5d2f82f3
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b643e0bf356e7ffb3bf6030ff46cf38ad4a1d98a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47524143"
---
# <a name="how-to-create-a-profiling-tools-call-trace-report"></a>Gewusst wie: Erstellen eines Aufrufablaufverfolgungsberichts für Profilerstellungstools
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Vorgehensweise: Erstellen eines Profiling Tools aufrufen Trace-Berichts](https://docs.microsoft.com/visualstudio/profiling/how-to-create-a-profiling-tools-call-trace-report).  
  
Im *Aufrufablaufverfolgungsbericht* für die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Profilerstellungstools werden Zeitsteuerungsinformationen für jeden Einstiegs- und Endpunkt der Funktionen Ihrer Anwendung sowie jeder Aufruf anderer Funktionen durch die Funktion aufgeführt. Aufrufablaufverfolgungsberichte sind nur für Profilerstellungsdaten verfügbar, wenn diese mit der Instrumentierungsmethode gesammelt wurden.  
  
> [!NOTE]
>  Sie können keine Aufrufablaufverfolgungsberichte in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] anzeigen. Sie müssen das Befehlszeilentool **VSPerfReport** verwenden, um einen durch Trennzeichen getrennten Wert (.csv) oder eine XML-Datei zu generieren. Weitere Informationen zu diesem Tool finden Sie unter [VSPerfReport](../profiling/vsperfreport.md).  
  
### <a name="to-create-a-call-trace-report"></a>So erstellen Sie einen Aufrufablaufverfolgungsbericht  
  
1.  Öffnen Sie ein **Eingabeaufforderungsfenster**.  
  
2.  Geben Sie an der Eingabeaufforderung folgenden Befehl ein:  
  
     *ToolsPath* **VSPerfReport** *VSPFile* **/CallTrace [/Xml]**  
  
    |||  
    |-|-|  
    |*ToolsPath*|Der Pfad für die Befehlszeilentools der Profilerstellungstools. Weitere Informationen finden Sie unter [Angeben des Pfads zu Tools für die Befehlszeile](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|  
    |*VSPFile*|Die Profilerstellungs-Datendatei (.vsp oder .vsps). Es werden vollständige und partielle Pfade angenommen.|  
    |Xml|Generiert einen Bericht im XML-Format.|  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Sammeln von Daten der Ereignisablaufverfolgung für Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)   
 [APIs für Profilerstellungstools](../profiling/profiling-tools-apis.md)



