---
title: Legen Sie eine Überwachung auf Variablen in Visual Studio | Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 04/04/2017
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
ms.openlocfilehash: 187c9e682877a0f0633e7d3210454d40cae9de0f
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
---
# <a name="set-a-watch-on-variables-using-the-watch-and-quickwatch-windows-in-visual-studio"></a>Legen Sie eine Überwachung auf Variablen mithilfe der überwachen "und" Schnellüberwachung Fenstern in Visual Studio
Während des Debuggens, können Sie die **Überwachen** und **Schnellüberwachung** Windows, Variablen und Ausdrücke zu beobachten.  Der Unterschied besteht darin, dass im Fenster **Überwachen** mehrere Variablen angezeigt werden können, im Fenster **Schnellüberwachung** hingegen jeweils nur eine Variable. 

Die Windows sind nur während einer Debugsitzung verfügbar. So öffnen die **Überwachen** Fenster, wählen Sie **Debuggen > Windows > Überwachen > überwachen (1, 2, 3, 4)**). So öffnen die **Schnellüberwachung** Fenster entweder mit der rechten Maustaste auf die Variable, und wählen Sie **Schnellüberwachung** , oder wählen Sie **Debuggen > Schnellüberwachung**.
  
## <a name="observing-a-single-variable-with-quickwatch"></a>Beobachten einer einzelnen Variable im Fenster "Schnellüberwachung"  
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
  
 Sie können eine Variable in dem Fenster Schnellüberwachung wie folgt beobachten:  
  
1.  Legen Sie einen Haltepunkt in der Zeile `a = a + b;` fest.  
  
2.  Beginnen Sie mit dem Debuggen. Die Ausführung hält am Haltepunkt an.  
  
3.  Öffnen der **Schnellüberwachung** Fenster (mit der rechten Maustaste auf `a`, wählen Sie dann **Schnellüberwachung**, oder wählen Sie `a` , und drücken Sie **UMSCHALT + F9**).

    Daraufhin sollte eine Variable in der **Werte** angezeigt, wobei der Wert 1.

    ![Ausdruck der Schnellüberwachung](../debugger/media/watchexpression.png "QuickWatchExpression")  

    Wenn Sie einen Ausdruck mit Variablen auswerten möchten, fügen Sie einen Ausdruck wie z. B. `a + b` auf die **Ausdruck** Fenster, und klicken Sie auf **neu auswerten**. 
  
4.  Fügen Sie die Variable an die **Überwachen** Fenster **Schnellüberwachung** durch Klicken auf **Überwachung hinzufügen**. 

    > [!NOTE]
    > Die **Schnellüberwachung** Fenster ist ein modales Dialogfeld an, damit Sie den Debugvorgang nicht fortsetzen, solange sie geöffnet ist.  
  
5.  Schließen Sie das Fenster **Schnellüberwachung** . Nun können Sie den Debugvorgang fortsetzen, während Sie den Wert im Fenster **Überwachen** .  
  
## <a name="observing-variables-with-the-watch-window"></a>Beobachten von Variablen im Fenster "Überwachen"  
 Mehrere Variablen können Sie im Fenster **Überwachen** beobachten. Wenn Ihr Code beispielsweise folgendermaßen lautet:  
  
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
  
 Fügen Sie die Werte der drei Variablen dem Fenster "Überwachen" wie folgt hinzu:  
  
1.  Legen Sie einen Haltepunkt in der Zeile `c = a + b;` fest.  
  
2.  Starten Sie das Debugging (**F5**). Die Ausführung hält am Haltepunkt an.  
  
3.  Öffnen Sie das Fenster "überwachen" (**Debuggen > Windows > Überwachen > Überwachen 1**, oder **STRG + ALT + W, 1**).  
  
4.  Fügen Sie die Variable `a` der ersten Zeile hinzu, die Variable `b` der zweiten Zeile und die Variable `c` der dritten Zeile.

    Sie können Variablen hinzufügen, indem Sie auf eine leere Zeile, und Sie den Variablennamen eingeben.
  
5.  Das Debuggen fortsetzen (drücken Sie **F11** um den Debugger zu wechseln).  
  
 Sie sollten sehen, wie sich die Variablenwerte ändern, während Sie die `for` -Schleife durchlaufen.  
  
 Wenn Sie in systemeigenen Code programmieren, müssen Sie in einigen Fällen den Kontext eines Variablennamens oder eines Ausdruck qualifizieren, der einen Variablennamen enthält. Mit dem Kontext sind die Funktion, die Quelldatei und das Modul gemeint, in denen eine Variable enthalten ist. Wenn Sie den Kontext qualifizieren müssen, können Sie die Kontext-Kontextoperatorsyntax verwenden. Weitere Informationen finden Sie unter [Context Operator (C++)](../debugger/context-operator-cpp.md).  
  
## <a name="observing-expressions-with-the-watch-window"></a>Beobachten von Ausdrücken im Fenster "Überwachen"  
 Jetzt sehen wir versuchen Sie es stattdessen mithilfe eines Ausdrucks. Sie können jeden gültigen vom Debugger erkannten Ausdruck hinzufügen.  
  
 Wenn Sie z. B. über den im vorherigen Beispiel aufgeführten Code verfügen, können Sie den Mittelwert der drei Werte wie folgt ermitteln:  
  
 ![Überwachungsausdruck](../debugger/media/watchexpression.png "WatchExpression")  
  
 Im Allgemeinen entsprechen die Regeln zum Auswerten von Ausdrücken im Fenster **Überwachen** den Regeln zum Auswerten von Ausdrücken in Ihrer Codesprache. Wenn der Ausdruck einen Syntaxfehler aufweist, können Sie den gleichen Compilerfehler wie im Code-Editor erwarten. Im Folgenden ein Beispiel:  
  
 ![Sehen Sie sich Ausdrucksfehler](../debugger/media/watchexpressionerror.png "WatchExpressionError")  
  
##  <a name="bkmk_refreshWatch"></a> Aktualisieren von veralteten Werten im Fenster "Überwachen"  
 Unter bestimmten Umständen möglicherweise ein Aktualisierungssymbol (ein Pfeil mit zirkuläre) bei der Auswertung eines Ausdrucks in der **Überwachen** Fenster.  Angenommen, wenn Sie die eigenschaftenauswertung deaktiviert haben (**Extras > Optionen > Debugging > eigenschaftenauswertung und andere implizite Funktionsaufrufe**), und Sie haben den folgenden Code:  
  
```csharp  
static void Main(string[] args)  
{  
    List<string> list = new List<string>();  
    list.Add("hello");  
    list.Add("goodbye");  
}  
  
```  
  
 Wenn Sie eine Überwachung für die `Count` -Eigenschaft der Liste festlegen, sollte in etwa Folgendes angezeigt werden:  
  
 ![RefreshWatch](../debugger/media/refreshwatch.png "RefreshWatch")  
  
 Die oben stehende Abbildung zeigt einen Fehler oder ein Wert, der veraltet ist. Sie können den Wert in der Regel durch Klicken auf das Symbol aktualisieren, aber es gibt auch Fälle, in denen Sie ihn nicht aktualisieren möchten. Zunächst müssen Sie wissen, warum der Wert nicht ausgewertet wurde.  
  
 Wenn Sie auf das Symbol zeigen, wird eine QuickInfo mit Informationen darüber angezeigt, weshalb der Ausdruck nicht ausgewertet wurde.  Wenn die kreisförmig verlaufenden Pfeile angezeigt werden, wurde der Ausdruck aus einem der folgenden Gründe nicht ausgewertet:  
  
-   Beim Auswerten des Ausdrucks ist ein Fehler aufgetreten. So kann beispielsweise ein Timeout aufgetreten sein, oder eine Variable kann außerhalb des gültigen Bereichs liegen.  
  
-   Der Ausdruck enthält einen Funktionsaufruf, der einen Nebeneffekt in der Anwendung auslösen könnte (siehe [Nebeneffekte und Ausdrücke](#bkmk_sideEffects)).  
  
-   Die automatische Auswertung von Eigenschaften und impliziten Funktionsaufrufen durch den Debugger ist deaktiviert (**Tools > Optionen > Debugging > eigenschaftenauswertung und andere implizite Funktionsaufrufe**), und klicken Sie dann der Ausdruck nicht automatisch ausgewertet.  
  
 Klicken Sie zum Aktualisieren des Werts auf das Aktualisierungssymbol, oder drücken Sie die LEERTASTE. Der Debugger versucht, den Ausdruck neu auszuwerten. Wenn das Aktualisierungssymbol angezeigt wurde, weil die automatische Auswertung von Eigenschaften und andere implizite Funktionsaufrufe deaktiviert wurde, kann der Ausdruck ausgewertet werden.  
  
 Wenn Sie ein Symbol in Form eines Kreises mit zwei Wellenlinien sehen, die Threads ähneln, wurde der Ausdruck aufgrund einer möglichen threadübergreifenden Abhängigkeit nicht ausgewertet. Mit anderen Worten: Für die Auswertung des Codes müssen andere Threads in der Anwendung vorübergehend ausgeführt werden. Wenn Sie sich im Unterbrechungsmodus befinden, sind alle Threads in der Anwendung typischerweise angehalten. Wenn die vorübergehende Ausführung anderer Threads zugelassen wird, kann dies unerwartete Auswirkungen auf den Zustand des Programms nach sich ziehen, und der Debugger ignoriert Ereignisse (wie z. B. Haltepunkte und für diese Threads ausgelöste Ausnahmen).  
  
##  <a name="bkmk_sideEffects"></a> Side Effects and Expressions  
 Die Auswertung bestimmter Ausdrücke kann zur Änderung des Werts einer Variablen führen oder sich auf den Programmzustand auswirken. Die Auswertung des folgenden Ausdrucks ändert beispielsweise den Wert von `var1`:  
  
```  
var1 = var2  
```  
  
 Dieser Code kann dazu führen, dass eine [Nebeneffekt](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)). Nebeneffekte können das Debugging erschweren, da sie die Funktionsweise des Programms ändern.  
  
 Ein Ausdruck mit Nebeneffekten wird nur einmal bei der ersten Eingabe ausgewertet. Nachfolgende Auswertungen werden deaktiviert. Sie können dieses Verhalten manuell überschreiben, indem Sie neben dem Wert auf das Aktualisierungssymbol klicken.  
  
 Eine Möglichkeit, alle Nebeneffekte zu vermeiden, deaktivieren die automatische funktionsauswertung ist (**Extras > Optionen > Debugging > eigenschaftenauswertung und andere implizite Funktionsaufrufe**).  
  
 Wenn die Auswertung von Eigenschaften oder impliziten Funktionen deaktiviert ist, können Sie die Auswertung mithilfe des **ac** -Formatmodifizierers erzwingen (nur für C#). Siehe [Format Specifiers in C#](../debugger/format-specifiers-in-csharp.md).  
  
## <a name="bkmk_objectIds"></a> Verwenden von Objekt-IDs im Fenster "Überwachen" (C# und Visual Basic)  

 Es gibt Situationen, wenn Sie das Verhalten eines bestimmten Objekts beobachten möchten. Sie möchten z. B. ein Objekt verweist auf eine lokale Variable nach dem die Variable den Gültigkeitsbereich verlassen hat nachverfolgen. In C# und Visual Basic können Sie Objekt-IDs für bestimmte Instanzen von Verweistypen erstellen und diese im Fenster "Überwachen" und in Haltepunktbedingungen verwenden. Die Objekt-ID wird von den Debugdiensten der CLR (Common Language Runtime) generiert und dem Objekt zugeordnet.  
  
> [!NOTE]
>  Objekt-IDs erstellen Weak-Verweise und verhindern nicht, dass das Objekt in die Garbage Collection aufgenommen wird. Sie gelten nur für die aktuelle Debugsitzung.  
  
 Im folgenden Code wird eine Methode erstellt eine `Person` mithilfe einer lokalen Variablen, aber Sie möchten erfahren, welche die `Person`des Name ist in einer anderen Methode:  
  
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
    List<Person> _people = new List<Person>();  
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
  
1.  Legen Sie im Code nach der Erstellung des Objekts einen Haltepunkt fest.  
  
2.  Starten Sie das Debugging, und suchen Sie die Variable, wenn die Ausführung im Haltepunkt anhält, im Fenster **Lokale** , klicken Sie mit der rechten Maustaste darauf, und wählen Sie **Objekt-ID erstellen**aus.  
  
3.  Daraufhin sollte eine **$** plus einer Zahl in die **"lokal"** Fenster, in dem die Objekt-ID darstellt  
  
4.  Fügen Sie die Objekt-ID dem Fenster "Überwachen" hinzu.  
  
5.  Legen Sie einen Haltepunkt, wo Sie das Verhalten des Objekts beobachten möchten.  Im vorangehenden Code wird, die in der `DoSomething()` Methode.  
  
6.  Setzen Sie das Debugging fort. Wenn die Ausführung in der `DoSomething()` Methode anhält, wird im Fenster **Überwachen** das Objekt `Person` angezeigt.  
  
> [!NOTE]
>  Wenn Sie die Eigenschaften des Objekts, wie etwa möchten `Person.Name` im obigen Beispiel, Sie müssen eigenschaftenauswertung aktiviert sein.  
  
## <a name="using-registers-in-the-watch-window-c-only"></a>Verwenden von Registern im Fenster "Überwachen" (nur C++)  
 Wenn Sie systemeigenen Code Debuggen, können Sie sowohl Registernamen als auch Variablennamen mit hinzufügen  **$ \<RegisterName >** oder  **@ \<RegisterName >**.  Weitere Informationen finden Sie unter [Pseudovariables](../debugger/pseudovariables.md).  
  
## <a name="dynamic-view-and-the-watch-window"></a>Dynamische Ansicht und das Fenster "überwachen"  
 Einige Skriptsprachen (z. B. JavaScript oder Python) verwenden eine dynamische oder [Ente eingeben](https://en.wikipedia.org/wiki/Duck_typing), und .NET-Sprachen (in Version 4.0 und höher) unterstützen Objekte, die in schwer beobachtet die normalen Debugfenstern sind, da sie möglicherweise Laufzeiteigenschaften und Methoden, die nicht angezeigt werden können.  
  
 Wenn das Fenster "überwachen" zeigt ein Objekt erstellt, die von einem Typ, der implementiert die [IDynamicMetaObjectProvider-Schnittstelle](/dotnet/api/system.dynamic.idynamicmetaobjectprovider?view=netframework-4.7), der Debugger Fügt eine spezielle **dynamische Ansicht** Knoten, um die **"Auto"**  anzuzeigen. Der Knoten zeigt die dynamischen Member des dynamischen Objekts an, ermöglicht jedoch keine Bearbeitung der Memberwerte.  
  
 Wenn Sie in einer **dynamischen Ansicht** mit der rechten Maustaste auf ein untergeordnetes Element klicken und **Überwachung hinzufügen**auswählen, fügt der Debugger eine neuen Überwachungsvariable ein, die ein Objekt in ein dynamisches Objekt umwandelt. Mit anderen Worten: **object Name** wird zu (**(dynamic)object).Name**.  
  
 Das Auswerten der Member einer **dynamischen Ansicht** kann Nebeneffekte haben. Eine Erläuterung der Nebeneffekte finden Sie unter [Side Effects and Expressions](#bkmk_sideEffects). Für C# wertet der Debugger die im Fenster **Dynamische Ansicht** angezeigten Werte nicht automatisch erneut aus, wenn Sie zur nächsten Codezeile wechseln. Visual Basic-Ausdrücke, die über die **dynamische Ansicht** hinzugefügt werden, werden automatisch aktualisiert.  
  
 Anweisungen zum Aktualisieren der Werte im Fenster "Dynamische Ansicht" finden Sie unter [Aktualisieren von veralteten Werten im Fenster "Überwachen"](#bkmk_refreshWatch).  
  
 Wenn Sie nur die **dynamische Ansicht** für ein Objekt anzeigen möchten, können Sie den **dynamic** -Formatbezeichner verwenden:  
  
-   C#: **ObjectName, dynamic**  
  
-   Visual Basic:: **$dynamic, ObjectName**  
  
 Die **dynamische Ansicht** verbessert auch die Debugvorgänge für COM-Objekte. Wenn der Debugger ein in **System.__ComObject**umschlossenes COM-Objekt findet, fügt er einen Knoten **Dynamische Ansicht** für das Objekt hinzu.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggerfenster](../debugger/debugger-windows.md)
