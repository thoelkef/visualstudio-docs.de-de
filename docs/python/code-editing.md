---
title: Bearbeiten von Python-Code in Visual Studio | Microsoft-Dokumentation
ms.custom: 
ms.date: 07/10/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 99859fc5b9e48078b037f6d68ad3d3847658a1d0
ms.sourcegitcommit: b7d3b90d0be597c9d01879338dd2678c881087ce
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/01/2017
---
# <a name="editing-python-code"></a>Bearbeiten von Python-Code

Entwickler verbringen einen Großteil Ihrer Zeit im Code-Editor, weshalb [die Python-Unterstützung in Visual Studio](installation.md) Funktionen bietet, die Ihre Produktivität erhöhen. Zu den Funktionen gehören die Syntaxhervorhebung von IntelliSense, die automatische Vervollständigung, Signaturhilfe, Methodenüberschreibungen, die Suche und die Navigation. 

In diesem Thema:

- [IntelliSense](#intellisense) einschließlich Vervollständigung, Signaturhilfe, QuickInfos und Codefarben.
- [Codeausschnitte](#code-snippets)
- [Navigieren im Code](#navigating-your-code)

Eine allgemeine Dokumentation zur Codebearbeitung in Visual Studio finden Sie unter [Schreiben von Code im Code- und Text-Editor](../ide/writing-code-in-the-code-and-text-editor.md). Lesen Sie auch den Artikel [Gliederung in Visual Studio](../ide/outlining.md) mit Informationen dazu, wie Sie Code ein- und ausblenden, um sich auf bestimmte Abschnitte Ihres Codes zu konzentrieren. Die Python-Unterstützung umfasst den Visual Studio-Objektkatalog (**Ansicht > Weitere Fenster > Objektkatalog** oder STRG+W, J), um die in den einzelnen Modulen definierten Klassen und die in diesen Klassen definierten Funktionen zu überprüfen. 

Der Editor ist darüber hinaus auch im interaktiven Fenster in Visual Studio integriert, sodass der Austausch von Code zwischen den beiden sehr leicht ist. Weitere Informationen finden Sie unter [Tutorial Step 3: Using the interactive REPL window (Tutorial Schritt 3: Verwenden des interaktiven REPL-Fensters)](vs-tutorial-01-03.md) und [Using the interactive window - Send code to interactive command (Verwenden des interaktiven Fensters: Befehl „An Interactive senden“)](interactive-repl.md#send-code-to-interactive-command).

Eine Einführung in die Bearbeitung von Python-Code finden Sie unter [Editing Python-Code (Bearbeiten von Python-Code)](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=r2iQH5LWE_4605918567) (Microsoft Virtual Academy, 2 Min. 30 Sek.):

> [!VIDEO https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Editing-Python-Code-r2iQH5LWE_4605918567]

## <a name="intellisense"></a>IntelliSense

IntelliSense bietet [Vervollständigung](#completions), [Signaturhilfe](#signature-help), [QuickInfos](#quick-info) und [Codefarben](#code-coloring). Zur Verbesserung der Leistung nutzt IntelliSense die Vervollständigungsdatenbank, die für jede Python-Umgebung in Ihrem Projekt generiert wird. Sie müssen Datenbanken möglicherweise aktualisieren, wenn Sie Pakete hinzufügen, entfernen oder aktualisieren. Der Status der Datenbank wird im Fenster **Python-Umgebungen** (dem Projektmappen-Explorer nebengeordnet) auf der Registerkarte **IntelliSense** angezeigt (siehe [Python-Umgebungen](python-environments.md)). 

### <a name="completions"></a>Vervollständigungen

Vervollständigungen werden für Anweisungen, Bezeichner oder andere Wörter angezeigt, die an der aktuellen Position im Editor eingegeben werden können. Die in der Liste angezeigten Elemente richten sich nach dem Kontext und werden gefiltert, um falsche oder störende Optionen auszulassen. Vervollständigungen werden häufig durch Eingabe verschiedener Anweisungen (z.B. `import`) und Operatoren (einschließlich eines Punkts) ausgelöst, Sie können sie jedoch jederzeit durch Drücken von STRG+J, LEERTASTE anzeigen.

![Membervervollständigung](media/code-editing-completions-simple.png)

Wenn eine Vervollständigungsliste geöffnet ist, können Sie mithilfe der Pfeiltasten, der Maus oder durch weitere Eingabe nach der gewünschten Vervollständigung suchen. Je mehr Buchstaben Sie eingeben, desto genauer wird die Liste gefiltert, um wahrscheinliche Vervollständigungen anzuzeigen. Ebenso können Sie diese Tastaturkombinationen verwenden:

- Eingeben von Buchstaben, die sich nicht am Anfang des gesuchten Begriffs befinden, z.B. „parse“ zum Suchen nach „argparse“
- Eingeben von Anfangsbuchstaben, z.B. „abc“ zum Suchen nach „AbstractBaseClass“ oder „air“ zum Suchen nach „as_integer_ratio“
- Auslassen von Buchstaben, z.B. „b64“ zum Suchen nach „base64“

Einige Beispiele:

![Membervervollständigung mit Filterung](media/code-editing-completion-filtering.png)

Membervervollständigungen werden automatisch angezeigt, wenn Sie nach einer Variable oder einem Wert einen Punkt zusammen mit dem Methoden und Attributen der möglichen Typen eingeben. Wenn eine Variable mehr als einen Typ aufweisen kann, enthält die Liste alle Möglichkeiten aller Typen und zeigt zusätzliche Informationen dazu an, welche Typen von der jeweiligen Vervollständigung unterstützt werden. Wenn eine Vervollständigung von allen möglichen Typen unterstützt wird, wird sie ohne Anmerkung angezeigt.

![Membervervollständigung in mehreren Typen](media/code-editing-completion-types.png)

Standardmäßig werden „dunder“-Member, die mit einem doppelten Unterstrich beginnen und enden, nicht angezeigt. Auf diese Member sollte grundsätzlich nicht direkt zugegriffen werden. Wenn Sie aber einen benötigen, können sie die doppelten Unterstriche vom Anfang eingeben, sodass diese Vervollständigungen der Liste hinzugefügt werden:

![Private Membervervollständigung](media/code-editing-completion-dunder.png)

Die Anweisungen `import` und `from ... import` zeigen eine Liste von Modulen an,die importiert werden können. Mit `from ... import` enthält die Liste Member, die aus dem angegebenen Modul importiert werden können.

![Importieren der Vervollständigung](media/code-editing-completion-import.png)

Die Anweisungen `raise` und `except` zeigen Listen mit Klassen an, bei denen es sich wahrscheinlich um Fehlertypen handelt. Diese umfasst möglicherweise nicht alle benutzerdefinierten Ausnahmen, hilft Ihnen aber dabei, schnell passende integrierte Ausnahmen zu finden:

![Ausnahmevervollständigung](media/code-editing-completion-exception.png)

Die Eingabe von @ startet einen Decorator und zeigt potenzielle Decorators an. Viele dieser Elemente können nicht als Decorator verwendet werden. Schauen Sie in der Dokumentation der Bibliothek nach, um zu ermitteln, welche Elemente Sie verwenden können:

![Decoratorvervollständigung](media/code-editing-completion-decorator.png)

> [!Tip]
> Über **Tools > Optionen > Text-Editor > Python > Erweitert** können Sie das Verhalten von Vervollständigungen konfigurieren. Einige Beispiele: **Liste basierend auf Suchzeichenfolge filtern** filtert die Vorschläge der Vervollständigung während der Eingabe (die Option ist standardmäßig aktiviert). **Membervervollständigung zeigt Schnittmenge der Member an** zeigt nur Vervollständigungen an, die von allen möglichen Typen unterstützt werden (die Option ist standardmäßig deaktiviert). Informationen finden Sie unter [Optionen: Vervollständigungsergebnisse](options.md#completion-results).

### <a name="signature-help"></a>Signaturhilfe

Wenn Sie Code schreiben, der eine Funktion aufruft, wird die Signaturhilfe angezeigt, sobald Sie die öffnende Klammer (`(`) eingeben. Die Signaturhilfe zeigt alle verfügbaren Informationen zu Dokumentation und Parametern an. Sie können die Signaturhilfe auch innerhalb eines Funktionsaufrufs mit STRG+UMSCHALT+LEERTASTE öffnen. Die angezeigten Informationen hängen von den Dokumentationszeichenfolgen im Quellcode der Funktion ab, enthalten aber alle Standardwerte.

![Signaturhilfe](media/code-editing-signature-help.png)

> [!Tip]
> Um die Signaturhilfe zu deaktivieren, wechseln Sie zu **Tools > Optionen > Text-Editor > Python > Allgemein**, und deaktivieren Sie die Option **Anweisungsvervollständigung > Parameterinformationen**.

### <a name="quick-info"></a>QuickInfo

Wenn Sie den Mauszeiger über einen Bezeichner bewegen, wird eine QuickInfo angezeigt. Je nach Bezeichner zeigt die QuickInfo die möglichen Werte oder Typen, die verfügbare Dokumentation, Rückgabetypen und Definitionsspeicherorte:

![QuickInfo](media/code-editing-quick-info.png)

### <a name="code-coloring"></a>Codefarben

Codefarben verwenden Informationen aus der Codeanalyse, um Variablen, Anweisungen und andere Teile Ihres Codes farbig hervorzuheben. Einige Beispiele: Variablen, die auf Module oder Klassen verweisen, werden in einer anderen Farbe angezeigt als Funktionen oder andere Werte. Parameternamen weisen eine andere Farbe auf als lokale oder globale Variablen: (Funktionen werden standardmäßig nicht fett hervorgehoben):

![Codefarben](media/code-editing-code-coloring.png)

Um die Farben anzupassen, wechseln Sie zu **Tools > Optionen > Umgebung > Schriftarten und Farben**, und bearbeiten Sie die Einträge für Python in der Liste **Elemente anzeigen**.

![Optionen für Schriftarten und Farben](media/code-editing-customize-colors.png)

> [!Tip]
> Um Codefarben zu deaktivieren, wechseln Sie zu **Tools > Optionen > Text-Editor > Python > Erweitert**, und deaktivieren Sie die Option **Verschiedene Optionen > Namen basierend auf Typ färben**. Informationen finden Sie unter [Optionen: Sonstige Optionen](options.md#miscellaneous-options).


## <a name="code-snippets"></a>Codeausschnitte

Codeausschnitte sind Codefragmente, die Sie durch Verwenden von Kurzeingaben und Drücken der TAB-TASTE in Ihre Dateien einfügen können. Alternativ dazu können Sie die Befehle **Bearbeiten > IntelliSense > Codeausschnitt einfügen** **Umschließen mit** verwenden. Wenn Sie z.B. `class` eingeben und dann die TAB-TASTE drücken, wird der Rest der Klasse generiert. Sie können in die Namens- und Basisliste schreiben, indem Sie mit der TAB-Taste zwischen den hervorgehobenen Feldern navigieren und dann die EINGABETASTE drücken, um mit dem Eingeben des Texts zu beginnen.

![Codeausschnitte](media/code-editing-code-snippets.png)

Sie können die verfügbaren Codeausschnitte im Codeausschnitt-Manager (**Tools > Codeausschnitt-Manager**) anzeigen, indem Sie **Python** als Sprache auswählen:

![Codeausschnitt-Manager](media/code-editing-code-snippets-manager.png)

Informationen zum Erstellen eigener Codeausschnitte finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines Codeausschnitts](../ide/walkthrough-creating-a-code-snippet.md). 

Wenn Sie einen Codeausschnitt geschrieben haben, den Sie gerne für andere Benutzer freigeben möchten, posten Sie ihn in einem Gist, und [informieren Sie uns darüber](https://github.com/Microsoft/PTVS/issues). Möglicherweise verwenden wir den Codeausschnitt in einer zukünftigen Version von Visual Studio.


## <a name="navigating-your-code"></a>Navigieren im Code

Die Python-Unterstützung in Visual Studio bietet verschiedene Möglichkeiten, schnell im Code zu navigieren, darunter Bibliotheken, für die Quellcode verfügbar ist: die [Navigationsleiste](#navigation-bar), [Gehe zu Definition](#go-to-definition), [Navigieren zu](#navigate-to) und [Alle Verweise suchen](#find-all-references). Sie können auch den [Objektkatalog](../ide/viewing-the-structure-of-code.md#BKMK_ObjectBrowser) von Visual Studio verwenden.

### <a name="navigation-bar"></a>Navigationsleiste

Die Navigationsleiste wird am oberen Rand jedes Editor-Fensters angezeigt und enthält eine Liste mit Definitionen auf zwei Ebenen. Die linke Dropdownliste enthält Klassen- und Funktionsdefinitionen auf oberster Ebene in der aktuellen Datei. Die rechte Dropdownliste zeigt eine Liste der Definitionen innerhalb des links gezeigten Geltungsbereichs. Wenn Sie sich im Editor bewegen, werden die Listen aktualisiert und zeigen den aktuellen Kontext an. Sie können auch einen Eintrag aus diesen Listen auswählen, um direkt an die entsprechende Stelle zu springen.

![Navigationsleiste](media/code-editing-navigation-bar.png)

> [!Tip]
> Um die Navigationsleiste auszublenden, wechseln Sie zu **Tools > Optionen > Text-Editor > Python > Allgemein**, und deaktivieren Sie die Option **Einstellungen > Navigationsleiste**.

### <a name="go-to-definition"></a>Gehe zu Definition

Mit **Gehe zu Definition** wechseln Sie schnell von einem Bezeichner (z.B. einem Funktionsnamen, einer Klasse oder einer Variablen) zu dem Quellcode, in dem dieser definiert ist. Um den Quellcode aufzurufen, klicken Sie mit der rechten Maustaste auf einen Bezeichner und wählen **Gehe zu Definition** aus, oder platzieren Sie den Textcursor in den Bezeichner und drücken F12. Dies funktioniert für Ihren gesamten Code und alle externen Bibliotheken, vorausgesetzt, der Quellcode ist verfügbar. Wenn der Quellcode der Bibliothek nicht verfügbar ist, springt **Gehe zu Definition** zur entsprechenden `import`-Anweisung für einen Modulverweis oder zeigt einen Fehler an.

![Gehe zu Definition](media/code-editing-go-to-definition.png)

### <a name="navigate-to"></a>Navigieren zu

Der Befehl **Bearbeiten > Navigieren zu...** (STRG-KOMMA) zeigt ein Suchfeld im Editor an, in das Sie eine beliebige Zeichenfolge eingeben und mögliche Übereinstimmungen in Ihrem Code anzeigen können, der eine Funktion, eine Klasse oder eine Variable definiert, die diese Zeichenfolge enthält. Diese Funktion bietet eine ähnliche Funktionalität wie **Gehe zu Definition**, ohne jedoch die Verwendung eines Bezeichners suchen zu müssen.

Indem Sie auf einen beliebigen Namen doppelklicken oder einen Namen mit den Pfeiltasten auswählen und die EINGABETASTE drücken, gelangen Sie zur Definition dieses Bezeichners.

![Navigieren zu](media/code-editing-navigate-to.png)

### <a name="find-all-references"></a>Alle Verweise suchen

**Alle Verweise suchen** ist eine nützliche Möglichkeit herauszufinden, wo ein bestimmter Bezeichner definiert und verwendet wird, einschließlich Importen und Zuweisungen. Um diese Funktionalität aufzurufen, klicken Sie mit der rechten Maustaste auf einen Bezeichner und wählen **Alle Verweise suchen** aus, oder platzieren Sie den Textcursor in den Bezeichner und drücken UMSCHALT+F12. Durch Doppelklicken auf ein Element in der Liste navigieren Sie zur entsprechenden Position.

![Ergebnisse von „Alle Verweise suchen“](media/code-editing-find-all-references.png)