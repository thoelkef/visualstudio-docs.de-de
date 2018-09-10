---
title: R Markdown
description: Erstellen von R Markdown-Dokumenten in Visual Studio zum Erstellen von Berichten, Präsentationen und Dashboards hoher Qualität.
ms.date: 11/16/2017
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: 1bb6779e0e8174dd10f209d9825ffb861d00455d
ms.sourcegitcommit: f685fa5e2df9dc307bf1230dd9dc3288aaa408b5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36235300"
---
# <a name="create-r-markdown-documents"></a>Erstellen von R Markdown-Dokumenten

[R Markdown](https://rmarkdown.rstudio.com/) ist ein Dokumentformat, mit dem Analysen in R in hochwertige Dokumente, Berichte, Präsentationen und Dashboards verwandelt werden können.

R Tools für Visual Studio (RTVS) bietet eine R Markdown-Elementvorlage, Editor-Unterstützung (einschließlich IntelliSense für R-Code im Editor), Funktionen zur Dateierstellung und eine Livevorschau.

## <a name="using-r-markdown"></a>Verwenden von R Markdown

1. Schließen Sie Visual Studio.
1. (Nur einmal) Installieren Sie `pandoc` aus [pandoc.org](http://pandoc.org/installing.html).
1. Starten Sie Visual Studio neu, wodurch die Installation von Pandoc weitergeführt werden sollte.
1. Installieren Sie die Pakete `knitr` und `rmarkdown` ggf. über das [interaktive Fenster](interactive-repl-for-r-in-visual-studio.md):

    ```R
    install.packages("knitr")
    install.packages("rmarkdown")

    ```
1. Erstellen Sie über den Menübefehl **Datei** > **Neu** > **Datei** und die Auswahl von **R** > **R Markdown** in der Liste eine neue R Markdown-Datei. Klicken Sie im Kontext eines Projekts im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt. Wählen Sie **R Markdown hinzufügen** aus (oder klicken Sie auf **Hinzufügen** > **Neues Element**, und wählen Sie **R Markdown** in der Liste aus).

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

Visual Studio 2017 bietet ab Version 15.5 für R Markdown automatisch eine Livevorschau. Klicken Sie auf **R-Tools** > **Markdown** > **Automatische Synchronisierung** (**STRG**+**UMSCHALT**+**Y**), um die automatische Synchronisierung zwischen dem Editor und der Vorschau zu aktivieren. Wenn Sie keine automatische Synchronisierung verwenden, können Sie die Vorschau über **R-Tools** > **Markdown** > **R Markdown-Vorschau neu laden** aktualisieren.

Sie können auch eine Vorschau der Datei in den Formaten HTML, PDF und Microsoft Word anzeigen, indem Sie im Editor mit der rechten Maustaste klicken und einen der **Vorschau**-Befehle auswählen. Dieselben Befehle sind auch im Menü **R-Tools** > **Markdown** verfügbar. (In früheren Versionen von Visual Studio finden Sie diese Befehle im Menü **R-Tools** > **Veröffentlichen**.)

![R Markdown-Livevorschau und andere Menübefehle für Vorschau](media/rmarkdown-live-preview.png)
