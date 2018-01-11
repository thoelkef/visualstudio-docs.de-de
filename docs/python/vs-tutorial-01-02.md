---
title: Arbeiten mit Python in Visual Studio, Schritt 2 | Microsoft-Dokumentation
ms.custom: 
ms.date: 10/16/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: get-started-article
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload: python
ms.openlocfilehash: 964ed265f4e2587a1bef4812797987c47d52fa80
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="step-2-writing-and-running-code"></a>Schritt 2: Schreiben und Ausführen von Code

**Vorheriger Schritt: [Erstellen eines neuen Python-Objekts](vs-tutorial-01-01.md)**

Obwohl Projektdateien im Projektmappen-Explorer verwaltet werden, arbeiten Sie mit dem *Inhalt* der Dateien, z.B. mit dem Quellcode, in der Regel im *Editor*-Fenster. Der Editor erkennt kontextbezogen den Typ der Datei, die Sie bearbeiten, einschließlich der Programmiersprache (basierend auf der Dateierweiterung) und bietet für diese Sprache angemessene Funktionen, z.B. Syntaxfarben und automatische Vervollständigung mithilfe von IntelliSense.

1. Nach dem Erstellen eines neuen Projekts „Python-Anwendung“ wird eine standardmäßige leere Datei mit dem Namen `PythonApplication1.py` im Visual Studio-Editor geöffnet. 

1. Beginnen Sie im Editor, `print("Hello, Visual Studio")` einzugeben, und beachten Sie, wie Visual Studio IntelliSense nebenbei Optionen zur automatischen Vervollständigung anzeigt. Die in der Dropdownliste dargestellte Option ist die Standardvervollständigung, die verwendet wird, wenn Sie die TAB-Taste drücken. Vervollständigungen können bei längeren Anweisungen oder Bezeichnern sehr hilfreich sein.

    ![IntelliSense-Popupfenster für automatische Vervollständigung](media/vs-getting-started-python-04-IntelliSense1b.png)

1. IntelliSense zeigt je nach der Anweisung, die Sie verwenden, verschiedene Informationen an, die Funktion, die Sie aufrufen usw. Geben Sie mit der `print`-Funktion `(` nach `print` ein, um anzugeben, dass ein Funktionsaufruf die vollständigen Nutzungsinformationen für diese Funktion anzeigen soll. Das IntelliSense-Popup zeigt ebenfalls das aktuelle Argument in Fettdruck an (**value**, wie im Folgenden dargestellt):

    ![IntelliSense-Popupfenster für automatische Vervollständigung für eine Funktion](media/vs-getting-started-python-05-IntelliSense2b.png)

1. Vervollständigen Sie die Anweisung, damit sie der folgenden entspricht:

    ```python
    print("Hello, Visual Studio")
    ```

1. Beachten Sie die Syntaxfarben, die die `print`-Anweisung vom `"Hello Visual Studio"`-Argument unterscheiden. Löschen Sie vorübergehend das letzte `"`-Zeichen aus der Zeichenfolge, und Sie sehen, dass Visual Studio den Code rot unterstreicht, wenn Syntaxfehler enthalten sind. Fügen Sie das `"`-Zeichen wieder hinzu, um den Code zu korrigieren.

    ![Syntaxfarben und Hervorheben von Fehlern mit IntelliSense](media/vs-getting-started-python-06-IntelliSense3b.png)

    > [!Tip]
    > Da eine Entwicklungsumgebung eine sehr persönliche Angelegenheit ist, bietet Visual Studio Ihnen die vollständige Steuerung über das Aussehen und Verhalten von Visual Studio. Klicken Sie auf den Menübefehl **Extras > Optionen**, um die Einstellungen der Registerkarten **Umgebung** und **Text-Editor** zu untersuchen. Standardmäßig wird Ihnen eine begrenzte Anzahl von Optionen angezeigt. Klicken Sie auf **Alle Einstellungen anzeigen** am unteren Rand des Dialogfelds, um jede Option für alle Programmiersprachen anzuzeigen. 

1. Führen Sie den Code aus, den Sie bis zu diesem Zeitpunkt geschrieben haben, indem Sie STRG+F5 drücken oder auf das Menüelement **Debuggen > Starten ohne Debuggen** klicken. Visual Studio warnt Sie, wenn noch Fehler in Ihrem Code vorliegen.

1. Wenn Sie das Programm ausführen, wird ein Konsolenfenster angezeigt, das die Ergebnisse anzeigt, genau wie bei der Ausführung eines Python-Interpreters mit `PythonApplication1.py` über die Befehlszeile. Drücken Sie eine Taste, um das Fenster zu schließen und zum Visual Studio-Editor zurückzukehren.

    ![Ausgabe für die erste Ausführung des Programms](media/vs-getting-started-python-07-output.png)

1. Zusätzlich zu der Vervollständigung von Anweisungen und Funktionen bietet IntelliSense Vervollständigungen für `import`- und `from`-Anweisungen von Python. Diese Vervollständigungen unterstützen Sie bei der Ermittlung, welche Module in Ihrer Umgebung verfügbar sind und welche Members diese enthalten. Löschen Sie im Editor die `print`-Zeile, und geben Sie `import ` ein. Eine Liste von Modulen wird angezeigt, wenn Sie einen Leerraum eingeben:

    ![IntellSense zeigt verfügbare Module für eine Import-Anweisung an](media/vs-getting-started-python-08-import1.png)

1. Vervollständigen Sie die Zeile durch Eingabe oder Auswahl von `sys`.

1. Geben Sie in der nächsten Zeile `from` ein, um erneut eine Liste der Module zu sehen:

    ![IntellSense zeigt verfügbare Module für eine Anweisung an](media/vs-getting-started-python-09-import2.png)

1. Geben Sie `math` ein bzw. wählen Sie es aus, fahren Sie dann mit einem Leerzeichen und `import` fort, sodass die Modulmember angezeigt werden:

    ![IntellSense zeigt Modulmember an](media/vs-getting-started-python-10-import3.png)

1. Importieren Sie abschließend die Member `sin`, `cos` und `radians`, und beachten Sie die jeweilige automatische Vervollständigung. Wenn Sie fertig sind, sollte der Code wie folgt aussehen:

    ```python
    import sys
    from math import sin, cos, radians
    ```

    > [!Tip]
    > Vervollständigungen arbeiten während der Eingabe mit Teilzeichenfolgen, übereinstimmenden Teilen von Wörtern, Buchstaben am Anfang der Wörter und sogar übersprungenen Zeichen. Weitere Informationen finden Sie im Abschnitt [Vervollständigungen](code-editing.md#completions) im Artikel „Bearbeiten von Python-Code“.

1. Fügen Sie etwas mehr Code hinzu, um die Kosinuswerte für 360 Grad auszugeben:

    ```python 
    for i in range(360):
        print(cos(radians(i)))
    ```

1. Führen Sie das Programm erneut mit STRG+F5 oder über **Debuggen > Starten ohne Debuggen** aus. Schließen Sie das Ausgabefenster, wenn Sie fertig sind.

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Verwenden des interaktiven REPL-Fensters](vs-tutorial-01-03.md)

## <a name="going-deeper"></a>Vertiefung

- [Bearbeiten von Code](code-editing.md)
- [Formatieren von Code](code-formatting.md)
- [Refactoringcode](code-refactoring.md)
- [Verwenden von PyLint](code-pylint.md)
