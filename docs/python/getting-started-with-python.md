---
title: "Erste Schritte mit Python | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-python"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 33f4f6fb-0ae4-4234-9df2-531f2d3af17f
caps.latest.revision: 11
caps.handback.revision: 10
author: "kraigb"
ms.author: "kraigb"
manager: "ghogen"
---
# Erste Schritte mit Python
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Microsoft stellt Python\-Tools für Visual Studio \(PTVS\), eine leistungsstarke Plug\-In\-Python\-IDE, kostenlos und als [Open\-Source\-Projekt](https://github.com/Microsoft/ptvs) bereit.  
  
## Die Sprache Python.  
 Python ist seit langem eine sehr beliebte Programmiersprache und wird von vielen Unternehmen, Wissenschaftlern, Hobby\- und Profiprogrammierern \(Apps, Cloud\-\/Webdienste und Websites\) sowie für das App\-Scripting verwendet.  Python weist eine Vielzahl positiver Eigenschaften auf:  
  
-   Zuverlässig  
  
-   Allgemeiner Einsatz zum schnellen Erstellen von Programmen, App\-Skripts, Desktopanwendungen, Webservern, Webdiensten und für wissenschaftliche Berechnungen  
  
-   Einfach zu erlernen, unterstützt dank seiner guten Struktur eine saubere Programmierung \(viele Universitäten nutzen die Sprache in Kursen zur Einführung in die Programmierung\)  
  
-   Unterstützt verschiedene Programmierstile: befehls\-, funktions\- und objektorientiert  
  
-   Kostenlos, Open Source, lässt sich problemlos auf allen wichtigen Betriebssystemen ausführen  
  
-   Viele kostenlose, hilfreiche und gut strukturierte Bibliotheken  
  
-   Vielzahl von Dokumentations\- und Hilfequellen sowie Beispielen im Internet  
  
 [Installieren von Python](http://python.org/download/)  
  
## PTVS  
 Microsoft stellt Python\-Tools für Visual Studio \(PTVS\), eine leistungsstarke Plug\-In\-Python\-IDE, kostenlos und als Open\-Source\-Projekt \([PTVS](http://pytools.codeplex.com/)\) bereit:  
  
 Einige Highlights von PTVS:  
  
-   Unterstützt mehrere Interpreter: verschiedene Versionen von CPython, IronPython und IPython  
  
-   Ein Projektsystem, das implizit eine Verzeichnisstruktur des Python\-Codes übernimmt, das Sie aber auch explizit steuern können, sodass App\-Code, Testcode, Webseiten, JavaScript, Buildskripts usw. klar voneinander abgegrenzt sind  
  
-   Projektvorlagen für Konsolenprogramme, Webprojekte, Azure\-Projekte, datenwissenschaftliche Projekte usw.  
  
-   Azure\-SDK für Python \(siehe unten\)  
  
-   Umfangreiche Funktionen zur Bearbeitung und Kennzeichnung von Code: Farbgebung, Abschluss über den gesamten Code und alle Bibliotheken hinweg, Signaturhilfe, Klassenansicht, "Gehe zu Definition", "Alle Verweise suchen", Umgestaltung usw.  
  
-   Interactive\-Fenster \(REPL\) und IPython mit Datenvisualisierungen  
  
-   Unterstützung für IronPython und .NET\/WPF  
  
-   Umfassendes Debugging ohne Projekt, Anfügen an vorhandene ausführbare Datei, Debugging im gemischten Modus, Remotedebugging für Windows\/Linux\/Mac und Debugging im Interactive\-Fenster  
  
-   Profilerstellungstools  
  
-   Testtools  
  
 [PTVS\-Homepage](https://www.visualstudio.com/en-us/explore/python-vs)  
  
 [Kurze Videos mit ersten Schritten und detaillierteren Informationen](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)  
  
 [Demo zu Installation und Funktionen \(27 Min.\)](https://www.youtube.com/watch?v=JNNAOypc6Ek)  
  
 [Wiki\-Dokumente](http://pytools.codeplex.com/documentation)  
  
 [Installieren von PTVS](http://pytools.codeplex.com/wikipage?title=PTVS%20Installation)  
  
## Azure  
 Das Azure\-SDK für Python vereinfacht die Nutzung und Verwaltung von Microsoft Azure\-Diensten.  Das Azure\-SDK für Python unterstützt Windows, Mac und Linux.  
  
 [Das Python Developer Center](http://azure.microsoft.com/en-us/develop/python/) bietet umfassende Unterstützung durch Lernprogramme – von der Installation bis hin zur Dokumentation.  Hier einige Highlights:  
  
-   [Speicherblob](http://azure.microsoft.com/en-us/develop/python/how-to-guides/blob-service/)  
  
-   [Speicherwarteschlange](http://azure.microsoft.com/en-us/develop/python/how-to-guides/queue-service/)  
  
-   [Speichertabelle](http://azure.microsoft.com/en-us/develop/python/how-to-guides/table-service/)  
  
-   [Service Bus\-Warteschlangen](http://azure.microsoft.com/en-us/develop/python/how-to-guides/service-bus-queues/)  
  
-   [Service Bus\-Themen\/\-Abonnements](http://azure.microsoft.com/en-us/develop/python/how-to-guides/service-bus-topics/)  
  
-   [Dienstverwaltung](http://azure.microsoft.com/en-us/develop/python/how-to-guides/service-management/)  
  
 [Das Azure\-SDK für Python\-Open\-Source\-Projekte](https://github.com/Azure/azure-sdk-for-python) bietet [Komponententests](https://github.com/Azure/azure-sdk-for-python/tree/master/tests), die auch eine gute Informationsquelle für APIs darstellen.  
  
 **Installation:** [Python\-Paketverzeichnis](https://pypi.python.org/pypi/azure) zur Verwendung von PIP. Weitere Informationen und [ausführbare Azure\-Installationsprogramme](http://azure.microsoft.com/en-us/documentation/articles/python-how-to-install/), die optional auch Python enthalten.  
  
## Wissenschaftliche Berechnungen  
 Zusätzlich zu den Python\-Bibliotheken für Datenwissenschaftler bietet PTVS Unterstützung für IPython und IPython Notebooks \(die Sie in Azure hosten können\).  Sie sollten Bibliotheken für IPython und wissenschaftliche Berechnungen \(matplotlib, scipy, numpy usw.\) aus einer Distribution \(nicht PyPi\) beziehen, beispielsweise von [UCI](http://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy-stack).  Vollständige Informationen zur Installation und Konfiguration von PTVS finden Sie unter [Installation und erste Schritte.](http://pytools.codeplex.com/wikipage?title=Using%20IPython%20with%20PTVS)  
  
## Siehe auch  
 [Erste Schritte mit PTVS: Einrichten von Visual Studio](../python/getting-started-with-ptvs-setting-up-visual-studio.md)   
 [Erste Schritte mit PTVS: Codieren beginnen \(Projekte\)](../python/getting-started-with-ptvs-start-coding-projects.md)   
 [Erste Schritte mit PTVS: Bearbeiten von Code](../python/getting-started-with-ptvs-editing-code.md)   
 [Erste Schritte mit PTVS: Debuggen](../python/getting-started-with-ptvs-debugging.md)   
 [Erste Schritte mit PTVS: Interaktives Python](../python/getting-started-with-ptvs-interactive-python.md)   
 [Erste Schritte mit PTVS: Erstellen einer Website in Azure](../python/getting-started-with-ptvs-building-a-website-in-azure.md)