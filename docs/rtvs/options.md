---
title: "Optionen für R Tools in Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 4/26/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
f1_keywords:
- vs.toolsoptionspages.r_tools
- vs.toolsoptionspages.r_tools.advanced
- vs.toolsoptionspages.r_tools.#150
ms.topic: article
ms.assetid: 554dc602-ecad-4cd0-8e6f-a60bb8a2328f
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
ms.openlocfilehash: 9b680c73d54c9809e3f4c46dc2841f1f320e4af9
ms.contentlocale: de-de
ms.lasthandoff: 05/12/2017

---


# <a name="r-tools-for-visual-studio-options"></a>Optionen für R Tools für Visual Studio
 
Sie erreichen die Einstellungen über das Menü **R Tools > Optionen** oder über **Tools > Optionen** und dann durch Scrollen zu **R Tools**.
 
  ![Dialogfeld „Optionen“ für R Tools](~/docs/rtvs/media/options-dialog.png)

In den folgenden Abschnitten sind die verschiedenen Optionen beschrieben, die auf dieser Seite verfügbar sind.

> [!Note]
> Wenn Sie auf Optionen über das allgemeine Menü **Tools > Optionen** zugreifen, müssen Sie möglicherweise das Feld **Alle Einstellungen anzeigen** am unteren Rand auswählen, damit die Seite **R Tools** angezeigt wird.

<a name="data-scientist-layout"</a>

Es gibt auch ein spezielles Menüelement, **R Tools > Data Science-Einstellungen**, das die Visual Studio-IDE mit einem Layout konfiguriert, das für die Bedürfnisse von Datenspezialisten optimiert wurde. Besonders ist, dass diese Option die Fenster [Interaktiv](interactive-repl.md), [Variablen-Explorer](variable-explorer.md) und [Arbeitsbereiche](workspaces.md) öffnet:

![Fensterlayout für Datenspezialisten in Visual Studio](~/docs/rtvs/media/installation-data-scientist-layout-result.png)

> [!Important]      
> Um andere Visual Studio-Einstellungen später wiederherzustellen, verwenden Sie zunächst den Befehl **Tools > Einstellungen importieren und exportieren**, wählen Sie **Ausgewählte Umgebungseinstellungen importieren** aus, und geben Sie den Dateinamen an. Verwenden Sie den gleichen Befehl, und wählen Sie **Ausgewählte Umgebungseinstellungen importieren** aus, um dieses Einstellungen wiederherzustellen. Sie können auch die gleichen Befehle verwenden, wenn Sie das Layout für Datenspezialisten ändern und es später erneut ausführen möchten und nicht direkt den Befehl **Data Science-Einstellungen** verwenden möchten.

## <a name="debugging"></a>Debuggen

Diese Optionen steuern, wie Werte im [Variablen-Explorer](variable-explorer.md) und in Debuggertoolfenstern für lokale Variablen und Überwachung verarbeitet werden (siehe [Debugging](debugging.md)).

| Option | Standardwert | Beschreibung | 
| --- | --- | --- |
| Aktive Bindungen auswerten | `True` | Wenn `True`, wird sichergestellt, dass Sie immer den aktuellsten Wert erhalten, wenn Sie Variablen und Eigenschaften prüfen. Das Risiko ist, dass die Überprüfung der Ausdrücke zu Nebenwirkungen führen kann, je nachdem, wie sie implementiert wurden. |
| Variablen mit vorangestelltem Punkt anzeigen | `False` | Gibt an, ob Variablen, denen `.` vorangestellt wird, angezeigt werden. |

## <a name="general"></a>Allgemein

| Option | Standardwert | Beschreibung | 
| --- | --- | --- |
| Abfrage-/Neuigkeitenprüfung | `Once a week` | Gibt an, wie oft R Tools den Server nach Neuigkeiten und Updates zu Abfragen abfragen soll. | 

## <a name="help"></a>Hilfe

| Option | Standardwert | Beschreibung | 
| --- | --- | --- |
| F1-Webbrowser | `Internal` | Steuert, wie Hilfe angezeigt wird, wenn Sie nach einem Begriff mithilfe von STRG+F1 suchen. Wenn sie auf `Internal` festgelegt ist, wird die Hilfe innerhalb eines Toolfensters in Visual Studio gerendert. Wenn sie auf `External` festgelegt ist, wird die Hilfe in Ihrem Standardwebbrowser angezeigt. | 
| F1-Websuchzeichenfolge | `R site:stackoverflow.com` | Steuert, wie Suchbegriffe Ihrer Suchmaschine übergeben werden, wenn Sie STRG+F1 auf einem Begriff im Editor drücken. Standardmäßig ist die Zeichenfolge `R site:stackoverflow.com`, was `R` an Ihren Suchbegriff anfügt. `site:stackoverflow.com` ist eine Direktive für die Suchmaschine, die dieser mitteilt, dass die Suche im Bereich der Seiten innerhalb der `stackoverflow.com`-Domäne durchgeführt werden soll. | 
| Browser der R-Hilfe | `Automatic` | Steuert, wie Hilfe angezeigt wird, wenn Sie nach in der R-Dokumentation mithilfe von F1, `?` oder `??` suchen. Wenn sie auf `Automatic` festgelegt wurde, wird die Hilfe im entsprechenden Fenster gerendert. Die HTML-Hilfe erscheint beispielsweise in einem Visual Studio-Toolfenster, wobei PDFs in Ihrem Standard-PDF-Programm angezeigt werden. Wenn sie auf `External` festgelegt wurde, wird die Hilfe in Ihrem Standardwebbrowser gerendert. |

## <a name="history"></a>Versionsgeschichte

| Option | Standardwert | Beschreibung | 
| --- | --- | --- |
| Verlauf immer speichern | `True` | Steuert, ob RTVS Ihren Verlauf immer in eine `.RHistory`-Datei Ihres Arbeitsverzeichnisses schreibt, wenn das Projekt geschlossen wird. Beachten Sie, dass dies auch geschieht, wenn Sie Ihr Projekt vor dem Schließen nicht speichern. |
| Suchfilter zurücksetzen | `True` | Bestimmt, ob das Fenster „Verlauf“ Ihren Befehlsverlauf filtern kann, damit nur die Befehle angezeigt werden, deren Teilzeichenfolge mit dem Filterbegriff im Dialogfeld „R-Verlauf“ übereinstimmen. Diese Einstellung bestimmt, ob Ihr Suchfilter „Verlauf“ zurückgesetzt werden soll, wenn Sie einen neuen Befehl ausführen oder zu einem neuen Projekt wechseln, wodurch eine andere `.RHistory`-Datei geladen wird. Mit der Standardeinstellung `True` müssen Sie sich beim Ausführen eines Befehls, für den ein Filter festgelegt wurde, nicht mehr wundern, warum der zuvor ausgeführte Befehl nicht im Verlauf angezeigt wurde. |
| Mehrzeilige Auswahl verwenden | `True` | Gibt an, ob Sie eine mehrzeilige Anweisung im Verlauf mit einem einzigen Klick auswählen können. Ermöglicht auch die Navigation in den interaktiven Fenstern nach Anweisungen statt nach Zeilen mit den Schaltflächen NACH-OBEN/NACH-UNTEN. |

## <a name="html"></a>HTML

| Option | Standardwert | Beschreibung | 
| --- | --- | --- |
| Browser für HTML-Seiten | `External` | Bestimmt, wo Inhalt gerendert wird, z.B. ein `ggvis`-Plot oder eine `shiny`-Anwendung. `Internal` zeigt HTML-Ausgabe in einem Toolfenster in Visual Studio an; `External` zeigt HTML-Ausgabe in Ihrem Standardbrowser an. | 

## <a name="logging"></a>Protokollierung

| Option | Standardwert | Beschreibung | 
| --- | --- | --- |
| Protokollieren von Ereignissen | `Normal` | Steuert die Ausführlichkeit der Protokollierung, die für die RTVS-Diagnose genutzt wird. Die Standardeinstellung `Normal` erstellt eine Protokolldatei in Ihrem `TEMP`-Verzeichnis. Wenn sie auf `Traffic` festgelegt sind, protokolliert die RTVS-Erweiterung alle Befehle und stellt die Antworten in Ihrer Sitzung dar. Diese Protokolldateien befinden sich immer auf Ihrem Computer, sind aber womöglich hilfreich, um Probleme in RTVS zu diagnostizieren. |

## <a name="markdown"></a>Markdown

| Option | Standardwert | Beschreibung | 
| --- | --- | --- |
| Markdownvorschaubrowser | `External` | Bestimmt, wo die RMarkdown-HTML-Ausgabe angezeigt wird. `Internal` zeigt RMarkdown-HTML-Dokumente in einem Toolfenster in Visual Studio an; `External` zeigt RMarkdown-HTML mithilfe Ihres Standardbrowsers an. | 

## <a name="r-engine"></a>R-Modul

| Option | Standardwert | Beschreibung | 
| --- | --- | --- |
| Codepage | `(OS Default)` | Legt die Codepage (Gebietsschema) für R fest. Standardmäßig wird das zugrundeliegende Gebietsschema des Betriebssystems verwendet. | 
| CRAN-Spiegel | `(Use .Rprofile)` | Legt den standardmäßigen CRAN-Spiegel für Paketinstallationen fest. Die Standardeinstellung von `Use .Rprofile` respektiert Einstellungen für den CRAN-Spiegel in Ihrer `.RProfile`-Datei. Sie können dies außer Kraft setzen, indem Sie einen der aufgeführten CRAN-Spiegel in der Dropdownliste auswählen. |
| Arbeitsverzeichnis | benutzerspezifischer Ordner | Legt das aktuelle Arbeitsverzeichnis fest, das in der Regel festgelegt wird, wenn ein Projekt geöffnet wird. |

## <a name="workspace"></a>Arbeitsbereich

| Option | Standardwert | Beschreibung | 
| --- | --- | --- |
| Arbeitsbereich beim Öffnen des Projekts laden | `No` | Die Einstellung auf `Yes` ermöglicht das Laden von Sitzungsdaten von der `.RData`-Datei in die globale Umgebung, wenn das Projekt geöffnet wird. |
| Beim Zurücksetzen zum Speichern des Arbeitsbereichs auffordern | `Yes` | Die Einstellung auf `No` deaktiviert die Aufforderung, Ihren Arbeitsbereich durch Klicken auf die Schaltfläche „Zurücksetzen“ im interaktiven Fenster zu speichern. |
| Beim Schließen des Projekts Arbeitsbereich speichern | `No` | Die Einstellung auf `Yes` ermöglicht die Speicherung der globalen Umgebung in die `.RData`-Datei, wenn das Projekt geschlossen wird. |
| Vor dem Arbeitsbereichswechsel Bestätigungsdialogfeld anzeigen | `Yes` | Die Einstellung auf `No` deaktiviert die Aufforderung zur Bestätigung, wenn zwischen unterschiedlichen Arbeitsbereichen gewechselt wird. Weitere Informationen finden Sie unter [Switching between workspaces (Wechseln zwischen Arbeitsbereichen)](workspaces.md#switching-between-workspaces). |
 
