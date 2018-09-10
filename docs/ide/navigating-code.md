---
title: Codenavigationsbefehle
ms.date: 08/14/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code editor, navigation
- code editor, go to
- code editor, go to definition
- code editor, go to line
- code editor, peek definition
- code editor, navigation bar
- go to definition
- peek definition
- go to line
- go to
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: eb711763e96cf6959a71b002f09cefa1ced44734
ms.sourcegitcommit: 4c60bcfa2281bcc1a28def6a8e02433d2c905be6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2018
ms.locfileid: "42627297"
---
# <a name="navigate-code"></a>Navigieren durch den Code

Der Editor von Visual Studio bietet zahlreiche Möglichkeiten, im Code zu navigieren. In diesem Artikel werden die verschiedenen Möglichkeiten, wie Sie in Ihrem Code navigieren können, zusammengefasst. Außerdem enthält er Links zu weiteren Abschnitten, die die Einzelthemen noch detaillierter behandeln.

## <a name="navigate-backward-and-navigate-forward-commands"></a>„Rückwärts navigieren“-Befehl und „Vorwärts navigieren“-Befehl

Sie können die Schaltflächen **Rückwärts navigieren** (**STRG**+**-**) und **Vorwärts navigieren** (**STRG**+**UMSCHALT**+**-**) auf der Symbolleiste verwenden, um die Einfügemarke auf vorherige Positionen oder von einer vorherigen Position auf eine erst kürzlich besuchte Position zu verschieben. Diese Schaltflächen speichern die letzten 20 Positionen der Einfügemarke. Diese Befehle sind auch im Menü **Ansicht** unter **Rückwärts navigieren** und **Vorwärts navigieren** verfügbar.

![Navigationsschaltflächen "Vor" und "Zurück"](../ide/media/vs2017_nav_buttons.png)

## <a name="navigation-bar"></a>Navigationsleiste

Sie können die **Navigationsleiste** (die Dropdownfelder am Anfang des Codefensters) verwenden, um in einer Codebasis zu Code zu navigieren. Sie können einen Typ oder Member auswählen und direkt zu diesem wechseln. Die Navigationsleiste wird angezeigt, wenn Sie Code in der Visual Basic-, C#- oder C++-Code-Basis bearbeiten. In einer partiellen Klasse sind Member, die außerhalb der aktuellen Codedatei definiert wurden, möglicherweise deaktiviert (werden grau angezeigt).

 ![Codenavigationsleiste](../ide/media/vside_navigation_bar.png)

Mithilfe der Dropdownfelder können Sie wie folgt navigieren:

- Um zu einem anderen Projekt zu navigieren, zu dem die aktuelle Datei gehört, wählen Sie dieses in der linken Dropdownliste aus.

- Um zu einer Klasse bzw. einem Typ zu navigieren, wählen Sie diese bzw. diesen in der mittleren Dropdownliste aus.

- Um direkt zu einer Prozedur oder einem anderen Member einer Klasse zu navigieren, wählen Sie diese bzw. dieses aus der rechten Dropdownliste aus.

- Um den Fokus vom Codefenster zur Navigationsleiste zu verschieben, drücken Sie die Tastenkombination **STRG**+**F2**.

- Um den Fokus auf der Navigationsleiste von Feld zu Feld zu verschieben, drücken Sie die **TAB**-TASTE.

- Um das Element mit dem Fokus auf der Navigationsleiste auszuwählen und zum Codefenster zurückzukehren, drücken Sie die **EINGABETASTE**.

- Um den Fokus von der Navigationsleiste wieder zum Code zu verschieben, ohne eine Auswahl zu treffen, drücken Sie **ESC**.

Ändern Sie zum Ausblenden der Navigationsleiste in der Text-Editor-Einstellung **Alle Sprachen** die Option **Navigationsleiste** (**Extras** > **Optionen** > **Text-Editor** > **Alle Sprachen**), oder ändern Sie die Einstellungen für einzelne Sprachen.

## <a name="find-all-references"></a>Alle Verweise suchen

Sucht alle Verweise auf das ausgewählte Element in der Projektmappe. Sie können dies verwenden, um mögliche Nebenwirkungen eines umfangreichen Refactorings zu überprüfen oder um auf „toten“ Code zu prüfen. Drücken Sie **F8**, um zwischen den Ergebnissen zu wechseln. Weitere Informationen finden Sie unter [Suchen von Verweisen im Code](finding-references.md).

Eingabe        | Funktion
------------ | ---
**Tastatur** | Platzieren Sie den Textcursor an einer beliebigen Position innerhalb des Typnamens, und drücken Sie **UMSCHALT**+**F12**.
**Maus**    | Wählen Sie im Kontextmenü **Alle Verweise suchen** aus.

## <a name="reference-highlighting"></a>Markieren von Verweisen

Wenn Sie auf ein Symbol im Quellcode klicken, werden alle Instanzen dieses Symbols im Dokument hervorgehoben. Die markierten Symbole können Deklarationen und Verweise sowie weitere Symbole umfassen, die von **Alle Verweise suchen** zurückgegeben werden können. Dazu zählen die Namen von Klassen, Objekten, Variablen, Methoden und Eigenschaften. In Visual Basic-Code werden auch Schlüsselwörter für viele Steuerungsstrukturen hervorgehoben. Um zum nächsten oder vorherigen hervorgehobenen Symbol zu springen, drücken Sie **STRG**+**UMSCHALT**+**NACH-UNTEN-TASTE** bzw. **STRG**+**UMSCHALT**+**NACH-OBEN-TASTE**. Sie können die Hervorhebungsfarbe unter **Extras** > **Optionen** > **Umgebung** > **Schriftarten und Farben** > **Hervorgehobener Verweis** ändern.

## <a name="go-to-commands"></a>„Gehe zu“-Befehle

Es existieren folgende „Gehe zu“-Befehle, die im Menü **Bearbeiten** unter **Gehe zu** zur Verfügung stehen:

- **Gehe zu Zeile** (**STRG**+**G**): zur angegebenen Zeilennummer im aktiven Dokument wechseln.

- **Gehe zu allen** (**STRG**+**T** oder **STRG**+**,**): zur angegebenen Zeile oder Datei bzw. zum angegebenen Typ, Member oder Symbol wechseln.

- **Zu Datei wechseln** (**STRG**+**1**, **STRG**+**F**): zur angegebenen Datei in der Projektmappe wechseln.

- **Go To Recent File** (Gehe zur zuletzt bearbeiteten Datei) (**STRG**+**1**, **STRG**+**R**): zur angegebenen und zuletzt besuchten Datei in der Projektmappe wechseln (neu in Visual Studio 2017 Version 15.8).

- **Gehe zu Typ** (**STRG**+**1**, **STRG**+**T**): zum angegebenen Typ in der Projektmappe wechseln.

- **Zu Member navigieren** (**STRG**+**1**, **STRG**+**M**): zum angegebenen Member in der Projektmappe wechseln.

- **Gehe zu Symbol** (**STRG**+**1**, **STRG**+**S**): zum angegebenen Symbol in der Projektmappe wechseln.

In Visual Studio 2017 Version 15.8 und höher, sind die folgenden **Gehe zu**-Navigationsbefehle ebenfalls verfügbar:

- **Go To Next Issue in File** (Gehe zum nächsten Problem in Datei) (**ALT**+**PgDn**) und **Go To Previous Issue in File** (Gehe zum vorherigen Problem in Datei) (**ALT**+**PgUp**)

- **Zum Speicherort der letzten Bearbeitung wechseln** (**STRG**+**UMSCHALTTASTE**+**RÜCKTASTE**)

Weitere Informationen zu diesen Befehlen finden Sie im Abschnitt [Code mithilfe von „Gehe zu“-Befehlen finden](../ide/go-to.md).

## <a name="go-to-definition"></a>Gehe zu Definition

Mithilfe der „Gehe zu Definition“ gelangen Sie zur Definition des ausgewählten Elements. Weitere Informationen finden Sie unter [„Gehe zu Definition“ und „Definition einsehen“](../ide/go-to-and-peek-definition.md).

Eingabe        | Funktion
------------ | ---
**Tastatur** | Platzieren Sie den Textcursor an einer beliebigen Position innerhalb des Typnamens, und drücken Sie **F12**
**Maus**    | Klicken Sie mit der rechten Maustaste auf den Typnamen, und wählen Sie **Gehe zu Definition** aus, ODER drücken Sie **STRG**, und klicken Sie auf den Typnamen (neu in Visual Studio 2017, Version 15.4).

## <a name="peek-definition"></a>Peek-Definition

Mithilfe von „Peek-Definition“ wird die Definition des ausgewählten Elements in einem Fenster angezeigt, ohne dass Ihre aktuelle Position im Code-Editor verlassen wird. Weitere Informationen finden Sie unter [Vorgehensweise: Anzeigen und Bearbeiten von Code mithilfe von „Definition einsehen“](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md) und [Go To Definition and Peek Definition („Gehe zu Definition“ und „Definition einsehen“)](../ide/go-to-and-peek-definition.md).

Eingabe        | Funktion
------------ | ---
**Tastatur** | Platzieren Sie den Textcursor an einer beliebigen Position innerhalb des Typnamens, und drücken Sie **ALT**+**F12**.
**Maus**    | Klicken Sie mit der rechten Maustaste auf den Typnamen, und wählen Sie **Peek Definition** (Peek-Definition) aus, oder drücken Sie **STRG**, und klicken Sie auf den Typnamen, falls Sie die Option **Definition in der Vorschauansicht öffnen** aktiviert haben.

## <a name="go-to-implementation"></a>Gehe zu Implementierung

Mithilfe von „Zur Implementierung wechseln“ können Sie von einer Basisklasse oder einem Basistyp zu deren bzw. seinen Implementierungen navigieren. Wenn mehrere Implementierungen vorhanden sind, sind sie im Fenster **Ergebnisse der Symbolsuche** aufgelistet:

Eingabe        | Funktion
------------ | ---
**Tastatur** | Platzieren Sie den Textcursor an einer beliebigen Position innerhalb des Typnamens, und drücken Sie **STRG**+**F12**.
**Maus**    | Klicken Sie mit der rechten Maustaste auf den Typnamen, und wählen Sie **Gehe zu Implementierung** aus

## <a name="call-hierarchy"></a>Aufrufhierarchie

Sie können Aufrufe an und aus einer Methode im [Fenster „Aufrufhierarchie“](../ide/reference/call-hierarchy.md) anzeigen:

Eingabe        | Funktion
------------ | ---
**Tastatur** | Platzieren Sie den Textcursor an einer beliebigen Position innerhalb des Typnamens, und drücken Sie **STRG**+**K**, **STRG**+**T**.
**Maus**    | Klicken Sie mit der rechten Maustaste auf den Membernamen, und wählen Sie **Aufrufhierarchie anzeigen** aus.

## <a name="next-method-and-previous-method-commands-visual-basic"></a>„Nächste Methode“-Befehl und „Vorherige Methode“-Befehl (Visual Basic)

Verwenden Sie diese Befehle in Visual Basic-Codedateien, um die Einfügemarke zu den verschiedenen Methoden zu verschieben. Klicken Sie auf **Bearbeiten** > **Nächste Methode** oder **Bearbeiten** > **Vorherige Methode**.

## <a name="structure-visualizer"></a>Strukturschnellansicht

Die Funktion „Strukturschnellansicht“ im Code-Editor zeigt *Strukturführungslinien*: vertikal gestrichelte Linien, die passende geschweifte Klammern in Ihrer Codebasis indizieren. Dadurch können Sie leichter erkennen, wo logische Blöcke anfangen und aufhören.

![Strukturschnellansicht](../ide/media/vside_structure_visualizer.png)

Um die Struktur von Hilfslinien zu deaktivieren, wechseln Sie zu **Extras** > **Optionen** > **Text-Editor** > **Allgemein**, und deaktivieren Sie das Feld **Strukturführungslinien anzeigen**.

## <a name="enhanced-scroll-bar"></a>Verbesserte Bildlaufleiste

Sie können die erweiterte Bildlaufleiste im Codefenster verwenden, um den Code aus der Vogelperspektive zu betrachten. Im Zuordnungsmodus können Sie eine Codevorschau sehen, wenn Sie den Cursor auf der Bildlaufleiste nach oben und unten bewegen. Weitere Informationen finden Sie unter [Vorgehensweise: Verfolgen von Code durch Anpassen der Scrollleiste](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md).

## <a name="codelens-information"></a>CodeLens-Informationen

Sie können Informationen über bestimmten Code, wie Änderungen und wer diese Änderungen vorgenommen hat, Verweise, Fehler, Arbeitsaufgaben und Codeüberprüfungen sowie Komponententeststatus anzeigen, wenn Sie CodeLens im Code-Editor verwenden. CodeLens funktioniert wie ein Heads-up-Display, wenn Sie Visual Studio Enterprise mit Team Foundation Server verwenden. Weitere Informationen finden Sie unter [Ermitteln von Änderungen am Code und anderer Verläufe](../ide/find-code-changes-and-other-history-with-codelens.md).

## <a name="see-also"></a>Siehe auch

- [Features des Code-Editors](../ide/writing-code-in-the-code-and-text-editor.md)
- [Anzeigen der Aufrufhierarchie](../ide/reference/call-hierarchy.md)
