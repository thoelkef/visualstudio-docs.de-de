---
title: Einstieg in die Arbeit mit Python in Visual Studio | Microsoft-Dokumentation
ms.custom: 
ms.date: 5/1/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a9087b19-275b-4cc1-8d0c-f9c4356c9ce8
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
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: 8001036077b8b14af80fabceafad5d3aff9b25f4
ms.contentlocale: de-de
ms.lasthandoff: 05/09/2017

---

# <a name="getting-started-with-python-in-visual-studio"></a>Erste Schritte mit Python in Visual Studio

Sobald Sie Visual Studio mit der Python-Arbeitsauslastung (Visual Studio 2017) oder mit den Python-Tools für Visual Studio (Visual Studio 2015 und früher) installiert haben, können Sie die Python-Entwicklungsumgebung erforschen. (Siehe bei Bedarf [Installation](installation.md).)

In dieser exemplarischen Vorgehensweise erstellen Sie eine neue leere Python-Anwendung, wählen eine Python-Umgebung für Ihre Arbeit aus und beginnen, Code zu schreiben, um IntelliSense kennenzulernen. Sie arbeiten dann für kurze Zeit mit dem interaktiven REPL-Fenster, um mehr Code zu erstellen, schließen dann das Programm ab und führen es sowohl eigenständig als auch im Debugger aus.

> [!Note]
> Diese exemplarische Vorgehensweise behandelt die Python-Benutzeroberfläche in Visual Studio 2017; andere Versionen sind ähnlich, können sich jedoch in den Details unterscheiden.

## <a name="create-a-new-python-project"></a>Erstellen eines neuen Python-Projekts

Die Python-Unterstützung in Visual Studio umfasst eine Reihe von [Projektvorlagen](python-projects.md) für Ihren Einstieg in verschiedene Arten von Projekten, einschließlich Webanwendungen, unter Verwendung der Bottle-, Flask- und Django-Frameworks zusammen mit Azure Cloud Services. Im Rahmen dieser exemplarischen Vorgehensweise beginnen wir jedoch mit einem leeren Projekt.

1. Wählen Sie in Visual Studio **Datei > Neues Projekt**, womit das Dialogfeld **Neues Projekt** geöffnet wird. Hier können Sie eine Vorlage suchen und auswählen und den Ordner angeben, in dem das Projekt erstellt werden soll.

1. Python-Vorlagen finden Sie auf der linken Seite unter **Vorlagen > Andere Sprachen > Python**, oder indem Sie einfach nach „Python“ suchen:

    ![Dialogfeld „Neues Projekt“ mit Python-Projekten](media/getting-started-new-project.png)

1. Wählen Sie die Vorlage „Python-Anwendung“, geben Sie einen Ordner für das Projekt an, und wählen Sie **OK**. (Wenn Sie sofort ein lokales Repository für das Projekt erstellen möchten, wählen Sie auch die Option **Zur Quellcodeverwaltung hinzufügen**).

    > [!Tip]
    > Mit der Vorlage „From exiting Python Code“ können Sie schnell aus einem Ordner ein Visual Studio-Projekt erstellen, das bereits Python-Code enthält, anstatt ein neues leeres Projekt zu erstellen und vorhandenen Code dahin zu importieren.

1. Nach einigen Augenblicken sehen Sie das geöffnete Projekt im Projektmappen-Explorer-Fenster von Visual Studio. Hier können Sie die Dateien und Ordner in Ihrem Projekt durchsuchen sowie Umgebungen verwalten.

    ![Projektmappen-Explorer mit einem Python-Projekt](media/getting-started-solution-explorer-1.png)

1. Erweitern Sie den Knoten **Python-Umgebungen**, und Sie werden sehen, welcher Python-Interpreter der aktuelle Standard für dieses Projekt ist. Wenn Sie auch den Interpreterknoten erweitern, sehen Sie eine Liste der Bibliotheken, die in der Umgebung zur Verfügung stehen:

    ![Projektmappen-Explorer mit der Python-Umgebung](media/getting-started-solution-explorer-2.png)

1. Wenn Sie Visual Studio 2015 oder früher verwenden, haben Sie standardmäßig keinen Python-Interpreter installiert. Informationen zu diesem Prozess finden Sie unter [Selecting and installing Python interpreters](python-environments.md#selecting-and-installing-python-interpreters) (Auswählen und Installieren von Python-Interpretern).

### <a name="going-deeper"></a>Vertiefung

- [Python-Projekte in Visual Studio](python-projects.md)
- [Webprojektvorlagen](template-web.md)
- [Django-Webprojektvorlage](template-django.md)
- [Vorlage des Azure Cloud-Diensts](template-azure-cloud-service.md)

## <a name="writing-and-running-code"></a>Schreiben und Ausführen von Code

1. Nach dem Erstellen eines neuen Projekts „Python-Anwendung“ wird eine standardmäßige leere Datei mit dem Namen `PythonApplication1.py` im Visual Studio-Editor geöffnet. Um diese umzubenennen, klicken Sie mit der rechten Maustaste im Projektmappen-Explorer auf die Datei, wählen Sie **Umbenennen**, und ändern Sie den Namen in `hello.py`.

1. Beginnen Sie, `print("Hello world")` einzugeben, und beachten Sie, wie Visual Studio IntelliSense nebenbei Optionen zur automatischen Vervollständigung anzeigt. Die in der Dropdownliste dargestellte Option ist die Standardvervollständigung, die verwendet wird, wenn Sie die TAB-Taste drücken. Dies kann bei längeren Anweisungen oder Bezeichnern sehr hilfreich sein.

    ![IntelliSense-Popupfenster für automatische Vervollständigung](media/getting-started-coding-1.png)

1. IntelliSense zeigt je nach der Anweisung, die Sie verwenden, verschiedene Informationen an, die Funktion, die Sie aufrufen usw. Bei der `print`-Funktion werden bei Eingabe von `(` für den Aufruf vollständige Nutzungsinformationen für diese Funktion angezeigt, und das aktuelle Argument, das Sie bereitstellen müssen (hier **value**), wird sogar fett formatiert:

    ![IntelliSense-Popupfenster für automatische Vervollständigung für eine Funktion](media/getting-started-coding-2.png)

1. Vervollständigen Sie die Anweisung, damit sie der folgenden entspricht:

  ```python
  print("Hello world")
  ```

1. Wählen Sie zum Ausführen des Codes auf der Symbolleiste unten die Schaltfläche **Start**, drücken Sie F5, oder wählen Sie das Menüelement **Debuggen > Debuggen starten**.

    ![Schaltfläche „Start“ auf der Debugsymbolleiste](media/getting-started-coding-3.png)

    > [!Note]
    > Wenn in Visual Studio 2015 oder früher die Meldung angezeigt wird, dass keine Interpreter vorhanden sind, informieren Sie sich unter [Selecting and installing Python interpreters](python-environments.md#selecting-and-installing-python-interpreters) (Auswählen und Installieren von Python-Interpretern), da standardmäßig kein Interpreter installiert ist.

1. Visual Studio führt den Code mithilfe der Standardumgebung im Projekt aus und zeigt die Ergebnisse in einem Befehlsfenster an. Drücken Sie eine Taste, um das Fenster zu schließen und die Debugsitzung beenden.

    ![Schaltfläche „Start“ auf der Debugsymbolleiste](media/getting-started-coding-4.png)

1. Zusätzlich zu Anweisungen und Funktionen bietet IntelliSense Vervollständigungen für `import`-Anweisungen. Dadurch können Sie leicht erkennen, welche Module in Ihrer Umgebung und welche Elemente in diesen Modulen verfügbar sind. Löschen Sie im Editor die `print`-Zeile, und geben Sie `import` ein. Sie sehen eine Liste von Modulen:

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

Das interaktive Visual Studio-Fenster für Python bietet eine komfortable „Lesen-Auswerten-Ausgeben“-Schleife, die den üblichen „Bearbeiten-Erstellen-Debuggen“-Zyklus erheblich verkürzt. Es ähnelt der REPL-Umgebung der Python-Befehlszeile, bietet aber einige zusätzliche Funktionen, wie Sie hier sehen werden.

1. Öffnen Sie das interaktive Fenster durch Auswahl von **Ansicht > Weitere Fenster > Interaktive Python-Fenster** im Hauptmenü von Visual Studio. Das Fenster wird mit der üblichen Python-REPL-Eingabeaufforderung >>> geöffnet. Beachten Sie, dass Sie die Umgebung im Dropdownmenü auf der Symbolleiste jederzeit ändern können:

    ![Interaktives Python-Fenster](media/getting-started-interactive-1.png)

1. Geben Sie einige Anweisungen (z.B. `print("hello")`) und Ausdrücke (z.B. `123/567`) ein, um sofortige Ergebnisse anzuzeigen:

    ![Sofortige Ergebnisse im interaktiven Python-Fenster](media/getting-started-interactive-2.png)

1. Beim Schreiben einer mehrzeiligen Anweisung, wie einer Funktionsdefinition, wird im interaktiven Fenster die Eingabeaufforderung ... zum Fortsetzen der Zeilen angezeigt, die im Gegensatz zum Befehlszeilen-REPL automatischen Einzug bietet:

    ![Interaktives Python-Fenster mit Anweisungsfortsetzung](media/getting-started-interactive-3.png)

1. Das interaktive Fenster enthält einen vollständigen Verlauf aller Elemente, die Sie eingegeben haben, und verbessert das Befehlszeilen-REPL mit mehrzeiligen Verlaufselementen. Beispielsweise können Sie einfach die vollständige Definition der `f`-Funktion oben als einzelne Einheit zurückrufen und den Namen mühelos in `make_double` ändern, anstatt die Funktion Zeile für Zeile neu erstellen zu müssen.

1. Ein weiteres sehr hilfreiches Feature ist die Möglichkeit, schnell mehrere Codezeilen aus einem Editorfenster an das interaktive Fenster zu senden, wo Sie sie in der schnellen REPL-Umgebung bearbeiten können, statt anderen Code zur Ausführung im Debugger zu schreiben. Um dies zu sehen, fügen Sie den folgenden Code Ihrer Datei „hello.py“ hinzu, die im Editor geöffnet ist:

  ```python
  def make_dot_string(x):  
      return ' ' * int(10 * cos(radians(x)) + 10) + 'o'
  ```

1. Wählen Sie den gesamten Code in „hello.py“ (einschließlich der `import`-Anweisungen) aus, klicken Sie mit der rechten Maustaste, und wählen Sie **An Interactive senden** (STRG+EINGABETASTE). Der Code wird direkt in das interaktive Fenster eingefügt und ausgeführt. Da der Code eine Funktion definiert, können Sie diese Funktion schnell testen, indem Sie sie mehrmals aufrufen:

    ![Senden von Code an das interaktive Fenster](media/getting-started-interactive-4.png)

1. **An Interactive senden** ermöglicht Ihnen, mehrere Zeilen Code (z.B. etwas, das Sie online finden) in das interaktive Fenster einzufügen, was nicht direkt möglich ist. Kopieren Sie z.B. den folgenden Code, und versuchen Sie, ihn in das interaktive Fenster einzufügen (STRG+V), und Sie sehen, dass nichts passiert. Aber Sie können ihn in den Editor einfügen, auswählen und den Befehl **An Interactive senden** verwenden, um seine Ausführung zu sehen.

  ```python
  for i in range(360):
      s = make_dot_string(i)  
      print(s) 
  ```

    ![Einfügen von mehrere Codezeilen mit „An Interactive senden“](media/getting-started-interactive-5.png)

1. Da die Definition der Funktion sich erneut als einzelne Einheit im REPL-Verlauf befindet, können Sie einfach zurückzugehen, beliebige Änderungen vornehmen und die Funktion erneut testen.

1. Wenn Sie mit dem Code den Sie geschrieben haben, zufrieden sind, können Sie ihn im interaktiven Fenster auswählen, mit der rechten Maustaste darauf klicken, **Code kopieren** wählen und ihn in den Editor einfügen. Die besondere Funktion des Befehls **Code kopieren** ist, dass er automatisch sowohl beliebige Ausgabe als auch den Aufforderungstext >>> und ... auslässt. Wenn Sie den Befehl z.B. mit der Auswahl unten verwenden:

  ![Interaktives Fenster mit dem Befehl „Code kopieren“](media/getting-started-interactive-6.png)

  wird nur Folgendes eingefügt:

  ```python
  make_dot_string(180)
  make_dot_string(135)
  for i in range(360):
      s = make_dot_string(i)  
      print(s) 
  ```

1. Schließlich enthält das interaktive Fenster eine Reihe von Metabefehlen, mit denen Sie Dateien laden, die Umgebung ohne Verlust des Verlaufs zurücksetzen und im Verlauf Ihrer Arbeit Kommentare einfügen können. Nähere Informationen finden Sie unter [Working with the Python Interactive Window](interactive-repl.md#meta-commands) (Arbeiten mit dem interaktiven Python-Fenster).

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

1. Um zu überprüfen, ob der Code ordnungsgemäß funktioniert, wählen Sie **Start** auf der Symbolleiste, drücken F5 oder wählen den Menübefehl **Debuggen > Debuggen starten**. Dadurch wird der Code im Debugger ausgeführt, aber da wir keine Haltepunkte festgelegt haben, sehen Sie einfach die Ausgabe eines Wellenmusters für ein paar Iterationen. Durch Drücken einer beliebigen Taste wird das Ausgabefenster an diesem Punkt geschlossen.

    > [!Tip]
    > Damit das Ausgabefenster automatisch geschlossen wird, wenn das Programm abgeschlossen ist, ersetzen Sie den `main()`-Aufruf durch den folgenden Code:
    >
    > ```python    
    > if __name__ == "__main__":  
    >     sys.exit(int(main() or 0))      
    > ```
    > 
    > Wenn Sie sich aber je in Situationen befinden, in denen sich das Ausgabefenster automatisch schließt, obwohl es das nicht soll, klicken Sie mit der rechten Maustaste auf das Projekt, wählen Sie **Eigenschaften** und dann die Registerkarte **Debuggen** aus, und fügen Sie anschließend `-i` zum Feld **Interpreterargumente** hinzu. Dadurch wird der Interpreter nach Abschluss des Programms in den interaktiven Modus versetzt, und das Fenster bleibt dabei offen, bis Sie STRG + Z, EINGABETASTE zum Beenden drücken.

1. Legen Sie in der ersten Zeile der `main`-Funktion durch Klicken auf den linken grauen Rand dieser Zeile oder Platzieren des Caretzeichens in dieser Zeile einen Haltepunkt fest, und verwenden Sie den Befehl *Debuggen > Haltepunkt ein/aus** (F9). Ein roter Punkt wird im grauen Rand angezeigt und kennzeichnet den Haltepunkt (siehe blauer Pfeil unten):

    ![Festlegen eines Haltepunkts](media/getting-started-debugging-1.png)

1. Starten Sie den Debugger erneut, und Sie sehen, dass die Codeausführung in der Zeile mit diesem Haltepunkt stoppt. Hier können Sie die Aufrufliste sehen und lokale Variablen im Fenster „Lokale“ überprüfen:

    ![Haltepunkt-Benutzeroberfläche für Python](media/getting-started-debugging-2.png)

1. Gehen Sie mit F10, dem Befehl **Debuggen > Prozedurschritt** oder der Symbolleistenschaltfläche „Prozedurschritt“ zeilenweise durch ein paar Iterationen der `for`-Schleife. Dies bedeutet, dass der Debugger jeden Aufruf von `make_dot_string` ausführt, jedoch nicht innerhalb dieser Funktion stoppt (es sei denn, Sie legen einen Haltepunkt fest).

1. Die unten gezeigten drei Schrittschaltflächen in der Symbolleiste sind von links nach rechts: „Einzelschritt“, „Prozedurschritt“ und „Ausführen bis Rücksprung“:

    ![Schrittschaltflächen in der Symbolleiste](media/getting-started-debugging-3.png)

1. Gehen Sie jetzt mithilfe des Befehls „Einzelschritt“ (F11) in `make_dot_string`. Sie sehen, dass Sie aus der `for`-Schleife in diese Funktion gehen. Beim nächsten Schritt kehren Sie zur `for`-Schleife zurück, aber wenn die Funktion zusätzliche Zeilen enthielte, würden Sie diese zeilenweise durchgehen. Wenn Sie sich in einer Funktion befinden, ihre restlichen Zeilen ausführen und zum aufrufenden Code zurückkehren möchten, verwenden Sie „Ausführen bis Rücksprung“ (UMSCHALT+F11).

1. Um die Ausführung des Codes fortzusetzen, bis der nächste Haltepunkt erreicht (oder das Programm beendet) ist, drücken Sie F5 erneut, oder wählen Sie die Symbolleistenschaltfläche **Weiter** bzw. **Debuggen > Weiter**. Da Sie in der `for`-Schleife einen Haltepunkt festgelegt haben, kommt es bei der nächsten Iteration zum Halt.

1. Hunderte von Iterationen einer Schleife zu durchlaufen, kann mühsam sein, also können Sie dem früher festgelegten Haltepunkt die Bedingung hinzufügen, nur dann zu stoppen, wenn der Wert von `i` eine bestimmte Grenze überschreitet, z.B. 1.600. Klicken Sie zu diesem Zweck mit der rechten Maustaste auf den roten Punkt, der den Haltepunkt markiert, und wählen Sie **Bedingung...**. Geben Sie im dann angezeigten Fenster „Haltepunkteinstellungen“ `i > 1600` als Ausdruck ein, und wählen Sie **Schließen**. Drücken Sie nun F5, um den Vorgang fortzusetzen, und Sie sehen, dass das Programm für eine Weile ausgeführt wird, bevor es erneut stoppt. 

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

