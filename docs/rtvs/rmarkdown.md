---
title: "R Markdown mit R Tools für Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/16/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload: data-science
ms.openlocfilehash: 340ab0b55de1bb6c5889bb15560065d71e438ca6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="creating-r-markdown-documents"></a>Erstellen von R Markdown-Dokumenten

[R Markdown](https://rmarkdown.rstudio.com/) ist ein Dokumentformat, mit dem Analysen in R in hochwertige Dokumente, Berichte, Präsentationen und Dashboards verwandelt werden können.

R Tools für Visual Studio (RTVS) bietet eine R Markdown-Elementvorlage, Editor-Unterstützung (einschließlich IntelliSense für R-Code im Editor), Funktionen zur Dateierstellung und eine Livevorschau.

## <a name="using-r-markdown"></a>Verwenden von R Markdown

1. Schließen Sie Visual Studio.
1. (Nur einmal) Installieren Sie `pandoc` aus [pandoc.org](http://pandoc.org/installing.html).
1. Starten Sie Visual Studio neu, wodurch die Installation von Pandoc weitergeführt werden sollte.
1. Installieren Sie die Pakete `knitr` und `rmarkdown` ggf. über das [interaktive Fenster](interactive-repl.md):

    ```R
    install.packages("knitr")
    install.packages("rmarkdown")

    ```
1. Erstellen Sie über den Menübefehl **Datei > Neu > Datei** und die Auswahl von **R > R Markdown** in der Liste eine neue R Markdown-Datei. Klicken Sie im Kontext eines Projekts im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt. Wählen Sie **R Markdown hinzufügen** (oder **Hinzufügen > Neues Element...**, und wählen Sie **R Markdown** in der Liste) aus.

1. Der standardmäßige Inhalt der neuen Datei lautet wie folgt:

    ~~~markdown
    ---
    title: "Untitled"
    output: html_document
    ---

    This is an R Markdown document. Markdown is a simple formatting syntax for authoring HTML, PDF, and Microsoft Word documents. For more details on using R Markdown see <http://rmarkdown.rstudio.com>.

    When you click the **R Tools | Publish | Preview** button a document will be generated that includes both content as well as the output of any embedded R code chunks within the document. You can embed an R code chunk like this:

    ```{r}
    summary(cars)
    ```

    You can also embed plots, for example:

    ```{r, echo=FALSE}
    plot(cars)
    ```

    Note that the `echo = FALSE` parameter was added to the code chunk to prevent printing of the R code that generated the plot.

    ~~~

## <a name="previews"></a>Preview-Versionen

Visual Studio 2017 bietet ab Version 15.5 für R Markdown automatisch eine Livevorschau. Um die automatische Synchronisierung zwischen dem Editor und der Vorschau einzuschalten, wählen Sie **R Tools > Markdown > Automatische Synchronisierung** (STRG+UMSCHALT+Y). Wenn Sie keine automatische Synchronisierung verwenden, können Sie die Vorschau über **R Tools > Markdown > R Markdown-Vorschau neu laden** aktualisieren.

Sie können auch eine Vorschau der Datei in den Formaten HTML, PDF und Microsoft Word anzeigen, indem Sie im Editor mit der rechten Maustaste klicken und einen der **Vorschau**-Befehle auswählen. Dieselben Befehle sind auch im Menü **R Tools > Markdown** verfügbar. (In früheren Versionen von Visual Studio finden Sie diese Befehle im Menü **R Tools > Veröffentlichen**.)

![R Markdown-Livevorschau und andere Menübefehle für Vorschau](media/rmarkdown-live-preview.png)
