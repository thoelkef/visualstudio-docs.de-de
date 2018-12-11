---
title: 'Vorgehensweise: Erstellen eines ETW-Berichts mit Profilerstellungstools | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bf5547b3-f6c7-4989-9d47-2fe4f1261444
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1901cf0800483ee4ce8ba0bce26fe3cf7ac073e6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51761600"
---
# <a name="how-to-create-a-profiling-tools-etw-report"></a>Gewusst wie: Erstellen eines ETW-Berichts mit den Profilerstellungstools
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In einem ETW-Bericht werden die ETW-Ereignisse aufgeführt, die während einer Leistungssitzung der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Profilerstellungstools aufgezeichnet wurden. ETW-Daten werden in einer Binärdatei (.etl) erfasst. Weitere Informationen zu diesem Bericht finden Sie unter [Bericht der Ereignisablaufverfolgung für Windows (ETW)](../profiling/event-tracing-for-windows-etw-report.md).  
  
> [!NOTE]
>  ETW-Berichte können in der Schnittstelle für [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nicht angezeigt werden.  
  
- Weitere Informationen zum Erfassen der ETW-Daten über die Schnittstelle für [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] finden Sie unter [Vorgehensweise: Erfassen von Daten der Ereignisablaufverfolgung für Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).  
  
- Informationen zum Erfassen von ETW-Daten über eine Eingabeaufforderung finden Sie unter [VSPerfCmd](../profiling/vsperfcmd.md) und [Events (Ereignisse)](../profiling/events-vsperfcmd.md).  
  
  Der ETW-Bericht wird über den Befehl **VSReport/summary:etw** erstellt. Die ETL-Datei, die die ETW-Daten enthält, muss sich in demselben Verzeichnis befinden wie die Profilerstellungsdatendatei (.vsp oder .vsps). Standardmäßig wird der Bericht als eine durch Trennzeichen getrennte Datei (.csv) generiert. Weitere Informationen finden Sie unter [VSPerfReport](../profiling/vsperfreport.md).  
  
### <a name="to-generate-an-etw-report"></a>So erstellen Sie einen ETW-Bericht  
  
-   Geben Sie im Fenster **Eingabeaufforderung** die folgende Befehlszeile ein:  
  
     *ToolsPath* **VSPerfReport** *VSPFile* **/Summary:ETW [/Xml]**  
  
    |||  
    |-|-|  
    |*ToolsPath*|Der Pfad zum Hilfsprogramm für die Profilerstellungstools. Weitere Informationen finden Sie unter [Angeben des Pfads zu Tools für die Befehlszeile](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|  
    |*VSPFile*|Die Profilerstellungs-Datendatei (.vsp oder .vsps). Es werden vollständige und partielle Pfade angenommen.|  
    |Xml|Generiert einen in XML formatierten Bericht.|



