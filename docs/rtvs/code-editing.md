---
title: "Bearbeiten von Code mit R Tools für Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 12/04/2017
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
ms.openlocfilehash: 013c32cb1567b3a4830a5c63059b14ea23df5427
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="editing-r-code-in-visual-studio"></a>Bearbeiten von R-Code in Visual Studio

R Tools für Visual Studio (RTVS) schneidet das Bearbeiten in Visual Studio speziell auf R zu, ohne dass Funktionen oder der Einsatz von Erweiterungen eingeschränkt werden. (Wenn Sie z.B. Vim-Schlüsselbindungen bevorzugen, können Sie die kostenlose [VsVim-Erweiterung](https://visualstudiogallery.msdn.microsoft.com/59ca71b3-a4a3-46ca-8fe1-0e90e3f79329) aus der Visual Studio Gallery herunterladen.)

In diesem Thema:

- [Syntaxhervorhebung](#syntax-highlighting)
- [Bearbeiten und Organisieren von Code](#editing-and-organizing-code)
- [Codenavigation](#code-navigation)
- [Senden von Code an das interaktive Fenster](#sending-code-to-the-interactive-window)
- [Formatieren von Code](#formatting-code)
- [Einfügen von Roxygen-Kommentaren](#inserting-roxygen-comments)
- [Editor-Optionen](#editor-options)

Sehen Sie sich auch die Themen zu [IntelliSense](code-intellisense.md), [Linting](code-linting.md), [Codeausschnitten](code-snippets.md) und [R Markdown](rmarkdown.md) an.

## <a name="syntax-highlighting"></a>Syntaxhervorhebung

Sie können mit RTVS Teile Ihres Codes (z.B. Zeichenfolgen, Kommentare und Schlüsselwörter) nicht nur farblich hervorheben, sondern auch Links in Kommentaren:

![Farben für Syntax für R-Code](media/editing-syntax-colors.png)

Um Schriftarten und bestimmte Hervorhebungsfarben anzupassen, klicken Sie auf den Befehl **Extras > Optionen**, navigieren Sie zu **Umgebung > Schriftarten und Farben**, und ändern Sie dort im Feld **Elemente anzeigen:** die Einstellungen für Elemente, die mit R-Code in Verbindung stehen:

![Optionen für Schriftarten und Farben für R-Code](media/editing-syntax-colors-options.png)

Außerdem unterstreicht Visual Studio Syntaxfehler im Editor:

![Hervorheben von Syntaxfehlern in R-Code](media/editing-syntax-error.png)

Um dieses Verhalten zu ändern, gehen Sie zur Einstellung **Erweitert > Syntaxüberprüfung** unter [Editor-Optionen](#editor-options).

## <a name="editing-and-organizing-code"></a>Bearbeiten und Organisieren von Code

Bei der Codeeingabe stellt RTVS die automatische Vervollständigung bereit, wie Sie auf der [IntelliSense](code-intellisense.md) nachlesen können. Außerdem nimmt es automatische Formatierungen vor, wie etwa das Schließen von Klammern: 

![Animation der Inlineformatierung](media/editing-inline-formatting.gif)

Wenn Sie Aufrufe von Funktionen eingeben, die über viele Parameter verfügen, sollten Sie die Parameter aufreihen, damit der Code leichter lesbar ist. RTVS erinnert sich an den Einzug Ihres Satzes von Parametern und wendet diesen Einzug auf alle folgenden Zeilen an:

![Animation des automatischer Einzugs](media/editing-auto-indentation.gif)

Um dieses Verhalten zu ändern, schauen Sie sich die [Editor-Optionen](#editor-options) für die Gruppe **Tabs** an.

Mit reduzierbaren Codebereichen können Sie Teile des Codes im Editor für eine gewisse Zeit ausblenden. Visual Studio erstellt automatisch verschiedene Bereiche für Sie, genauso wie für Anweisungen mit mehreren Zeilen, es sei denn, die Option **Erweitert > Gliederung > Codegliederung** ist deaktiviert.

Um selbst einen Bereich zu erstellen, umschließen Sie den gewünschte Code mit Kommentaren, die auf `---` enden. Mit den kleinen Steuerelementen „+/-“ links vom Code können Sie dann den Bereich erweitern bzw. reduzieren:

![Erstellen eines reduzierbaren Bereichs mithilfe von Kommentaren](media/editing-collapsible-regions.gif)

Visual Studio fügt standardmäßig Leerzeichen ein, wenn Sie die TAB-TASTE drücken. Wie Sie dieses Verhalten ändern, wird in [Options, Text Editor, Tabs (Optionen, Text-Editor, Registerkarten)](../ide/reference/options-text-editor-all-languages.md) beschrieben.

## <a name="code-navigation"></a>Codenavigation

Mit der Codenavigation können Sie schnell auf den Quellcode Ihres R-Programm und dessen Bibliotheken zugreifen. Diese Funktionen tragen dazu bei, dass Sie im Arbeitsfluss bleiben, ohne dass Sie Ihren Code manuell durchsuchen müssen.

Die **Gehe zu Definition** springt schnell zu einer Funktionsdefinition oder öffnet einen kleinen Inline-Editor zum Lesen des Quellcodes einer Bibliotheksfunktion. Klicken Sie einfach mit der rechten Maustaste auf die relevante Funktion, und wählen Sie **Gehe zu Definition**, oder gehen Sie mit dem Cursor in die Funktion und drücken F12.

Dieser Befehl öffnet ein neues Editor-Fenster, das den Quellcode für die Funktion enthält. Der Cursor ist praktischerweise direkt am Anfang der Funktionsdefinition platziert.

Die **Peek-Definition**, die über das Kontextmenü oder ALT+F12 aufgerufen werden kann, fügt einen schreibgeschützten, durchscrollbaren Bereich ein, der den Quellcode der Funktion unter dem Funktionsaufruf enthält:

![Animation für die Peek-Definition](media/editing-peek-definition.gif)

## <a name="sending-code-to-the-interactive-window"></a>Senden von Code an das interaktive Fenster

Viele Entwickler schreiben Code bevorzugt im Editor und senden diesen dann an das [interaktive Fenster](interactive-repl.md) zum sofortigen Testen (dies wird auch als „Lesen, Auswerten, Ausgeben“-Schleife oder REPL bezeichnet). Wenn Sie STRG + EINGABE im E-Editor drücken, wird die aktuelle Zeile an das interaktive Fenster gesendet, wonach der Cursor in die nächste Zeile gesetzt wird. Dann können Sie mit STRG+EINGABE effektiv aus dem Editor durch den Code navigieren.

Außerdem können Sie Code auswählen und STRG+EINGABE drücken, um den gesamten Abschnitt anzuwenden. Alternativ könne Sie auch mit der rechten Maustaste auf die Auswahl klicken und **In interaktivem Fenster ausführen** auswählen.

## <a name="formatting-code"></a>Formatieren von Code

Die automatische Formatierung von Visual Studio speichert den von Ihnen geschriebenen und von Ihnen im Editor eingefügten Code, und zwar so wie durch Ihre Einstellungen vorgegeben. Sie können auch etwas auswählen, rechtsklicken und dann **Auswahl formatieren** auswählen (STRG+K,F), um diese Einstellungen zu übernehmen. Wenn Sie z.B. eine Funktionsdefinition komplett in einer Zeile haben:

```R
f<-function  (a){  return(a + 1) }
```

Wenn Sie die Formatierung anwenden, wird es so bereinigt, dass es:

```R
f <- function(a) { return(a + 1) }
```

Um die gesamte Codedatei neu zu formatieren, wählen Sie **Bearbeiten > Erweitert > Dokument formatieren** (STRG+E, D).

Die automatische Formatierung ist ein anderer Vorgang, der rückgängig gemacht werden kann. Wenn Sie z.B. Code in den Editor einfügen und eine Formatierung anwenden, können Sie **Bearbeiten > Rückgängig machen** drücken oder STRG+Z einmal drücken, um die Formatierung rückgängig zu machen. Wenn Sie dann erneut auf „Rückgängig machen“ drücken, wird das Einfügen an sich aufgehoben.

Formatierungsoptionen (einschließlich der Deaktivierung der Formatierung) werden über **Extras > Optionen** auf der Registerkarte **Text-Editor > R > Erweitert** festgelegt. Sie können mit dem Befehl **R Tools > Editor-Optionen** direkt zu dieser Seite gehen. Alternativ können Sie auch im Editor rechtsklicken und auf **Formatierungsoptionen...** klicken. Weitere Informationen finden Sie im Abschnitt [Editor-Optionen](#editor-options).

## <a name="inserting-roxygen-comments"></a>Einfügen von Roxygen-Kommentaren

RTVS bietet eine Verknüpfung zum Generieren von [Roxygen](http://roxygen.org/)-Kommentaren mit den Parameternamen einer Funktion. Geben Sie einfach `###` in einer leeren Zeile oberhalb der Funktionsdefinition ein:

![Animation des Einfügens eines Roxygen-Kommentars](media/editing-roxygen-comments.gif)

## <a name="editor-options"></a>Editor-Optionen

Editor-spezifische Optionen werden über den Befehl **Extras > Optionen**, das Navigieren zu **Text-Editor > R** oder den Kurzbefehl **R Tools > Editor-Optionen...** festgelegt.

Optionen auf den Registerkarten **Allgemein**, **Scrollleisten** und **Registerkarten** sind nicht für R spezifisch, sondern sind recht allgemeine Einstellungen für Visual Studio, die in allen Sprachen verfügbar sind, und die pro Sprache angewendet werden. Einzelheiten dazu finden Sie in folgenden Themen:

- [Optionen, Text-Editor, Alle Sprachen](../ide/reference/options-text-editor-all-languages.md)
- [Verfolgen von Code durch Anpassen der Scrollleiste](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md)
- [Optionen, Text-Editor, Registerkarten](../ide/reference/options-text-editor-all-languages-tabs.md)

Optionen auf der Registerkarte **R > Erweitert** sind für RTVS spezifisch:

| Gruppieren | Option | Standard | description |
| --- | --- | --- | --- |
| Formatierung | Automatische Formatierung | Ein | Formatiert Code während der Eingabe neu. Wirkt sich nicht auf die Befehle **Auswahl formatieren** oder **Dokument formatieren** aus. |
| | Expanded braces | Aus | Platziert eine öffnende { in eine neue Zeile |
| | Beim Einfügen formatieren | Ein | Wendet die Formatierung beim Einfügen an |
| | Format scope on } | Ein | Formatiert den Bereich, nachdem eine schließende } eingegeben wurde |
| | Space after comma | Ein | Platziert ein Leerzeichen hinter Kommas |
| | Space after keyword | Ein | Platziert ein Leerzeichen hinter Schlüsselwörter wie `if`, `while` und `repeat` |
| | Space before { | Ein | Platziert ein Leerzeichen vor eine öffnende { |
| | Spaces around = | Ein | Platziert Leerzeichen vor und hinter einem Gleichzeichen |
| IntelliSense | Commit on Enter key | Aus | Übernimmt die Auswahl der automatischen Vervollständigung, wenn EINGABE gedrückt wird |
| | Commit on Space key | Aus | Übernimmt die Auswahl der automatischen Vervollständigung, wenn die LEERTASTE gedrückt wird|
| | Vervollständigungsliste beim ersten Zeichen | Ein | Zeigt eine Vervollständigungsliste bei den ersten eingegebenen Zeichen. Wenn dies deaktiviert ist, wird eine Vervollständigungsliste mit **Bearbeiten > IntelliSense** angezeigt (STRG+J). |
| | Vervollständigungliste beim Drücken der TAV-TASTE | Aus | Ruft eine Vervollständigungliste auf, wenn Sie ein oder mehrere Zeichen eingeben und dann auf die TAB-TASTE drücken |
| | Match gibt den Argumentnamen teilweise ein | Aus | Wenn Sie in einem Funktionsaufruf Argumentnamen eingeben, zeigt die Signaturhilfe eine Beschreibung der Arguments an, dass am besten passt. |
| Interaktives Fenster | Syntax-Prüfung in der R-Konsole | Aus | Wendet die Syntaxüberprüfung im interaktiven Fenster an Die Syntaxüberprüfung funktioniert bei Anweisungen mit mehreren Zeilen möglicherweise nicht ordnungsgemäß. | 
| Gliedern | Code outlining | Ein | Erstellt automatisch reduzierbare Codebereiche für Bereiche mit Anweisungen mit mehreren Zeilen |
| Syntax check | Syntaxfehler anzeigen | Ein | Aktiviert die automatische Syntaxüberprüfung von Code |
