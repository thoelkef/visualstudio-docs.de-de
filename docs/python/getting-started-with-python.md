---
title: Erste Schritte mit Python in Visual Studio | Microsoft-Dokumentation
ms.custom: 
ms.date: 1/3/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33f4f6fb-0ae4-4234-9df2-531f2d3af17f
caps.latest.revision: 11
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 7d0b0b0b12b9d65f26b67d6f797abc0cf7a0c2c9
ms.openlocfilehash: e7cc978dabb401a8e9bab6791988aa737edb76b0
ms.lasthandoff: 02/22/2017

---
# <a name="getting-started-with-python-in-visual-studio"></a>Erste Schritte mit Python in Visual Studio

Python ([http://python.org/download/](http://python.org/download/)) ist eine beliebte Programmiersprache, die zuverlässig, flexibel, leicht zu erlernen und kostenlos ist und von einer starken Entwicklercommunity und vielen kostenlosen Bibliotheken unterstützt wird. Python funktioniert auf allen wichtigen Betriebssystemen und eignet sich für viele Zwecke, einschließlich Webanwendungen, Webdiensten, Desktopanwendungen, Skripts und wissenschaftliche Berechnungen. Deshalb wird Python von vielen Universitäten, Wissenschaftlern, gelegentlichen und professionellen Entwicklern gleichermaßen verwendet.

Für weitere Informationen zur Sprache beginnen Sie mit [Python for Beginners](https://www.python.org/about/gettingstarted/) (python.org).

## <a name="python-tools-for-visual-studio"></a>Python-Tools für Visual Studio

Das Python-Tool für Visual Studio (PTVS) ist eine kostenlose, Open Source-Erweiterung für Visual Studio, die eine leistungsfähige Python-Entwicklungsumgebung anbietet, einschließlich einem Projektsystem und Vorlagen, umfassende Bearbeitungsfunktionen und IntelliSense, voll funktionsfähiges Debuggen und eine Vielzahl von anderen Tools.

Die Erweiterung stellt die folgenden Funktionen bereit:

- Unterstützung von mehreren Interpretern: verschiedene Versionen von CPython, IronPython und IPython
- Ein Projektsystem, das implizit eine Ordnerstruktur des Python-Codes übernimmt, und auch eine explizite Steuerung ermöglicht, sodass Sie App-Code, Testcode, Webseiten, JavaScript, Buildskripts usw. identifizieren können.
- Projektvorlagen für Konsole, Internet, Azure, Data Science und andere Projekttypen.
- Umfangreiche Funktionen zur Bearbeitung und Kennzeichnung von Codes: Syntaxfarbgebung, automatischer Abschluss über den gesamten Code und allen Bibliotheken hinweg, Signaturhilfe, Klassenansicht, „Gehe zu Definition“, „Alle Verweise suchen“ und vieles mehr.
- Ein Interactive (REPL)-Fenster
- Umfassendes Debugging ohne ein Visual Studio-Projekt, die Möglichkeit zum Anfügen an vorhandene ausführbare Datei, Debugging im gemischten Modus, Remotedebugging für Windows/Linux/Mac und Debugging im Interactive-Fenster.

- IPhyton mit Datenvisualisierungen.
- Unterstützung für IronPython und .NET/WPF.
- Profilerstellungstools.
- Testtools.
- Das [Azure-SDK für Python](#azure-sdk-for-python)

Die folgenden Ressourcen helfen Ihnen beim Einstieg:

- [Python-Tools für Visual Studio installieren](https://www.visualstudio.com/vs/python/).
- [Installationshandbuch](https://github.com/Microsoft/PTVS/wiki/PTVS-Installation)
- [Videos: Einstieg und ausführliche Erläuterungen](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)
- Demo zu Installation und Funktionen (27 Min.)(https://www.youtube.com/watch?v=JNNAOypc6Ek)
- [Dokumentation](https://github.com/Microsoft/PTVS/wiki)
- [Quellcode](https://github.com/Microsoft/ptvs)


## <a name="azure-sdk-for-python"></a>Azure-SDK für Python

Das Azure-SDK für Python, das Windows, Max und Linux unterstützt, vereinfacht die Nutzung und Verwaltung von Microsoft Azure-Diensten. Weitere Informationen finden Sie in den folgenden Ressourcen:

- Verwenden Sie den [Python Package Index](https://pypi.python.org/pypi/azure) oder folgen Sie der Dokumentation [Python und SDK installieren](https://azure.microsoft.com/documentation/articles/python-how-to-install/), um das SDK zu installieren.
- [Das Azure SDK für Python Developer Center](http://azure.microsoft.com/en-us/develop/python/) bietet umfassende Unterstützung durch Tutorials: von der Installation bis hin zur Dokumentation.  Hier einige Highlights:
- Anleitungen:
  - [Speicher-Blob](http://azure.microsoft.com/en-us/develop/python/how-to-guides/blob-service/)
  - [Speicher-Warteschlange](http://azure.microsoft.com/en-us/develop/python/how-to-guides/queue-service/)
  - [Speichertabelle](http://azure.microsoft.com/en-us/develop/python/how-to-guides/table-service/)
  - [Servicebus-Warteschlangen](http://azure.microsoft.com/en-us/develop/python/how-to-guides/service-bus-queues/)   - [Servicebus-Themen/Abonnements](http://azure.microsoft.com/en-us/develop/python/how-to-guides/service-bus-topics/)
  - [Dienstverwaltung](http://azure.microsoft.com/en-us/develop/python/how-to-guides/service-management/)
- Die [SDK GitHub-Repository](https://github.com/Azure/azure-sdk-for-python) hat [Komponententests](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-mgmt/tests), die ebenfalls eine gute Informationsquelle für APIs darstellen.


## <a name="scientific-computing"></a>Wissenschaftliche Berechnungen
Zusätzlich zu den Python-Bibliotheken für Datenwissenschaftler bietet das Python-Tool für Visual Studio Unterstützung für IPython und IPython Notebooks, die Sie in Azure hosten können.

Das Beschaffen von IPython und wissenschaftlichen Berechnungsbibliotheken (Matplotlib, Scipy, Numpy usw.) von [University of California, Irvine](http://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy-stack) wird empfohlen.

## <a name="see-also"></a>Siehe auch
 [Erste Schritte mit PTVS: Einrichten von Visual Studio](../python/getting-started-with-ptvs-setting-up-visual-studio.md)
 [Erste Schritte mit PTVS: Programmieren beginnen (Projekte) ](../python/getting-started-with-ptvs-start-coding-projects.md)
 [Erste Schritte mit PTVS: Bearbeiten von Code](../python/getting-started-with-ptvs-editing-code.md)
 [Erste Schritte mit PTVS: Debuggen](../python/getting-started-with-ptvs-debugging.md)
 [Erste Schritte mit PTVS: Interaktives Python](../python/getting-started-with-ptvs-interactive-python.md)
 [Erste Schritte mit PTVS: Erstellen einer Website in Azure](../python/getting-started-with-ptvs-building-a-website-in-azure.md)
