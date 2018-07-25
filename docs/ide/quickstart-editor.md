---
title: Einführung in das Bearbeiten mit Visual Studio
ms.date: 11/30/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: quickstart
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 265e0a4c596a78e53de6fe92d837796f2e52a703
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39079147"
---
# <a name="quickstart-use-the-code-editor"></a>Schnellstart: Verwenden des Code-Editors

In dieser Einführung in den Code-Editor von Visual Studio, die etwa zehn Minuten Ihrer Zeit in Anspruch nehmen wird, wird Code zu einer Datei hinzugefügt, um zu veranschaulichen, inwiefern Visual Studio das Schreiben, Navigieren und Verstehen von Code vereinfacht.

Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) kostenlos herunterladen.

Bei diesem Schnellstart wird davon ausgegangen, dass Sie bereits mit einer Programmiersprache vertraut sind. Sollte dies nicht der Fall sein, empfehlen wir Ihnen, sich zuerst einen der Schnellstarts zum Thema Programmierung anzusehen, beispielsweise zum Erstellen einer Web-App mit [Python](../ide/quickstart-python.md) oder [C#](../ide/tutorial-csharp-aspnet-core.md) oder zum Erstellen einer Konsolen-App mit [Visual Basic](../ide/quickstart-visual-basic-console.md) oder [C++](../ide/getting-started-with-cpp-in-visual-studio.md).

## <a name="create-a-new-code-file"></a>Erstellen einer neuen Codedatei

Beginnen Sie mit dem Erstellen einer neuen Datei, und fügen Sie dieser Code hinzu.

1. Öffnen Sie Visual Studio, und klicken Sie im Menü **Datei** in der Menüleiste auf **Neu** > **Datei**.

1. Klicken Sie im Dialogfeld **Neue Datei** unter der Kategorie **Allgemein** auf die Option **Visual C#-Klasse**, und klicken Sie dann auf **Öffnen**.

   Im Editor öffnet sich eine neue Datei mit dem Skelett einer C#-Klasse. (Beachten Sie, dass Sie kein vollständiges Visual Studio-Projekt erstellen müssen, um einen Nutzen aus dem Code-Editor zu ziehen; Sie benötigen lediglich eine Codedatei.)

   ![C#-Codedatei in Visual Studio](media/quickstart-editor.png)

## <a name="use-code-snippets"></a>Verwenden von Codeausschnitten

Visual Studio stellt nützliche *Codeausschnitte* bereit, die Sie verwenden können, um häufig verwendete Codeblöcke schnell und einfach zu generieren. Die [Codeausschnitte](../ide/code-snippets.md) sind für verschiedene Programmiersprachen verfügbar, einschließlich C#, Visual Basic und C++. Fügen Sie den C#-Ausschnitt `void Main` zu Ihrer Datei hinzu.

1. Platzieren Sie Ihren Cursor direkt oberhalb der letzten schließenden geschweiften Klammer **}** in der Datei, und geben Sie die Zeichen `svm` ein (dies steht für `static void Main`&mdash;machen Sie sich nicht allzu viele Sorgen, wenn Sie nicht wissen, was dies bedeutet).

   Ein Popup-Dialogfeld mit Informationen zum Codeausschnitt `svm` wird angezeigt.

   ![IntelliSense für Codeausschnitte in Visual Studio](media/quickstart-intellisense-snippet.png)

1. Drücken Sie zweimal auf die **TAB-TASTE**, um den Codeausschnitt einzufügen.

   Daraufhin wir die Methodensignatur `static void Main()` zu der Datei hinzugefügt. Die [Main()](/dotnet/csharp/programming-guide/main-and-command-args/)-Methode ist der Einstiegspunkt für C#-Anwendungen.

Die verfügbaren Codeausschnitte variieren je nach Programmiersprache. Sie können sich die für Ihre Sprache verfügbaren Codeausschnitte anzeigen lassen, indem Sie **Bearbeiten** > **IntelliSense** > **Ausschnitt einfügen** und anschließend den Ordner für Ihre Sprache auswählen. Für C# sieht die Liste wie folgt aus:

![Liste der Codeausschnitte für C#](media/quickstart-code-snippet-list.png)

Die Liste enthält u.a. Ausschnitte zum Erstellen einer [Klasse](/dotnet/csharp/programming-guide/classes-and-structs/classes), eines [Konstruktors](/dotnet/csharp/programming-guide/classes-and-structs/constructors), einer [for](/dotnet/csharp/language-reference/keywords/for)-Schleife und einer [if](/dotnet/csharp/language-reference/keywords/if-else)- oder [switch](/dotnet/csharp/language-reference/keywords/switch)-Anweisung.

## <a name="comment-out-code"></a>Auskommentieren von Code

Durch die Symbolleiste – der Zeile mit Schaltflächen unter der Menüleiste in Visual Studio – können Sie Ihre Produktivität beim Codieren steigern. Sie können beispielsweise den IntelliSense-Beendigungsmodus umschalten ([IntelliSense](using-intellisense.md) ist eine Codierungshilfe, die u.a. eine Liste von übereinstimmenden Methoden anzeigt), einen Zeileneinzug verkleinern oder vergrößern oder Code auskommentieren, der nicht kompiliert werden soll. In diesem Abschnitt wird Code auskommentiert.

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
    };

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

1. Die Variable `morewords` wird an dieser Stelle zwar nicht verwendet, allerdings sollte sie nicht vollständig gelöscht werden, weil sie unter Umständen später noch benötigt wird. Kommentieren Sie diese Zeilen stattdessen aus. Ordnen Sie die komplette Definition von `morewords` dem Semikolon zu, das zum Abschluss gesetzt wird, und klicken Sie anschließend in der Symbolleiste auf die Schaltfläche **Comment out the selected lines** (Ausgewählte Zeilen auskommentieren). Wenn Sie lieber die Tastatur verwenden möchten, drücken Sie **STRG**+**K**, **STRG**+**C**.

   ![Auskommentieren der Schaltfläche](media/quickstart-comment-out.png)

   Die C#-Kommentarzeichen `//` werden am Anfang jeder ausgewählten Zeile hinzugefügt, um den Code auszukommentieren.

## <a name="collapse-code-blocks"></a>Reduzieren von Codeblöcken

Es soll kein leerer [Konstruktor](/dotnet/csharp/programming-guide/classes-and-structs/constructors) für die generierte `Class1` angezeigt werden. Reduzieren Sie daher die Ansicht des Codes, damit unnötige Informationen ausgeblendet werden. Klicken Sie auf das kleine graue Feld mit dem Minuszeichen auf dem Rand neben der ersten Zeile des Konstruktors. Wenn Sie lieber mit der Tastatur arbeiten, platzieren Sie den Cursor an einer beliebigen Stelle im Konstruktorcode, und drücken Sie **STRG**+**M**, **STRG**+**M**.

![Gliedern der Schaltfläche zum Reduzieren](media/quickstart-collapse.png)

Der Codeblock wird bis auf die erste Zeile reduziert, an die Auslassungspunkte angehängt werden (`...`). Klicken Sie nun auf dasselbe graue Feld, das diesmal mit einem Pluszeichen versehen ist, um den Codeblock erneut zu erweitern, oder drücken Sie zweimal **STRG**+**M**, **STRG**+**M**. Dieses Feature wird als [Gliedern](../ide/outlining.md) bezeichnet und ist besonders nützlich, wenn Sie lange Methoden oder ganze Klassen reduzieren möchten.

## <a name="view-symbol-definitions"></a>Anzeigen von Symboldefinitionen

Der Visual Studio-Editor erleichtert u.a. die Prüfung der Definition eines Typs oder einer Methode. Sie können z.B. zu der Datei navigieren, die die Definition enthält, indem Sie an einer beliebigen Stelle, an der auf das Symbol verwiesen wird, **Gehe zu Definition** auswählen. Sie können auch die Option [Definition einsehen](../ide/go-to-and-peek-definition.md#peek-definition) verwenden. Dies stellt eine schnellere Möglichkeit dar, bei der der Fokus weiterhin auf der Datei liegt. Im Folgenden wird die Definition von Typ `string` dargestellt.

1. Klicken Sie mit der rechten Maustaste auf eine beliebige Darstellung von `string`, und wählen Sie im Inhaltsmenü die Option **Definition einsehen** aus. Drücken Sie alternativ **ALT**+**F12**.

   Daraufhin wird ein Popupfenster mit der Definition der `String`-Klasse angezeigt. Sie können in dem Popupfenster scrollen oder sogar die Definition eines anderen Typs des eingesehenen Codes einsehen.

   ![Fenster „Definition einsehen“](media/quickstart-peek-definition.png)

1. Schließen Sie das eingesehene Definitionsfenster, indem Sie auf das kleine „x“ in der oberen rechten Ecke des Popupfensters klicken.

## <a name="use-intellisense-to-complete-words"></a>Verwenden von IntelliSense zum Vervollständigen von Wörtern

[IntelliSense](../ide/using-intellisense.md) ist eine wichtige Ressource beim Codieren. Damit erhalten Sie Informationen zu verfügbaren Members eines Typs oder Parameterdetails für verschiedene Überladungen einer Methode. Sie können IntelliSense auch verwenden, um Wörter zu vervollständigen, nachdem genug Zeichen eingegeben wurden, um sie eindeutig zu machen. Fügen Sie eine einzige Codezeile hinzu, um die geordneten Zeichenfolgen im Konsolenfenster auszugeben. Dies ist der standardmäßige Ort für die Programmausgabe.

1. Beginnen Sie unter der Variable `query` mit dem Eingeben des folgenden Codes:

   ```csharp
   foreach (string str in qu
   ```

   Dann zeigt IntelliSense Ihnen **QuickInfo** zum `query`-Symbol an.

   ![IntelliSense-Wortvervollständigung in Visual Studio](media/quickstart-intellisense-completion-list.png)

1. Drücken Sie die **TAB-TASTE**, um den Rest des Worts `query` über die IntelliSense-Funktion zur Wortvervollständigung einzufügen.

1. Vervollständigen Sie den Codeblock, sodass dieser wie der folgende Code aussieht. Sie können das Verwenden von Codeausschnitten noch einmal üben, indem Sie `cw` eingeben und dann zweimal die **TAB-TASTE** drücken, um den `Console.WriteLine`-Code zu generieren.

   ```csharp
   foreach (string str in query)
   {
      Console.WriteLine(str);
   }
   ```

## <a name="refactor-a-name"></a>Refactoring eines Namens

Niemandem gelingt das Codieren schon beim ersten Versuch. Es ist also sehr wahrscheinlich, dass Sie irgendwann den Namen einer Variablen oder Methode ändern möchten. Testen Sie die Funktion [Refactoring](../ide/refactoring-in-visual-studio.md) von Visual Studio, um die `_words`-Variable in `words` umzubenennen.

1. Platzieren Sie den Cursor über der Definition der `_words`-Variable, und klicken Sie im Kontextmenü (Rechtsklick) auf **Umbenennen**, oder drücken Sie **STRG**+**R**, **STRG**+**R**.

   Daraufhin wird das Dialogfeld **Umbenennen** in der oberen rechten Ecke des Editors angezeigt.

1. Geben Sie den gewünschten Namen **Wörter** ein. Beachten Sie dabei, dass der Verweis auf `words` in der Abfrage ebenfalls automatisch umbenannt wird. Aktivieren Sie das Kontrollkästchen **Kommentare einbeziehen** im Dialogfeld **Umbenennen**, bevor Sie auf die **EINGABETASTE** drücken.

   ![Umbenennen (Dialogfeld)](media/quickstart-rename.png)

1. Drücken Sie die **EINGABETASTE**.

   Beide Instanzen von `words` sowie der Verweis auf `words` im Codekommentar wurden umbenannt.

## <a name="next-steps"></a>Nächste Schritte

Dieser Schnellstart für den Visual Studio-Editor wurde nun abgeschlossen. Als Nächstes können Sie einige der anderen Schnellstarts für die Visual Studio-Entwicklungsumgebung testen (z.B. [Schnellstart: Projekte und Projektmappen](../ide/quickstart-projects-solutions.md) oder [Schnellstart: Personalisieren von Visual Studio](../ide/quickstart-personalize-the-ide.md)), sich weitere Möglichkeiten zum [Navigieren durch Code](../ide/navigating-code.md) ansehen oder über die Links weitere Informationen zu den hier vorgestellten Features erhalten. Ansonsten wünschen wir Ihnen viel Spaß beim Codieren.

## <a name="see-also"></a>Siehe auch

- [Schnellstart: Ein erster Blick auf die Visual Studio-IDE](../ide/quickstart-ide-orientation.md)
- [Schnellstart: Personalisieren von Visual Studio](../ide/quickstart-personalize-the-ide.md)
- [Schnellstart: Projekte und Projektmappen](../ide/quickstart-projects-solutions.md)
- [Codeausschnitte](../ide/code-snippets.md)
- [Gliedern](../ide/outlining.md)
- [Go To Definition and Peek Definition („Gehe zu Definition“ und „Definition einsehen“)](../ide/go-to-and-peek-definition.md)
- [Refactoring](../ide/refactoring-in-visual-studio.md)
- [Verwendung von IntelliSense](../ide/using-intellisense.md)
