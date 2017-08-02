---
title: "Bearbeiten von Code mit R Tools für Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 4/28/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a198ccc3-5506-48e7-b3b2-9399661b80d5
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
ms.openlocfilehash: e8b42484d471d4deac0eabcd4c55e09297d0873f
ms.contentlocale: de-de
ms.lasthandoff: 05/12/2017

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

Schauen Sie sich auch die Themen zu [IntelliSense](code-intellisense.md), [Codeausschnitten](code-snippets.md) und [R Markdown](rmarkdown.md) an.


## <a name="syntax-highlighting"></a>Syntaxhervorhebung 

Sie können mit RTVS Teile Ihres Codes (z.B. Zeichenfolgen, Kommentare und Schlüsselwörter) nicht nur farblich hervorheben, sondern auch Links in Kommentaren:

![Farben für Syntax für R-Code](~/docs/rtvs/media/editing-syntax-colors.png)

Um Schriftarten und bestimmte Hervorhebungsfarben anzupassen, klicken Sie auf den Befehl **Extras > Optionen**, navigieren Sie zu **Umgebung > Schriftarten und Farben**, und ändern Sie dort im Feld **Elemente anzeigen:** die Einstellungen für Elemente, die mit R-Code in Verbindung stehen:

![Optionen für Schriftarten und Farben für R-Code](~/docs/rtvs/media/editing-syntax-colors-options.png)

Außerdem unterstreicht Visual Studio Syntaxfehler im Editor:

![Hervorheben von Syntaxfehlern in R-Code](~/docs/rtvs/media/editing-syntax-error.png)

Um dieses Verhalten zu ändern, gehen Sie zur Einstellung **Erweitert > Syntaxüberprüfung** unter [Editor-Optionen](#editor-options).

## <a name="editing-and-organizing-code"></a>Bearbeiten und Organisieren von Code

Bei der Codeeingabe stellt RTVS die automatische Vervollständigung bereit, wie Sie auf der [IntelliSense](code-intellisense.md) nachlesen können. Außerdem nimmt es automatische Formatierungen vor, wie etwa das Schließen von Klammern: 

![Animation der Inlineformatierung](~/docs/rtvs/media/editing-inline-formatting.gif)

Wenn Sie Aufrufe von Funktionen eingeben, die über viele Parameter verfügen, sollten Sie die Parameter aufreihen, damit der Code leichter lesbar ist. RTVS erinnert sich an den Einzug Ihres Satzes von Parametern und wendet diesen Einzug auf alle folgenden Zeilen an:

![Animation des automatischer Einzugs](~/docs/rtvs/media/editing-auto-indentation.gif)

Um dieses Verhalten zu ändern, schauen Sie sich unten die [Editor-Optionen](#editor-options) für die Gruppe **Tabs** an.

Mit reduzierbaren Codebereichen können Sie Teile des Codes im Editor für eine gewisse Zeit ausblenden. Visual Studio erstellt automatisch verschiedene Bereiche für Sie, genauso wie für Anweisungen mit mehreren Zeilen, es sei denn, die Option **Erweitert > Gliederung > Codegliederung** ist deaktiviert.

Um selbst einen Bereich zu erstellen, umschließen Sie den gewünschte Code mit Kommentaren, die auf `---` enden. Mit den kleinen Steuerelementen „+/-“ links vom Code können Sie dann den Bereich erweitern bzw. reduzieren:

![Erstellen eines reduzierbaren Bereichs mithilfe von Kommentaren](~/docs/rtvs/media/editing-collapsible-regions.gif)
 
Visual Studio fügt standardmäßig Leerzeichen ein, wenn Sie die TAB-TASTE drücken. Wie Sie dieses Verhalten ändern, wird in [Options, Text Editor, Tabs (Optionen, Text-Editor, Registerkarten)](../ide/reference/options-text-editor-all-languages.md) beschrieben.

## <a name="code-navigation"></a>Codenavigation

Mit der Codenavigation können Sie schnell auf den Quellcode Ihres R-Programm und dessen Bibliotheken zugreifen. Durch diese Navigationsfunktionen wird Ihr Arbeitsfluss gewahrt, da er nicht durch das Suchen und manuelle Navigieren zum relevanten Code unterbrochen wird.

Die **Gehe zu Definition** springt schnell zu einer Funktionsdefinition oder öffnet einen kleinen Inline-Editor zum Lesen des Quellcodes einer Bibliotheksfunktion. Klicken Sie einfach mit der rechten Maustaste auf die relevante Funktion, und wählen Sie **Gehe zu Definition**, oder gehen Sie mit dem Cursor in die Funktion und drücken F12.

Dadurch wird ein neues Editor-Fenster geöffnet, das den Quellcode für die Funktion enthält. Außerdem befindet sich der Cursor praktischerweise am Anfang der Funktionsdefinition.

Die **Peek-Definition**, die über das Kontextmenü oder ALT+F12 aufgerufen werden kann, fügt einen schreibgeschützten, durchscrollbaren Bereich ein, der den Quellcode der Funktion unter dem Funktionsaufruf enthält:

![Animation für die Peek-Definition](~/docs/rtvs/media/editing-peek-definition.gif)

## <a name="sending-code-to-the-interactive-window"></a>Senden von Code an das interaktive Fenster

Viele Entwickler schreiben Code bevorzugt im Editor und senden diesen dann an das [interaktive Fenster](interactive-repl.md) zum sofortigen Testen (dies wird auch als „Lesen, Auswerten, Ausgeben“-Schleife oder REPL bezeichnet). Dies können Sie im R-Code-Editor über das Drücken der Tasten STRG+EINGABE für die aktuelle Codezeile durchführen, wonach der Cursor in die nächste Zeile gesetzt wird. Dann können Sie mit STRG+EINGABE effektiv aus dem Editor durch den Code navigieren.

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
 
Formatierungsoptionen (einschließlich des Deaktivierens des Formatierens) werden unter **Extras > Optionen** auf der Registerkarte **Text-Editor > Erweitert** festgelegt. Dahin gelangen Sie entweder direkt über den Befehl **R Tools > Editor-Optionen...**, oder indem Sie im Editor rechtsklicken und **Formatierungsoptionen** auswählen. Weitere Informationen finden Sie unten in den [Editor-Optionen](#editor-options).
 
## <a name="inserting-roxygen-comments"></a>Einfügen von Roxygen-Kommentaren

RTVS bietet eine Verknüpfung zum Generieren von [Roxygen](http://roxygen.org/)-Kommentaren mit den Parameternamen einer Funktion. Geben Sie einfach `###` in einer leeren Zeile oberhalb der Funktionsdefinition ein:

![Animation des Einfügens eines Roxygen-Kommentars](~/docs/rtvs/media/editing-roxygen-comments.gif)

## <a name="editor-options"></a>Editor-Optionen

Editor-spezifische Optionen werden über den Befehl **Extras > Optionen**, das Navigieren zu **Text-Editor > R** oder den Kurzbefehl **R Tools > Editor-Optionen...** festgelegt.

Optionen auf den Registerkarten **Allgemein**, **Scrollleisten** und **Registerkarten** sind nicht für R spezifisch, sondern sind recht allgemeine Einstellungen für Visual Studio, die in allen Sprachen verfügbar sind, und die pro Sprache angewendet werden. Einzelheiten dazu finden Sie in folgenden Themen:

- [Optionen, Text-Editor, Alle Sprachen](../ide/reference/options-text-editor-all-languages.md)
- [Verfolgen von Code durch Anpassen der Scrollleiste](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md)
- [Optionen, Text-Editor, Registerkarten](../ide/reference/options-text-editor-all-languages-tabs.md)

Optionen auf der Registerkarte **R > Erweitert** sind für RTVS spezifisch:

| Gruppieren | Option | Standard | Beschreibung |
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
| | Completion list on first character | Ein | Zeigt eine Vervollständigungsliste bei den ersten eingegebenen Zeichen. Wenn dies deaktiviert ist, wird eine Vervollständigungsliste mit **Bearbeiten > IntelliSense** angezeigt (STRG+J). |
| | Completion list on Tab key | Aus | Ruft eine Vervollständigungliste auf, wenn Sie ein oder mehrere Zeichen eingeben und dann auf die TAB-TASTE drücken |
| | Match partially types argument names | Aus | Wenn Sie in einem Funktionsaufruf Argumentnamen eingeben, zeigt die Signaturhilfe eine Beschreibung der Arguments an, dass am besten passt. |
| Interaktives Fenster | Syntax check in R Console | Aus | Wendet die Syntaxüberprüfung im interaktiven Fenster an Die Syntaxüberprüfung funktioniert bei Anweisungen mit mehreren Zeilen möglicherweise nicht ordnungsgemäß. | 
| Gliedern | Code outlining | Ein | Erstellt automatisch reduzierbare Codebereiche für Bereiche mit Anweisungen mit mehreren Zeilen | 
| Syntax check | Syntaxfehler anzeigen | Ein | Aktiviert die automatische Syntaxüberprüfung von Code |

