---
title: Einstellen einer Uhr für Variablen | Microsoft Docs
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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301014"
---
# <a name="watch-variables-with-watch-windows-and-quickwatch"></a>Beobachten von Variablen mit Watch-Fenstern und QuickWatch

Während des Debuggens können Sie Mithilfe von **Überwachungsfenstern** und **QuickWatch** Variablen und Ausdrücke anzeigen. Die Fenster sind nur während einer Debugsitzung verfügbar.

**Überwachungsfenster** können beim Debuggen mehrere Variablen gleichzeitig anzeigen. Das **QuickWatch-Dialogfeld** zeigt gleichzeitig eine einzelne Variable an und muss geschlossen werden, bevor das Debuggen fortgesetzt werden kann.

Wenn Sie zum ersten Mal versucht haben, Code zu debuggen, sollten Sie [Debugging für absolute Anfänger](../debugger/debugging-absolute-beginners.md) und [Debugging-Techniken und -Tools](../debugger/write-better-code-with-visual-studio.md) lesen, bevor Sie diesen Artikel durchgehen.

## <a name="observe-variables-with-a-watch-window"></a>Variablen mit einem Überwachungsfenster beobachten

Sie können mehr als ein **Überwachungsfenster** öffnen und mehr als eine Variable in einem **Überwachungsfenster** beobachten.

Um z. B. eine Uhr `a` `b`für `c` die Werte von festzulegen, und im folgenden Code:

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

1. Legen Sie einen `c = a + b;` Haltepunkt in der Linie fest, indem Sie auf den linken Rand klicken, **Debug Toggle** > **Breakpoint**auswählen oder **F9**drücken.

1. Beginnen Sie mit dem Debuggen, indem Sie den grünen **Startpfeil** oder**Debugstart-Debugging** **auswählen,** > oder drücken Sie **F5**. Die Ausführung wird am Haltepunkt angehalten.

1. Öffnen Sie ein **Überwachungsfenster,** indem Sie**Windows** > **Watch** > **1** **debuggen** > oder **Strg**+**Alt**+**W** > **1**drücken.

   Sie können zusätzliche **Überwachungsfenster** öffnen, indem Sie Fenster **2**, **3**oder **4**auswählen.

1. Wählen Sie im **Überwachungsfenster** eine leere `a`Zeile aus, und geben Sie die Variable ein. Tun Sie `b` dasselbe für und `c`.

   ![Watch-Variablen](../debugger/media/watchvariables.png "WatchVariables")

1. Fahren Sie mit dem Debuggen fort, indem Sie **Debugstep** > **Into** auswählen oder **F11** nach Bedarf drücken, um voranzukommen. Die Variablenwerte im **Überwachungsfenster** ändern sich, `for` wenn Sie durch die Schleife iterieren.

>[!NOTE]
>Nur für C++
>- Möglicherweise müssen Sie den Kontext eines Variablennamens oder eines Ausdrucks qualifizieren, der einen Variablennamen verwendet. Der Kontext ist die Funktion, Quelldatei oder das Modul, in dem sich eine Variable befindet. Wenn Sie den Kontext qualifizieren müssen, verwenden Sie die [Syntax des Kontextoperators (C++)](../debugger/context-operator-cpp.md) im **Namen** im **Überwachungsfenster.**
>
>- Sie können Registernamen und Variablennamen mithilfe des ** $ \<&nbsp;Registernamens>** oder **Name** ** @ \<&nbsp;** des Registernamens>zum Namen im **Überwachungsfenster** hinzufügen. Weitere Informationen finden Sie unter [Pseudovariables](../debugger/pseudovariables.md).

## <a name="use-expressions-in-a-watch-window"></a>Verwenden von Ausdrücken in einem Überwachungsfenster

Sie können jeden gültigen Ausdruck beobachten, der vom Debugger in einem **Überwachungsfenster** erkannt wird.

Für den Code im vorherigen Abschnitt können Sie z. B. `(a + b + c) / 3` den Durchschnitt der drei Werte abrufen, indem Sie im **Überwachungsfenster** eingeben:

![Watch-Ausdruck](../debugger/media/watchexpression.png "Watch-Ausdruck")

Die Regeln zum Auswerten von Ausdrücken im **Überwachungsfenster** entsprechen im Allgemeinen den Regeln zum Auswerten von Ausdrücken in der Codesprache. Wenn ein Ausdruck einen Syntaxfehler aufweist, erwarten Sie denselben Compilerfehler wie im Code-Editor. Ein Tippfehler im vorhergehenden Ausdruck erzeugt diesen Fehler z. B. im **Überwachungsfenster:**

![Watch-Ausdrucksfehler](../debugger/media/watchexpressionerror.png "Watch-Ausdrucksfehler")

Ein Kreis mit zwei wellenförmigen Liniensymbolen kann im **Überwachungsfenster** angezeigt werden. Dieses Symbol bedeutet, dass der Debugger den Ausdruck aufgrund einer potenziellen Threadübergreifenden Abhängigkeit nicht auswertet. Das Auswerten des Codes erfordert, dass andere Threads in Ihrer App vorübergehend ausgeführt werden, aber da Sie sich im Unterbrechungsmodus befinden, werden in der Regel alle Threads in Ihrer App angehalten. Das vorübergehende Ausführen anderer Threads kann unerwartete Auswirkungen auf den Status Ihrer App haben, und der Debugger ignoriert möglicherweise Ereignisse wie Haltepunkte und Ausnahmen in diesen Threads.

::: moniker range=">= vs-2019" 
## <a name="search-in-the-watch-window"></a>Suchen im Überwachungsfenster

Sie können in den Spalten Name, Wert und Typ des **Überwachungsfensters** über die Suchleiste über jedem Fenster nach Schlüsselwörtern suchen. Klicken Sie auf ENTER oder wählen Sie einen der Pfeile aus, um eine Suche auszuführen. Um eine laufende Suche abzubrechen, wählen Sie das Symbol "x" in der Suchleiste aus.

Verwenden Sie die Pfeile nach links und rechts (Shift+F3 bzw. F3), um zwischen gefundenen Übereinstimmungen zu navigieren.

![Suche im Uhrenfenster](../debugger/media/ee-search-watch.png "Suche im Uhrenfenster")

Um die Suche mehr oder weniger gründlich zu gestalten, verwenden Sie die Dropdownliste **"Tiefer suchen"** oben im **Überwachungsfenster,** um auszuwählen, wie viele Ebenen tief in verschachtelte Objekte suchen möchten. 

## <a name="pin-properties-in-the-watch-window"></a>Pin-Eigenschaften im Überwachungsfenster

>[!NOTE]
> Diese Funktion wird in .NET Core 3.0 oder höher unterstützt.

Sie können Objekte schnell anhand ihrer Eigenschaften im Überwachungsfenster mit dem Werkzeug **Pinnable Properties** überprüfen.  Um dieses Werkzeug zu verwenden, bewegen Sie den Mauszeiger über eine Eigenschaft, und wählen Sie das symbolsymbol aus, das angezeigt wird, oder klicken Sie mit der rechten Maustaste, und wählen Sie die Option **Mitglied als Favorit** anheften im resultierenden Kontextmenü aus.  Dadurch wird diese Eigenschaft an den Anfang der Eigenschaftenliste des Objekts geblasen, und der Eigenschaftsname und -wert wird in der Spalte **Wert** angezeigt.  Um das Aufdecken einer Eigenschaft aufzudecken, wählen Sie das Pin-Symbol erneut aus, oder wählen Sie im Kontextmenü die Option **Element als Favorit** auflegen aus.

![Pin-Eigenschaften im Überwachungsfenster](../debugger/media/basic-pin-watch.gif "Pin-Eigenschaften im Überwachungsfenster")

Sie können auch Eigenschaftsnamen umschalten und nicht angeheftete Eigenschaften herausfiltern, wenn Sie die Eigenschaftenliste des Objekts im Überwachungsfenster anzeigen.  Sie können auf beide Optionen zugreifen, indem Sie die Schaltflächen in der Symbolleiste über dem Überwachungsfenster auswählen.

::: moniker-end

### <a name="refresh-watch-values"></a><a name="bkmk_refreshWatch"></a>Aktualisieren der Uhrwerte

Ein Aktualisierungssymbol (Kreispfeil) wird möglicherweise im **Überwachungsfenster** angezeigt, wenn ein Ausdruck ausgewertet wird. Das Aktualisierungssymbol zeigt einen Fehler oder einen Wert an, der veraltet ist.

Um den Wert zu aktualisieren, wählen Sie das Aktualisierungssymbol aus, oder drücken Sie die Leertaste. Der Debugger versucht, den Ausdruck neu auszuwerten. Es kann jedoch sein, dass Sie den Ausdruck nicht neu bewerten möchten oder können, je nachdem, warum der Wert nicht ausgewertet wurde.

Zeigen Sie mit der Maus auf das Aktualisierungssymbol, oder sehen Sie die **Spalte Wert,** weil der Ausdruck nicht ausgewertet wurde. Hierfür kann es folgende Gründe geben:

- Beim Auswerten des Ausdrucks ist ein Fehler aufgetreten, wie im vorherigen Beispiel. Es kann zu einem Timeout kommen, oder eine Variable liegt anicht im Gültigkeitsbereich.

- Der Ausdruck verfügt über einen Funktionsaufruf, der einen Nebeneffekt in der App auslösen könnte. Siehe [Ausdrucksideeffekte](#bkmk_sideEffects).

- Die automatische Auswertung von Eigenschaften und impliziten Funktionsaufrufen ist deaktiviert.

Wenn das Aktualisierungssymbol angezeigt wird, weil die automatische Auswertung von Eigenschaften und impliziten Funktionsaufrufen deaktiviert ist, können Sie es aktivieren, indem Sie In **Tools** > **Options** > **Debugging** > **General**die Option **Eigenschaftenauswertung aktivieren und andere implizite Funktionsaufrufe** auswählen.

So demonstrieren Sie mit dem Aktualisierungssymbol:

1. Deaktivieren **Sie** > unter Tools**Options** > **Debugging** > **General**das Kontrollkästchen **Eigenschaftenauswertung aktivieren und andere implizite Funktionsaufrufe.**

1. Geben Sie den folgenden Code ein, und legen `list.Count` Sie im **Überwachungsfenster** eine Uhr für die Eigenschaft fest.

   ```csharp
   static void Main(string[] args)
   {
       List<string> list = new List<string>();
       list.Add("hello");
       list.Add("goodbye");
   }
   ```

1. Beginnen Sie mit dem Debuggen. Das **Überwachungsfenster** zeigt so etwas wie die folgende Meldung an:

   ![Refresh Watch](../debugger/media/refreshwatch.png "Refresh Watch")

1. Um den Wert zu aktualisieren, wählen Sie das Aktualisierungssymbol aus, oder drücken Sie die Leertaste. Der Debugger wertet den Ausdruck neu aus.

### <a name="expression-side-effects"></a><a name="bkmk_sideEffects"></a>Expression-Nebenwirkungen

Das Auswerten einiger Ausdrücke kann den Wert einer Variablen ändern oder sich auf andere Weise auf den Status Ihrer App auswirken. Die Auswertung des folgenden Ausdrucks ändert beispielsweise den Wert von `var1`:

```csharp
var1 = var2
```

Dieser Code kann eine [Nebenwirkung](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\))verursachen . Nebenwirkungen können das Debuggen erschweren, indem Sie die Funktionsweise Ihrer App ändern.

Ein Ausdruck mit Nebenwirkungen wird nur einmal ausgewertet, wenn Sie ihn zum ersten Mal eingeben. Danach wird der Ausdruck im **Überwachungsfenster** ausgegraut angezeigt, und weitere Auswertungen sind deaktiviert. In der QuickInfo- oder **Value-Spalte** wird erläutert, dass der Ausdruck einen Nebeneffekt verursacht. Sie können eine Neubewertung erzwingen, indem Sie das Aktualisierungssymbol auswählen, das neben dem Wert angezeigt wird.

Eine Möglichkeit, die Bezeichnung von Nebenwirkungen zu verhindern, besteht darin, die automatische Funktionsauswertung auszuschalten. Deaktivieren **Sie** > unter Tools**Options** > **Debugging** > **General**die Option **Eigenschaftenauswertung und andere implizite Funktionsaufrufe aktivieren**.

Wenn die Auswertung von Eigenschaften oder impliziten Funktionsaufrufen deaktiviert ist, können Sie die Auswertung erzwingen, indem Sie den Ac-Formatmodifikator zu einer Variablen **Name** im **Überwachungsfenster** hinzufügen. **ac** Weitere Informationen finden Sie unter [Formatieren von Spezifizierern in C#](../debugger/format-specifiers-in-csharp.md).

## <a name="use-object-ids-in-the-watch-window-c-and-visual-basic"></a><a name="bkmk_objectIds"></a>Verwenden von Objekt-IDs im Überwachungsfenster (C- und Visual Basic)

Manchmal möchten Sie das Verhalten eines bestimmten Objekts beobachten. Sie können z. B. ein Objekt nachverfolgen, auf das von einer lokalen Variablen verwiesen wird, nachdem diese Variable den Gültigkeitsbereich nicht mehr erweitert hat. In C# und Visual Basic können Sie Objekt-IDs für bestimmte Instanzen von Verweistypen erstellen und diese im Fenster **Überwachen** und in Haltepunktbedingungen verwenden. Die Objekt-ID wird von den Debugdiensten der CLR (Common Language Runtime) generiert und dem Objekt zugeordnet.

> [!NOTE]
> Objekt-IDs erstellen schwache Verweise, die nicht verhindern, dass das Objekt garbage collected wird. Sie gelten nur für die aktuelle Debugsitzung.

Im folgenden Code `MakePerson()` erstellt die `Person` Methode eine mit einer lokalen Variablen:

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

Um den Namen der `Person` in `DoSomething()` der Methode zu ermitteln, `Person` können Sie einen Verweis auf die Objekt-ID im **Überwachungsfenster** hinzufügen.

1. Legen Sie einen Haltepunkt `Person` im Code fest, nachdem das Objekt erstellt wurde.

1. Beginnen Sie mit dem Debuggen.

1. Wenn die Ausführung am Haltepunkt angehalten wird, öffnen Sie das **Fenster Locals,** indem Sie**Windows** > **Locals** **debuggen** > auswählen.

1. Klicken **Locals** Sie im Fenster Locals `Person` mit der rechten Maustaste auf die Variable, und wählen Sie **Objekt-ID erstellen**aus.

   Im Fenster**$** **"Locals"** (Objektid) sollte ein Dollarzeichen ( ) sowie eine Zahl angezeigt werden.

1. Fügen Sie die Objekt-ID zum **Überwachungsfenster** hinzu, indem Sie mit der rechten Maustaste auf die Objekt-ID klicken und **"Uhr hinzufügen"** auswählen.

1. Legen Sie einen `DoSomething()` weiteren Haltepunkt in der Methode fest.

1. Debuggen fortsetzen. Wenn die Ausführung `DoSomething()` in der Methode angehalten `Person` wird, zeigt das **Überwachungsfenster** das Objekt an.

   > [!NOTE]
   > Wenn Sie die Eigenschaften des Objekts `Person.Name`anzeigen möchten, z. B. , müssen Sie die Eigenschaftenauswertung aktivieren, indem Sie **Tools** > **Options** > **Debugging** > **General** > **Enable-Eigenschaftsauswertung und andere implizite Funktionsaufrufe**auswählen.

## <a name="dynamic-view-and-the-watch-window"></a>Dynamische Ansicht und das Uhrenfenster

Einige Skriptsprachen (z. B. JavaScript oder Python) verwenden dynamische oder [Enteneingabe,](https://en.wikipedia.org/wiki/Duck_typing) und .NET Version 4.0 und höher unterstützt Objekte, die in den normalen Debugfenstern schwer zu beobachten sind.

Im **Überwachungsfenster** werden diese Objekte als dynamische Objekte angezeigt, die aus Typen erstellt werden, die die <xref:System.Dynamic.IDynamicMetaObjectProvider> Schnittstelle implementieren. Dynamische Objektknoten zeigen die dynamischen Elemente der dynamischen Objekte an, erlauben jedoch keine Bearbeitung der Elementwerte.

Um **dynamische Ansichtswerte** zu aktualisieren, wählen Sie das [Aktualisierungssymbol](#bkmk_refreshWatch) neben dem dynamischen Objektknoten aus.

Um nur die **dynamische Ansicht** für ein Objekt anzuzeigen, fügen Sie einen **dynamischen** Formatbezeichner nach dem dynamischen Objektnamen im **Überwachungsfenster** hinzu:

- Für C#: `ObjectName, dynamic`
- Für Visual Basic: `$dynamic, ObjectName`

>[!NOTE]
>- Der Debugger "C" wertet die Werte in der **dynamischen Ansicht** nicht automatisch neu aus, wenn Sie zur nächsten Codezeile gehen.
>- Der Visual Basic-Debugger aktualisiert automatisch Ausdrücke, die über die **dynamische Ansicht**hinzugefügt wurden.
>- Wenn Sie die Member einer **dynamischen Ansicht** auswerten, kann das zu [Nebenwirkungen](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)) führen.

**So fügen Sie eine neue Watch-Variable ein, die ein Objekt in ein dynamisches Objekt umgibt:**

1. Klicken Sie mit der rechten Maustaste auf ein beliebiges untergeordnetes Element einer **dynamischen Ansicht**.
1. Wählen Sie **Watch hinzufügen**. Der `object.name` `((dynamic) object).name` wird und wird in einem neuen **Überwachungsfenster** angezeigt.

Der Debugger fügt dem **Fenster "Autos"** auch einen **untergeordneten Dynamic View-Knoten** des Objekts hinzu. Um das **Fenster Autos** zu öffnen, wählen Sie während des Debuggens**Windows** > **Autos** **debuggen** > aus.

**Dynamic View** verbessert auch das Debuggen für COM-Objekte. Wenn der Debugger zu einem COM-Objekt gelangt, das in **System.__ComObject**umschlossen ist, fügt er einen **Dynamic View-Knoten** für das Objekt hinzu.

## <a name="observe-a-single-variable-or-expression-with-quickwatch"></a>Beobachten einer einzelnen Variablen oder eines Ausdrucks mit QuickWatch

Sie können **QuickWatch** verwenden, um eine einzelne Variable zu beobachten.

Zum Beispiel für den folgenden Code:

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

1. Wählen Sie `a` die Variable im Code aus.

1. Wählen Sie **QuickWatch debug** > **debug**, drücken **Sie Umschalttaste**+**F9**, oder klicken Sie mit der rechten Maustaste, und wählen Sie **QuickWatch**aus.

   Das **QuickWatch-Dialogfeld** wird angezeigt. Die `a` Variable befindet sich im **Feld Ausdruck** mit dem **Wert** **1**.

   ![QuickWatch-Variable](../debugger/media/quickwatchvariable.png "QuickWatch-Variable")

1. Um einen Ausdruck mit der Variablen auszuwerten, geben Sie einen Ausdruck ein, z. `a + b` B. im Feld **Ausdruck,** und wählen Sie **Neuauswerten**aus.

   ![QuickWatch-Ausdruck](../debugger/media/quickwatchexpression.png "QuickWatch-Ausdruck")

1. Um die Variable oder den Ausdruck aus **QuickWatch** zum **Überwachungsfenster** hinzuzufügen, wählen Sie **Uhr hinzufügen**aus.

1. Wählen Sie **Schließen** aus, um das **QuickWatch-Fenster** zu schließen. (**QuickWatch** ist ein modales Dialogfeld, sodass Sie das Debuggen nicht fortsetzen können, solange es geöffnet ist.)

1. Debuggen fortsetzen. Sie können die Variable im **Überwachungsfenster** beobachten.

## <a name="see-also"></a>Weitere Informationen
- [Was bedeutet „Debuggen“?](../debugger/what-is-debugging.md)
- [Debugverfahren und -tools](../debugger/write-better-code-with-visual-studio.md)
- [Erster Blick auf das Debuggen](../debugger/debugger-feature-tour.md)
- [Debuggerfenster](../debugger/debugger-windows.md)
