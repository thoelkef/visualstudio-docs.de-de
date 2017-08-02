---
title: "Variablen-Explorer in R Tools für Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 4/10/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6c669434-40d8-4970-92cc-502a98c8b5ab
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
ms.openlocfilehash: 7a72afdf01a9c1efb389efc893beedfc1eed87c1
ms.contentlocale: de-de
ms.lasthandoff: 05/12/2017

---


# <a name="variable-explorer"></a>Variablen-Explorer

Das Fenster **Variablen-Explorer**, das über **R Tools > Windows > Variablen-Explorer** (oder STRG+8, wenn Sie **R Tools > Data Science-Einstellungen** verwendet haben) geöffnet wird, zeigt alle Variablen in einem bestimmten Bereich in der aktuellen R-Sitzung. Wenn Sie beispielsweise den Variablen-Explorer geöffnet haben und die folgenden Zeilen im [interaktiven Fenster](interactive-repl.md) eingeben:

```R
x <- 42
y <- 43
n <- c(1,2,3,5,8,13)
```
 
Das Fenster des Variablen-Explorers wird folgendermaßen angezeigt:

![Fenster „Variablen-Explorer“ in Visual Studio](~/rtvs/media/variable-explorer-window.png)

Wenn Sie einen komplexeren, in der Sitzung definierten R-Datenrahmen haben, können Sie in den Daten navigieren. Nach der Ausführung von `cars <- mtcars` können Sie z.B. in dem Dataset navigieren, indem Sie die anderen Knoten im Variablen-Explorer erweitern:
 
![Erweiterte Ansicht des Variablen-Explorers](~/rtvs/media/variable-explorer-expanded-results.png)
 
Klicken Sie zum Löschen von Variablen mit der rechten Maustaste darauf, und wählen Sie **Löschen** aus. Wählen Sie alternativ die Variable aus, und drücken Sie ENTF.

Sie können auch mithilfe der inkrementellen Suche in einem Datenrahmen nach einer Beobachtung suchen. Erweitern Sie zuerst die Knoten im Datenrahmen, die Sie suchen möchten, und geben Sie dann Suchbegriffe in das Suchfeld ein.

## <a name="details-table-view"></a>Detailansicht (Tabelle)

Da Daten in Tabellen erfasst werden, können Sie alle komplexen Datentypen als separate Tabelle anzeigen, indem Sie das Lupensymbol auswählen oder mit der rechten Maustaste darauf klicken und anschließend **Details anzeigen** auswählen. 

![Tabellenansicht des Variablen-Explorers](~/rtvs/media/variable-explorer-table-view.png)

Durch einen Klick auf eine Spaltenüberschrift werden die Daten nach Spalten sortiert (abwechselnd in aufsteigender und absteigender Reihenfolge). Wird die UMSCHALTTASTE gedrückt gehalten und auf zusätzliche Spalten geklickt, werden diese Spalten ebenfalls der Sortierung hinzugefügt. Wenn Sie ohne UMSCHALT auf eine Spalte klicken, wird wieder nach einer Spalte sortiert.

Die Reihenfolge, in der Sie auf die Spaltenüberschriften klicken, bestimmt die Reihenfolge, in der die Sortierung ausgeführt wird. Wenn Sie z.B. bei gedrückter UMSCHALTTASTE auf die **cyl**-Spalte klicken und dann zweimal ebenfalls bei gedrückter UMSCHALTTASTE auf die **mpg**-Spalte klicken, wird die Liste aufsteigend nach Zylindern und absteigend nach Meilen pro Gallone sortiert:

![Tabellenansicht der Daten, nach zwei Spalten sortiert](~/rtvs/media/variable-explorer-table-view-sorting.png)

Da sich der Variablen-Explorer und die Tabellenansichten in separaten Visual Studio-Fenstern befinden, können Sie sie für die gleichzeitige Arbeit beliebig anordnen. Allgemeine Anweisungen finden Sie unter [Anpassen von Fensterlayouts in Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md).

## <a name="open-in-excel-or-other-csv-capable-application"></a>Öffnen in Excel (oder anderen CSV-fähigen Anwendungen)

Für die weitere Bearbeitung und Analyse ist es oft hilfreich, Sitzungsvariablen in das CSV-Format zu exportieren. Dies erreichen Sie mit dem kleinen Excel-Symbol (![Excelexportsymbol](~/rtvs/media/variable-explorer-excel-icon.png)) neben den einzelnen Knoten im Variablen-Explorer oder indem Sie mit der rechten Maustaste auf ein Element klicken und **In CSV-App öffnen** auswählen. Durch Auswählen des Symbols werden die Daten in eine neue CSV-Datei im `%userprofile%\Documents\RTVS_CSV_Exports`-Ordner geschrieben und dann gestartet, wodurch die Datei in der Anwendung geöffnet wird, die der `.csv`-Erweiterung zugeordnet ist.

## <a name="scopes"></a>Bereiche

Der Variablen-Explorer wird standardmäßig im globalen Gültigkeitsbereich geöffnet. Sie können zu einem Paketbereich wechseln, indem Sie ein Paket aus der Dropdownliste am oberen Rand des Fensters auswählen.

![Variablen-Explorer, der einen Paketbereich zeigt](~/rtvs/media/variable-explorer-package-scopes.png)

Sie können auch zu einem Funktionsbereich wechseln, wenn Sie an einem Breakpoint im Debugger angehalten werden (beachten Sie, dass der Variablen-Explorer nicht automatisch in den Funktionsbereich des debuggten Codes wechselt):

![Variablen-Explorer, der einen Datenrahmen während des Debuggens zeigt](~/rtvs/media/variable-explorer-as-locals-window.png)

Der Variablen-Explorer ändert automatisch den Funktionsbereich, während der Code im Debugger durchlaufen wird, z.B. beim Anzeigen lokaler Variablen in einer Funktion.


## <a name="importing-data-into-variable-explorer"></a>Importieren von Daten in den Variablen-Explorer

Es gibt zwei Befehle auf der Symbolleiste des Variablen-Explorers, die auch über das Menü **R Tools > Daten** verfügbar sind, die externe CSV-Datasets in Ihre R-Sitzung importieren: **Dataset aus Web-URL in R-Sitzung importieren** und **Dataset aus Textdatei in R-Sitzung importieren**. 

Wenn Sie die zu importierende CSV-Datei ermittelt haben, zeigt R Tools für Visual Studio ein Dialogfeld **Dataset importieren** an, in dem Sie mit Optionen steuern können, wie eine Datendatei analysiert wird (d.h. wie der Feldseparator definiert ist und wie Zitate behandelt werden), und eine Vorschau des importierten Datenrahmens und der ursprünglichen Datendatei aufrufen können:

![Dialogfeld „Dataset importieren“](~/rtvs/media/variable-explorer-import-dataset-dialog.png)

