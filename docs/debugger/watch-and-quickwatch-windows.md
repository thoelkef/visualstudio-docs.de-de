---
title: Festlegen eines Überwachungselements für Variablen in Visual Studio | Microsoft-Dokumentation
ms.custom: H1Hack27Feb2017
ms.date: 10/11/2018
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ad08799c0dce3792e096291dfaf62d52e2515df4
ms.sourcegitcommit: 48bc8492973e93612e5afaba3b47d0f98aecf97c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2018
ms.locfileid: "49325015"
---
# <a name="set-a-watch-on-variables-using-the-watch-and-quickwatch-windows-in-visual-studio"></a>Festlegen eines überwachungselements für Variablen mit den Fenstern "überwachen" und "Schnellüberwachung" in Visual Studio

Während des Debuggens, können Sie die **Watch** und **Schnellüberwachung** Windows, um Variablen und Ausdrücke zu beobachten.  Der Unterschied besteht darin, dass im Fenster **Überwachen** mehrere Variablen angezeigt werden können, im Fenster **Schnellüberwachung** hingegen jeweils nur eine Variable.

Die Windows sind nur verfügbar, während einer Debugsitzung. Zum Öffnen der **sehen Sie sich** Fenster wählen **Debuggen** > **Windows** > **sehen Sie sich**, und wählen Sie dann auf **Überwachen 1**, **Überwachen 2**, **Überwachen 3**, oder **Überwachen 4**. Zum Öffnen der **Schnellüberwachung** Fenster entweder mit der rechten Maustaste in der Variablenwerts, und wählen **Schnellüberwachung**, oder wählen Sie einfach **Debuggen** > **Schnellüberwachung** .

## <a name="observe-variables-with-the-watch-window"></a>Beobachten Sie Variablen mit dem Fenster "überwachen"

Sie können beobachten, dass mehr als eine Variable mit der **Watch** Fenster. Wenn Ihr Code beispielsweise folgendermaßen lautet:

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

Fügen Sie die Werte der drei Variablen, die **Watch** Fenster wie folgt:

1. Wählen Sie die `c = a + b;` Zeile.

2. Festlegen eines Haltepunkts (durch Auswahl **Debuggen** > **Haltepunkt ein/aus** oder drücken F9).

3. Starten des Debuggens (F5). Die Ausführung hält am Haltepunkt an.

4. Öffnen der **Überwachen** Fenster (durch Auswahl **Debuggen** > **Windows** > **Watch**  >   **Überwachen 1**, oder drücken Strg + Alt + W, 1).

5. Wählen Sie eine leere Zeile, und geben Sie die Variable `a`. Führen Sie dann auf das gleiche gilt für Variablen `b` und `c`.

   ![Beobachten Sie Variablen](../debugger/media/watchvariables.png "WatchVariables")

6. Den fortsetzen Sie Debugvorgang, durch Drücken von F11 je nach Bedarf, um den Debugger zu gelangen.

Sie sollten sehen, wie sich die Variablenwerte ändern, während Sie die `for` -Schleife durchlaufen.

Wenn Sie in nativem Code programmieren, müssen Sie möglicherweise manchmal qualifizieren Kontext eines Variablennamens oder ein Ausdruck, der einen Variablennamen enthält. Mit dem Kontext sind die Funktion, die Quelldatei und das Modul gemeint, in denen eine Variable enthalten ist. Wenn Sie den Kontext qualifizieren müssen, können Sie die Syntax der Kontext-Operator. Weitere Informationen finden Sie unter [Kontextoperator (C++)](../debugger/context-operator-cpp.md).

## <a name="observe-expressions-with-the-watch-window"></a>Beobachten Sie Ausdrücke mit dem Fenster "überwachen"

Nun Probieren Sie stattdessen mithilfe eines Ausdrucks. Sie können jeden gültigen vom Debugger erkannten Ausdruck hinzufügen.

Z. B. Wenn Sie den im vorherigen Abschnitt aufgeführten Code verfügen, erhalten den Mittelwert der drei Werte Sie mithilfe dieses Ausdrucks:

![Überwachungsausdruck](../debugger/media/watchexpression.png "WatchExpression")

Die Regeln zum Auswerten von Ausdrücken in der **Watch** Fenster werden in der Regel identisch mit den Regeln zum Auswerten von Ausdrücken in Ihrer Codesprache. Wenn der Ausdruck einen Syntaxfehler aufweist, erwarten Sie den gleichen Compilerfehler, den im Code-Editor angezeigt werden. Im Folgenden ein Beispiel:

![Sehen Sie sich Ausdrucksfehler](../debugger/media/watchexpressionerror.png "WatchExpressionError")

## <a name="bkmk_refreshWatch"></a> Aktualisieren von Überwachungswerten, die nicht mehr aktuell sind.

Möglicherweise ein Aktualisierungssymbol (ein kreisförmigen Pfeil) angezeigt, bei der Auswertung eines Ausdrucks in der **Watch** Fenster. Wenn Sie die eigenschaftenauswertung deaktiviert haben (durch Auswahl **Tools** > **Optionen** > **Debuggen**  >   **Allgemeine**, klicken Sie dann löschen **eigenschaftenauswertung und andere implizite Funktionsaufrufe**), und Sie den folgenden Code geschrieben haben:

```csharp
static void Main(string[] args)
{
    List<string> list = new List<string>();
    list.Add("hello");
    list.Add("goodbye");
}

```

Sie sollte etwa der folgenden Abbildung angezeigt werden, setzen Sie eine Überwachung auf der `Count` -Eigenschaft der Liste:

![RefreshWatch](../debugger/media/refreshwatch.png "RefreshWatch")

Die oben stehende Abbildung zeigt einen Fehler oder ein Wert, der nicht mehr aktuell ist. Sie können den Wert in der Regel durch Auswählen des Symbols aktualisieren, aber in einigen Fällen auch nicht, um sie zu aktualisieren. Zunächst müssen Sie wissen, warum der Wert ausgewertet wurde nicht.

Eine QuickInfo wird erläutert, wie Sie warum der Ausdruck ausgewertet wurde nicht, wenn Sie auf das Symbol zeigen. Wenn die kreisförmig verlaufenden Pfeile angezeigt werden, wurde nicht der Ausdruck für eine der folgenden Gründe ausgewertet:

- Beim Auswerten des Ausdrucks ist ein Fehler aufgetreten. So kann beispielsweise ein Timeout aufgetreten sein, oder eine Variable kann außerhalb des gültigen Bereichs liegen.

- Der Ausdruck hat einen Funktionsaufruf, die einen Nebeneffekt in der Anwendung auslösen könnte (finden Sie unter den [Nebeneffekte und Ausdrücke](#bkmk_sideEffects) Abschnitt).

- Sie haben die automatische Auswertung von Eigenschaften deaktiviert, und implizite Funktionsaufrufe durch den Debugger (durch Auswahl **Tools** > **Optionen** > **Debuggen**  >  **Allgemeine**, klicken Sie dann löschen **eigenschaftenauswertung und andere implizite Funktionsaufrufe**). Der Ausdruck kann dann automatisch ausgewertet werden.

Um den Wert zu aktualisieren, wählen Sie das Symbol zum Aktualisieren oder drücken Sie die LEERTASTE. Der Debugger versucht, den Ausdruck neu auszuwerten. Das Symbol "Aktualisieren" möglicherweise angezeigt, weil die automatische Auswertung von Eigenschaften und andere implizite Funktionsaufrufe deaktiviert wurde. In diesem Fall kann der Debugger den Ausdruck auswerten.

Möglicherweise wird ein Symbol angezeigt, die ein Kreis mit zwei Wellenlinien, die Threads ähneln. Dieses Symbol weist darauf hin, dass der Debugger der Ausdruck aufgrund einer möglichen threadübergreifenden Abhängigkeit nicht. Mit anderen Worten: Für die Auswertung des Codes müssen andere Threads in der Anwendung vorübergehend ausgeführt werden. Wenn Sie sich im Unterbrechungsmodus befinden, sind alle Threads in der Anwendung typischerweise angehalten. Wenn die vorübergehende Ausführung anderer Threads zugelassen wird, kann dies unerwartete Auswirkungen auf den Zustand des Programms nach sich ziehen, und der Debugger ignoriert Ereignisse (wie z. B. Haltepunkte und für diese Threads ausgelöste Ausnahmen).

## <a name="bkmk_sideEffects"></a> Nebeneffekte und Ausdrücke

Die Auswertung bestimmter Ausdrücke kann zur Änderung des Werts einer Variablen führen oder sich auf den Programmzustand auswirken. Die Auswertung des folgenden Ausdrucks ändert beispielsweise den Wert von `var1`:

```csharp
var1 = var2
```

Dieser Code kann dazu führen, dass eine [Nebeneffekt](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)). Nebeneffekte können das Debugging erschweren, da sie die Funktionsweise des Programms ändern.

Ein Ausdruck, der bekannte Nebeneffekten wird ausgewertet, nur einmal bei der ersten Eingabe. Weitere auswertungen werden deaktiviert. Sie können dieses Verhalten manuell überschreiben, durch Auswählen des Update-Symbols, das neben dem Wert angezeigt wird.

Eine Möglichkeit, um alle Nebeneffekte zu vermeiden ist die automatische funktionsauswertung zu deaktivieren (durch Auswahl **Tools** > **Optionen** > **Debuggen**  >  **Allgemeine**, klicken Sie dann löschen **eigenschaftenauswertung und andere implizite Funktionsaufrufe**).

Wenn die Auswertung von Eigenschaften oder impliziten Funktionen deaktiviert ist, können Sie die Auswertung mithilfe des **ac** -Formatmodifizierers erzwingen (nur für C#). Finden Sie unter [Formatbezeichner in c#](../debugger/format-specifiers-in-csharp.md).

## <a name="bkmk_objectIds"></a> Verwenden von Objekt-IDs im Fenster "überwachen" (C#- und Visual Basic)

Gelegentlich möchten Sie das Verhalten eines bestimmten Objekts beobachten. Beispielsweise empfiehlt es sich um ein Objekt, das auf eine lokale Variable verweist, nachdem diese Variable den Gültigkeitsbereich verlassen hat nachzuverfolgen. In c# und Visual Basic können Sie Objekt-IDs für bestimmte Instanzen von Verweistypen erstellen und verwenden sie in der **Watch** Fenster und in haltepunktbedingungen. Die Objekt-ID wird von den Debugdiensten der CLR (Common Language Runtime) generiert und dem Objekt zugeordnet.

> [!NOTE]
> Objekt-IDs erstellen weak-Verweise, die das Objekt nicht nicht von der Garbage collection. Sie gelten nur für die aktuelle Debugsitzung.

Im folgenden Code wird eine Methode erstellt eine `Person` mithilfe einer lokalen Variablen, aber Sie möchten erfahren, welche die `Person`Name ist in einer anderen Methode:

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

Sie können wie folgt einen Verweis auf dieses `Person` -Objekt im Fenster **Überwachen** hinzufügen:

1. Wählen Sie eine Zeile im Code, der auftritt, ob das Objekt erstellt wurde.

2. Festlegen eines Haltepunkts (durch Auswahl **Debuggen** > **Haltepunkt ein/aus** oder drücken F9).

3. Beginnen Sie mit dem Debuggen.

4. Öffnen Sie nach Ausführung am Haltepunkt angehalten wird, die **"lokal"** Fenster (durch Auswahl **Debuggen** > **Windows** > **"lokal"**) mit der rechten Maustaste auf die Variable, und wählen Sie **Objekt-ID**.

   Daraufhin sollte ein Dollarzeichen (**$**) plus eine Zahl in die **"lokal"** Fenster, die Objekt-ID.

   > [!NOTE]
   > Wenn Sie die Eigenschaften des Objekts, z. B. anzeigen möchten `Person.Name`, müssen Sie die Auswertung von Eigenschaften durch Auswahl aktivieren **Tools** > **Optionen**  >   **Debuggen von** > **allgemeine**, dann **eigenschaftenauswertung und andere implizite Funktionsaufrufe**.

5. Fügen Sie den Objekt-ID, die **Watch** Fenster, indem Sie mit der rechten Maustaste die Dollarzeichen und die Anzahl, dann **Überwachung hinzufügen**.

6. Legen Sie einen Haltepunkt, wo Sie das Verhalten des Objekts beobachten möchten.  Im vorangehenden Code ist das in der `DoSomething()` Methode.

7. Debuggen fortsetzen. Beendigung der Ausführung der `DoSomething()` -Methode, die **sehen Sie sich** Fenster zeigt die `Person` Objekt.

## <a name="use-registers-in-the-watch-window-c-only"></a>Verwenden von Registern im Fenster "überwachen" (nur C++)

Sie können Registernamen und Variablennamen mit hinzufügen  **$ \<registrieren&nbsp;Name >** oder  **@ \<registrieren&nbsp;Name >** während des Debuggens von nativen Codes. Weitere Informationen finden Sie unter [Pseudovariables](../debugger/pseudovariables.md).

## <a name="dynamic-view-and-the-watch-window"></a>Dynamische Ansicht und das Fenster "überwachen"

Einige Skriptsprachen (z. B. JavaScript oder Python) verwenden eine dynamische oder [Duck-typing](https://en.wikipedia.org/wiki/Duck_typing), und .NET-Sprachen (in Version 4.0 und höher) unterstützen Objekte, die in nur schwer beobachtet die normalen Debugfenstern sind, da sie möglicherweise Laufzeiteigenschaften und Methoden, die nicht angezeigt werden können.

Die **Watch** Fenster zeigen Sie ein dynamisches Objekt, das von einem Typ erstellt wird, die implementiert möglicherweise die <xref:System.Dynamic.IDynamicMetaObjectProvider> Schnittstelle. Wenn dieses Objekt angezeigt wird, fügt der Debugger eine spezielle **dynamische Ansicht** untergeordneten Knoten des Objekts beim Öffnen der **"Auto"** Fenster (durch Auswahl **Debuggen**  >  **Windows** > **"Auto"**). Dieser Knoten zeigt die dynamischen Member des dynamischen Objekts nicht, ermöglicht jedoch Bearbeitung der Memberwerte.

Wenn Sie eine neue Überwachung einfügen wandelt Variable, die ein Objekt in ein dynamisches Objekt:

1. Mit der rechten Maustaste ein untergeordnetes Element eine **dynamische Ansicht**.
2. Wählen Sie **Überwachung hinzufügen**. Klicken Sie dann `object.name` wird `((dynamic) object).name`.

Das Auswerten der Member einer **dynamischen Ansicht** kann Nebeneffekte haben. Eine Erläuterung der Nebeneffekte, finden Sie unter den [Nebeneffekte und Ausdrücke](#bkmk_sideEffects) Abschnitt. Für C#-Code, der Debugger nicht automatisch erneut auswerten, die Werte in der **dynamische Ansicht** Wenn Sie wechseln in eine neue Zeile des Codes. Visual Basic-Ausdrücke, die über die **dynamische Ansicht** hinzugefügt werden, werden automatisch aktualisiert.

Anweisungen zum Aktualisieren der **dynamische Ansicht** -Werte finden Sie in der [Watch aktualisieren-Werte, die nicht mehr aktuell sind](#bkmk_refreshWatch) Abschnitt.

Sollten Sie nur angezeigt, die **dynamische Ansicht** für ein Objekt können Sie die **dynamische** Formatbezeichner in der **Überwachen** Fenster:

- C#: `ObjectName, dynamic`
- Visual Basic: `$dynamic, ObjectName`

Die **dynamische Ansicht** verbessert auch die Debugvorgänge für COM-Objekte. Wenn der Debugger erreicht, um ein COM-Objekt, das umschlossen **System. __ComObject**, fügt es einer **dynamische Ansicht** Knoten für das Objekt.

## <a name="observe-a-single-variable-or-expression-with-quickwatch"></a>Beachten Sie, eine einzelne Variable oder einen Ausdruck, Fenster "schnellüberwachung"

Sie können das Fenster **Schnellüberwachung** verwenden, um eine einzelne Variable zu beobachten. Wenn Ihr Code beispielsweise folgendermaßen lautet:

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

Sie können beobachten, dass eine Variable in der **Schnellüberwachung** Fenster wie folgt:

1. Legen Sie einen Haltepunkt in der Zeile `a = a + b;` fest.

2. Beginnen Sie mit dem Debuggen. Die Ausführung hält am Haltepunkt an.

3. Wählen Sie die Variable `a`.

4. Wählen Sie entweder **Debuggen** > **Schnellüberwachung** , oder drücken Sie **UMSCHALT + F9**. Die **Schnellüberwachung** Fenster wird angezeigt. In der **Wert** Feld der `a` Variable mit einem Wert von 1 angezeigt wird.

   ![Schnellüberwachung Variable](../debugger/media/quickwatchvariable.png "QuickWatchVariable")

   Geben Sie zum Auswerten eines Ausdrucks, mit der Variable einen Ausdruck ein, z. B. `a + b` auf die **Ausdruck** ein, und klicken Sie auf **neu auswerten**.

   ![Ausdruck der Schnellüberwachung](../debugger/media/quickwatchexpression.png "QuickWatchExpression")

   Variable oder einen Ausdruck zum Hinzufügen der **Watch** Fenster **Schnellüberwachung**, wählen Sie **Überwachung hinzufügen**.

   > [!NOTE]
   > Die **Schnellüberwachung** Fenster ist ein modales Dialogfeld, d. h. Sie Debugvorgang nicht fortsetzen, solange sie geöffnet ist.

5. Schließen Sie das Fenster **Schnellüberwachung** . Nun können Sie den Debugvorgang fortsetzen, während Sie den Wert im Fenster **Überwachen** .

## <a name="see-also"></a>Siehe auch

[Debuggerfenster](../debugger/debugger-windows.md)
