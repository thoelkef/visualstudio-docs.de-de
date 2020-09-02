---
title: Sammeln ausführlicher Zeitsteuerungsdaten mithilfe der Instrumentierung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,instrumentation method
- instrumentation profiling method
ms.assetid: e9deb370-c459-45ac-84d3-14d646590d05
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c129ddf016e02fe6c29d5cf63fe57ba07fbd4e95
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68176646"
---
# <a name="collecting-detailed-timing-data-by-using-instrumentation"></a>Sammeln ausführlicher Zeitsteuerungsdaten mithilfe der Instrumentierung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bei der Instrumentationsmethode der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Profilerstellungstools wird Profilerstellungscode in eine Kopie eines Moduls eingefügt. Der Code zeichnet während der Profilerstellung jeden Funktionseinstieg, jedes Funktionsende und jeden Funktionsaufruf im Modul auf. Mithilfe der Instrumentationsmethode können ausführliche Zeitsteuerungsdaten zu einem Abschnitt des Codes erfasst werden. Zudem werden mit dieser Methode die Auswirkungen von Eingabe- und Ausgabeoperationen auf die Leistung der Anwendung besser verständlich.  
  
 Sie können die Instrumentationsmethode mit einem der folgenden Verfahren angeben:  
  
- Wählen Sie auf der ersten Seite des Profilerstellungs-Assistenten **Instrumentation**aus.  
  
- Klicken Sie auf der Symbolleiste **Leistungs-Explorer** in der Liste **Methode** auf **Instrumentation**.  
  
- Wählen Sie auf der Seite **Allgemein** im Dialogfeld „Eigenschaften“ für die Leistungssitzung **Instrumentation**aus.  
  
## <a name="common-tasks"></a>Allgemeine Aufgaben  
 Weitere Optionen können Sie im Dialogfeld _Leistungssitzung_**Eigenschaftenseiten** der Leistungssitzung angeben. So öffnen Sie dieses Dialogfeld  
  
- Klicken Sie im **Leistungs-Explorer**mit der rechten Maustaste auf den Namen der Leistungssitzung, und klicken Sie dann auf **Eigenschaften**.  
  
  Die Aufgaben in der folgenden Tabelle beschreiben Optionen, die Sie im Dialogfeld _Leistungssitzung_**Eigenschaftenseiten** angeben können, wenn Sie die Profilerstellung mit der Instrumentationsmethode ausführen.  
  
|Aufgabe|Verwandte Inhalte|  
|----------|---------------------|  
|Fügen Sie auf der Seite **Allgemein** Daten zur .NET-Speicherbelegung und Lebensdauer hinzu, und geben Sie Namensdetails für die generierte Profilerstellungs-Datendatei (VSP) an.|-   [Sammeln von Daten zur .NET-Speicherbelegung und Lebensdauer](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Vorgehensweise: Dateinamensoptionen für Profilerstellungsdaten](../profiling/how-to-set-performance-data-file-name-options.md)|  
|Wenn sich in der Projektmappe mehrere EXE-Projekte befinden, geben Sie auf der Seite **Starten** die zu startenden Anwendungen sowie die Startreihenfolge an.|-   [Gewusst wie: Angeben der zu Start-Binärdatei](../profiling/how-to-specify-the-binary-to-start.md)|  
|Geben Sie auf der Seite **Binärdateien** einen Speicherort für die instrumentierten Kopien der Module an. Standardmäßig werden die ursprünglichen Binärdateien in einen Sicherungsordner verschoben.|-   [Vorgehensweise: Verschieben instrumentierter Binärdateien](../profiling/how-to-relocate-instrumented-binaries.md)|  
|Fügen Sie der Profilerstellung auf der Seite **Ebeneninteraktion** ADO.NET-Aufrufdaten hinzu.|-   [Hinzufügen von Ebeneninteraktionsdaten über die Befehlszeile](../profiling/collecting-tier-interaction-data.md)|  
|Schließen Sie auf der Seite **Instrumentation** kleine Funktionen von der Profilerstellung aus, um den Profilerstellungsaufwand zu reduzieren, erstellen Sie für JavaScript-Code in ASP.NET-Webseiten ein Profil, und geben Sie Befehle an, die vor und nach der Instrumentation über eine Eingabeaufforderung ausgeführt werden sollen.|-   [Gewusst wie: ausschließen oder Einschließen kurzer Funktionen in die Instrumentierung](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)<br />-   [Gewusst wie: Profilerstellung für JavaScript-Code in Webseiten](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />-   [Gewusst wie: Angeben von Präinstrumentations-und Post Instrumentations Befehlen](../profiling/how-to-specify-pre-and-post-instrument-commands.md)|  
|Geben Sie auf der Seite **CPU-Indikatoren** einen oder mehrere Prozessorleistungsindikatoren an, die den Profilerstellungsdaten hinzugefügt werden sollen.|-   [Vorgehensweise: Sammeln von CPU-Zählers](../profiling/how-to-collect-cpu-counter-data.md)|  
|Wählen Sie auf der Seite **Windows-Ereignisse** ein oder mehrere ETW-Ereignisse (Ereignisse der Ereignisablaufverfolgung für Windows) aus, die mit den Samplingdaten erfasst werden sollen.|-   [Gewusst wie: Erfassen von Daten der Ereignis Ablauf Verfolgung für Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|  
|Geben Sie auf der Seite **Windows-Indikatoren** einen oder mehrere Betriebssystem-Leistungsindikatoren an, die den Profilerstellungsdaten als Markierungen hinzugefügt werden sollen.|-   [Gewusst wie: Sammeln von Windows-Counter-Daten](../profiling/how-to-collect-windows-counter-data.md)|  
|Geben Sie auf der Seite **Erweitert** zusätzliche Optionen an, die Sie an das VSInstr-Instrumentationsprogramm übergeben möchten, z. B. Optionen zum Ein- oder Ausschließen bestimmter Funktionen.|-   [Gewusst wie: Angeben zusätzlicher Instrumentierungs Optionen](../profiling/how-to-specify-additional-instrumentation-options.md)<br />-   [Gewusst wie: Beschränken der Instrumentierung auf bestimmte Funktionen](../profiling/how-to-limit-instrumentation-to-specific-functions.md)<br />-   [VSInstr](../profiling/vsinstr.md)|
