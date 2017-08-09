---
title: Einstieg in die Arbeit mit Python in Visual Studio | Microsoft-Dokumentation
ms.custom: 
ms.date: 7/13/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: get-started-article
ms.assetid: a9087b19-275b-4cc1-8d0c-f9c4356c9ce8
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6d25db4639f2c8391c1e32542701ea359f560178
ms.openlocfilehash: 6dbf4f2bfabbfe5dc780eb4e973c6fae7ca6b1d9
ms.contentlocale: de-de
ms.lasthandoff: 07/18/2017

---

# <a name="getting-started-with-python-in-visual-studio"></a>Erste Schritte mit Python in Visual Studio

Sobald Sie Visual Studio mit der Python-Arbeitsauslastung (Visual Studio 2017) oder mit den Python-Tools für Visual Studio (Visual Studio 2015 und früher) installiert haben, können Sie die Python-Entwicklungsumgebung erforschen. (Siehe bei Bedarf [Installation](installation.md).)

Diese exemplarischen Vorgehensweise führt Sie durch die Erstellung einer neuen, leeren Python-Anwendung, das Auswählen einer Python-Umgebung, mit der sie arbeiten möchten und das Schreiben von Code, um IntelliSense in der Praxis zu sehen. Sie arbeiten dann für kurze Zeit mit dem interaktiven REPL-Fenster, um mehr Code zu erstellen, schließen dann das Programm ab und führen es sowohl eigenständig als auch im Debugger aus.

> [!Note]
> Diese exemplarische Vorgehensweise behandelt die Python-Benutzeroberfläche in Visual Studio 2017; andere Versionen sind ähnlich, können sich jedoch in den Details unterscheiden.

## <a name="create-a-new-python-project"></a>Erstellen eines neuen Python-Projekts

Die Python-Unterstützung in Visual Studio umfasst eine Reihe von [Projektvorlagen](python-projects.md) für Ihren Einstieg in verschiedene Arten von Projekten, einschließlich Webanwendungen, unter Verwendung der Bottle-, Flask- und Django-Frameworks zusammen mit Azure Cloud Services. Im Rahmen dieser exemplarischen Vorgehensweise beginnen wir jedoch mit einem leeren Projekt.

1. Wählen Sie in Visual Studio **Datei > Neues Projekt**, womit das Dialogfeld **Neues Projekt** geöffnet wird. Hier können Sie eine Vorlage suchen und auswählen und den Ordner angeben, in dem das Projekt erstellt werden soll.

1. Python-Vorlagen finden Sie auf der linken Seite unter **Vorlagen > Andere Sprachen > Python**, oder indem Sie nach „Python“ suchen:

    ![Dialogfeld „Neues Projekt“ mit Python-Projekten](media/getting-started-new-project.png)

1. Wählen Sie die Vorlage „Python-Anwendung“, geben Sie einen Ordner für das Projekt an, und wählen Sie **OK**. (Wenn Sie sofort ein lokales Repository für das Projekt erstellen möchten, wählen Sie auch die Option **Zur Quellcodeverwaltung hinzufügen**).

    > [!Tip]
    > Mit der Vorlage „From exiting Python Code“ können Sie schnell aus einem Ordner ein Visual Studio-Projekt erstellen, das bereits Python-Code enthält, anstatt ein neues leeres Projekt zu erstellen und vorhandenen Code dahin zu importieren.

1. Nach einigen Augenblicken wird das Projekt im Projektmappen-Explorer-Fenster von Visual Studio geöffnet. Hier können Sie die Dateien und Ordner in Ihrem Projekt durchsuchen sowie Umgebungen verwalten.

    ![Projektmappen-Explorer mit einem Python-Projekt](media/getting-started-solution-explorer-1.png)

1. Erweitern Sie den Knoten **Python-Umgebungen**, und sehen Sie, welcher Python-Interpreter der aktuelle Standard für dieses Projekt ist. Wenn Sie auch den Interpreterknoten erweitern, wird eine Liste der Bibliotheken angezeigt, die in der Umgebung zur Verfügung stehen:

    ![Projektmappen-Explorer mit der Python-Umgebung](media/getting-started-solution-explorer-2.png)

1. Wenn Sie Visual Studio 2015 oder früher verwenden, haben Sie standardmäßig keinen Python-Interpreter installiert. Informationen zu diesem Prozess finden Sie unter [Selecting and installing Python interpreters](python-environments.md#selecting-and-installing-python-interpreters) (Auswählen und Installieren von Python-Interpretern).

### <a name="going-deeper"></a>Vertiefung

- [Python-Projekte in Visual Studio](python-projects.md)
- [Webprojektvorlagen](template-web.md)
- [Django-Webprojektvorlage](template-django.md)
- [Vorlage des Azure Cloud-Diensts](template-azure-cloud-service.md)

## <a name="writing-and-running-code"></a>Schreiben und Ausführen von Code

1. Nach dem Erstellen eines neuen Projekts „Python-Anwendung“ wird eine standardmäßige leere Datei mit dem Namen `PythonApplication1.py` im Visual Studio-Editor geöffnet. Um diese umzubenennen, klicken Sie mit der rechten Maustaste im Projektmappen-Explorer auf die Datei, wählen Sie **Umbenennen**, und ändern Sie den Namen in `hello.py`.

1. Beginnen Sie, `print("Hello world")` einzugeben, und beachten Sie, wie Visual Studio IntelliSense nebenbei Optionen zur automatischen Vervollständigung anzeigt. Die in der Dropdownliste dargestellte Option ist die Standardvervollständigung, die verwendet wird, wenn Sie die TAB-Taste drücken. Vervollständigungen können bei längeren Anweisungen oder Bezeichnern sehr hilfreich sein.

    ![IntelliSense-Popupfenster für automatische Vervollständigung](media/getting-started-coding-1.png)

1. IntelliSense zeigt je nach der Anweisung, die Sie verwenden, verschiedene Informationen an, die Funktion, die Sie aufrufen usw. Bei der `print`-Funktion werden bei Eingabe von `(` für den Aufruf vollständige Nutzungsinformationen für diese Funktion angezeigt, und das aktuelle Argument, das Sie bereitstellen müssen, wird in Fettdruck dargestellt (**Wert** wie hier gezeigt):

    ![IntelliSense-Popupfenster für automatische Vervollständigung für eine Funktion](media/getting-started-coding-2.png)

1. Vervollständigen Sie die Anweisung, damit sie der folgenden entspricht:

  ```python
  print("Hello world")
  ```

1. Um den Code auszuführen, drücken Sie F5, oder wählen Sie das Menüelement **Debuggen > Debuggen starten**.

    > [!Note]
    > Wenn in Visual Studio 2015 oder früher die Meldung angezeigt wird, dass keine Interpreter vorhanden sind, informieren Sie sich unter [Selecting and installing Python interpreters](python-environments.md#selecting-and-installing-python-interpreters) (Auswählen und Installieren von Python-Interpretern), da standardmäßig kein Interpreter installiert ist.

1. Visual Studio führt den Code mithilfe der Standardumgebung im Projekt aus und zeigt die Ergebnisse in einem Befehlsfenster an. Drücken Sie eine Taste, um das Fenster zu schließen und die Debugsitzung beenden.

    ![Schaltfläche „Start“ auf der Debugsymbolleiste](media/getting-started-coding-4.png)

1. Zusätzlich zu Anweisungen und Funktionen bietet IntelliSense Vervollständigungen für `import`-Anweisungen. Durch importierte Vervollständigungen können Sie leicht erkennen, welche Module in Ihrer Umgebung und welche Elemente in diesen Modulen verfügbar sind. Löschen Sie im Editor die `print`-Zeile, und geben Sie `import` ein. Eine Liste von Modulen wird angezeigt:

    ![IntellSense zeigt verfügbare Module für eine Import-Anweisung an](media/getting-started-coding-5.png)

1. Vervollständigen Sie die Zeile durch Eingabe oder Auswahl von `sys`.

1. Geben Sie in der nächsten Zeile `from` ein, um erneut eine Liste der Module zu sehen:

    ![IntellSense zeigt verfügbare Module für eine Anweisung an](media/getting-started-coding-6.png)

1. Geben Sie `math` ein bzw. wählen Sie es aus, fahren Sie dann mit einem Leerzeichen und `import` fort, sodass die Modulmember angezeigt werden:

    ![IntellSense zeigt Modulmember an](media/getting-started-coding-7.png)

1. Importieren Sie abschließend die Member `sin`, `cos` und `radians`, und beachten Sie die jeweilige automatische Vervollständigung. Wenn Sie fertig sind, sollte der Code wie folgt aussehen:

  ```python
  import sys  
  from math import sin, cos, radians          
  ```

> [!Tip]
> Vervollständigungen arbeiten während der Eingabe mit Teilzeichenfolgen, übereinstimmenden Teilen von Wörtern, Buchstaben am Anfang der Wörter und sogar übersprungenen Zeichen. Näheres finden Sie unter [Completions](code-editing.md#completions) (Vervollständigungen).

Im nächsten Schritt arbeiten wir mit dem interaktiven REPL-Fenster, um Code zu schreiben, den wir sofort ohne Debugger testen können.

### <a name="going-deeper"></a>Vertiefung

- [Bearbeiten von Code](code-editing.md)
- [Formatieren von Code](code-formatting.md)
- [Umgestalten von Code](code-refactoring.md)
- [Verwenden von PyLint](code-pylint.md)


## <a name="using-the-interactive-repl-window"></a>Verwenden des interaktiven REPL-Fensters

Das interaktive Visual Studio-Fenster für Python bietet eine komfortable „Lesen-Auswerten-Ausgeben“ (REPL)-Schleife, die den üblichen „Bearbeiten-Erstellen-Debuggen“-Zyklus erheblich verkürzt. Es ähnelt der REPL-Umgebung der Python-Befehlszeile, bietet aber einige zusätzliche Funktionen, wie hier gezeigt wird.

1. Öffnen Sie das interaktive Fenster durch Auswahl von **Ansicht > Weitere Fenster > Interaktive Python-Fenster** im Hauptmenü von Visual Studio. Das Fenster wird mit der üblichen Python-REPL-Eingabeaufforderung >>> geöffnet. Beachten Sie, dass Sie die Umgebung im Dropdownmenü auf der Symbolleiste jederzeit ändern können:

    ![Interaktives Python-Fenster](media/getting-started-interactive-1.png)

1. Geben Sie einige Anweisungen (z.B. `print("hello")`) und Ausdrücke (z.B. `123/567`) ein, um sofortige Ergebnisse anzuzeigen:

    ![Sofortige Ergebnisse im interaktiven Python-Fenster](media/getting-started-interactive-2.png)

1. Beim Schreiben einer mehrzeiligen Anweisung, wie einer Funktionsdefinition, wird im interaktiven Fenster die Eingabeaufforderung ... zum Fortsetzen der Zeilen angezeigt, die im Gegensatz zum Befehlszeilen-REPL automatischen Einzug bietet:

    ![Interaktives Python-Fenster mit Anweisungsfortsetzung](media/getting-started-interactive-3.png)

1. Das interaktive Fenster enthält einen vollständigen Verlauf aller Elemente, die Sie eingegeben haben, und verbessert das Befehlszeilen-REPL mit mehrzeiligen Verlaufselementen. Beispielsweise können Sie einfach die vollständige Definition der `f`-Funktion oben als einzelne Einheit zurückrufen und den Namen mühelos in `make_double` ändern, anstatt die Funktion Zeile für Zeile neu erstellen zu müssen.

1. Ein weiteres hilfreiches Feature ist die Möglichkeit, schnell mehrere Codezeilen aus einem Editorfenster an das interaktive Fenster zu senden, wo Sie sie in der schnellen REPL-Umgebung bearbeiten können, statt anderen Code zur Ausführung im Debugger zu schreiben. Um diese Features zu sehen, fügen Sie den folgenden Code Ihrer Datei „hello.py“ hinzu, die im Editor geöffnet ist:

  ```python
  def make_dot_string(x):  
      return ' ' * int(10 * cos(radians(x)) + 10) + 'o'
  ```

1. Wählen Sie den gesamten Code in „hello.py“ (einschließlich der `import`-Anweisungen) aus, klicken Sie mit der rechten Maustaste, und wählen Sie **An Interactive senden** (STRG+EINGABETASTE). Der Code wird direkt in das interaktive Fenster eingefügt und ausgeführt. Da der Code eine Funktion definiert, können Sie diese Funktion schnell testen, indem Sie sie mehrmals aufrufen:

    ![Senden von Code an das interaktive Fenster](media/getting-started-interactive-4.png)

1. Das Verwenden von STRG+EINGABETASTE mit dem Caretzeichen in einer einzelnen Zeile des Editors ist ebenfalls ein einfacher Weg, um Ihren Code schrittweise zu durchlaufen. STRG+EINGABETASTE führt die aktuelle Zeile in einem interaktiven Fenster aus und legt das Caretzeichen dann automatisch auf die nächste Zeile fest. Durch wiederholtes Drücken von STRG+EINGABETASTE können Sie den gesamten Code einer Datei ausführen.

1. In Visual Studio 2017 können Sie mehrere Zeilen direkt in das interaktive Fenster einfügen (in vorherigen Versionen müssen Sie diese Zeilen in ein Editor-Fenster einfügen, alle auswählen und anschließend den Befehl **Send to Interactive** (An Interactive senden) verwenden. Nach dem Einfügen führt das interaktive Fenster diesen Code aus, wie Sie im Folgenden sehen können:

  ```python
  for i in range(360):
      s = make_dot_string(i)  
      print(s) 
  ```

    ![Einfügen von mehrere Codezeilen mit „An Interactive senden“](media/getting-started-interactive-5.png)

1. Da die Definition der Funktion sich als einzelne Einheit im REPL-Verlauf befindet, können Sie einfach zurückzugehen, beliebige Änderungen vornehmen und die Funktion erneut testen.

1. Wenn Sie mit dem Code, den Sie im interaktiven Fenster geschrieben haben, zufrieden sind, können Sie ihn auswählen, mit der rechten Maustaste darauf klicken, **Code kopieren** wählen und ihn dann in den Editor einfügen. Der Befehl **Code kopieren** lässt automatisch sowohl beliebige Ausgaben als auch den Aufforderungstext >>> und ... aus. Wenn Sie den Befehl z.B. mit der unten gezeigten Auswahl verwenden:

  ![Interaktives Fenster mit dem Befehl „Code kopieren“](media/getting-started-interactive-6.png)

  Nur Folgendes wird eingefügt:

  ```python
  make_dot_string(180)
  make_dot_string(135)
  for i in range(360):
      s = make_dot_string(i)  
      print(s) 
  ```

1. Schließlich enthält das interaktive Fenster eine Reihe von Metabefehlen, um Dateien zu laden, die Umgebung ohne Verlust des Verlaufs zurückzusetzen und im Verlauf Ihrer Arbeit Kommentare einzufügen. Nähere Informationen finden Sie unter [Working with the Python Interactive Window](interactive-repl.md#meta-commands) (Arbeiten mit dem interaktiven Python-Fenster).

### <a name="going-deeper"></a>Vertiefung

- [Working with the Python Interactive Window](interactive-repl.md) (Arbeiten mit dem interaktiven Python-Fenster)
- [Verwenden von IPython REPL](interactive-repl-ipython.md)

## <a name="running-code-in-the-debugger"></a>Ausführen von Code im Debugger

Zusätzlich zum Verwalten von Projekten, das mit seinen umfassenden Bearbeitungsfunktionen sehr benutzerfreundlich ist, und dem interaktiven Fenster bietet Visual Studio die umfassende Debugunterstützung für Python-Code.

1. Bearbeiten Sie den Code in der Datei „hello.py“, sodass sie mit Folgendem übereinstimmt:

  ```python  
  from math import sin, cos, radians  
  import sys  
    
  def make_dot_string(x):  
      return ' ' * int(10 * cos(radians(x)) + 10) + 'o'  
    
  def main():  
      for i in range(360 * 5):
          s = make_dot_string(i)  
          print(s)  
            
  main()
  ```  

1. Überprüfen Sie, ob der Code ordnungsgemäß funktioniert, indem Sie F5 drücken oder den Menübefehl **Debuggen > Debuggen starten** wählen. Durch diesen Befehl wird der Code im Debugger ausgeführt, aber da Sie keine Haltepunkte festgelegt haben, werden nur Wellenmusters für ein paar Iterationen ausgegeben. Durch Drücken einer beliebigen Taste wird das Ausgabefenster an diesem Punkt geschlossen.

    > [!Tip]
    > Damit das Ausgabefenster automatisch geschlossen wird, wenn das Programm abgeschlossen ist, ersetzen Sie den `main()`-Aufruf durch den folgenden Code:
    >
    > ```python    
    > if __name__ == "__main__":  
    >     sys.exit(int(main() or 0))      
    > ```
    > 
    > Wenn Sie sich aber je in Situationen befinden, in denen sich das Ausgabefenster automatisch schließt, obwohl es das nicht soll, klicken Sie mit der rechten Maustaste auf das Projekt, wählen Sie **Eigenschaften** und dann die Registerkarte **Debuggen** aus, und fügen Sie anschließend `-i` zum Feld **Interpreterargumente** hinzu. Durch dieses Argument wird der Interpreter nach Abschluss des Programms in den interaktiven Modus versetzt. Das Fenster bleibt dabei offen, bis Sie STRG + Z, EINGABETASTE zum Beenden drücken.

1. Legen Sie in der ersten Zeile der `main`-Funktion durch Klicken auf den linken grauen Rand dieser Zeile oder Platzieren des Caretzeichens in dieser Zeile einen Haltepunkt fest, und verwenden Sie den Befehl **Debuggen > Haltepunkt ein/aus** (F9). Ein roter Punkt wird im grauen Rand angezeigt und kennzeichnet den Haltepunkt (siehe blauer Pfeil unten):

    ![Festlegen eines Haltepunkts](media/getting-started-debugging-1.png)

1. Starten Sie den Debugger erneut, und Sie sehen, dass die Codeausführung in der Zeile mit diesem Haltepunkt stoppt. Hier können Sie die Aufrufliste und lokale Variablen im Fenster „Lokale“ überprüfen:

    ![Haltepunkt-Benutzeroberfläche für Python](media/getting-started-debugging-2.png)

1. Gehen Sie mit F10, dem Befehl **Debuggen > Prozedurschritt** oder der Symbolleistenschaltfläche „Prozedurschritt“ zeilenweise durch ein paar Iterationen der `for`-Schleife. Prozedurschritt bedeutet, dass der Debugger jeden Aufruf von `make_dot_string` ausführt, jedoch nicht innerhalb dieser Funktion stoppt (es sei denn, Sie legen einen Haltepunkt fest).

1. Die unten gezeigten drei Schrittschaltflächen in der Symbolleiste sind von links nach rechts: „Einzelschritt“, „Prozedurschritt“ und „Ausführen bis Rücksprung“:

    ![Schrittschaltflächen in der Symbolleiste](media/getting-started-debugging-3.png)

1. Gehen Sie jetzt mithilfe des Befehls „Einzelschritt“ (F11) in `make_dot_string`. Sie sehen, dass Sie aus der `for`-Schleife in diese Funktion gehen. Beim nächsten Schritt kehren Sie zur `for`-Schleife zurück, aber wenn die Funktion zusätzliche Zeilen enthält, gehen Sie diese zeilenweise durch. Wenn Sie sich in einer Funktion befinden, ihre restlichen Zeilen ausführen und zum aufrufenden Code zurückkehren möchten, verwenden Sie „Ausführen bis Rücksprung“ (UMSCHALT+F11).

1. Um die Ausführung des Codes fortzusetzen, bis der nächste Haltepunkt erreicht (oder das Programm beendet) ist, drücken Sie F5 erneut, oder wählen Sie die Symbolleistenschaltfläche **Weiter** bzw. **Debuggen > Weiter**. Da Sie in der `for`-Schleife einen Haltepunkt festgelegt haben, kommt es bei der nächsten Iteration zum Halt.

1. Hunderte von Iterationen einer Schleife zu durchlaufen, kann mühsam sein, also können Sie dem früher festgelegten Haltepunkt die Bedingung hinzufügen, nur dann zu stoppen, wenn der Wert von `i` eine bestimmte Grenze überschreitet, z.B. 1.600. Zum Festlegen einer Bedingung klicken Sie mit der rechten Maustaste auf den roten Punkt, der den Haltepunkt markiert, und wählen Sie **Bedingung...**. Geben Sie im dann angezeigten Fenster „Haltepunkteinstellungen“ `i > 1600` als Ausdruck ein, und wählen Sie **Schließen**. Drücken Sie nun F5, um den Vorgang fortzusetzen, und beobachten Sie, dass das Programm für eine Weile ausgeführt wird, bevor es erneut stoppt. 

    ![Festlegen einer Haltepunktbedingung](media/getting-started-debugging-4.png)

1. Um das Programm abzuschließen, können Sie den Haltepunkt ausschalten und F5 drücken. Visual Studio kehrt in den Bearbeitungsmodus zurück, wenn das Debuggen abgeschlossen ist.

### <a name="going-deeper"></a>Vertiefung

- [Debuggen](debugging.md).
- Die vollständige Dokumentation der Debugfeatures von Visual Studio finden Sie unter [Debugging in Visual Studio](../debugger/debugging-in-visual-studio.md) (Debuggen in Visual Studio).

## <a name="next-steps"></a>Nächste Schritte

Zusätzlich zu den obigen „Vertiefung“-Links behandeln folgende Themen zusätzliche Funktionen der Python-Umgebung in Visual Studio:

- Wie Visual Studio eine Verbindung mit einem Azure App Service herstellt, erfahren Sie unter [Publishing to Azure App Service](publishing-to-azure.md) (Veröffentlichen in Azure App Service).
- Wie Sie verschiedene Umgebungen sowohl global als auch für einzelne Projekte einschließlich virtueller Umgebungen verwalten, erfahren Sie unter [Python Environments](python-environments.md) (Python-Umgebungen).
- Visual Studio bietet die Möglichkeit zum Debuggen Ihrer Anwendung auf Remoteservern. Dies wird unter [Remotely Debugging Python Code](debugging-cross-platform-remote.md) (Remotedebuggen von Python Code) und [Remotely Debugging Python Code on Azure](debugging-azure-remote.md) (Remotedebuggen von Python Code in Azure) beschrieben.
- Sie können die Leistung Ihres Python-Codes mit [Visual Studio-Profilerstellung](profiling.md) auswerten.
- In Python geschriebene Komponententests werden direkt in den Visual Studio-Test-Explorer integriert, wie in [Setting Up Unit Testing for Python Code](unit-testing.md) (Einrichten von Komponententests für Python Code) erläutert.
- [Kostenlose Python-Kurse in der Microsoft Virtual Academy](https://mva.microsoft.com/search/SearchResults.aspx#!q=python)
- [Top Python Questions at Microsoft Virtual Academy (Meistgestellte Fragen an der Microsoft Virtual Academy)](https://aka.ms/mva-top-python-questions)

