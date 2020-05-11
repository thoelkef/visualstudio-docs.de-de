---
title: Erste Schritte mit Python | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: 33f4f6fb-0ae4-4234-9df2-531f2d3af17f
caps.latest.revision: 13
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 97d60fe31f838c4cc497701f4560dc426ebc1cc9
ms.sourcegitcommit: 054815dc9821c3ea219ae6f31ebd9cd2dc8f6af5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/02/2020
ms.locfileid: "80543975"
---
# <a name="getting-started-with-python"></a>Erste Schritte mit Python
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Python-Tools für Visual Studio (PTVS) ist ein kostenloses [Open-Source-Plug-In](https://github.com/Microsoft/ptvs) für Visual Studio, das eine leistungsstarke Python-Entwicklungserfahrung bietet.  
  
## <a name="python-the-language"></a>Die Sprache Python.
  
Python ist eine beliebte Programmiersprache, die von vielen Universitäten, Wissenschaftlern, App-Skriptern, Gelegenheitsentwicklern und professionellen Entwicklern verwendet wird, die an Anwendungen, Websites und Cloud-Diensten arbeiten.

Als Programmiersprache ist Python:
  
- Zuverlässig.
- Im Allgemeinen nützlich für das Skripten von Schnellprogrammen, App-Skripting, Desktop-Apps, Webservern, Webdiensten und wissenschaftlichem Computing.
- Einfach zu erlernen und unterstützt dank seiner übersichtlichen Struktur eine saubere Programmierung (viele Universitäten wenden Python in Einführungskursen in die Programmierung an).
- Flexible, unterstützende Imperative, funktionale und objektorientierte Programmierstile.
- Kostenlos und Open Source.
- Läuft gut auf allen gängigen Betriebssystemen.  
- Unterstützt von vielen kostenlosen, nützlichen und gut gestalteten Bibliotheken.  
- Unterstützt durch viele Dokumentationen, Beispiele und eine starke Entwicklercommunity.  

Um mehr über die Sprache zu erfahren, beginnen Sie mit [Python for Beginners](https://www.python.org/about/gettingstarted/) on python.org.

Um Python selbst [https://www.python.org/download/](https://www.python.org/download/)zu installieren, besuchen Sie .

## <a name="python-tools-for-visual-studio"></a>Python Tools for Visual Studio
  
Die Python-Tools für Visual Studio, die Sie von [visualstudio.com](https://www.visualstudio.com/explore/python-vs)installieren können, bieten die folgenden Funktionen:  
  
- Unterstützung von mehreren Interpretern: verschiedene Versionen von CPython, IronPython und IPython  
- Ein Projektsystem, das implizit eine Ordnerstruktur aus Python-Code übernimmt und eine explizite Steuerung ermöglicht, sodass Sie App-Code, Testcode, Webseiten, JavaScript, Buildskripts usw. identifizieren können.  
- Projektvorlagen für Konsole, Internet, Azure, Data Science und andere Projekttypen.    
- Das Azure SDK für Python (siehe unten)    
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
- Installation und Features Demo (27 min)](https://www.youtube.com/watch?v=JNNAOypc6Ek)  
- [Dokumentation](https://github.com/Microsoft/PTVS/wiki)  

Beachten Sie, dass Visual Studio derzeit nicht die Möglichkeit bietet, eine eigenständige ausführbare Datei mit Python zu erstellen, was im Wesentlichen ein Programm mit einem eingebetteten Python-Interpreter bedeutet. Es gibt jedoch innerhalb der Python-Community verschiedene Arten, wie dies erreicht werden kann, wie unter [StackOverflow](https://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency) beschrieben wird. CPython unterstützt es auch, in eine native Anwendung eingebettet zu werden, wie im Blogbeitrag [Using CPython's Embeddable Zip File (Verwenden der eingebetteten ZIP-Datei von CPython)](https://devblogs.microsoft.com/python/cpython-embeddable-zip-file/) beschrieben wird.
  
## <a name="building-ui-with-python"></a>Erstellen der Benutzeroberfläche mit Python  

Das Hauptangebot zum Erstellen einer Benutzeroberfläche mit Python ist das [Qt-Projekt](https://www.qt.io/qt-for-application-development/), mit Bindungen für Python, bekannt als [PySide (die offizielle Bindung)](https://wiki.qt.io/PySide) (siehe auch [PySide-Downloads](https://download.qt.io/official_releases/pyside/.)) und [PyQt](https://wiki.python.org/moin/PyQt). Derzeit umfasst die Python-Unterstützung in Visual Studio keine bestimmten Tools für die Entwicklung von Benutzeroberflächen.

## <a name="azure-sdk-for-python"></a>Azure SDK für Python
  
Das Azure-SDK für Python, das Windows, Max und Linux unterstützt, vereinfacht die Nutzung und Verwaltung von Microsoft Azure-Diensten. Weitere Informationen finden Sie in den folgenden Ressourcen: 

- Verwenden Sie den [Python Package Index](https://pypi.python.org/pypi/azure) oder folgen Sie der Dokumentation [Python und SDK installieren](/azure/developer/python/azure-sdk-install), um das SDK zu installieren. 
- [Das Azure SDK für Python Developer Center](https://azure.microsoft.com/develop/python/) bietet umfassende Unterstützung durch Tutorials: von der Installation bis hin zur Dokumentation.  Hier einige Highlights:  
- Anleitungen:
  - [Speicher-Blob](https://azure.microsoft.com/develop/python/how-to-guides/blob-service/)  
  - [Speicherwarteschlange](https://azure.microsoft.com/develop/python/how-to-guides/queue-service/)  
  - [Aufbewahrungstabelle](https://azure.microsoft.com/develop/python/how-to-guides/table-service/)  
  - [Service Bus-Warteschlangen](https://azure.microsoft.com/develop/python/how-to-guides/service-bus-queues/)
  - [Service Bus Themen/Abonnements](https://azure.microsoft.com/develop/python/how-to-guides/service-bus-topics/) 
  - [Service-Management](https://azure.microsoft.com/develop/python/how-to-guides/service-management/)  

## <a name="scientific-computing"></a>Wissenschaftliche Berechnungen

Zusätzlich zu den Python-Bibliotheken für Datenwissenschaftler bietet das Python-Tool für Visual Studio Unterstützung für IPython und IPython Notebooks, die Sie in Azure hosten können.

Das Beschaffen von IPython und wissenschaftlichen Berechnungsbibliotheken (Matplotlib, Scipy, Numpy usw.) von [University of California, Irvine](https://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy-stack) wird empfohlen.  
  
## <a name="see-also"></a>Weitere Informationen  

[Erste Schritte mit PTVS: Einrichten von Visual Studio](../python/getting-started-with-ptvs-setting-up-visual-studio.md)
[Erste Schritte mit PTVS: Starten der Codierung (Projekte)](../python/getting-started-with-ptvs-start-coding-projects.md)
[Erste Schritte mit PTVS: Bearbeiten von Code-](../python/getting-started-with-ptvs-editing-code.md)
[Erste Schritte mit PTVS: Debuggen](../python/getting-started-with-ptvs-debugging.md)
[Der ersten Schritte mit PTVS: Interaktive Python](../python/getting-started-with-ptvs-interactive-python.md)
[erste Schritte mit PTVS: Erstellen einer Website in Azure](../python/getting-started-with-ptvs-building-a-website-in-azure.md)
