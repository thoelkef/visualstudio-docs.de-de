---
title: Festlegen einer Überwachung für Variablen | Microsoft-Dokumentation
ms.custom: seodec18
ms.date: 10/11/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.watch
helpviewer_keywords:
- debugging [Visual Studio], Watch window
- expressions [debugger], evaluating
- variables [debugger], evaluating
- expression evaluation
- registers, evaluating
- debugging [Visual Studio], expression evaluation
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ea3d2a1e82e92473859fef29754fbb831cf3685b
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409338"
---
# <a name="watch-variables-with-watch-windows-and-quickwatch"></a>Überwachen von Variablen mit Überwachungs Fenstern und schnell Überwachung

Beim Debuggen können Sie die über **Wachen** von Fenstern und **schnell Überwachung** verwenden, um Variablen und Ausdrücke zu beobachten. Die Fenster sind nur während einer Debugsitzung verfügbar.

**Überwachungs** Fenster können während des Debuggens mehrere Variablen gleichzeitig anzeigen. Im Dialogfeld **schnell Überwachung** wird jeweils eine einzelne Variable angezeigt, und Sie muss geschlossen werden, bevor das Debugging fortgesetzt werden kann.

Wenn Sie den Code zum ersten Mal debuggen möchten, sollten Sie vor dem Durcharbeiten dieses Artikels das [Debuggen für absolute Einsteiger](../debugger/debugging-absolute-beginners.md) und [Debuggingtechniken und-Tools](../debugger/write-better-code-with-visual-studio.md) lesen.

## <a name="observe-variables-with-a-watch-window"></a>Variablen mit einem Überwachungsfenster beobachten

Sie können mehr als ein **Überwachungs** Fenster öffnen und mehr als eine Variable in einem **Überwachungs** Fenster beobachten.

Um z. b. eine Überwachung der Werte von `a`, `b`und `c` im folgenden Code festzulegen:

```C++
int main()
{
    int a, b, c;
    a = 1;
    b = 2;
    c = 0;

    for (int i = 0; i < 10; i++)
    {
        a++;
        b *= 2;
        c = a + b;
    }

    return 0;
}

```

1. Legen Sie einen Haltepunkt in der `c = a + b;` Zeile fest, indem Sie auf den linken Rand klicken, **Debuggen** > halte **Punkt**umschalten oder **F9**drücken.

1. Beginnen Sie mit dem Debuggen, indem Sie den grünen **Start** Pfeil auswählen oder **Debuggen** > das **Debuggen starten** Die Ausführung wird am Haltepunkt angehalten.

1. Öffnen Sie ein **Überwachungs** Fenster, indem Sie **Debuggen** > **Windows** > **Watch** > über **Wachen 1**, oder drücken Sie **STRG**+**alt**+**W** > **1**.

   Sie können zusätzliche **Überwachungs** Fenster öffnen, indem Sie Windows **2**, **3**oder **4**auswählen.

1. Wählen Sie im **Überwachungs** Fenster eine leere Zeile aus, und geben Sie Variable `a`ein. Führen Sie die gleichen Schritte für `b` und `c`aus.

   ![Überwachen von Variablen](../debugger/media/watchvariables.png "Watchvariables")

1. Setzen Sie das Debuggen fort, indem Sie **Debuggen** > Einzel **Schritt** **oder drücken,** Wenn Sie nach Bedarf Die Variablen Werte im **Überwachungs** Fenster ändern sich, wenn Sie die `for` Schleife durchlaufen.

>[!NOTE]
>Nur C++ für
>- Möglicherweise müssen Sie den Kontext eines Variablen namens oder einen Ausdruck qualifizieren, der einen Variablennamen verwendet. Der Kontext ist die Funktion, die Quelldatei oder das Modul, in der sich eine Variable befindet. Wenn Sie den Kontext qualifizieren müssen, verwenden Sie die **Syntax des** [KontextC++Operators ()](../debugger/context-operator-cpp.md) im Fenster "über **Wachen** ".
>
>- Sie können Registernamen und Variablennamen mithilfe **$\<Register&nbsp;Name >** oder **@\<registrieren&nbsp;Name** > dem **Namen** im Fenster über **Wachen** hinzufügen. Weitere Informationen finden Sie unter [Pseudovariables](../debugger/pseudovariables.md).

## <a name="use-expressions-in-a-watch-window"></a>Verwenden von Ausdrücken in einem Überwachungsfenster

Sie können jeden gültigen vom Debugger erkannten Ausdruck in einem **Überwachungs** Fenster beobachten.

Beispielsweise können Sie für den Code im vorherigen Abschnitt den Mittelwert der drei Werte erzielen, indem Sie `(a + b + c) / 3` im Fenster über **Wachen** eingeben:

![Watch-Ausdruck](../debugger/media/watchexpression.png "Watch-Ausdruck")

Die Regeln zum Auswerten von Ausdrücken im Fenster über **Wachen** sind in der Regel mit den Regeln zum Auswerten von Ausdrücken in der Codesprache identisch. Wenn ein Ausdruck einen Syntax Fehler aufweist, erwarten Sie den gleichen Compilerfehler wie im Code-Editor. Beispielsweise erzeugt ein Tippfehler im vorangehenden Ausdruck diesen Fehler im Fenster über **Wachen** :

![Fehler bei Überwachungs Ausdruck](../debugger/media/watchexpressionerror.png "Fehler bei Überwachungs Ausdruck")

Ein Kreis mit zwei Wellenlinien (Symbol) wird möglicherweise im Fenster "über **Wachen** " angezeigt. Dieses Symbol bedeutet, dass der Debugger den Ausdruck aufgrund einer möglichen Thread übergreifenden Abhängigkeit nicht ausgewertet hat. Für die Auswertung des Codes müssen andere Threads in der APP temporär ausgeführt werden, aber da Sie sich im unterbrechen Modus befinden, werden alle Threads in der app in der Regel angehalten. Wenn andere Threads vorübergehend ausgeführt werden können, kann dies unerwartete Auswirkungen auf den Zustand Ihrer APP haben, und der Debugger ignoriert möglicherweise Ereignisse wie z. b. Breakpoints und Ausnahmen in diesen Threads.

::: moniker range=">= vs-2019" 
## <a name="search-in-the-watch-window"></a>Suchen Sie im Überwachungsfenster

Sie können nach Schlüsselwörtern in den Spalten Name, Wert und Typ des Fensters über **Wachen** suchen, indem Sie die Suchleiste oberhalb der einzelnen Fenster verwenden. Drücken Sie die EINGABETASTE, oder wählen Sie einen der Pfeile aus, um eine Suche auszuführen. Zum Abbrechen einer laufenden Suche wählen Sie das Symbol "x" in der Suchleiste aus.

Verwenden Sie die Pfeile nach links und rechts (UMSCHALT + F3 bzw. F3), um zwischen gefundenen Übereinstimmungen zu navigieren.

![Im Überwachungs Fenster suchen](../debugger/media/ee-search-watch.png "Im Überwachungs Fenster suchen")

Wenn Sie die Suche mehr oder weniger gründlich durchführen möchten, wählen Sie in der Dropdown Liste **tiefer suchen** am oberen Rand des Fensters über **Wachen** aus, wie viele Ebenen in geschaltete Objekte durchsucht werden sollen. 

## <a name="pin-properties-in-the-watch-window"></a>Anheften von Eigenschaften im Überwachungsfenster

>[!NOTE]
> Diese Funktion wird in .net Core 3,0 oder höher unterstützt.

Sie können Objekte **mithilfe der Eigenschaften** im Überwachungsfenster schnell überprüfen.  Um dieses Tool zu verwenden, zeigen Sie auf eine Eigenschaft, und wählen Sie das angezeigte anheft Symbol aus, und wählen Sie im resultierenden Kontextmenü die Option **Member als Favorit** anheften aus.  Dadurch wird diese Eigenschaft an den Anfang der Eigenschaften Liste des Objekts hochskalieren, und der Eigenschaftsname und-Wert wird in der Spalte **Wert** angezeigt.  Wenn Sie eine Eigenschaft lösen möchten, wählen Sie das anheft Symbol erneut aus, oder wählen Sie im Kontextmenü die Option **Member als Favorit lösen** aus.

![Anheften von Eigenschaften im Überwachungsfenster](../debugger/media/basic-pin-watch.gif "Anheften von Eigenschaften im Überwachungsfenster")

Sie können Eigenschaftsnamen auch umschalten und nicht fixierte Eigenschaften herausfiltern, wenn Sie die Eigenschaften Liste des Objekts im Überwachungsfenster anzeigen.  Sie können auf beide Optionen zugreifen, indem Sie die Schaltflächen auf der Symbolleiste oberhalb des Fensters Überwachen auswählen.

::: moniker-end

### <a name="bkmk_refreshWatch"></a>Überwachungs Werte aktualisieren

Wenn ein Ausdruck ausgewertet wird, wird möglicherweise ein Aktualisierungs Symbol (Zirkel Pfeil) im Fenster "über **Wachen** " angezeigt. Das Aktualisierungs Symbol weist auf einen Fehler oder einen veralteten Wert hin.

Um den Wert zu aktualisieren, wählen Sie das Aktualisierungs Symbol aus, oder drücken Sie die Leertaste. Der Debugger versucht, den Ausdruck neu auszuwerten. Abhängig davon, warum der Wert nicht ausgewertet wurde, ist es jedoch möglicherweise nicht möglich, den Ausdruck neu auszuwerten.

Zeigen Sie auf das Aktualisierungs Symbol, oder sehen Sie sich die Spalte **Wert** an, warum der Ausdruck nicht ausgewertet wurde. Hierfür kann es folgende Gründe geben:

- Beim Auswerten des Ausdrucks ist ein Fehler aufgetreten, wie im vorherigen Beispiel gezeigt. Möglicherweise tritt ein Timeout auf, oder eine Variable kann außerhalb des gültigen Bereichs liegen.

- Der Ausdruck verfügt über einen Funktions Aufruf, der einen Nebeneffekt in der APP auslöst. Siehe [Ausdrucks Nebeneffekte](#bkmk_sideEffects).

- Die automatische Auswertung von Eigenschaften und impliziten Funktionsaufrufen ist deaktiviert.

Wenn das Aktualisierungs Symbol angezeigt wird, weil die automatische Auswertung von Eigenschaften und impliziten Funktionsaufrufen deaktiviert ist, können Sie es aktivieren, indem Sie die Eigenschaften **Auswertung aktivieren und andere implizite Funktionsaufrufe** **in Extras** > **Optionen** > **Debugging** > **Allgemein**auswählen.

So veranschaulichen Sie die Verwendung des Aktualisierungs Symbols:

1. Deaktivieren **Sie unter Extras > ** **Optionen** > **Debuggen** > **Allgemein**das Kontrollkästchen **Eigenschaften Auswertung und andere implizite Funktionsaufrufe aktivieren** .

1. Geben Sie den folgenden Code ein, und legen Sie im **Überwachungs** Fenster eine Überwachung für die `list.Count`-Eigenschaft fest.

   ```csharp
   static void Main(string[] args)
   {
       List<string> list = new List<string>();
       list.Add("hello");
       list.Add("goodbye");
   }
   ```

1. Beginnen Sie mit dem Debuggen. Das Fenster über **Wachen** zeigt Folgendes an:

   ![Überwachung aktualisieren](../debugger/media/refreshwatch.png "Überwachung aktualisieren")

1. Um den Wert zu aktualisieren, wählen Sie das Aktualisierungs Symbol aus, oder drücken Sie die Leertaste. Der Debugger wertet den Ausdruck erneut aus.

### <a name="bkmk_sideEffects"></a>Ausdrucks Nebeneffekte

Das Auswerten einiger Ausdrücke kann den Wert einer Variablen ändern oder sich anderweitig auf den Status der APP auswirken. Die Auswertung des folgenden Ausdrucks ändert beispielsweise den Wert von `var1`:

```csharp
var1 = var2
```

Dieser Code kann zu einem [Nebeneffekt](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\))führen. Nebeneffekte können das Debugging erschweren, indem Sie die Funktionsweise ihrer App ändern.

Ein Ausdruck mit Nebeneffekten wird nur einmal ausgewertet, wenn Sie ihn zum ersten Mal eingeben. Danach erscheint der Ausdruck im **Überwachungs** Fenster ausgegraut, und weitere Auswertungen werden deaktiviert. In der QuickInfo-oder **value** -Spalte wird erläutert, dass der Ausdruck einen Nebeneffekt auslöst. Sie können die erneute Auswertung erzwingen, indem Sie das Aktualisierungs Symbol auswählen, das neben dem Wert angezeigt wird.

Eine Möglichkeit, die Bezeichnung für Nebeneffekte zu verhindern, besteht darin, die automatische Funktions Auswertung zu deaktivieren. Deaktivieren Sie unter **Extras > ** Optionen > **Debuggen** > **Allgemein**die **Option** **Eigenschaften Auswertung und andere implizite Funktionsaufrufe aktivieren**.

Wenn C# die Auswertung von Eigenschaften oder impliziten Funktionsaufrufen nur für deaktiviert ist, können Sie die Auswertung erzwingen, indem Sie den **AC** -formatmodifizierer einem Variablen **Namen** im Fenster über **Wachen** hinzufügen. Weitere Informationen finden Sie unter [Formatieren von Spezifizierern in C#](../debugger/format-specifiers-in-csharp.md).

## <a name="bkmk_objectIds"></a>Verwenden von Objekt-IDs im ÜberwachungsfensterC# (und Visual Basic)

Manchmal möchten Sie das Verhalten eines bestimmten Objekts beobachten. Beispielsweise können Sie ein Objekt nachverfolgen, auf das eine lokale Variable verweist, nachdem diese Variable den Gültigkeitsbereich verlassen hat. In C# und Visual Basic können Sie Objekt-IDs für bestimmte Instanzen von Verweistypen erstellen und diese im Fenster **Überwachen** und in Haltepunktbedingungen verwenden. Die Objekt-ID wird von den Debugdiensten der CLR (Common Language Runtime) generiert und dem Objekt zugeordnet.

> [!NOTE]
> Objekt-IDs erstellen schwache Verweise, die nicht verhindern, dass das Objekt in die Garbage Collection aufgenommen wird. Sie gelten nur für die aktuelle Debugsitzung.

Im folgenden Code erstellt die `MakePerson()`-Methode eine `Person` mithilfe einer lokalen Variablen:

```csharp
class Person
{
    public Person(string name)
    {
        Name = name;
    }
    public string Name { get; set; }
}

public class Program
{
    static List<Person> _people = new List<Person>();
    public static void Main(string[] args)
    {
        MakePerson();
        DoSomething();
    }

    private static void MakePerson()
    {
        var p = new Person("Bob");
        _people.Add(p);
    }

    private static void DoSomething()
    {
        // more processing
         Console.WriteLine("done");
    }
}
```

Wenn Sie den Namen der `Person` in der `DoSomething()`-Methode ermitteln möchten, können Sie im Fenster über **Wachen** einen Verweis auf die `Person` Objekt-ID hinzufügen.

1. Legen Sie einen Haltepunkt im Code fest, nachdem das `Person` Objekt erstellt wurde.

1. Beginnen Sie mit dem Debuggen.

1. Wenn die Ausführung am Haltepunkt angehalten wird, öffnen **Sie das Fenster** lokal, indem Sie **Debuggen** > **Fenster** > **lokale**auswählen.

1. Klicken Sie im **Lokal Fenster mit** der rechten Maustaste auf die `Person` Variable, und wählen Sie Objekt- **ID erstellen**aus.

   Es sollte ein Dollarzeichen ( **$** ) plus eine Zahl **im Fenster Lokal angezeigt werden** . Dies ist die Objekt-ID.

1. Fügen Sie dem **Überwachungs** Fenster die Objekt-ID hinzu, indem Sie mit der rechten Maustaste auf die Objekt-ID klicken und **Überwachung hinzufügen**auswählen

1. Legen Sie einen anderen Haltepunkt in der `DoSomething()`-Methode fest.

1. Debuggen fortsetzen. Wenn die Ausführung in der `DoSomething()`-Methode angehalten wird, zeigt das Fenster über **Wachen** das `Person` Objekt an.

   > [!NOTE]
   > Wenn Sie die Eigenschaften des Objekts anzeigen möchten, z. b. `Person.Name`, müssen Sie die Eigenschaften Auswertung aktivieren, indem Sie **Extras > ** **Optionen** > **Debuggen** > **Allgemein** auswählen > die Eigenschaften **Auswertung und andere implizite Funktionsaufrufe aktivieren**.

## <a name="dynamic-view-and-the-watch-window"></a>Dynamische Ansicht und der Überwachungsfenster

Einige Skriptsprachen (z. b. JavaScript oder python) verwenden dynamische oder [Ente](https://en.wikipedia.org/wiki/Duck_typing) Typisierung, und .NET-Version 4,0 und höher unterstützen Objekte, die in den normalen Debugfenstern schwer zu beobachten sind.

Im Fenster über **Wachen** werden diese Objekte als dynamische Objekte angezeigt, die aus Typen erstellt werden, die die <xref:System.Dynamic.IDynamicMetaObjectProvider>-Schnittstelle implementieren. Dynamische Objekt Knoten zeigen die dynamischen Member der dynamischen Objekte an, ermöglichen jedoch keine Bearbeitung der Element Werte.

Zum Aktualisieren **dynamischer Ansichts** Werte Wählen Sie das [Aktualisierungs Symbol](#bkmk_refreshWatch) neben dem Knoten "dynamischer Objekt" aus.

Wenn Sie nur die **dynamische Ansicht** für ein Objekt anzeigen möchten, fügen Sie einen **dynamischen** Format Bezeichner nach dem dynamischen Objektnamen im **Überwachungs** Fenster hinzu:

- Für C#: `ObjectName, dynamic`
- Für Visual Basic: `$dynamic, ObjectName`

>[!NOTE]
>- Der C# Debugger wertet die Werte in der **dynamischen Ansicht** nicht automatisch erneut aus, wenn Sie zur nächsten Codezeile wechseln.
>- Der Visual Basic Debugger aktualisiert die durch die **dynamische Ansicht**hinzugefügten Ausdrücke automatisch.
>- Wenn Sie die Member einer **dynamischen Ansicht** auswerten, kann das zu [Nebenwirkungen](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)) führen.

**So fügen Sie eine neue Überwachungs Variable ein, die ein Objekt in ein dynamisches Objekt umwandelt:**

1. Klicken Sie mit der rechten Maustaste auf ein untergeordnetes Element einer **dynamischen Ansicht**.
1. Wählen Sie **Überwachung hinzufügen**aus. Der `object.name` wird `((dynamic) object).name` und wird in einem neuen **Überwachungs** Fenster angezeigt.

Der Debugger fügt **dem Fenster Auto** außerdem einen **dynamischen Ansichts** untergeordneten Knoten des-Objekts hinzu. Wählen **Sie zum Öffnen des Fensters** Auto während des Debuggens > Windows ** > Auto** **Debuggen** aus.

Die **dynamische Ansicht** verbessert auch das Debuggen von COM-Objekten. Wenn der Debugger zu einem COM-Objekt gelangt, das in **System. __ComObject**integriert ist, wird ein **dynamischer Ansichts** Knoten für das-Objekt hinzugefügt.

## <a name="observe-a-single-variable-or-expression-with-quickwatch"></a>Beobachten einer einzelnen Variable oder eines Ausdrucks mit der schnell Überwachung

Sie können **schnell Überwachung** verwenden, um eine einzelne Variable zu beobachten.

Beispielsweise für den folgenden Code:

```csharp
static void Main(string[] args)
{
    int a, b;
    a = 1;
    b = 2;
    for (int i = 0; i < 10; i++)
    {
        a = a + b;
    }
}
```

Um die `a` Variable zu beobachten,

1. Legen Sie einen Haltepunkt in der Zeile `a = a + b;` fest.

1. Beginnen Sie mit dem Debuggen. Die Ausführung wird am Haltepunkt angehalten.

1. Wählen Sie die Variable aus, die im Code `a` wird.

1. Wählen Sie **Debuggen** > **schnell Überwachung**, drücken Sie **UMSCHALT**+**F9**, oder klicken Sie mit der rechten Maustaste, und wählen Sie **schnell Überwachung**

   Das Dialogfeld **schnell Überwachung** wird angezeigt. Die `a` Variable befindet sich im Feld **Ausdruck** mit dem **Wert** **1**.

   ![Quickwatch-Variable](../debugger/media/quickwatchvariable.png "Quickwatch-Variable")

1. Wenn Sie einen Ausdruck mit der Variablen auswerten möchten, geben Sie im Feld **Ausdruck** einen Ausdruck ein, z. b. `a + b`, und wählen Sie **neu auswerten**aus.

   ![Quickwatch-Ausdruck](../debugger/media/quickwatchexpression.png "Quickwatch-Ausdruck")

1. Um die Variable oder den Ausdruck aus der **schnell Überwachung** dem Fenster über **Wachen** hinzuzufügen, wählen Sie **Überwachung hinzufügen**aus.

1. Wählen Sie **Schließen** aus, um das Fenster **schnell Überwachung** zu schließen. (**Schnell Überwachung** ist ein modales Dialogfeld, sodass Sie das Debuggen nicht fortsetzen können, solange es geöffnet ist.)

1. Debuggen fortsetzen. Sie können die Variable im Fenster über **Wachen** beobachten.

## <a name="see-also"></a>Siehe auch
- [What is debugging? (Was bedeutet „Debuggen“?)](../debugger/what-is-debugging.md)
- [Debugging techniques and tools (Debugverfahren und -tools)](../debugger/write-better-code-with-visual-studio.md)
- [Erster Einblick in das Debuggen](../debugger/debugger-feature-tour.md)
- [Debuggerfenster](../debugger/debugger-windows.md)
