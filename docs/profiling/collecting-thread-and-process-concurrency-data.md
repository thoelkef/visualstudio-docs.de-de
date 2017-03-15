---
title: "Sammeln von Parallelit&#228;tsdaten zu Threads und Prozessen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Parallelitätsmethode zur Profilerstellung"
  - "Profilerstellungstools, Parallelitätsmethode"
ms.assetid: fa03d381-a9ee-408c-876d-05111e29225b
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Sammeln von Parallelit&#228;tsdaten zu Threads und Prozessen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profilerstellungstoolnebenläufigkeits\-Profilerstellungsmethode können Sie, um Ressourcenkonfliktdaten zu sammeln, die Informationen über jedes Synchronisierungsereignis enthält, das eine Funktion in der Anwendung mit Profil, auf Zugriff auf eine Ressource warten muss.  
  
 **Voraussetzungen**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 Zum Angeben der Parallelitätsmethode zur Profilerstellung haben Sie folgende Möglichkeiten:  
  
-   Auf der ersten Seite des Profilerstellungs\-Assistenten, klicken Sie auf **Nebenläufigkeit**  
  
-   Auf der Seite **Allgemein** des Eigenschaftendialogfelds für die Leistungssitzung, klicken Sie auf **Nebenläufigkeit**.  
  
-   Klicken Sie in der Symbolleiste **Leistungs\-Explorer** in der Liste **Methode** auf **Parallelität**.  
  
## Allgemeine Aufgaben  
 Sie können Optionen im Dialogfeld *Performance Session***Eigenschaftenseiten** der Leistungssitzung angeben.  So öffnen Sie dieses Dialogfeld  
  
-   Klicken Sie im **Leistungs\-Explorer** mit der rechten Maustaste auf den Namen der Leistungssitzung, und klicken Sie dann auf **Eigenschaften**.  
  
 Die Aufgaben in der folgenden Tabelle beschreiben Optionen, die Sie im Dialogfeld *Performance Session***Eigenschaftenseiten** angeben können, wenn Sie ein Profil erstellen, indem Sie die Parallelitätsmethode.  
  
|Aufgabe|Verwandter Inhalt|  
|-------------|-----------------------|  
|Geben Sie auf der Seite **Allgemein** Namensdetails für die generierte Profilerstellungs\-Datendatei \(.vsp\) an.|-   [Gewusst wie: Dateinamenoptionen für Profilerstellungsdaten](../profiling/how-to-set-performance-data-file-name-options.md)|  
|Geben Sie auf der Seite **Starten** die Anwendung an, die gestartet werden soll, wenn mehrere EXE\-Projekte in der Codeprojektmappe vorhanden sind.|-   [Gewusst wie: Angeben der zu startenden Binärdatei](../profiling/how-to-specify-the-binary-to-start.md)|  
|Fügen Sie der Profilerstellung auf der Seite **Ebeneninteraktionen** ADO.NET\-Aufrufdaten hinzu.|-   [Erfassen von Ebeneninteraktionsdaten](../profiling/collecting-tier-interaction-data.md)|  
|Geben Sie auf der Seite **Windows\-Indikatoren** einen oder mehrere Betriebssystem\-Leistungsindikatoren an, die den Profilerstellungsdaten als Markierungen hinzugefügt werden sollen.|-   [Gewusst wie: Sammeln von Windows\-Indikatordaten](../profiling/how-to-collect-windows-counter-data.md)|  
|Geben Sie auf der Seite **Erweitert** die Version der .NET Framework\-Laufzeit für die Profilerstellung an, wenn die Anwendungsmodule mehrere Versionen verwenden.  Standardmäßig wird die zuerst geladene Version für die Profilerstellung verwendet.|-   [Gewusst wie: Angeben der .NET Framework\-Laufzeit für die Profilerstellung in parallelen Szenarios](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|