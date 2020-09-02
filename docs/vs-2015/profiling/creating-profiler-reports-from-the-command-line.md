---
title: Erstellen von Profiler-Berichten über die Befehlszeile | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: c886f8af-2014-4fec-9b24-d98b68ecafb7
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 489ebd4e5aff3ef9b93ef0d8fe18f9ae8cc85011
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62537201"
---
# <a name="creating-profiler-reports-from-the-command-line"></a>Erstellen von Profiler-Berichten über die Befehlszeile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Das **VSPerfReport** -Befehlszeilen Tool ermöglicht Ihnen das Erstellen von XML-oder CSV-Berichten (durch Trennzeichen getrennte Werte) aus Profil Erstellungs Daten (VSP-Dateien). VSPerfReport-Berichtstypen entsprechen in den tabellenbasierten Ansichten der Schnittstelle für [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Sie können den Bericht filtern, sodass nur Ihr Code und nur ein Teil der Profilerstellungs-Datendatei angezeigt wird. Weitere Informationen finden Sie unter [VSPerfReport](../profiling/vsperfreport.md).  
  
 Sie können die Freigabe der Profilerstellungs-Datendateien auch vereinfachen, indem Sie Symbole in die VSP-Dateien einbetten und bereits voranalysierte Berichtdateien (.vsps) erstellen, die kleiner sind und sich schneller öffnen lassen.  
  
## <a name="common-tasks"></a>Allgemeine Aufgaben  
  
|Aufgabe|Verwandte Inhalte|  
|----------|---------------------|  
|**Erstellen eines einfachen Berichts:** Erstellen Sie alle oder eine Teilmenge der VSPerfReport-Berichtstypen.|-   [Erstellen von grundlegenden Berichten](../profiling/creating-basic-profiling-reports-from-the-command-line.md)|  
|**Vergleichen von zwei Profilerstellungs-Datendateien:** Erstellen Sie einen Vergleichsbericht, in dem die Leistungsdaten in zwei Profilerstellungs-Datendateien verglichen werden.|-   [Vorgehensweise: Erstellen eines Profiler-Vergleichs Berichts über eine Eingabeaufforderung](../profiling/how-to-create-a-profiler-comparison-report-from-a-command-prompt.md)|  
|**Anzeigen von Daten über Aufrufablaufverfolgung und Ereignisablaufverfolgung für Windows (ETW):** Erstellen Sie einen Aufrufablaufverfolgungsbericht, in dem Zeitsteuerungsinformationen für jeden Einstiegs- und Endpunkt der Funktionen Ihrer Anwendung sowie jeder Aufruf anderer Funktionen durch die Funktion aufgeführt sind. Sie können auch eine ausführliche Auflistung aller ETW-Ereignisse erstellen, die bei einer Profilerstellungsausführung erfasst wurden.|-   [Vorgehensweise: Erstellen eines aufrufsablauf Verfolgungs Berichts](../profiling/how-to-create-a-profiling-tools-call-trace-report.md)|  
|**Filtern eines Berichts:** Filtern Sie einen Bericht auf nur die Funktionen im Code oder auf eine Zeit in der Profilerstellungs-Datendatei.|-   [Gewusst wie: Filtern von Berichten über die Befehlszeile](../profiling/how-to-filter-reports-from-the-command-line.md)|  
|**Erstellen portierbarer Profilerstellungs-Datendateien:** Um die Freigabe von Profilerstellungsdaten zu vereinfachen, können Sie die Symbole für eine Profilerstellungsausführung in die VSP-Datei einbetten. Sie können auch eine bereits analysierte Profilerstellungs-Datendatei (.vsps) erstellen, die kleiner ist und sich schneller öffnen lässt.|-   [Erstellen portabler Profil Erstellungs Datendateien](../profiling/creating-portable-profiling-data-files-from-the-command-line.md)|
