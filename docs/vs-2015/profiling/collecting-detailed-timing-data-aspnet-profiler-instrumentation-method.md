---
title: Sammeln ausführlicher Zeitsteuerungsdaten für eine ASP.NET-Webanwendung über die Befehlszeile mit der Profiler-Instrumentierungsmethode | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- profiling tools,instrumentation method
- instrumentation profiling method
ms.assetid: 29f2fc55-aaf7-4e18-a672-8815455fba73
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a1a6e53eb896a1e38033667620d07752294eb6a5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49255351"
---
# <a name="collecting-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line"></a>Sammeln ausführlicher Zeitsteuerungsdaten für eine ASP.NET-Webanwendung über die Befehlszeile mit der Profiler-Instrumentierungsmethode
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Abschnitt werden die Prozeduren und die Optionen zum Sammeln ausführlicher Leistungsdaten für eine [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Webanwendung unter Verwendung der Instrumentationsmethode und der Befehlszeile **VSPerfCmd** beschrieben.  
  
> [!NOTE]
>  Mit dem Tool **VSPerfCmd** stehen Ihnen sämtliche Funktionen der Profilerstellungstools zur Verfügung, beispielsweise Anhalten und Fortsetzen der Profilerstellung oder Sammeln zusätzlicher Daten aus Prozessor- und Windows-Leistungsindikatoren. Sie können auch das Befehlszeilentool **VSPerfASPNETCmd** verwenden, wenn Sie diese Funktionen nicht benötigen. Verglichen mit dem [VSPerfCmd](../profiling/vsperfcmd.md)-Befehlszeilentool stehen weniger Optionen zur Verfügung, es müssen keine Umgebungsvariablen festgelegt werden, und ein Neustart des Computers ist nicht erforderlich. Weitere Informationen finden Sie unter [Schnelle Website-Profilerstellung mit VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).  
  
## <a name="common-tasks"></a>Allgemeine Aufgaben  
  
|Aufgabe|Verwandter Inhalt|  
|----------|---------------------|  
|**Profile statically compiled binaries (Erstellen eines Profils für statisch kompilierte Binärdateien)**|-   [Vorgehensweise: Instrumentieren einer statisch kompilierten ASP.NET-Anwendung und Sammeln von ausführlichen Zeitsteuerungsdaten](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)|  
|**Profile dynamically compiled binaries (Erstellen eines Profils für dynamisch kompilierte Binärdateien)**|-   [Vorgehensweise: Instrumentieren einer dynamisch kompilierten ASP.NET-Anwendung und Sammeln von ausführlichen Zeitsteuerungsdaten](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)|  
  
## <a name="related-tasks"></a>Verwandte Aufgaben  
  
### <a name="profiling-aspnet-web-applications"></a>Profilerstellung für ASP.NET-Webanwendungen  
  
|Aufgabe|Verwandter Inhalt|  
|----------|---------------------|  
|**Profilerstellung mit der Samplingmethode**|-   [Sammeln von Anwendungsstatistiken durch Sampling](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**Profilerstellung der Speicherbelegung und Garbage Collection**|-   [Sammeln von Speicherdaten aus einer ASP.NET-Webanwendung über die Profiler-Befehlszeile](../profiling/collecting-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line.md)|  
|**Profilerstellung für Ressourcenkonflikte und Threadaktivität**|-   [Sammeln von Parallelitätsdaten](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
  
### <a name="profiling-by-using-the-instrumentation-method"></a>Profilerstellung mithilfe der Instrumentierungsmethode  
  
|Aufgabe|Verwandter Inhalt|  
|----------|---------------------|  
|**Profilerstellung für eigenständige (Client-)Anwendungen**|-   [Sammeln ausführlicher Zeitsteuerungsdaten mithilfe der Instrumentation](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application-by-using-the-profiler-command-line.md)|  
|**Profilerstellung für Dienste**|-   [Sammeln ausführlicher Zeitsteuerungsdaten mithilfe der Instrumentation](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method-from-the-profiler-command-line.md)|  
  
### <a name="analyzing-instrumentation-data-views-and-reports"></a>Analysieren von Instrumentationsdatenansichten und -berichten  
 [Datenansichten der Instrumentierungsmethode](../profiling/instrumentation-method-data-views.md)



