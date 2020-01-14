---
title: Einstieg in python | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: 33f4f6fb-0ae4-4234-9df2-531f2d3af17f
caps.latest.revision: 13
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 960511fcfb83dfc6ac3c58a806d8a23f1ff61597
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2020
ms.locfileid: "75918777"
---
# <a name="getting-started-with-python"></a>Erste Schritte mit Python
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der python Tools für Visual Studio (ptvs) ist ein kostenloses [Open-Source](https://github.com/Microsoft/ptvs) -Plug-in für Visual Studio, das eine leistungsstarke Python-Entwicklung bietet.  
  
## <a name="python-the-language"></a>Die Sprache Python.
  
Python ist eine beliebte Programmiersprache, die von vielen Universitäten, Wissenschaftlern, App-Scriptern, Gelegenheits Entwicklern und professionellen Entwicklern verwendet wird, die an Anwendungen, Websites und Clouddiensten arbeiten.

Die Programmiersprache Python ist:
  
- Zuverlässig.
- Im Allgemeinen nützlich für die Skripterstellung für schnelle Programme, App-Skripts, Desktop-Apps, Webserver, Webdienste und wissenschaftliche Berechnungen.
- Einfach zu erlernen und unterstützt dank seiner übersichtlichen Struktur eine saubere Programmierung (viele Universitäten wenden Python in Einführungskursen in die Programmierung an).
- Flexible, unterstützende imperative, funktionale und objektorientierte Programmier Stile.
- Kostenlos und Open Source.
- Funktioniert gut auf allen wichtigen Betriebssystemen.  
- Wird von vielen kostenlosen, nützlichen und gut entworfenen Bibliotheken unterstützt.  
- Wird von vielen Dokumentationen, Beispielen und einer starken Entwickler Community unterstützt.  

Wenn Sie mehr über die Sprache erfahren möchten, beginnen Sie mit [python für Einsteiger](https://www.python.org/about/gettingstarted/) auf Python.org.

Besuchen Sie [https://www.python.org/download/](https://www.python.org/download/), um python selbst zu installieren.

## <a name="python-tools-for-visual-studio"></a>Python Tools für Visual Studio
  
Die python Tools für Visual Studio, die Sie über [VisualStudio.com](https://www.visualstudio.com/explore/python-vs)installieren können, bieten die folgenden Features:  
  
- Unterstützung von mehreren Interpretern: verschiedene Versionen von CPython, IronPython und IPython  
- Ein Projektsystem, das implizit eine Ordnerstruktur aus Python-Code übernimmt und eine explizite Steuerung ermöglicht, sodass Sie App-Code, Testcode, Webseiten, JavaScript, Buildskripts usw. identifizieren können.  
- Projektvorlagen für Konsole, Internet, Azure, Data Science und andere Projekttypen.    
- Azure SDK für python (siehe unten)    
- Umfangreiche Funktionen zur Bearbeitung und Kennzeichnung von Codes: Syntaxfarbgebung, automatischer Abschluss über den gesamten Code und allen Bibliotheken hinweg, Signaturhilfe, Klassenansicht, „Gehe zu Definition“, „Alle Verweise suchen“ und vieles mehr.    
- Ein Interactive (REPL)-Fenster
- IPhyton mit Datenvisualisierungen.
- Unterstützung für IronPython und .NET/WPF.    
- Umfassendes Debugging ohne ein Visual Studio-Projekt, die Möglichkeit zum Anfügen an vorhandene ausführbare Datei, Debugging im gemischten Modus, Remotedebugging für Windows/Linux/Mac und Debugging im Interactive-Fenster.   
- Profilerstellungstools.  
- Testtools.  
  
Die folgenden Ressourcen helfen Ihnen beim Einstieg:

- [Installationshandbuch](https://github.com/Microsoft/PTVS/wiki/PTVS-Installation)    
- [Videos: Einstieg und ausführliche Erläuterungen](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)  
- Demo zu Installation und Funktionen (27 min.)] (https://www.youtube.com/watch?v=JNNAOypc6Ek)  
- [Dokumentation](https://github.com/Microsoft/PTVS/wiki)  

Beachten Sie, dass Visual Studio derzeit nicht die Möglichkeit bietet, eine eigenständige ausführbare Datei mithilfe von Python zu erstellen. Dies bedeutet im Wesentlichen ein Programm mit einem eingebetteten Python-Interpreter. Es gibt jedoch innerhalb der Python-Community verschiedene Arten, wie dies erreicht werden kann, wie unter [StackOverflow](https://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency) beschrieben wird. CPython unterstützt es auch, in eine native Anwendung eingebettet zu werden, wie im Blogbeitrag [Using CPython's Embeddable Zip File (Verwenden der eingebetteten ZIP-Datei von CPython)](https://devblogs.microsoft.com/python/cpython-embeddable-zip-file/) beschrieben wird.
  
## <a name="building-ui-with-python"></a>Aufbauen von Benutzeroberflächen mit python  

Das wichtigste Angebot zum Entwickeln einer Benutzeroberfläche mit Python ist [das Qt-Projekt](https://www.qt.io/qt-for-application-development/)mit Bindungen für python, [die als pyside (die offizielle Bindung)](https://wiki.qt.io/PySide) (siehe auch [pyside-Downloads](https://download.qt.io/official_releases/pyside/.)) und [pyqt](https://wiki.python.org/moin/PyQt)bezeichnet werden. Derzeit umfasst die Python-Unterstützung in Visual Studio keine bestimmten Tools für die Entwicklung von Benutzeroberflächen.

## <a name="azure-sdk-for-python"></a>Azure-SDK für Python
  
Das Azure-SDK für Python, das Windows, Max und Linux unterstützt, vereinfacht die Nutzung und Verwaltung von Microsoft Azure-Diensten. Weitere Informationen finden Sie in den folgenden Ressourcen: 

- Verwenden Sie den [Python Package Index](https://pypi.python.org/pypi/azure) oder folgen Sie der Dokumentation [Python und SDK installieren](/azure/python/python-sdk-azure-install), um das SDK zu installieren. 
- [Das Azure SDK für Python Developer Center](https://azure.microsoft.com/develop/python/) bietet umfassende Unterstützung durch Tutorials: von der Installation bis hin zur Dokumentation.  Hier einige Highlights:  
- Anleitungen:
  - [Speicher-Blob](https://azure.microsoft.com/develop/python/how-to-guides/blob-service/)  
  - [Speicher-Warteschlange](https://azure.microsoft.com/develop/python/how-to-guides/queue-service/)  
  - [Speichertabelle](https://azure.microsoft.com/develop/python/how-to-guides/table-service/)  
  - [Service Bus-Warteschlangen](https://azure.microsoft.com/develop/python/how-to-guides/service-bus-queues/)
  - [Service Bus-Themen/-Abonnements](https://azure.microsoft.com/develop/python/how-to-guides/service-bus-topics/) 
  - [Dienstverwaltung](https://azure.microsoft.com/develop/python/how-to-guides/service-management/)  

## <a name="scientific-computing"></a>Wissenschaftliche Berechnungen

Zusätzlich zu den Python-Bibliotheken für Datenwissenschaftler bietet das Python-Tool für Visual Studio Unterstützung für IPython und IPython Notebooks, die Sie in Azure hosten können.

Das Beschaffen von IPython und wissenschaftlichen Berechnungsbibliotheken (Matplotlib, Scipy, Numpy usw.) von [University of California, Irvine](https://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy-stack) wird empfohlen.  
  
## <a name="see-also"></a>Siehe auch  

[Erste Schritte mit PTVS: Einrichten von Visual Studio](../python/getting-started-with-ptvs-setting-up-visual-studio.md)
[Erste Schritte mit PTVS: Programmieren beginnen (Projekte) ](../python/getting-started-with-ptvs-start-coding-projects.md)
[Erste Schritte mit PTVS: Bearbeiten von Code](../python/getting-started-with-ptvs-editing-code.md)
[Erste Schritte mit PTVS: Debuggen](../python/getting-started-with-ptvs-debugging.md)
[Erste Schritte mit PTVS: Interaktives Python](../python/getting-started-with-ptvs-interactive-python.md)
[Erste Schritte mit PTVS: Erstellen einer Website in Azure](../python/getting-started-with-ptvs-building-a-website-in-azure.md)
