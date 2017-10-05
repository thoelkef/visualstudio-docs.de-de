---
title: "R Markdown mit R Tools für Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 6/29/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3ac955b2-b6e1-4d32-b1a4-2882c93311fc
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 712cc780388acc5e373f71d51fc8f1f42adb5bed
ms.openlocfilehash: b29ae0240a29616edcdf2ae0dced7a9fca0f9584
ms.contentlocale: de-de
ms.lasthandoff: 07/12/2017

---

# <a name="creating-r-markdown-documents"></a>Erstellen von R Markdown-Dokumenten

[R Markdown](https://rmarkdown.rstudio.com/) ist ein Dokumentformat, mit dem Analysen in R in hochwertige Dokumente, Berichte, Präsentationen und Dashboards verwandelt werden können.

R Tools für Visual Studio (RTVS) bietet eine R Markdown-Elementvorlage, Editor-Unterstützung (einschließlich IntelliSense für R-Code im Editor) und Funktionen zur Dateierstellung.

So verwenden Sie R Markdown:

1. Schließen Sie Visual Studio.
1. (Nur einmal) Installieren Sie `pandoc` aus [pandoc.org](http://pandoc.org/installing.html).
1. Starten Sie Visual Studio neu, wodurch die Installation von Pandoc weitergeführt werden sollte.
1. Installieren Sie die Pakete `knitr` und `rmarkdown` ggf. über das [interaktive Fenster](interactive-repl.md):

    ```R
    install.packages("knitr")
    install.packages("rmarkdown")

    ```
1. Erstellen Sie eine neue R Markdown-Datei, indem Sie entweder den Menübefehl **Datei > Neu** verwenden und **R Markdown** aus der Liste auswählen oder indem Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt klicken und **R Markdown hinzufügen** (oder **Hinzufügen > Neues Element...** und **R Markdown** aus der Liste) auswählen.

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

1. Klicken Sie zu einem beliebigen Zeitpunkt während der Bearbeitung mit der rechten Maustaste in den Editor, und wählen Sie **Vorschauversion** aus, die Optionen für HTML, PDF und Microsoft Word enthält. Über diese Vorschau können Sie die Datei entsprechend dem Format speichern, das Sie auswählen.

