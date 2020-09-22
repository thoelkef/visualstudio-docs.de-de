---
title: Profilerstellung für Dienste über die Befehlszeile | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling toos,services
- profiling services
ms.assetid: f0d62318-b0e8-49c6-9a30-9f7a6adef2f6
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 64cd62c29df9a7c43d690119194582b20a784c3c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841078"
---
# <a name="command-line-profiling-of-services"></a>Profilerstellung für Dienste über die Befehlszeile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Abschnitt werden die Prozeduren und Optionen zum Sammeln von Leistungsdaten für Windows-Dienste mithilfe der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Profilerstellungstools über die Befehlszeile beschrieben.  
  
> [!NOTE]
> Verbesserte Sicherheitsfeatures in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio-Profilers auf diesen Plattformen. Außerdem benötigen Windows Store-Apps neue Erfassungsmethoden. Siehe [Profilerstellungstools für Windows 8- und Windows Server 2012-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="common-tasks"></a>Allgemeine Aufgaben  
  
|Aufgabe|Verwandte Inhalte|  
|----------|---------------------|  
|**Sammeln von Anwendungsstatistikdaten:** Sammeln Sie Leistungsstatistikdaten mit der Samplingmethode. Datensampling ist beim Analysieren von CPU-Auslastungsproblemen und zum Verständnis der allgemeinen Leistungsmerkmale einer Anwendung hilfreich.|-   [Sammeln von Anwendungs Statistiken mithilfe von Sampling](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|  
|**Sammeln ausführlicher Zeitsteuerungsdaten:** Sammeln Sie ausführliche Zeitsteuerungsinformationen mit der Instrumentationsmethode. Instrumentationsdaten sind beim Analysieren von EA-Problemen und für die detaillierte Analyse von Anwendungsszenarios hilfreich.|-   [Sammeln ausführlicher Zeit Steuerungsdaten mithilfe der Instrumentierung](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method-from-the-profiler-command-line.md)|  
|**Sammeln von .NET-Arbeitsspeicherdaten:** Sammeln Sie mit Sampling oder Instrumentation Daten zur .NET-Speicherbelegung, die Auskunft über die Größe und Anzahl zugeordneter Objekte geben. Sie können auch Objektlebensdauerdaten sammeln, die die Größe und Anzahl von Objekten angeben, die in jeder Garbage Collection-Generation freigegeben werden.|-   [Sammeln von .NET-Arbeitsspeicherdaten](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|  
|**Sammeln von Parallelitätsdaten:** Sammeln Sie mit der Parallelitätsmethode Ressourcenkonfliktdaten und Threadaktivitätsdaten, die Auskunft über CPU-Auslastung, Threadkonflikte, Threadmigration, Synchronisierungsverzögerungen, überlappende EA-Bereiche und andere Systemereignisse geben.|-   [Sammeln von Parallelitätsdaten](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|  
|**Hinzufügen von Ebeneninteraktionsdaten:** Sie können Leistungsdaten zu synchronen ADO.NET-Aufrufen des Diensts hinzufügen, die an eine Microsoft [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Datenbank erfolgt sind.|-   [Hinzufügen von Ebeneninteraktionsdaten über die Befehlszeile](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Aufgabe|Verwandte Inhalte|  
|----------|---------------------|  
|**Profilerstellung für eigenständige (Client-)Anwendungen**|-   [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)|  
|**Profilerstellung für ASP.NET-Anwendungen**|-   [Profilerstellung ASP.NET Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)|
