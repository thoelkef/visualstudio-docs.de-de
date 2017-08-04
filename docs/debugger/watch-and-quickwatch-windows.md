---
title: "Fenster &quot;&#220;berwachen&quot; und &quot;Schnell&#252;berwachung&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.watch"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
helpviewer_keywords: 
  - "Debuggen [Visual Studio], Überwachen (Fenster)"
  - "Ausdrücke [Debugger], Auswerten"
  - "Variablen [Debugger], Auswerten"
  - "Ausdrucksauswertung"
  - "Register, Auswerten"
  - "Debuggen [Visual Studio], Ausdrucksauswertung"
ms.assetid: d5c18377-2a0e-4819-a645-407e24ccc58c
caps.latest.revision: 45
caps.handback.revision: 44
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Fenster &quot;&#220;berwachen&quot; und &quot;Schnell&#252;berwachung&quot;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können die Fenster **Überwachen** \(**Debuggen \> Fenster \> Überwachen \> Überwachen \(1, 2, 3, 4\)**\) und **Schnellüberwachung** \(**Debuggen \> Schnellüberwachung**\) verwenden, um Variablen und Ausdrücke während einer Debugsitzung zu überwachen. Der Unterschied besteht darin, dass im Fenster **Überwachen** mehrere Variablen angezeigt werden können, im Fenster **Schnellüberwachung** hingegen jeweils nur eine Variable.  
  
## Beobachten einer einzelnen Variable im Fenster "Schnellüberwachung"  
 Sie können das Fenster **Schnellüberwachung** verwenden, um eine einzelne Variable zu beobachten. Wenn Ihr Code beispielsweise folgendermaßen lautet:  
  
```c#  
static void Main(string[] args) { int a, b; a = 1; b = 2; for (int i = 0; i < 10; i++) { a = a + b; } }  
```  
  
 Sie können die Variable "a" im Fenster "Schnellüberwachung" wie folgt beobachten:  
  
1.  Legen Sie einen Haltepunkt in der Zeile `a = a + b;` fest.  
  
2.  Beginnen Sie mit dem Debuggen. Die Ausführung hält am Haltepunkt an.  
  
3.  Öffnen Sie das Fenster **Schnellüberwachung** \(klicken Sie mit der rechten Maustaste auf "a", wählen Sie dann **Debuggen \> Schnellüberwachung** aus, oder drücken Sie **UMSCHALT\+F9**\). Sie können das Fenster öffnen und die Variable "a" dem Fenster **Ausdruck** hinzufügen. Klicken Sie dann auf **Neu auswerten**. Die Variable "a" sollte im Fenster **Werte** mit einem Wert von 2 angezeigt werden.  
  
4.  Das Fenster **Schnellüberwachung** ist ein modales Dialogfeld, d. h., Sie können den Debugvorgang nicht fortsetzen, solange es geöffnet ist. Sie können die Variable dem Fenster **Überwachen** hinzufügen, indem Sie auf **Überwachung hinzufügen** klicken.  
  
5.  Schließen Sie das Fenster **Schnellüberwachung**. Nun können Sie den Debugvorgang fortsetzen, während Sie den Wert im Fenster **Überwachen** beobachten  
  
## Beobachten von Variablen im Fenster "Überwachen"  
 Mehrere Variablen können Sie im Fenster **Überwachen** beobachten. Wenn Ihr Code beispielsweise folgendermaßen lautet:  
  
```c#  
static void Main(string[] args) { int a, b, c; a = 1; b = 2; c = 0; for (int i = 0; i < 10; i++) { a++; b *= 2; c = a + b; } }  
  
```  
  
 Fügen Sie die Werte der drei Variablen dem Fenster "Überwachen" wie folgt hinzu:  
  
1.  Legen Sie einen Haltepunkt in der Zeile `c = a + b;` fest.  
  
2.  Starten Sie das Debugging \(**F5**\). Die Ausführung hält am Haltepunkt an.  
  
3.  Öffnen Sie das Fenster "Überwachen" \(**Debuggen \> Fenster \> Überwachen \> Überwachen 1** oder **STRG\+ALT\+W, 1**\).  
  
4.  Fügen Sie die Variable `a` der ersten Zeile hinzu, die Variable `b` der zweiten Zeile und die Variable `c` der dritten Zeile.  
  
5.  Debuggen fortsetzen.  
  
 Sie sollten sehen, wie sich die Variablenwerte ändern, während Sie die `for`\-Schleife durchlaufen.  
  
 Wenn Sie in systemeigenen Code programmieren, müssen Sie in einigen Fällen den Kontext eines Variablennamens oder eines Ausdruck qualifizieren, der einen Variablennamen enthält. Mit dem Kontext sind die Funktion, die Quelldatei und das Modul gemeint, in denen eine Variable enthalten ist. Falls Sie den Kontext qualifizieren müssen, können Sie dazu die Kontextoperatorsyntax verwenden. Weitere Informationen finden Sie unter "Ausdrücke \(C\+\+\)".  
  
## Beobachten von Ausdrücken im Fenster "Überwachen"  
 Nun erfahren Sie, wie Sie Ausdrücke beobachten können. Sie können jeden gültigen vom Debugger erkannten Ausdruck hinzufügen.  
  
 Wenn Sie z. B. über den im vorherigen Beispiel aufgeführten Code verfügen, können Sie den Mittelwert der drei Werte wie folgt ermitteln:  
  
 ![WatchExpression](~/debugger/media/watchexpression.png "WatchExpression")  
  
 Im Allgemeinen entsprechen die Regeln zum Auswerten von Ausdrücken im Fenster **Überwachen** den Regeln zum Auswerten von Ausdrücken in Ihrer Codesprache. Wenn der Ausdruck einen Syntaxfehler aufweist, können Sie den gleichen Compilerfehler wie im Code\-Editor erwarten. Im Folgenden ein Beispiel:  
  
 ![WatchExpressionError](~/debugger/media/watchexpressionerror.png "WatchExpressionError")  
  
##  <a name="bkmk_refreshWatch"></a> Aktualisieren von veralteten Werten im Fenster "Überwachen"  
 Unter bestimmten Umständen wird ein Aktualisierungssymbol \(ein Kreis mit zwei Pfeilen oder ein Kreis mit zwei Wellenlinien\) angezeigt, wenn ein Ausdruck im Fenster **Überwachen** ausgewertet wird.  Beispiel: Wenn Sie die Eigenschaftenauswertung deaktiviert haben \(**Tools \> Optionen \> Debugging \> Eigenschaftenauswertung und andere implizite Funktionsaufrufe zulassen**\) und der folgende Code angezeigt wird:  
  
```c#  
static void Main(string[] args) { List<string> list = new List<string>(); list.Add("hello"); list.Add("goodbye"); }  
  
```  
  
 Wenn Sie eine Überwachung für die `Count`\-Eigenschaft der Liste festlegen, sollte in etwa Folgendes angezeigt werden:  
  
 ![RefreshWatch](../debugger/media/refreshwatch.png "RefreshWatch")  
  
 Dies weist auf einen Fehler oder auf einen veralteten Wert hin. Sie können den Wert in der Regel durch Klicken auf das Symbol aktualisieren, aber es gibt auch Fälle, in denen Sie ihn nicht aktualisieren möchten. Zunächst müssen Sie wissen, warum der Wert nicht ausgewertet wurde.  
  
 Wenn Sie auf das Symbol zeigen, wird eine QuickInfo mit Informationen darüber angezeigt, weshalb der Ausdruck nicht ausgewertet wurde. Wenn die kreisförmig verlaufenden Pfeile angezeigt werden, wurde der Ausdruck aus einem der folgenden Gründe nicht ausgewertet:  
  
-   •	Beim Auswerten des Ausdrucks ist ein Fehler aufgetreten. So kann beispielsweise ein Timeout aufgetreten sein, oder eine Variable kann außerhalb des gültigen Bereichs liegen.  
  
-   •	Der Ausdruck enthält einen Funktionsaufruf, der einen Nebeneffekt in der Anwendung auslösen könnte \(siehe [Nebeneffekte und Ausdrücke](#bkmk_sideEffects)\).  
  
-   Die automatische Auswertung von Eigenschaften\- und impliziten Funktionsaufrufen durch den Debugger ist deaktiviert \(**Tools \> Optionen \> Debugging \> Eigenschaftenauswertung und andere implizite Funktionsaufrufe zulassen**\). In diesem Fall kann der Ausdruck nicht automatisch ausgewertet werden.  
  
 Klicken Sie zum Aktualisieren des Werts auf das Aktualisierungssymbol, oder drücken Sie die LEERTASTE. Der Debugger versucht, den Ausdruck neu auszuwerten. Wenn das Aktualisierungssymbol angezeigt wurde, weil die automatische Auswertung von Eigenschaften und impliziten Nebeneffekten deaktiviert war, kann der Ausdruck ausgewertet werden.  
  
 Wenn Sie ein Symbol in Form eines Kreises mit zwei Wellenlinien sehen, die Threads ähneln, wurde der Ausdruck aufgrund einer möglichen threadübergreifenden Abhängigkeit nicht ausgewertet. Mit anderen Worten: Für die Auswertung des Codes müssen andere Threads in der Anwendung vorübergehend ausgeführt werden. Wenn Sie sich im Unterbrechungsmodus befinden, sind alle Threads in der Anwendung typischerweise angehalten. Wenn die vorübergehende Ausführung anderer Threads zugelassen wird, kann dies unerwartete Auswirkungen auf den Zustand des Programms nach sich ziehen, und der Debugger ignoriert Ereignisse \(wie z. B. Haltepunkte und für diese Threads ausgelöste Ausnahmen\).  
  
##  <a name="bkmk_sideEffects"></a> Nebeneffekte und Ausdrücke  
 Die Auswertung bestimmter Ausdrücke kann zur Änderung des Werts einer Variablen führen oder sich auf den Programmzustand auswirken. Die Auswertung des folgenden Ausdrucks ändert beispielsweise den Wert von `var1`:  
  
```  
var1 = var2  
```  
  
 Dies wird als [Nebeneffekt](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)) bezeichnet. Nebeneffekte können das Debugging erschweren, da sie die Funktionsweise des Programms ändern.  
  
 Ein Ausdruck mit Nebeneffekten wird nur bei der ersten Eingabe ausgewertet. Nachfolgende Auswertungen werden deaktiviert. Sie können dieses Verhalten manuell überschreiben, indem Sie neben dem Wert auf das Aktualisierungssymbol klicken.  
  
 Eine Möglichkeit, um alle Nebeneffekte zu vermeiden, besteht darin, die automatische Funktionsauswertung zu deaktivieren \(**Tools \> Optionen \> Debugging \> Eigenschaftenauswertung und andere implizite Funktionsaufrufe zulassen**\).  
  
 Wenn die Auswertung von Eigenschaften oder impliziten Funktionen deaktiviert ist, können Sie die Auswertung mithilfe des **ac**\-Formatmodifizierers erzwingen \(nur für C\#\). Siehe [Formatbezeichner in C\#](../debugger/format-specifiers-in-csharp.md).  
  
## Verwenden von Objekt\-IDs im Fenster "Überwachen" \(C\# und Visual Basic\)  
 Es kann durchaus sein, dass Sie das Verhalten eines bestimmten Objekts beobachten möchten. Beispielsweise möchten Sie ein Objekt nachverfolgen, auf das eine lokale Variable verweist, nachdem diese Variable den Gültigkeitsbereich verlassen hat. In C\# und Visual Basic können Sie Objekt\-IDs für bestimmte Instanzen von Verweistypen erstellen und diese im Fenster "Überwachen" und in Haltepunktbedingungen verwenden. Die Objekt\-ID wird von den Debugdiensten der CLR \(Common Language Runtime\) generiert und dem Objekt zugeordnet.  
  
> [!NOTE]
>  Objekt\-IDs erstellen Weak\-Verweise und verhindern nicht, dass das Objekt in die Garbage Collection aufgenommen wird. Sie gelten nur für die aktuelle Debugsitzung.  
  
 Im folgenden Code erstellt eine Methode eine `Person` mithilfe einer lokalen Variablen. Den Namen der `Person` finden Sie in einer anderen Methode heraus:  
  
```c#  
class Person { public Person(string name) { Name = name; } public string Name { get; set; } } public class Program { List<Person> _people = new List<Person>(); public static void Main(string[] args) { MakePerson(); DoSomething(); } private static void MakePerson() { var p = new Person("Bob"); _people.Add(p); } private static void DoSomething() { // more processing Console.WriteLine("done"); } }  
  
```  
  
 Sie können wie folgt einen Verweis auf dieses `Person`\-Objekt im Fenster **Überwachen** hinzufügen:  
  
1.  Legen Sie im Code nach der Erstellung des Objekts einen Haltepunkt fest.  
  
2.  Starten Sie das Debugging, und suchen Sie die Variable, wenn die Ausführung im Haltepunkt anhält, im Fenster **Lokale**, klicken Sie mit der rechten Maustaste darauf, und wählen Sie **Objekt\-ID erstellen** aus.  
  
3.  Sie sollten ein **$** und eine Zahl im **Lokalfenster** sehen. Dies ist die Objekt\-ID.  
  
4.  Fügen Sie die Objekt\-ID dem Fenster "Überwachen" hinzu.  
  
5.  Legen Sie einen Haltepunkt dort fest, wo Sie das Verhalten des Objekts beobachten möchten.  Im oben stehenden Code ist das in der `DoSomething()`\-Methode.  
  
6.  Setzen Sie das Debugging fort. Wenn die Ausführung in der `DoSomething()`Methode anhält, wird im Fenster **Überwachen** das Objekt `Person` angezeigt.  
  
> [!NOTE]
>  Wenn Sie die Eigenschaften des Objekts anzeigen möchten, z. B. `Person.Name` im oben stehenden Beispiel, muss die Eigenschaftenauswertung aktiviert sein.  
  
## Verwenden von Registern im Fenster "Überwachen" \(nur C\+\+\)  
 Wenn Sie systemeigenen Code debuggen, können Sie sowohl Registernamen als auch Variablennamen mit **$\<Registername\>** oder **@\<Registername\>** hinzufügen.  Weitere Informationen finden Sie unter [Pseudovariablen](../debugger/pseudovariables.md).  
  
## Dynamische Ansicht und das Fenster "Überwachen"  
 Einige Skriptsprachen \(z. B. JavaScript und Python\) verwenden eine dynamische Typisierung oder das [Ducktyping](https://en.wikipedia.org/wiki/Duck_typing), und .NET\-Sprachen \(ab Version 4.0\) unterstützen Objekte, die in den normalen Debugfenstern nur schwer beobachtet werden können, da sie möglicherweise Laufzeiteigenschaften und Methoden aufweisen, die nicht angezeigt werden können.  
  
 Wenn im Fenster "Überwachen" "a" oder ein Objekt angezeigt wird, das aus einem Typ erstellt wurde, der [IDynamicMetaObjectProvider Schnittstelle](../Topic/IDynamicMetaObjectProvider%20Interface.md) implementiert, fügt der Debugger einen bestimmten Knoten für die **dynamische Ansicht** zur Anzeige **Auto** hinzu. Der Knoten zeigt die dynamischen Member des dynamischen Objekts an, ermöglicht jedoch keine Bearbeitung der Memberwerte.  
  
 Wenn Sie in einer **dynamischen Ansicht** mit der rechten Maustaste auf ein untergeordnetes Element klicken und **Überwachung hinzufügen** auswählen, fügt der Debugger eine neuen Überwachungsvariable ein, die ein Objekt in ein dynamisches Objekt umwandelt. Mit anderen Worten: **object Name** wird zu \(**\(dynamic\)object\).Name**.  
  
 Das Auswerten der Member einer **dynamischen Ansicht** kann Nebeneffekte haben. Eine Erläuterung der Nebeneffekte finden Sie unter [Nebeneffekte und Ausdrücke](#bkmk_sideEffects). Für C\# wertet der Debugger die im Fenster **Dynamische Ansicht** angezeigten Werte nicht automatisch erneut aus, wenn Sie zur nächsten Codezeile wechseln. Visual Basic\-Ausdrücke, die über die **dynamische Ansicht** hinzugefügt werden, werden automatisch aktualisiert.  
  
 Anweisungen zum Aktualisieren der Werte im Fenster "Dynamische Ansicht" finden Sie unter [Aktualisieren von veralteten Werten im Fenster "Überwachen"](#bkmk_refreshWatch).  
  
 Wenn Sie nur die **dynamische Ansicht** für ein Objekt anzeigen möchten, können Sie den **dynamic**\-Formatbezeichner verwenden:  
  
-   C\#: **ObjectName, dynamic**  
  
-   Visual Basic:: **$dynamic, ObjectName**  
  
 Die **dynamische Ansicht** verbessert auch die Debugvorgänge für COM\-Objekte. Wenn der Debugger ein in **System.\_\_ComObject** umschlossenes COM\-Objekt findet, fügt er einen Knoten **Dynamische Ansicht** für das Objekt hinzu.  
  
## Siehe auch  
 [Debuggerfenster](../debugger/debugger-windows.md)