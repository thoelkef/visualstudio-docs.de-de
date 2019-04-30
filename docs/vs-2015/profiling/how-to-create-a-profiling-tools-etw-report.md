---
title: 'Vorgehensweise: Erstellen eines ETW-Berichts mit Profilerstellungstools | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: bf5547b3-f6c7-4989-9d47-2fe4f1261444
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6b172ffbf481ea077d099288b3b79254b89b13a5
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432745"
---
# <a name="how-to-create-a-profiling-tools-etw-report"></a>Vorgehensweise: Erstellen einer Profilerstellung ETW-Berichts
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In einem ETW-Bericht werden die ETW-Ereignisse aufgeführt, die während einer Leistungssitzung der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Profilerstellungstools aufgezeichnet wurden. ETW-Daten werden in einer Binärdatei (.etl) erfasst. Weitere Informationen zu diesem Bericht finden Sie unter [Bericht der Ereignisablaufverfolgung für Windows (ETW)](../profiling/event-tracing-for-windows-etw-report.md).  
  
> [!NOTE]
> ETW-Berichte können in der Schnittstelle für [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nicht angezeigt werden.  
  
- Weitere Informationen zum Erfassen der ETW-Daten über die Schnittstelle für [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] finden Sie unter [Vorgehensweise: Sammeln der Ereignisablaufverfolgung für Windows (ETW) Daten](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).  
  
- Informationen zum Erfassen von ETW-Daten über eine Eingabeaufforderung finden Sie unter [VSPerfCmd](../profiling/vsperfcmd.md) und [Events (Ereignisse)](../profiling/events-vsperfcmd.md).  
  
  Der ETW-Bericht wird über den Befehl **VSReport/summary:etw** erstellt. Die ETL-Datei, die die ETW-Daten enthält, muss sich in demselben Verzeichnis befinden wie die Profilerstellungsdatendatei (.vsp oder .vsps). Standardmäßig wird der Bericht als eine durch Trennzeichen getrennte Datei (.csv) generiert. Weitere Informationen finden Sie unter [VSPerfReport](../profiling/vsperfreport.md).  
  
### <a name="to-generate-an-etw-report"></a>So erstellen Sie einen ETW-Bericht  
  
- Geben Sie im Fenster **Eingabeaufforderung** die folgende Befehlszeile ein:  
  
     *ToolsPath* **VSPerfReport** *VSPFile* **/Summary:ETW [/Xml]**  
  
    |||  
    |-|-|  
    |*ToolsPath*|Der Pfad zum Hilfsprogramm für die Profilerstellungstools. Weitere Informationen finden Sie unter [Angeben des Pfads zu Tools für die Befehlszeile](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|  
    |*VSPFile*|Die Profilerstellungs-Datendatei (.vsp oder .vsps). Es werden vollständige und partielle Pfade angenommen.|  
    |Xml|Generiert einen in XML formatierten Bericht.|
