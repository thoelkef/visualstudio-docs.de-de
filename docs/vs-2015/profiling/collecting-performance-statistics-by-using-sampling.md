---
title: Sammeln von Leistungsstatistiken durch Sampling | Microsoft-Dokumentation
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
- Profiling Tools,sampling
- sampling profiling method
ms.assetid: 8e36361b-bb3d-40c6-b286-0e68c0ecb915
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3a6ed7ba926869359db9c9602f316cb0fc3934d7
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/05/2018
ms.locfileid: "47590662"
---
# <a name="collecting-performance-statistics-by-using-sampling"></a>Sammeln von Leistungsstatistiken durch Sampling
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Sammeln von Leistungsstatistiken durch Sampling](https://docs.microsoft.com/visualstudio/profiling/collecting-performance-statistics-by-using-sampling).  
  
Standardmäßig werden mit der Samplingmethode der [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)]-Profilerstellungstools nach jeweils 10.000.000 Prozessorzyklen Profilerstellungsinformationen gesammelt (etwa jede Hundertstelsekunde auf einem 1-GHz-Computer). Die Samplingmethode ist nützlich für das Auffinden von Prozessornutzungsproblemen und ist die vorgeschlagene Methode zum Starten der meisten Leistungsuntersuchungen.  
  
 **Anforderungen**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
> [!NOTE]
>  Verbesserte Sicherheitsfunktionen in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio-Profilers auf diesen Plattformen. Außerdem benötigen Windows Store-Apps neue Erfassungsmethoden. Siehe [Profilerstellung für Windows 8- und Windows Server 2012-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 Zum Angeben der Samplingmethode haben Sie folgende Möglichkeiten:  
  
-   Klicken Sie auf der ersten Seite des Profilerstellungs-Assistenten auf **CPU-Sampling (empfohlen)**.  
  
-   Klicken Sie in der Symbolleiste **Leistungs-Explorer** in der Liste **Methode** auf **Sampling**.  
  
-   Klicken Sie im Eigenschaftendialogfeld der Leistungssitzung auf der Seite **Allgemein** auf **Sampling**.  
  
## <a name="common-tasks"></a>Allgemeine Aufgaben  
 Weitere Optionen können Sie im Dialogfeld _Leistungssitzung_**Eigenschaftenseiten** der Leistungssitzung angeben. So öffnen Sie dieses Dialogfeld  
  
-   Klicken Sie im **Leistungs-Explorer**mit der rechten Maustaste auf den Namen der Leistungssitzung, und klicken Sie dann auf **Eigenschaften**.  
  
 Die Aufgaben in der folgenden Tabelle beschreiben Optionen, die Sie im Dialogfeld _Leistungssitzung_**Eigenschaftenseiten** angeben können, wenn Sie ein Profil mithilfe der Samplingmethode erstellen.  
  
|Aufgabe|Verwandter Inhalt|  
|----------|---------------------|  
|Fügen Sie auf der Seite **Allgemein** gesammelte Daten zur .NET-Speicherbelegung und Lebensdauer hinzu, und geben Sie Namensdetails für die generierte Profilerstellungs-Datendatei (VSP) an.|-   [Sammeln von Daten zur .NET-Speicherbelegung und Lebensdauer](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [How to: Set Performance Data File Name Option (Vorgehensweise: Festlegen von Dateinamenoptionen für Profilerstellungsdaten)](../profiling/how-to-set-performance-data-file-name-options.md)|  
|Ändern Sie auf der Seite **Sampling** die Samplingrate, ändern Sie das Samplingereignis von Prozessortaktzyklen in einen anderen Prozessorleistungsindikator, oder ändern Sie beide Werte.|-   [Vorgehensweise: Auswählen von Samplingereignissen](../profiling/how-to-choose-sampling-events.md)|  
|Wenn sich in der Codeprojektmappe mehrere EXE-Projekte befinden, geben Sie auf der Seite **Starten** die zu startenden Anwendungen sowie die Startreihenfolge an.|-   [Hinzufügen von Ebeneninteraktionsdaten über die Befehlszeile](../profiling/collecting-tier-interaction-data.md)|  
|Fügen Sie auf der Seite **Ebeneninteraktionen** ADO.NET-Aufrufinformationen zu den Daten hinzu, die während der Profilerstellung gesammelt wurden.|-   [Erfassen von Ebeneninteraktionsdaten](../profiling/collecting-tier-interaction-data.md)|  
|Geben Sie auf der Seite **Windows-Ereignisse** ein oder mehrere ETW-Ereignisse (Ereignisse der Ereignisablaufverfolgung für Windows) an, die mit den Samplingdaten erfasst werden sollen.|-   [Vorgehensweise: Sammeln von Daten der Ereignisablaufverfolgung für Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|  
|Geben Sie auf der Seite **Windows-Indikatoren** einen oder mehrere Betriebssystem-Leistungsindikatoren an, die den Profilerstellungsdaten als Markierungen hinzugefügt werden sollen.|-   [Vorgehensweise: Sammeln von Windows-Indikatordaten](../profiling/how-to-collect-windows-counter-data.md)|  
|Geben Sie auf der Seite **Erweitert** die Version der .NET Framework-Laufzeit für die Profilerstellung an, wenn die Anwendungsmodule mehrere Versionen verwenden. Standardmäßig wird die zuerst geladene Version für die Profilerstellung verwendet.|-   [Vorgehensweise: Angeben der .NET Framework-Laufzeit](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|



