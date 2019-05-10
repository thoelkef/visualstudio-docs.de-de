---
title: Codeausschnitte
description: Informationen zur Verwendung von Codeausschnitten für ein effizientes Programmieren in Visual Studio für Mac
author: conceptdev
ms.author: crdun
ms.date: 02/07/2019
ms.assetid: 0FE27C0C-A861-4133-A74E-8D0505CF5342
ms.openlocfilehash: 56f736aa1e32530b1db96ad301091151731b7d28
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62540100"
---
# <a name="code-snippets"></a>Codeausschnitte

Codeausschnitte, die oft auch als  _Codevorlagen_ bezeichnet werden, sind für ein effizientes Programmieren sehr nützlich, da mit ihnen vorgeschriebene Codeblöcke eingefügt und bearbeitet werden können. Das Verwenden von Codeausschnitten ist praktisch, um gängige Muster schnell hinzuzufügen oder um neue Muster zu erlernen, falls Sie sich als Entwickler unsicher über die Syntax sind. Es werden Vorlagen für C#, F#, HTML, XML, Python und Razor bereitgestellt.

In diesem Abschnitt wird das Erstellen, Einfügen und Verwenden von Codeausschnitten erläutert.

## <a name="inserting-a-snippet"></a>Einfügen eines Ausschnitts

Es gibt verschiedene Möglichkeiten, Codeausschnitte hinzuzufügen, einige davon werden im Folgenden erläutert:

- **Befehlsergänzung mit der Tabulatortaste** &ndash; geben Sie zunächst den Namen der Vorlage ein. Wählen Sie ihn anschließend aus der Liste aus, und drücken Sie **TAB**, **TAB**, um ihn hinzuzufügen:

  ![Befehlsergänzung mit der Tabulatortaste im Code](media/source-editor-image13.png)

- **Toolbox** &ndash; verwenden Sie das Pad „Toolbox“, um eine Liste aller Codeausschnitte anzuzeigen. Ziehen Sie eine beliebige Vorlage aus der Toolbox an die richtige Stelle im Quellcode:

  [![Codeausschnitte in der Toolbox](media/source-editor-image14-sml.png)](media/source-editor-image14.png#lightbox)

- **Befehl „Vorlagen einfügen“** &ndash; derzeit ist keine standardmäßige Tastenbindung festgelegt, um eine Vorlage einzufügen. Navigieren Sie zum Erstellen einer Tastenbindung zu **Visual Studio > Einstellungen > Tastenbindungen**, und suchen Sie nach `template`. Dadurch können Sie die gewünschte Tastenbindung in das Feld „Bindung bearbeiten“ hinzufügen und anschließend auf  **Übernehmen** klicken:

  ![Befehl „Vorlagen einfügen“](media/source-editor-image15.png)

## <a name="creating-a-new-template"></a>Erstellen einer neuen Vorlage

Es gibt viele bestehende Vorlagen in einer Vielzahl von Sprachen, die Sie verwenden und bearbeiten können. Sie können jedoch auch neue Vorlagen hinzufügen, indem Sie zu **Visual Studio > Einstellungen > Text-Editor > Codeausschnitte** navigieren:

![Einfügen einer neuen Vorlage](media/source-editor-image12.png)

Drücken Sie die Schaltflächen **Hinzufügen** oder **Bearbeiten** zum Erstellen oder Bearbeiten von Codeausschnitten.

## <a name="keywords-in-code-snippets"></a>Schlüsselwörter in Codeausschnitten

Nachdem Sie einen Codeausschnitt in den Editor eingefügt haben, werden definierte Schlüsselwörter hervorgehoben, und Sie können sie bearbeiten, indem Sie mittels der TAB-Taste zwischen ihnen wechseln. Schlüsselwörter verhalten sich im Codeausschnitt wie „Variablen“ und werden definiert, indem Sie ein Dollarzeichen `$` vor und hinter dem Namen des Schlüsselworts platzieren. 

Das Fenster **Vorlage bearbeiten** ist unten mit der Bearbeitung des integrierten `prop`-Codeausschnitts dargestellt. Der Ausschnitt enthält zwei Schlüsselwörter &ndash; `$type$` und `$name$` &ndash; für die zusätzliche Eigenschaften (z.B. ein Standardwert und eine QuickInfo) auf der rechten Seite des Fensters festgelegt werden können:

![Fenster „Vorlage bearbeiten“](media/source-editor-image12z.png)

Die folgenden Felder werden verwendet, um einen Ausschnitt zu definieren:

- **Verknüpfung** &ndash; der Text, den der Benutzer eingibt, um den Ausschnitt einzufügen.
- **Gruppe** &ndash; Codeausschnitte werden mit diesem Wert im Codeausschnittinhalts-Menü gruppiert.
- **Beschreibung** &ndash; Erläuterung des Zwecks des Ausschnitts.
- **MIME** &ndash; steuert, in welchen Dateitypen der Ausschnitt verfügbar ist.
- **Ist erweiterbare Vorlage** &ndash; stellen Sie sicher, dass diese Option aktiviert ist, sodass der Codeausschnitt durch Eingabe der Verknüpfung an der Cursorposition eingefügt werden kann.
- **Ist mit einer Vorlage umschlossen** &ndash; aktivieren Sie diese Option, um diese Verknüpfung im Inhaltsmenü **Umschließen mit** im Editor aufzulisten.
- **Vorlagentext** &ndash; der tatsächliche Ausschnitt, der in den Editor eingefügt wird. Schlüsselwortplatzhalter können durch Umschließen eines Tokens mit dem Dollarzeichen definiert werden, z.B. `$type$`.
- **Schlüsselworteigenschaftenbereich** &ndash; wählen Sie auf der rechten Seite des Fensters in der Dropdownliste am oberen Rand ein Schlüsselwort aus (z.B. `type`), und bearbeiten Sie Eigenschaften wie Standardwert und QuickInfo.

## <a name="using-keywords-in-the-editor"></a>Verwenden von Schlüsselwörtern im Editor

Um einen Ausschnitt mit Schlüsselwörtern zu verwenden, wie z.B. die oben definierten, geben Sie die Verknüpfung ein, drücken Sie zweimal auf die **TAB**-Taste, und der Inhalt des Ausschnitts wird an der Cursorposition eingefügt:

![Eingefügter Ausschnitt mit Schlüsselwörtern](media/source-editor-image12a.png)

Drücken Sie die **TAB**-Taste zum Wechsel zwischen `object` und `MyProperty`, um den Codeausschnitt für Ihre Klasse anzupassen.

Ein Schlüsselwort kann in einem Ausschnitt wiederholt werden, wie etwa dieses `for`-Beispiel; beachten Sie, dass das `$i$`-Schlüsselwort 3-mal angezeigt wird:

![Ausschnittvorlage mit wiederholten Schlüsselwörtern](media/source-editor-image12b.png)

Im Editor schalten Sie mit der **TAB**-Taste zwischen dem ersten `i` und `max` um. Wenn Sie `i` mit einem anderen Variablennamen überschreiben, werden alle drei Instanzen aktualisiert:

![Eingefügter Ausschnitt mit mehreren Schlüsselwörtern](media/source-editor-image12c.png)

### <a name="reserved-keywords"></a>Reservierte Schlüsselwörter

Es gibt zwei reservierte Schlüsselwörter, die Sie in einem Ausschnitt verwenden können:

- `$selected$` &ndash; Wenn für den Codeausschnitt **Ist mit einer Vorlage umschlossen** aktiviert ist, wird dieses Schlüsselwort durch den Text ersetzt, der bei der Auswahl des Codeausschnitts im Editor markiert wurde.
- `$end$` &ndash; wenn der Benutzer die Bearbeitung der Schlüsselwörter in einem Ausschnitt abgeschlossen hat, wird der Cursor an der Position des `$end$`-Schlüsselworts platziert.

Der `for`-Ausschnitt im vorherigen Abschnitt ist ein Beispiel für diese beiden reservierten Schlüsselwörter.

Weitere Informationen finden Sie in der [Codeausschnittreferenz in Visual Studio](/visualstudio/ide/code-snippets-schema-reference#keywords).

## <a name="see-also"></a>Siehe auch

- [Codeausschnitte (Visual Studio unter Windows)](/visualstudio/ide/code-snippets)