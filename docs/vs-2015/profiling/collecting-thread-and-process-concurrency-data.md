---
title: Sammeln von Parallelitätsdaten zu Threads und Prozessen | Microsoft-Dokumentation
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
- concurrency profiling method
- Profiling Tools, concurrency method
ms.assetid: fa03d381-a9ee-408c-876d-05111e29225b
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fd63966dba73d57d12d68552e57828b9d17ee84e
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/05/2018
ms.locfileid: "47590705"
---
# <a name="collecting-thread-and-process-concurrency-data"></a>Sammeln von Parallelitätsdaten zu Threads und Prozessen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Collecting Thread and Process Concurrency Data](https://docs.microsoft.com/visualstudio/profiling/collecting-thread-and-process-concurrency-data).  
  
Mit der Parallelitätsmethode zur Profilerstellung der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Profilerstellungswerkzeuge können Sie Ressourcenkonfliktdaten sammeln, die Informationen zu jedem Synchronisierungsereignis enthalten, das dazu führt, dass eine Funktion in der mit einem Profil versehenen Anwendung auf den Zugriff auf eine Ressource warten muss.  
  
 **Anforderungen**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
 Sie können die Parallelitätsmethode zur Profilerstellung mit einem der folgenden Verfahren angeben:  
  
-   Klicken Sie auf der ersten Seite des Profilerstellungs-Assistenten auf **Parallelität**.  
  
-   Klicken Sie auf der Seite **Allgemein** im Dialogfeld „Eigenschaften“ für die Leistungssitzung auf **Instrumentation**.  
  
-   Klicken Sie auf der Symbolleiste **Leistungs-Explorer** in der Liste **Methode** auf **Parallelität**.  
  
## <a name="common-tasks"></a>Allgemeine Aufgaben  
 Weitere Optionen können Sie im Dialogfeld _Leistungssitzung_**Eigenschaftenseiten** der Leistungssitzung angeben. So öffnen Sie dieses Dialogfeld  
  
-   Klicken Sie im **Leistungs-Explorer**mit der rechten Maustaste auf den Namen der Leistungssitzung, und klicken Sie dann auf **Eigenschaften**.  
  
 Die Aufgaben in der folgenden Tabelle beschreiben Optionen, die Sie im Dialogfeld _Leistungssitzung_**Eigenschaftenseiten** angeben können, wenn Sie die Profilerstellung mit der Parallelitätsmethode ausführen.  
  
|Aufgabe|Verwandter Inhalt|  
|----------|---------------------|  
|Geben Sie auf der Seite **Allgemein** Namensdetails für die generierte Profilerstellungs-Datendatei (VSP) an.|-   [How to: Set Performance Data File Name Option (Vorgehensweise: Festlegen von Dateinamenoptionen für Profilerstellungsdaten)](../profiling/how-to-set-performance-data-file-name-options.md)|  
|Wenn sich in Ihrer Codelösung mehrere EXE-Projekte befinden, geben Sie auf der Seite **Starten** die zu startende Anwendung an.|-   [Vorgehensweise: Angeben der zu startenden Binärdatei](../profiling/how-to-specify-the-binary-to-start.md)|  
|Fügen Sie der Profilerstellung auf der Seite **Ebeneninteraktion** ADO.NET-Aufrufdaten hinzu.|-   [Hinzufügen von Ebeneninteraktionsdaten über die Befehlszeile](../profiling/collecting-tier-interaction-data.md)|  
|Geben Sie auf der Seite **Windows-Indikatoren** einen oder mehrere Betriebssystem-Leistungsindikatoren an, die den Profilerstellungsdaten als Markierungen hinzugefügt werden sollen.|-   [Vorgehensweise: Sammeln von Windows-Indikatordaten](../profiling/how-to-collect-windows-counter-data.md)|  
|Geben Sie auf der Seite **Erweitert** die Version der .NET Framework-Laufzeit für die Profilerstellung an, wenn Ihre Anwendungsmodule mehrere Versionen verwenden. Standardmäßig wird die zuerst geladene Version für die Profilerstellung verwendet.|-   [Vorgehensweise: Angeben der .NET Framework-Laufzeit](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|



