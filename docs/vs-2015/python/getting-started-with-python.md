---
title: Erste Schritte mit Python | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: 33f4f6fb-0ae4-4234-9df2-531f2d3af17f
caps.latest.revision: 13
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 18e55aef8d95110dc44f20084eb5e45f643bf3cf
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54833942"
---
# <a name="getting-started-with-python"></a>Erste Schritte mit Python
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Python-Tools für Visual Studio (PTVS) ist eine kostenlose, [Open-Source-](https://github.com/Microsoft/ptvs) -Plug-In für Visual Studio, die eine leistungsfähige Python-Entwicklung.  
  
## <a name="python-the-language"></a>Die Sprache Python.
  
Python ist eine beliebte Programmiersprache, die von vielen Universitäten, Wissenschaftlern, app-Scripting, gelegentlichen und professionelle Entwickler, die an Anwendungen, Websites und Cloud-Dienste verwendet wird.

Ist als eine Programmiersprache Python:
  
- Zuverlässig
- In der Regel nützlich für die Skripterstellung schnellen Erstellen von Programmen, app-Skripts, desktop-apps, Webserver, Webdienste und wissenschaftliche Berechnungen.
- Einfach zu erlernen, unterstützt dank seiner guten Struktur eine saubere Programmierung (viele Universitäten nutzen die Sprache in Kursen zur Einführung in die Programmierung)
- Flexible, zwingend erforderlich, funktionale und objektorientierte Programmierung Formate unterstützen.
- Kostenlos und Open Source
- Lässt sich problemlos auf allen wichtigen Betriebssystemen.  
- Unterstützt viele kostenlose, hilfreiche und gut entworfene-Bibliotheken.  
- Unterstützt zahlreiche Dokumentation, Beispiele und einer starken Entwicklercommunity.  

Weitere Informationen zur Sprache beginnen Sie mit [Python for Beginners](https://www.python.org/about/gettingstarted/) auf python.org.

Um Python selbst zu installieren, besuchen Sie [ https://www.python.org/download/ ](https://www.python.org/download/).
 
  
## <a name="python-tools-for-visual-studio"></a>Python-Tools für Visual Studio
  
Die Python-Tools für Visual Studio, die Installation von [visualstudio.com](https://www.visualstudio.com/explore/python-vs), bieten die folgenden Features:  
  
- Unterstützung von mehreren Interpretern: verschiedene Versionen von CPython, IronPython und IPython  
- Ein Projektsystem, das implizit eine Ordnerstruktur des Python-Codes übernimmt, und auch eine explizite Steuerung ermöglicht, sodass Sie App-Code, Testcode, Webseiten, JavaScript, Buildskripts usw. identifizieren können.  
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
- Demo zu Installation und Funktionen (27 Min.)])https://www.youtube.com/watch?v=JNNAOypc6Ek)  
- [Dokumentation](https://github.com/Microsoft/PTVS/wiki)  


Beachten Sie, dass Visual Studio keine derzeit die Möglichkeit bietet, erstellen eine eigenständige ausführbare Datei, die mithilfe von Python, das im Wesentlichen ein Programm mit einem eingebetteten Python-Interpreter bedeutet. Es gibt jedoch innerhalb der Python-Community verschiedene Arten, wie dies erreicht werden kann, wie unter [StackOverflow](http://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency) beschrieben wird. CPython unterstützt es auch, in eine native Anwendung eingebettet zu werden, wie im Blogbeitrag [Using CPython's Embeddable Zip File (Verwenden der eingebetteten ZIP-Datei von CPython)](https://blogs.msdn.microsoft.com/pythonengineering/2016/04/26/cpython-embeddable-zip-file/) beschrieben wird.
  
## <a name="building-ui-with-python"></a>Erstellen von Benutzeroberflächen mit Python  

Die wichtigsten Angebot, für das Erstellen einer Benutzeroberflächenautomatisierungs mit Python ist die [Qt-Projekt](https://www.qt.io/qt-for-application-development/), mit Bindungen für Python [PySide (die offizielle Bindung)](http://wiki.qt.io/PySide) (Siehe auch [PySide-downloads](https://download.qt.io/official_releases/pyside/.)) und [PyQt](https://wiki.python.org/moin/PyQt). Derzeit umfasst die Python-Unterstützung in Visual Studio keine bestimmten Tools für die Entwicklung von Benutzeroberflächen.

## <a name="azure-sdk-for-python"></a>Azure-SDK für Python
  
Das Azure-SDK für Python, das Windows, Max und Linux unterstützt, vereinfacht die Nutzung und Verwaltung von Microsoft Azure-Diensten. Weitere Informationen finden Sie in den folgenden Ressourcen: 

- Verwenden Sie den [Python Package Index](https://pypi.python.org/pypi/azure) oder folgen Sie der Dokumentation [Python und SDK installieren](https://azure.microsoft.com/documentation/articles/python-how-to-install/), um das SDK zu installieren. 
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

Das Beschaffen von IPython und wissenschaftlichen Berechnungsbibliotheken (Matplotlib, Scipy, Numpy usw.) von [University of California, Irvine](http://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy-stack) wird empfohlen.  
  
## <a name="see-also"></a>Siehe auch  

[Erste Schritte mit PTVS: Einrichten von Visual Studio](../python/getting-started-with-ptvs-setting-up-visual-studio.md)
[erste Schritte mit PTVS: Codieren beginnen (Projekte)](../python/getting-started-with-ptvs-start-coding-projects.md)
[erste Schritte mit PTVS: Bearbeiten von Code](../python/getting-started-with-ptvs-editing-code.md)
[erste Schritte mit PTVS: Debuggen von](../python/getting-started-with-ptvs-debugging.md)
[erste Schritte mit PTVS: Interaktives Python](../python/getting-started-with-ptvs-interactive-python.md)
[erste Schritte mit PTVS: Erstellen einer Website in Azure](../python/getting-started-with-ptvs-building-a-website-in-azure.md)
