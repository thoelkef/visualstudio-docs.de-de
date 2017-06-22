---
title: "Beispielprojekte für R Tools für Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 4/26/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa52ed0e-cdb5-4fb2-814c-c94cac2ffc6f
caps.latest.revision: 1
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: d58ff34914af9185ce5282bdc8848db2b12f1aea
ms.contentlocale: de-de
ms.lasthandoff: 05/12/2017

---

# <a name="r-tools-for-visual-studio-sample-projects"></a>Beispielprojekte für R Tools für Visual Studio

Mit dieser Sammlung von Beispielen können Sie mit R, R Tools für Visual Studio (RTVS) und Microsoft R Server beginnen:

1. Laden Sie die [ZIP-Beispieldatei](https://github.com/Microsoft/RTVS-docs/archive/master.zip) herunter, und extrahieren Sie sie in einem Ordner Ihrer Wahl.
1. Öffnen Sie `examples/Examples.sln`. Es werden zwei Ordner im Projekt angezeigt:

    - *Erster Einblick in R* enthält einfache Anleitungen für Einsteiger in R.
    - *MRS und maschinelles Lernen* enthält Beispiele zur Verwendung von R und Microsoft R Server für das maschinelle Lernen.

## <a name="a-first-look-at-r"></a>Erster Einblick in R

Dieses Beispiel bietet eine detaillierte Einführung in R über die umfangreichen Kommentaren in den Quelldateien. Die beste Möglichkeit, beide zu testen, ist es, den Cursor an den Anfang der Datei zu setzen und dann STRG+EINGABE zu drücken, um nacheinander jede Zeile zum **R Interactive**-Fenster zu senden, in dem Sie die Ergebnisse sehen können. Beachten Sie, dass einige Zeilen Pakete installieren, was wenige Minuten in Anspruch nehmen kann.

- `1-Getting Started with R.R` deckt viele Grundlagen von R ab, einschließlich die Verwendung von Paketen, das Laden und Analysieren von Daten und das Zeichnen.

    ![Beispielausgabe des Beispiels „1-Getting Started with R.R“](media/samples-getting-started-output.png)

- `2-Introduction to ggplot2.R` führt das „ggplot2“-Grafikpaket ein, das für seine visuell ansprechenden Zeichnungen und die einfache Syntax bekannt ist. Diese Beispiel stellt Erdbebendaten aus Fiji visuell dar.

    ![Beispielausgabe aus dem Beispiel „2-Introduction to ggplot2.R“](media/samples-ggplot-output.png)


## <a name="microsoft-r-server-and-machine-learning"></a>Microsoft R Server und maschinelles Lernen

Diese Sammlung von Beispielen zeigt, wie Sie R und Microsoft R Server zum Erstellen von Modellen für das maschinelle Lernen verwenden und wie Sie von der Funktionalität von [Microsoft R Server (MRS)](http://aka.ms/rtvs-msft-r) profitieren können. Beachten Sie, dass Sie MRS installieren müssen, um Skripts mit `MRS` im Titel – und woanders vermerkt – auszuführen.

Eine gute Möglichkeit, um nicht nur die oben genannten Beispiele zu testen, ist es, die Datei zu öffnen, den Cursor an den Anfang zu setzen und dann Zeile für Zeile mit STRG+EINGABE durch den Code zu gehen. Beachten Sie auch die Markdowndateien in jedem Ordner, die weitere Details enthalten.

- `Benchmarks` führt eine Reihe rechenintensiver Benchmarks aus, um die Leistungssteigerungen darzustellen, die mithilfe der Verwendung von Microsoft R Open und der Intel Math Kernel Library (MLK) für schnelle, parallele und lineare Algebraberechnungen ermöglicht werden. Mit simulierten Daten werden besonders zwei Threads für bestimmte der Matrix zugeordneten Berechnungen gegenüber einem Thread verglichen.   

    ![Benchmark-Beispielzeichnung](media/samples-mro-benchmark-plot.png)

- `Bike_Rental_Estimation_with_MRS` erstellt ein Vorhersagemodell für die Nachfrage mithilfe von Microsoft R Server für Fahrradverleihe, die auf einem Satz von Verlaufsdaten basieren. 

- `Data_Exploration` enthält drei Skripts:  
    - `Import Data from URL.R` zeigt, wie eine durch die URL identifizierte Datendatei in R geladen wird.
    - `Import Data from URL to xdf.R` zeigt, wie Sie eine durch die URL identifizierte Datendatei als XDF in Microsoft R Server laden. (MRS erforderlich.)
    - `Using ggplot2.R` ist eine Erweiterung des `A First Look at R/2-Introduction to ggplot2.R`-Beispiels, das Ihnen einen tieferen Einblick in die Funktionalität von „ggplot2.R“ bietet, einschließlich des interaktiven 3D-Zeichnens.

        ![Ausgabe eines „ggplot2.R“-Beispiels](media/samples-3d-interactive.png)

- `Datasets` enthält drei `.csv`-Dateien, die von anderen Beispielen verwendet werden
- `Flight_Delays_Prediction_with_R` und `Flight_Delays_Prediction_with_MRS` zeigen, wie Verspätungen bei Flügen mithilfe von R, des maschinellen Lernens sowie mithilfe der historischen Echtzeitleistung und Wetterdaten vorhergesagt werden. 
- `Machine learning` enthält drei Beispiele, mit denen die Vorhersage von Verspätungen von Flügen, Immobilienpreisen sowie Fahrradverleihen erlernt werden kann, was die Anwendung von R und MRS im Zusammenhang mit Problemen der echten Welt demonstriert. Es wird auch gezeigt, wie Sie mehrere beliebte Modelle für das maschinelle Lernen verwenden können und diese als Azure-Webdienst mithilfe eines [Azure Machine Learning](https://azure.microsoft.com/services/machine-learning/)-Arbeitsbereichs bereitstellen können.

- `R_MRO_MRS_Comparison` ist ein Vergleich mit sechs Teilen, der die Ähnlichkeiten und Unterschiede von R, Microsoft R Open und Microsoft R Server mit Befehlen, Syntax, Konstrukten und Leistung darstellt.

## <a name="whats-special-about-microsoft-r-open-and-microsoft-r-server"></a>Was ist so besonders an Microsoft R Open und Microsoft R Server?

[Microsoft R Open](http://aka.ms/rtvs-r-open), die Verteilung von R von Microsoft, unterscheidet sich in zwei wichtigen Punkten von [CRAN R](https://cran.r-project.org/):

1. [Bessere Rechnungsleistung](https://mran.revolutionanalytics.com/rro/#intelmkl1) unter Verwendung der [Intel Math Kernel Libraries](https://software.intel.com/intel-mkl). Diese sind als kostenloser Download unter Microsoft für die Verwendung mit Microsoft R Open erhältlich.

1. [Reproduzierbares R-Toolkit](https://mran.revolutionanalytics.com/rro/#reproducibility), das sicherstellt, dass die Bibliotheken, die Sie zum Erstellen Ihres R-Programms verwendet haben, immer für andere Personen verfügbar sind, die Ihre Arbeit reproduzieren möchten.

[Microsoft R Server](http://aka.ms/rtvs-msft-r) ist eine Erweiterung von R, mit der Sie mehr Daten schneller verarbeiten können. R enthält dadurch zwei leistungsstarke Funktionen:

1. Größere Datasets MRS kann out-of-memory-Daten aus einer Vielzahl von Quellen verarbeiten, einschließlich Hadoop-Clustern, Datenbanken und Data Warehouses. Sie werden nie wieder von Ihrem RAM eingeschränkt.

1. Parallele Mehrkernverarbeitung. MRS kann Berechnungen effektiv über alle verfügbaren Berechnungsressourcen verteilen. MRS erhält auf Ihrer persönlichen Arbeitsstation oder einem Remotecluster schneller eine Antwort.

Der folgende Vergleich zeigt, dass MRS und MRO mit MKL eine weitaus bessere Berechnungsleistung im Zusammenhang mit bestimmten Matrixberechnungen im Vergleich zu R und MRO ohne MKL haben. In dieser Berechnung werden simulierte Daten verwendet:

![Vergleich von MRS und MRO mit MKL zu R und MRO ohne MKL](media/samples-speed-comparison.png)

Einen technischen Vergleich von R mit MRO und MRS finden Sie in der [detaillierten Diskussion von Lixun Zhang](http://htmlpreview.github.io/?https://github.com/lixzhang/R-MRO-MRS/blob/master/Introduction_to_MRO_and_MRS.html) zu diesem Thema.

In der folgenden Abbildung wird dann die verstrichene Zeit in Sekunden verglichen, die zum Erstellen von logistischen Regressionsmodellen verwendet wird, um vorherzusagen, ob sich die geplante Ankunft von Passagierflügen um mehr als 15 Minuten verzögern wird. Die verstrichene Zeit, die in CRAN R verwendet wird, erhöht sich signifikant, wenn eine niedrige Anzahl von Zeilen erhöht wird, während MRS nur etwa zweimal erhöht wird. Informationen zu diesem Benchmark finden Sie im `Benchmarks/rxGlm_benchmark.R`-Beispiel.

![„rxGlm“-Benchmark](media/samples-rxGLM-benchmark.png)

