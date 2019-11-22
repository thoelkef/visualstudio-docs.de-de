---
title: Getting Started with Python | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: 33f4f6fb-0ae4-4234-9df2-531f2d3af17f
caps.latest.revision: 13
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 21e724e585f2a5bf0e1fe2a6b70f89c1bd5f5eec
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298196"
---
# <a name="getting-started-with-python"></a>Erste Schritte mit Python
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

The Python Tools for Visual Studio (PTVS), is a free, [open-source](https://github.com/Microsoft/ptvs) plug-in for Visual Studio that a powerful Python development experience.  
  
## <a name="python-the-language"></a>Die Sprache Python.
  
Python is a popular programming language that is used by many universities, scientists, app scripters, casual developers, and professional developers, working on applications, web sites, and cloud services.

As a programming language, Python is:
  
- Zuverlässig.
- Generally useful for scripting quick programs, app scripting, desktop apps, web servers, web services, and scientific computing.
- Einfach zu erlernen und unterstützt dank seiner übersichtlichen Struktur eine saubere Programmierung (viele Universitäten wenden Python in Einführungskursen in die Programmierung an).
- Flexible, supporting imperative, functional, and object-oriented programming styles.
- Kostenlos und Open Source.
- Runs well on all major operating systems.  
- Supported by many free, useful, and well-designed libraries.  
- Supported by lots of documentation, samples, and a strong developer community.  

To learn more about the language, start with [Python for Beginners](https://www.python.org/about/gettingstarted/) on python.org.

To install Python itself, visit [https://www.python.org/download/](https://www.python.org/download/).

## <a name="python-tools-for-visual-studio"></a>Python-Tools für Visual Studio
  
The Python Tools for Visual Studio, which you can install from [visualstudio.com](https://www.visualstudio.com/explore/python-vs), provide the following features:  
  
- Unterstützung von mehreren Interpretern: verschiedene Versionen von CPython, IronPython und IPython  
- Ein Projektsystem, das implizit eine Ordnerstruktur aus Python-Code übernimmt und eine explizite Steuerung ermöglicht, sodass Sie App-Code, Testcode, Webseiten, JavaScript, Buildskripts usw. identifizieren können.  
- Projektvorlagen für Konsole, Internet, Azure, Data Science und andere Projekttypen.    
- The Azure SDK for Python (see below)    
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
- Installation and features demo (27 min)](https://www.youtube.com/watch?v=JNNAOypc6Ek)  
- [Dokumentation](https://github.com/Microsoft/PTVS/wiki)  

Note that Visual Studio does not at present provide the means to create a stand-alone executable using Python, which essentially means a program with an embedded Python interpreter. Es gibt jedoch innerhalb der Python-Community verschiedene Arten, wie dies erreicht werden kann, wie unter [StackOverflow](https://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency) beschrieben wird. CPython unterstützt es auch, in eine native Anwendung eingebettet zu werden, wie im Blogbeitrag [Using CPython's Embeddable Zip File (Verwenden der eingebetteten ZIP-Datei von CPython)](https://devblogs.microsoft.com/python/cpython-embeddable-zip-file/) beschrieben wird.
  
## <a name="building-ui-with-python"></a>Building UI with Python  

The main offering for building a UI with Python is the [Qt Project](https://www.qt.io/qt-for-application-development/), with bindings for Python known as [PySide (the official binding)](https://wiki.qt.io/PySide) (also see [PySide downloads](https://download.qt.io/official_releases/pyside/.))and [PyQt](https://wiki.python.org/moin/PyQt). Derzeit umfasst die Python-Unterstützung in Visual Studio keine bestimmten Tools für die Entwicklung von Benutzeroberflächen.

## <a name="azure-sdk-for-python"></a>Azure-SDK für Python
  
Das Azure-SDK für Python, das Windows, Max und Linux unterstützt, vereinfacht die Nutzung und Verwaltung von Microsoft Azure-Diensten. Weitere Informationen finden Sie in den folgenden Ressourcen: 

- Verwenden Sie den [Python Package Index](https://pypi.python.org/pypi/azure) oder folgen Sie der Dokumentation [Python und SDK installieren](https://docs.microsoft.com/azure/python/python-sdk-azure-install), um das SDK zu installieren. 
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
