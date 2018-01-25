---
title: "Einführung in das Bearbeiten mit Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/30/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: quickstart
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs: CSharp
ms.workload: multiple
ms.openlocfilehash: 67927715cc88373040d1820f70faaf70198388c1
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2018
---
# <a name="quickstart-coding-in-the-editor"></a>Schnellstart: Codieren im Editor

In dieser Einführung in den Editor, die etwa zehn Minuten Ihrer Zeit in Anspruch nehmen wird, wird Code zu einer Datei hinzugefügt, um zu veranschaulichen, inwiefern Visual Studio das Schreiben, Navigieren und Verstehen von Code vereinfacht.

## <a name="create-a-new-code-file"></a>Erstellen einer neuen Codedatei

Beginnen Sie mit dem Erstellen einer neuen Datei, und fügen Sie dieser Code hinzu. Beachten Sie, dass es nicht nötig ist, ein Projekt zu erstellen, um von den Vorteilen des Editors profitieren zu können.

1. Öffnen Sie Visual Studio, und klicken Sie im Menü **Datei** in der Menüleiste auf **Neu** > **Datei...**.

1. Klicken Sie im Dialogfeld **Neue Datei** unter der Kategorie **Allgemein** auf die Option **Visual C#-Klasse**, und klicken Sie dann auf **Öffnen**.

   Im Editor öffnet sich eine neue Datei mit dem Skelett einer C#-Klasse.

## <a name="using-code-snippets"></a>Verwenden von Codeausschnitten

Visual Studio stellt nützliche Codeausschnitte bereit, die Sie verwenden können, um häufig verwendete Codeblöcke schnell und einfach zu generieren. Die [Codeausschnitte](../ide/code-snippets.md) sind für verschiedene Programmiersprachen verfügbar, einschließlich C#, Visual Basic und C++. Fügen Sie den C#-Ausschnitt `void Main` zu Ihrer Datei hinzu.

1. Platzieren Sie Ihren Cursor unter der schließenden geschweiften Klammer des `Class1`-Konstruktors, und geben Sie die Zeichen `svm` ein.

   Dann wird ein IntelliSense-Dialogfeld mit Informationen zum `svm`-Ausschnitt angezeigt.

   ![IntelliSense-Ausschnitt](media/quickstart-intellisense-snippet.png)

1. Drücken Sie zweimal auf die **TAB-TASTE**, um den Codeausschnitt einzufügen.

   Daraufhin wir die Methodensignatur `static void Main()` zu der Datei hinzugefügt. Die `Main()`-Methode ist der Einstiegspunkt für C#-Anwendungen.

Die verfügbaren Codeausschnitte unterscheiden sich von Sprache zu Sprache. Sie können sich die für Ihre Programmiersprache verfügbaren Codeausschnitte anzeigen lassen, indem Sie auf **Bearbeiten** > **IntelliSense** > **Ausschnitt einfügen** klicken und dann Ihren Sprachordner auswählen. Für C# sieht die Liste wie folgt aus:

![Liste der Codeausschnitte für C#](media/quickstart-code-snippet-list.png)

Die Liste beinhaltet u.a. Ausschnitte zum Erstellen einer Klasse, eines Konstruktors, von `Console.WriteLine()`, einer `for`-Schleife und von `if`- und `switch`-Anweisungen.

## <a name="commenting-out-code"></a>Auskommentieren von Code

In der Symbolleiste finden Sie einige Schaltflächen, die das Codieren produktiver machen. Beispielsweise können Sie den IntelliSense-Beendigungsmodus umschalten, Einzüge vergrößern oder verkleinern, ein Lesezeichen festlegen oder Code auskommentieren. In diesem Abschnitt wird ein Teil des Codes auskommentiert, der nicht kompiliert werden soll.

![Editor-Symbolleiste](media/quickstart-editor-toolbar.png)

1. Fügen Sie den folgenden Code in den Methodentext `Main()` ein.

    ```csharp
    // _words is a string array that we'll sort alphabetically
    string[] _words = {
        "the",
        "quick",
        "brown",
        "fox",
        "jumps"
    }

    string[] morewords = {
        "over",
        "the",
        "lazy",
        "dog"
    };

    IEnumerable<string> query = from word in _words
                                orderby word.Length
                                select word;
    ```

1. Die Variable `morewords` wird an dieser Stelle zwar nicht verwendet, allerdings sollte sie nicht gelöscht werden, weil sie unter Umständen später noch benötigt wird. Kommentieren Sie diese Zeilen stattdessen aus. Ordnen Sie die vollständige Definition von `morewords` dem Semikolon zu, dass zum Abschluss gesetzt wird, und klicken Sie dann in der Symbolleiste auf die Schaltfläche **Kommentiert die ausgewählten Textzeilen aus**, oder drücken Sie **STRG**+**K** > **STRG**+**C**.

   ![Auskommentieren der Schaltfläche](media/quickstart-comment-out.png)

   Die C#-Kommentarzeichen `//` werden am Anfang jeder ausgewählten Zeile hinzugefügt, um den Code auszukommentieren.

## <a name="collapsing-code-blocks"></a>Reduzieren von Codeblöcken

Es soll kein leerer Konstruktor für die generierte `Class1` angezeigt werden. Reduzieren Sie daher die Ansicht des Codes, damit unnötige Informationen ausgeblendet werden. Klicken Sie auf das kleine graue Feld mit dem Minuszeichen auf dem Rand neben der ersten Zeile des Konstruktors. Wenn Sie lieber mit der Tastatur arbeiten, platzieren Sie den Cursor auf einer beliebigen Stelle im Konstruktorcode, und drücken Sie zweimal **STRG**+**M**, **STRG**+**M**.

![Gliedern der Schaltfläche zum Reduzieren](media/quickstart-collapse.png)

Der Codeblock wird bis auf die erste Zeile reduziert, an die Auslassungspunkte angehängt werden (`...`). Klicken Sie nun auf dasselbe graue Feld, das diesmal mit einem Pluszeichen versehen ist, um den Codeblock erneut zu erweitern, oder drücken Sie zweimal **STRG**+**M**, **STRG**+**M**. Diese Funktion wird [Gliederung](../ide/outlining.md) genannt und ist besonders nützlich, wenn Sie lange Methoden oder ganze Klassen reduzieren möchten.

## <a name="viewing-symbol-definitions"></a>Anzeigen von Symboldefinitionen

Der Visual Studio-Editor erleichtert u.a. die Prüfung der Definition eines Typs oder einer Methode. Sie können z.B. zu der Datei navigieren, die die Definition enthält, indem Sie an einer beliebigen Stelle, an der auf das Symbol verwiesen wird, **Gehe zu Definition** auswählen. Sie können auch die Option [Definition einsehen](../ide/go-to-and-peek-definition.md#peek-definition) verwenden. Dies stellt eine schnellere Möglichkeit dar, bei der der Fokus weiterhin auf der Datei liegt. Im Folgenden wird die Definition von `string` dargestellt.

1. Klicken Sie mit der rechten Maustaste auf eine beliebige Darstellung von `string`, und klicken Sie im Inhaltsmenü auf **Definition einsehen**, oder drücken Sie auf **ALT**+**F12**.

   Daraufhin wird ein Popupfenster mit der Definition der `String`-Klasse angezeigt. Sie können in dem Popupfenster scrollen oder sogar die Definition eines anderen Typs des eingesehenen Codes einsehen.

   ![Fenster „Definition einsehen“](media/quickstart-peek-definition.png)

1. Schließen Sie das eingesehene Definitionsfenster, indem Sie auf das kleine „x“ in der oberen rechten Ecke des Popupfensters klicken.

## <a name="using-intellisense-to-complete-words"></a>Verwenden von IntelliSense zum vervollständigen von Wörtern

[IntelliSense](../ide/using-intellisense.md) ist eine wichtige Ressource beim Codieren. Damit erhalten Sie Informationen zu verfügbaren Members eines Typs oder Parameterdetails für verschiedene Überladungen einer Methode. Sie können IntelliSense auch verwenden, um Wörter zu vervollständigen, nachdem genug Zeichen eingegeben wurden, um sie eindeutig zu machen. Fügen Sie eine Codezeile hinzu, um die geordneten Zeichenfolgen im Konsolenfenster auszudrucken.

1. Beginnen Sie unter der Variable `query` mit dem Eingeben des folgenden Codes:

   ```csharp
   foreach (string str in qu
   ```

   Dann zeigt IntelliSense Ihnen **QuickInfo** zum `query`-Symbol an.

   ![Vervollständigen von Wörtern durch IntelliSense](media/quickstart-intellisense-completion-list.png)

1. Drücken Sie die **TAB-TASTE**, um den Rest des Worts `query` über die IntelliSense-Funktion „Wort vervollständigen“ einzufügen.

1. Vervollständigen Sie den Codeblock, sodass dieser wie der folgende Code aussieht. Sie können das Verwenden von Codeausschnitten noch einmal üben, indem Sie `cw` eingeben und dann zweimal die **TAB-TASTE** drücken, um den `Console.WriteLine`-Code zu generieren.

   ```csharp
   foreach (string str in query)
   {
      Console.WriteLine(str);
   }
   ```

## <a name="refactoring-a-name"></a>Umgestalten eines Namens

Niemandem gelingt das Codieren schon beim ersten Versuch. Es ist also sehr wahrscheinlich, dass Sie irgendwann den Namen einer Variablen oder Methode ändern möchten. Testen Sie die Funktion [Umgestalten](../ide/refactoring-in-visual-studio.md) von Visual Studio, um die `_words`-Variable in `words` umzubenennen.

1. Platzieren Sie den Cursor über der Definition der `words`-Variable, und klicken Sie im Kontextmenü (Rechtsklick) auf **Umbenennen...**, oder drücken Sie zweimal auf **STRG**+**R**, **STRG**+**R**.

   Daraufhin wird das Dialogfeld **Umbenennen** in der oberen rechten Ecke des Editors angezeigt.

1. Geben Sie den gewünschten `words`-Namen ein. Beachten Sie dabei, dass der Verweis auf `words` in der Abfrage ebenfalls automatisch umbenannt wird. Aktivieren Sie das Kontrollkästchen **Kommentare einbeziehen** im Dialogfeld **Umbenennen**, bevor Sie auf die **EINGABETASTE** drücken.

   ![Umbenennen (Dialogfeld)](media/quickstart-rename.png)

1. Drücken Sie die **EINGABETASTE**.

   Beide Instanzen von `words` sowie der Verweis auf `words` im Codekommentar wurden umbenannt.

## <a name="next-steps"></a>Nächste Schritte

Dieser Schnellstart für den Visual Studio-Editor wurde nun abgeschlossen. Wenn Sie einige der anderen Schnellstarts für die Visual Studio-IDE testen möchten, schauen Sie sich weitere Möglichkeiten zum [Navigieren im Code](../ide/navigating-code.md) an, oder prüfen Sie die Links zu Artikeln zu den hier vorgestellten Funktionen. Ansonsten wünschen wir Ihnen viel Spaß beim Codieren.

## <a name="see-also"></a>Siehe auch

[Schnellstart: ein erster Blick auf die Visual Studio-IDE](../ide/quickstart-ide-orientation.md)  
[Schnellstart: Personalisieren der Visual Studio-IDE und des Editors](../ide/quickstart-personalize-the-ide.md)  
[Schnellstart: Projekte und Projektmappen](../ide/quickstart-projects-solutions.md)  
[Codeausschnitte](../ide/code-snippets.md)  
[Gliedern](../ide/outlining.md)  
[„Gehe zu Definition“ und „Definition einsehen“](../ide/go-to-and-peek-definition.md)  
[Refactoring](../ide/refactoring-in-visual-studio.md)  
[Verwenden von IntelliSense](../ide/using-intellisense.md)