---
title: Workload von Data Science und analytischen Anwendungen
description: Die Visual Studio-Workload kombiniert Python, R, F# und die entsprechenden Laufzeitverteilungen einschließlich Anaconda miteinander.
ms.date: 01/24/2018
ms.prod: visual-studio-dev15
ms.topic: overview
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- python
- data-science
ms.openlocfilehash: c7ef2fb2e9d438fb4129d6835cd88663d3025e64
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55004694"
---
# <a name="install-data-science-support-in-visual-studio"></a>Installieren von Data Science-Unterstützung in Visual Studio

Die Workload für Data Science und analytische Anwendungen, die Sie über den Visual Studio-Installer auswählen und installieren, kombiniert drei Sprachen und deren jeweilige Runtimeverteilungen:

- [R und Microsoft R Client](../rtvs/index.md)
- [Python und Anaconda](../python/overview-of-python-tools-for-visual-studio.md)
- [F# mit .NET Framework](/dotnet/fsharp/)

![Workload von Data Science und analytischen Anwendungen im Visual Studio-Installer](media/data-science-workload.png)

R und Python sind zwei der primär für Data Science verwendeten Skriptsprachen. Beide Sprachen sind einfach zu erlernen und werden durch eine große Vielfalt an Paketen unterstützt. Solche Pakete existieren für eine Vielzahl an Verwendungsszenarios, z.B. Datenerfassung, Bereinigung, Modelltraining, Bereitstellung und Zeichnen. F# ist auch eine leistungsfähige, funktionsorientierte .NET-Sprache, die für eine Vielzahl an Datenverarbeitungsaufgaben geeignet ist.

<!--Note link on the image because this one is large -->
[![Screenshots von Visual Studio mit R, Python und F#](media/data-science-workload-screens.png)](media/data-science-workload-screens.png#lightbox)

## <a name="workload-options"></a>Workloadoptionen

Durch die Workload werden standardmäßig folgende Optionen installiert, die Sie im Visual Studio-Installer unter dem Abschnitt für die Workload „Zusammenfassung“ ändern können:

- F#-Sprachunterstützung
- Python:
  - Unterstützung der Sprache Python
  - [64-Bit-Anaconda3](https://www.continuum.io) (eine Python-Distribution, die umfangreiche Data Science-Bibliotheken sowie einen Python-Interpreter enthält)
  - Webunterstützung für Python
  - Unterstützung von Cookiecutter-Vorlagen
- R:
  - Unterstützung der Sprache R
  - Laufzeitunterstützung für R-Entwicklungstools
  - [Microsoft R Client](/machine-learning-server/r-client/what-is-microsoft-r-client) (der vollständig kompatible, durch die Community unterstützter R-Interpreter mit ScaleR-Bibliotheken für schnellere Berechnung auf einzelnen Knoten oder Clustern von Microsoft). Sie können auch eine beliebige R-Sprache aus [CRAN](https://cran.r-project.org/) verwenden.)

Obwohl F# in verschiedenen Workloads enthalten ist und Python seine eigene Workload mitbringt, ist „Data Science und analytische Anwendungen“ derzeit die einzige Workload, die R beinhaltet. Sie können R jedoch auch unabhängig von der Workload installieren. Wählen Sie auf der Registerkarte **Einzelne Komponenten** im Installer die folgenden Optionen für R aus:

- **Entwicklungsaktivitäten** > **R-Sprachunterstützung**
- **Entwicklungsaktivitäten** > **Microsoft R Client**
- **Compiler, Buildtools und Runtimes** > **Runtimeunterstützung für R-Entwicklungstools**

## <a name="sql-server-integration"></a>Integration von SQL Server

SQL Server unterstützt die unmittelbare Verwendung von R und Python in SQL Server zum Durchführen erweiterter Analysen. R-Unterstützung ist im Lieferumfang von SQL Server 2016 oder neueren Versionen enthalten; Python-Unterstützung ist in SQL Server 2017 CTP 2.0 oder neueren Versionen verfügbar.

Wenn Sie Ihren Code dort ausführen, wo sich Ihre Daten bereits befinden, hat das die folgenden Vorteile:

- **Wegfall der Datenverschiebung**: Anstatt Daten aus der Datenbank in Ihre Anwendung oder Ihr Modell zu verschieben, können Sie R- und Python-Anwendungen direkt in der Datenbank erstellen. Dank dieser Funktion stellen Themen wie Sicherheit, Einhaltung, Governance, Integrität und eine Reihe ähnlicher Themen, mit denen man sich beim Verschieben großer Datenmengen auseinandersetzen muss, kein Problem mehr dar. Darüber hinaus können Sie damit Datasets nutzen, die die Arbeitsspeicherkapazität eines Clientcomputers übersteigen.

- **Einfache Bereitstellung**: Sobald Sie ein R- oder Python-Modell fertiggestellt haben, können Sie es für die Produktion mühelos bereitstellen, indem Sie es in ein T-SQL-Skript einbetten. Sämtliche, in beliebigen Sprachen geschriebene SQL-Clientanwendungen können dann die Modelle und Informationen durch Aufruf einer gespeicherten Prozedur nutzen. Es sind keine bestimmten R- oder Python-Integrationen erforderlich.

- **Leistung und Skalierung auf Unternehmensniveau**: Sie können die erweiterten Funktionen von SQL Server mit den leistungsstarken, skalierbaren APIs der Pakete „RevoScaleR“ und „RevoScalePy“ nutzen, z. B. Indizes zur In-Memory-Speicherung von Tabellen und Spalten. Das Wegfallen der Datenverschiebung bedeutet auch, dass Sie Einschränkungen des Clientspeichers umgehen können, z.B. wenn sich ihre Datenmenge vergrößert oder Sie die Leistung der Anwendung erhöhen möchten.

- **Umfangreiche Erweiterungsmöglichkeiten**: In SQL Server können Sie die neuesten Open Source-Pakete für R oder Python installieren und ausführen, und damit in SQL Server Deep Learning- und KI-Anwendungen auf Basis sehr großer Datenmengen erstellen. Das Installieren eines Pakets in SQL Server ist so einfach, wie ein Paket auf Ihrem lokalen Computer zu installieren.

- **Breite Verfügbarkeit ohne zusätzliche Kosten**: R- und Python-Integrationen stehen in allen Editionen von SQL Server 2017 sowie neueren Editionen zur Verfügung, einschließlich der Express-Edition. (Unterstützung für R ist in SQL Server 2016 oder neueren Versionen verfügbar.)

Verwenden Sie den Visual Studio-Installer, um die Workload **Datenspeicherung und -verarbeitung** mit der Option **SQL Server Data Tools** zu installieren. So können Sie die Integration von SQL Server bestmöglich nutzen. Diese zweite Option ermöglicht SQL-IntelliSense, Syntaxhervorhebung sowie die Bereitstellung.

![Workload von Datenspeicherung und -verarbeitung](media/data-storage-workload.png) &nbsp;&nbsp;&nbsp;&nbsp; ![Workloadoptionen von Datenspeicherung und -verarbeitung](media/data-storage-workload-options.png)

Weitere Informationen finden Sie unter: 

- [Arbeiten mit SQL Server und R](integrating-sql-server-with-r.md)
- [In-database Advanced Analytics with R in SQL Server 2016 (blog) (Advanced Analytics mit R in SQL Server 2016 in der Datenbank (Blogbeitrag))](https://blogs.technet.microsoft.com/dataplatforminsider/2016/03/29/in-database-advanced-analytics-with-r-in-sql-server-2016/)
- [Python in SQL Server 2017: enhanced in-database machine learning (blog) (Python in SQL Server 2017: verbessertes, datenbankinternes Machine Learning (Blogbeitrag))](https://blogs.technet.microsoft.com/dataplatforminsider/2017/04/19/python-in-sql-server-2017-enhanced-in-database-machine-learning/)

## <a name="additional-services-and-sdks"></a>Weitere Dienste und SDKs

Für Data Science sind zusätzlich zu dem, was die Workload „Data Science und analytische Anwendungen“ unmittelbar bietet, auch der Dienst „Azure Notebooks“ sowie das „Azure SDK für Python“ nützlich.

Das Azure SDK für Python vereinfacht die Nutzung und Verwaltung von Microsoft Azure-Diensten in Anwendungen unter Windows, Mac und Linux. Weitere Informationen finden Sie unter [Azure SDK für Python](../python/azure-sdk-for-python.md).

Azure Notebooks (zurzeit als Vorschau verfügbar) bietet kostenlosen Onlinezugriff auf die Anwendung „Jupyter Notebooks“, die in der Cloud auf Microsoft Azure ausgeführt wird. Der Dienst enthält Beispiel-Notebooks in den Sprachen Python, R und F#, um Ihnen den Einstieg zu erleichtern. Besuchen Sie [notebooks.azure.com](https://notebooks.azure.com/).

<!--Note link on the image because this one is large -->
[![Azure Notebooks-Screenshots für das Beispiel „Introduction to R“](media/data-science-workload-notebooks.png)](media/data-science-workload-notebooks.png#lightbox)
