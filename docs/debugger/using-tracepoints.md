---
title: Verwenden von Ablauf Verfolgungs Punkten im Debugger | Microsoft-Dokumentation
ms.date: 9/17/2019
ms.topic: conceptual
helpviewer_keywords:
- tracepoints, about tracepoints
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 263657213f1720eaca7a0462bb31585adaacf9bb
ms.sourcegitcommit: 8a96a65676fd7a2a03b0803d7eceae65f3fa142b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72516391"
---
# <a name="use-tracepoints-in-the-visual-studio-debugger"></a>Verwenden von Ablauf Verfolgungs Punkten im Visual Studio-Debugger

Mit Ablauf Verfolgungs Punkten können Sie Informationen im Ausgabefenster unter konfigurierbare Bedingungen protokollieren, ohne den Code zu ändern oder zu beenden. Diese Funktion wird sowohl für verwalteten als auch für nativen Code sowie für verschiedene Sprachen wie JavaScript und C#unterstützt.

## <a name="let39s-take-an-example"></a>Sehen&#39;Sie sich ein Beispiel an

Das folgende Beispielprogramm ist eine einfache `for`-Schleife mit einer Counter-Variablen, die sich bei jeder Ausführung einer anderen Iterations Schleife um eins vergrößert.

![Counter-Beispiel](../debugger/media/counterexample.png "Counter-Beispiel")

## <a name="set-tracepoints-in-source-code"></a>Festlegen von Ablauf Verfolgungs Punkten im Quellcode

Sie können Ablauf Verfolgungs Punkte festlegen, indem Sie im Fenster "halte **Punkt Einstellungen** " unter dem Kontrollkästchen **Aktion** eine Ausgabe Zeichenfolge angeben.

1. Um einen Ablauf Verfolgungs Punkt zu initialisieren, klicken Sie zuerst auf den bundbundrand links neben der Zeilennummer, in der Sie den Ablauf Verfolgungs Punkt festlegen möchten.

   ![Initialisierung von Haltepunkten](../debugger/media/breakpointinitialization.png "Initialisierung von Haltepunkten")

2. Zeigen Sie auf den roten Kreis, und klicken Sie dann auf das Zahnrad Symbol.
3. Dadurch wird das Fenster halte **Punkt Einstellungen** geöffnet.

   ![Haltepunkt Fenster](../debugger/media/breakpointwindow.png "Haltepunkt Fenster")

4. Aktivieren Sie das Kontrollkästchen **Aktion** .

   ![Aktivierte Aktionsfelder](../debugger/media/checkedactionsbox.png "Aktivierte Aktionsfelder")

   Beachten Sie, dass sich der rote Kreis in einen Diamanten ändert, der anzeigt, dass Sie von einem Haltepunkt zu Ablauf Verfolgungs Punkt gewechselt haben.

5. Geben Sie die Meldung ein, die Sie beim **Anzeigen einer Meldung in das Ausgabefenster** Textfeld anmelden möchten (Ausführliche Informationen finden Sie in den Abschnitten weiter unten in diesem Artikel).

   Der Ablauf Verfolgungs Punkt ist jetzt festgelegt. Klicken Sie auf die Schaltfläche &quot;Close &quot;, wenn Sie nur einige Informationen in der Ausgabefenster protokollieren möchten.

6. Wenn Sie Bedingungen hinzufügen möchten, die bestimmen, ob Ihre Meldung angezeigt wird, aktivieren Sie das Kontrollkästchen **Bedingungen** .

   ![Feld für aktivierte Bedingungen](../debugger/media/checkedconditionsbox.png "Feld für aktivierte Bedingungen")

   Sie haben drei Möglichkeiten für Bedingungen: **bedingter Ausdruck**, **Filter**und **Treffer Anzahl**.

## <a name="actions-menu"></a>Menü "Aktionen"

Mit diesem Menü können Sie eine Meldung im Ausgabefenster protokollieren. Geben Sie die Zeichen folgen ein, die im Meldungs Feld ausgegeben werden sollen (keine Anführungszeichen erforderlich). Wenn Sie Werte von Variablen anzeigen möchten, stellen Sie sicher, dass Sie diese in geschweiften Klammern einschließen.

Wenn Sie z. b. den Wert der `counter` Variablen in der Ausgabe Konsole anzeigen möchten, geben Sie im Textfeld Nachricht den Wert {Counter} ein.

![Counter-Ausgabe Meldung](../debugger/media/counteroutputmessage.png "Counter-Ausgabe Meldung")

Wenn Sie auf **Schließen** klicken und dann das Programm Debuggen (**F5**), wird im Ausgabefenster die folgende Ausgabe angezeigt.

![Aktions Meldung in Ausgabefenster](../debugger/media/actionsmessageinoutputwindow.png "Aktions Meldung in Ausgabefenster")

Sie können auch spezielle Schlüsselwörter verwenden, um spezifischere Informationen anzuzeigen. Geben Sie das Schlüsselwort genau wie unten dargestellt ein (verwenden Sie "$" vor jedem Schlüsselwort und alle Caps für das Schlüsselwort selbst).

| Stichwort | Was wird angezeigt? |
| --- | --- |
| $ADDRESS | Aktuelle Anweisung |
| $CALLER | Aufrufen des Funktionsnamens |
| $CALLSTACK | Aufrufliste |
| $FUNCTION | Name der aktuellen Funktion |
| $PID | Prozess-ID |
| $PNAME | Prozessname |
| $TID | Thread-ID |
| $TNAME   | Threadname |
| $TICK | Tick-Anzahl (aus Windows GetTickCount) |

## <a name="conditions-menu"></a>Menü "Bedingungen"

Mit Bedingungen können Sie Ihre Ausgabemeldungen filtern, sodass Sie nur in bestimmten Szenarien angezeigt werden. Ihnen stehen drei Hauptarten von Bedingungen zur Verfügung.

### <a name="conditional-expression"></a>Bedingter Ausdruck
Bei einem bedingten Ausdruck wird eine Ausgabe Meldung nur angezeigt, wenn bestimmte Bedingungen erfüllt sind.

Für bedingte Ausdrücke können Sie entweder den Ablauf Verfolgungs Punkt so festlegen, dass eine Meldung ausgegeben wird, wenn eine bestimmte Bedingung erfüllt ist oder sich geändert hat. Wenn Sie z. b. nur den Wert des Zählers während der Iterationen der `for` Schleife anzeigen möchten, können Sie die Option **ist true** auswählen und dann `i%2 == 0` in das Textfeld Nachricht eingeben.

![Bedingter Ausdruck ist true](../debugger/media/conditionalexpressionistrue.png "Bedingter Ausdruck ist "true"")

Wenn Sie den Wert des Zählers ausgeben möchten, wenn sich die Iterations `for` Schleife ändert, wählen Sie die Option **bei Änderung** aus, und geben Sie `i` in das Textfeld Nachricht ein.

![Bedingter Ausdruck bei Änderung](../debugger/media/conditionalexpressionwhenchanged.png "Bedingter Ausdruck bei Änderung")

Das Verhalten der Option **bei Änderung** unterscheidet sich für verschiedene Programmiersprachen.

- Bei nativem Code betrachtet der Debugger die erste Auswertung der Bedingung nicht als Änderung, sodass bei der ersten Auswertung nicht der Ablauf Verfolgungs Punkt auftritt.
- Bei verwaltetem Code trifft der Debugger auf den Ablauf Verfolgungs Punkt bei der ersten Auswertung, nachdem **geändert** ausgewählt wurde.

Einen umfassenderen Einblick in gültige Ausdrücke, die Sie beim Festlegen von Bedingungen verwenden können, finden Sie unter [Ausdrücke im Debugger](expressions-in-the-debugger.md).

### <a name="hit-count"></a>Treffer Anzahl
Mit der Bedingung "Treffer Anzahl" können Sie die Ausgabe nur dann senden, wenn die Codezeile, in der der Ablauf Verfolgungs Punkt festgelegt ist, eine angegebene Anzahl von Wiederholungen ausgeführt hat.

Bei der Treffer Anzahl können Sie angeben, dass eine Meldung ausgegeben werden soll, wenn die Codezeile, in der der Ablauf Verfolgungs Punkt festgelegt ist, mehrmals ausgeführt wurde, ein Vielfaches von ist oder größer oder gleich dem angegebenen Treffer Anzahl Wert ist. Wählen Sie die Option aus, die Ihren Anforderungen am besten entspricht, und geben Sie im Feld (z. b. 5) einen ganzzahligen Wert ein, der die betreffende Iterations Rate darstellt.

![Treffer Anzahl für bedingten Ausdruck](../debugger/media/conditionalexpressionhitcount.png "Treffer Anzahl für bedingten Ausdruck")

### <a name="filter"></a>Filter
Legen Sie für eine Filterbedingung fest, für welche Geräte, Prozesse oder Threads die Ausgabe angezeigt wird.

![Bedingter Ausdrucks Filter](../debugger/media/conditionalexpressionfilter.png "Bedingter Ausdrucks Filter")

Liste der Filter Ausdrücke:

- MachineName = "name"
- ProcessId = value
- ProcessName = "name"
- ThreadId = value
- ThreadName = "name"

Schließen Sie Zeichen folgen (z. b. Namen) in doppelte Anführungszeichen ein. Werte können ohne Anführungszeichen eingegeben werden. Sie können Klauseln mit `&` (`AND`), `||` (`OR`), `!` (`NOT`) und Klammern kombinieren.

## <a name="considerations"></a>Weitere Überlegungen

Obwohl Ablauf Verfolgungs Punkte dazu gedacht sind, das Debuggen zu bereinigen und zu vereinfachen, sollten Sie sich über einige Aspekte im klaren sein, die Sie bei der Verwendung berücksichtigen sollten.

Manchmal kann sich der Wert ändern, wenn Sie eine Eigenschaft oder ein Attribut eines Objekts überprüfen. Dies ist kein Fehler, der von der Ablauf Verfolgungs Punkt-Funktion selbst verursacht wird. es ist jedoch erwähnenswert, dass durch die Verwendung von Ablauf Verfolgungs Punkten zum Überprüfen von Objekten diese unbeabsichtigten Änderungen nicht vermieden werden.

Die Art und Weise, wie Ausdrücke im **Aktions** Meldungs Feld ausgewertet werden, unterscheidet sich möglicherweise von der Sprache, die Sie zurzeit für die Entwicklung verwenden. Wenn Sie z. b. eine Zeichenfolge ausgeben möchten, müssen Sie eine Nachricht nicht in Anführungszeichen einschließen, auch wenn Sie `Debug.WriteLine()` oder `console.log()` normalerweise verwenden. Außerdem kann sich die Syntax der geschweiften Klammer (`{ }`) für Ausgabe Ausdrücke von der Konvention zum Ausgeben von Werten in der Entwicklungssprache unterscheiden. (Der Inhalt innerhalb der geschweiften Klammern (`{ }`) sollte jedoch immer noch mit der Syntax Ihrer Entwicklungssprache geschrieben werden.)

Wenn Sie versuchen, eine Live Anwendung zu Debuggen und nach einer ähnlichen Funktion zu suchen, sehen Sie sich unser Protokoll Punkt-Feature im Momentaufnahmedebugger an. Der Snapshot Debugger ist ein Tool, mit dem Probleme in Produktionsanwendungen untersucht werden können. Mit Protokoll Punkten können Sie auch Nachrichten an den Ausgabefenster senden, ohne den Quellcode ändern zu müssen und sich nicht auf die laufende Anwendung auswirken. Weitere Informationen finden Sie unter [Debuggen einer Azure-Live Anwendung](../debugger/debug-live-azure-applications.md).

## <a name="see-also"></a>Siehe auch

- [Was bedeutet „Debuggen“?](../debugger/what-is-debugging.md)
- [Schreiben von C# besserem Code mithilfe von Visual Studio](../debugger/write-better-code-with-visual-studio.md)
- [Erster Einblick in das Debuggen](../debugger/debugger-feature-tour.md)
- [Ausdrücke im Debugger](expressions-in-the-debugger.md)
- [Verwenden von Haltepunkten](../debugger/using-breakpoints.md)
- [Azure-Live Anwendungen debuggen](../debugger/debug-live-azure-applications.md)
