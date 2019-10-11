---
title: Debugverfahren und -tools
description: Schreiben Sie mit weniger Fehlern besseren Code, indem Sie Visual Studio verwenden, um Ausnahmen zu beheben, Fehler zu beheben und den Code zu verbessern.
ms.custom:
- debug-experiment
- seodec18
ms.date: 01/24/2019
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b1fe0a9bb1e966bd1451bb5d816eaab814071fb5
ms.sourcegitcommit: 7825d4163e52d724e59f6c0da209af5fbef673f7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2019
ms.locfileid: "72000176"
---
# <a name="debugging-techniques-and-tools-to-help-you-write-better-code"></a>Debuggingtechniken und-Tools, mit denen Sie besseren Code schreiben

Das Beheben von Fehlern und Fehlern im Code kann zeitaufwändig und manchmal frustrierend sein. Es dauert viel Zeit, um zu erfahren, wie Sie effektiv Debuggen, aber eine leistungsstarke IDE wie Visual Studio kann Ihre Aufgabe viel leichter machen. Eine IDE kann Ihnen helfen, Fehler zu beheben und den Code schneller zu debuggen. Dies ist nicht nur das, sondern Sie kann auch Ihnen helfen, besseren Code mit weniger Fehlern zu schreiben. Unser Ziel dieses Artikels besteht darin, Ihnen einen ganzheitlichen Überblick über den "Fehlerbehebungsprozess" zu geben, damit Sie wissen, wann Sie den Code Analyzer verwenden sollten, wann der Debugger verwendet werden soll, wie Ausnahmen behoben werden und wie der Code für beabsichtigt ist. Wenn Sie bereits wissen, dass Sie den Debugger verwenden müssen, lesen Sie [zuerst den Debugger](../debugger/debugger-feature-tour.md).

In diesem Artikel wird die Nutzung der IDE erläutert, um Ihre Codierungs Sitzungen produktiver zu gestalten. Wir berühren uns für verschiedene Aufgaben, z. b.:

* Vorbereiten des Codes für das Debuggen mithilfe der Code Analyse der IDE

* Beheben von Ausnahmen (Laufzeitfehler)

* Minimieren von Fehlern durch Codieren der Absicht (mithilfe von Assert)

* Verwendungszwecke des Debuggers

Um diese Aufgaben zu veranschaulichen, zeigen wir einige der gängigsten Arten von Fehlern und Fehlern, die beim Debuggen Ihrer Apps auftreten. Obwohl der Beispielcode lautet C#, sind die konzeptionellen Informationen in der Regel C++auf, Visual Basic, JavaScript und andere von Visual Studio unterstützte Sprachen anwendbar (sofern nicht anders angegeben). Die Screenshots wurden in C# erstellt.

## <a name="create-a-sample-app-with-some-bugs-and-errors-in-it"></a>Erstellen Sie eine Beispiel-App mit einigen Fehlern und Fehlern darin.

Der folgende Code enthält einige Fehler, die Sie mithilfe der Visual Studio-IDE beheben können. Bei der App handelt es sich um eine einfache APP, die das Abrufen von JSON-Daten aus einem Vorgang simuliert, die Daten in ein Objekt deserialisiert und eine einfache Liste mit den neuen Daten aktualisiert.

So erstellen Sie die App:

1. Öffnen Sie Visual Studio, und wählen Sie **Datei** > **Neues** > -**Projekt**aus. Wählen **Sie C#unter Visualisierung** die Option **Windows-Desktop** oder **.net Core**aus, und wählen Sie dann im mittleren Bereich eine **Konsolen-App**aus.

    > [!NOTE]
    > Wenn Ihnen die Projektvorlage **Konsolenanwendung** nicht angezeigt wird, klicken Sie im linken Bereich des Dialogfelds **Neues Projekt** auf den Link **Visual Studio-Installer öffnen**. Der Visual Studio-Installer wird gestartet. Wählen Sie die Workload **.NET-Desktopentwicklung** oder **Plattformübergreifende .NET Core-Entwicklung** aus, und klicken Sie dann auf **Anpassen**.

2. Geben Sie im Feld **Name den Namen** **Console_Parse_JSON** ein, und klicken Sie auf **OK**. Visual Studio erstellt daraufhin das Projekt.

3. Ersetzen Sie den Standard Code in der *Program.cs* -Datei des Projekts durch den unten stehenden Beispielcode.

```csharp
using System;
using System.Collections.Generic;
using System.Runtime.Serialization.Json;
using System.Runtime.Serialization;
using System.IO;

namespace Console_Parse_JSON
{
    class Program
    {
        static void Main(string[] args)
        {
            var localDB = LoadRecords();
            string data = GetJsonData();

            User[] users = ReadToObject(data);

            UpdateRecords(localDB, users);

            for (int i = 0; i < users.Length; i++)
            {
                List<User> result = localDB.FindAll(delegate (User u) {
                    return u.lastname == users[i].lastname;
                    });
                foreach (var item in result)
                {
                    Console.WriteLine($"Matching Record, got name={item.firstname}, lastname={item.lastname}, age={item.totalpoints}");
                }
            }

            Console.ReadKey();
        }

        // Deserialize a JSON stream to a User object.
        public static User[] ReadToObject(string json)
        {
            User deserializedUser = new User();
            User[] users = { };
            MemoryStream ms = new MemoryStream(Encoding.UTF8.GetBytes(json));
            DataContractJsonSerializer ser = new DataContractJsonSerializer(users.GetType());

            users = ser.ReadObject(ms) as User[];

            ms.Close();
            return users;
        }

        // Simulated operation that returns JSON data.
        public static string GetJsonData()
        {
            string str = "[{ \"points\":4o,\"firstname\":\"Fred\",\"lastname\":\"Smith\"},{\"lastName\":\"Jackson\"}]";
            return str;
        }

        public static List<User> LoadRecords()
        {
            var db = new List<User> { };
            User user1 = new User();
            user1.firstname = "Joe";
            user1.lastname = "Smith";
            user1.totalpoints = 41;

            db.Add(user1);

            User user2 = new User();
            user2.firstname = "Pete";
            user2.lastname = "Peterson";
            user2.totalpoints = 30;

            db.Add(user2);

            return db;
        }
        public static void UpdateRecords(List<User> db, User[] users)
        {
            bool existingUser = false;

            for (int i = 0; i < users.Length; i++)
            {
                foreach (var item in db)
                {
                    if (item.lastname == users[i].lastname && item.firstname == users[i].firstname)
                    {
                        existingUser = true;
                        item.totalpoints += users[i].points;

                    }
                }
                if (existingUser == false)
                {
                    User user = new User();
                    user.firstname = users[i].firstname;
                    user.lastname = users[i].lastname;
                    user.totalpoints = users[i].points;

                    db.Add(user);
                }
            }
        }
    }

    [DataContract]
    internal class User
    {
        [DataMember]
        internal string firstname;

        [DataMember]
        internal string lastname;

        [DataMember]
        // internal double points;
        internal string points;

        [DataMember]
        internal int totalpoints;
    }
}
```

## <a name="find-the-red-and-green-squiggles"></a>Suchen Sie die roten und grünen Wellenlinien.

Bevor Sie versuchen, die Beispiel-APP zu starten und den Debugger auszuführen, überprüfen Sie den Code im Code-Editor auf die roten und grünen Wellenlinien. Diese Stellen Fehler und Warnungen dar, die durch die Code Analyse der IDE identifiziert werden. Die roten Wellenlinien sind Kompilierzeitfehler, die Sie beheben müssen, bevor Sie den Code ausführen können. Bei den grünen Wellenlinien handelt es sich um Warnungen. Obwohl Sie Ihre APP häufig ausführen können, ohne die Warnungen zu beheben, können Sie eine Fehlerquelle sein, und Sie sparen sich häufig Zeit und Probleme, indem Sie Sie untersuchen. Diese Warnungen und Fehler werden auch im **Fehlerliste** Fenster angezeigt, wenn Sie eine Listenansicht bevorzugen.

In der Beispiel-App werden mehrere rote Wellenlinien angezeigt, die Sie beheben müssen, und ein grünes Bild, das Sie betrachten. Dies ist der erste Fehler.

![Fehler, der als rote Wellenlinie angezeigt wird.](../debugger/media/write-better-code-red-squiggle.png)

Um diesen Fehler zu beheben, sehen Sie sich ein weiteres Feature der IDE an, das durch das Glühbirnen Symbol dargestellt wird.

## <a name="check-the-light-bulb"></a>Überprüfen Sie die Glühbirne!

Die erste rote Wellenlinie stellt einen Kompilierzeitfehler dar. Bewegen Sie den Mauszeiger darüber, und die Meldung ```The name `Encoding` does not exist in the current context``` angezeigt.

Beachten Sie, dass dieser Fehler ein Glühbirnen Symbol unten links anzeigt. Zusammen mit dem Schrauben Schraubensymbol ![schrauben Schraubensymbol @ no__t-1 stellt das Glühbirnen Symbol ![LIGHT Bulb Icon @ no__t-3 schnelle Aktionen dar, mit denen Sie Code Inline beheben oder umgestalten können. Die Glühbirne stellt Probleme dar, die Sie beheben *sollten* . Der Schraubendreher ist für Probleme, die Sie beheben können. Verwenden Sie die erste vorgeschlagene Korrektur, um diesen Fehler zu beheben, indem Sie auf der linken Seite auf " **System. Text** " klicken.

![Verwenden der Glühbirne zum Korrigieren von Code](../debugger/media/write-better-code-missing-include.png)

Wenn Sie auf dieses Element klicken, fügt Visual Studio die `using System.Text`-Anweisung am Anfang der *Program.cs* -Datei hinzu, und die rote Wellenlinie verschwindet. (Wenn Sie nicht sicher sind, was eine vorgeschlagene Korrektur tun wird, wählen Sie den Link **Vorschau der Änderungen** auf der rechten Seite aus, bevor Sie die Korrektur anwenden.)

Der vorherige Fehler ist ein allgemeiner Fehler, den Sie normalerweise beheben, indem Sie dem Code eine neue `using`-Anweisung hinzufügen. Es gibt mehrere häufige, ähnliche Fehler, wie z. b. ```The type or namespace `Name` cannot be found.``` diese Arten von Fehlern können auf einen fehlenden Assemblyverweis hindeuten (Klicken Sie mit der rechten Maustaste auf das Projekt, wählen Sie  > -**Verweis** **Hinzufügen**), ein falsch geschriebener Name oder eine fehlende Bibliothek aus, die Sie benötigen. um (für hinzu C#zufügen, klicken Sie mit der rechten Maustaste auf das Projekt und wählen **nuget-Pakete verwalten**aus.)

## <a name="fix-the-remaining-errors-and-warnings"></a>Beheben der restlichen Fehler und Warnungen

In diesem Code sind einige weitere Wellenlinien zu sehen. Hier sehen Sie einen allgemeinen Typkonvertierungs Fehler. Wenn Sie auf die Wellenlinie zeigen, sehen Sie, dass der Code versucht, eine Zeichenfolge in eine ganze Zahl zu konvertieren. Dies wird nicht unterstützt, es sei denn, Sie fügen expliziten Code hinzu, um die Konvertierung vorzunehmen.

![Typkonvertierungs Fehler](../debugger/media/write-better-code-conversion-error.png)

Da der Code Analyzer ihre Absicht nicht erraten kann, gibt es keine Glühbirnen, die Ihnen dabei helfen, dieses Mal zu unterstützen. Um diesen Fehler zu beheben, müssen Sie die Absicht des Codes kennen. In diesem Beispiel ist es nicht allzu schwer zu erkennen, dass `points` ein numerischer Wert (Integer) sein sollte, da Sie versuchen, `points` zu `totalpoints` hinzuzufügen.

Um diesen Fehler zu beheben, ändern Sie den `points`-Member der `User`-Klasse von:

```csharp
[DataMember]
internal string points;
```

in:

```csharp
[DataMember]
internal int points;
```

Die roten Wellenlinien im Code-Editor verschwinden.

Zeigen Sie dann auf die grüne Wellenlinie in der Deklaration des `points`-Datenmembers. Der Code Analyse zeigt Ihnen, dass der Variablen nie ein Wert zugewiesen wird.

![Warnmeldung für nicht zugewiesene Variable](../debugger/media/write-better-code-warning-message.png)

In der Regel ist dies ein Problem, das behoben werden muss. Allerdings speichern Sie in der Beispiel-APP tatsächlich während des Deserialisierungsprozesses Daten in der `points`-Variablen und fügen diesen Wert dann dem Datenmember `totalpoints` hinzu. In diesem Beispiel wissen Sie den Zweck des Codes und können die Warnung gefahrlos ignorieren. Wenn Sie die Warnung jedoch vermeiden möchten, können Sie den folgenden Code ersetzen:

```csharp
item.totalpoints = users[i].points;
```

durch diesen:

```csharp
item.points = users[i].points;
item.totalpoints += users[i].points;
```

Die grüne Wellenlinie wird entfernt.

## <a name="fix-an-exception"></a>Beheben einer Ausnahme

Wenn Sie alle roten Wellenlinien korrigiert und behoben oder zumindest untersucht haben (alle grünen Wellenlinien), können Sie den Debugger starten und die app ausführen.

Drücken Sie die Taste **F5** (**Debuggen > Debuggen starten**), oder klicken Sie in der Symbolleiste „Debuggen“ auf die Schaltfläche **Debuggen starten** ![Debuggen starten](../debugger/media/dbg-tour-start-debugging.png "Start Debugging").

An diesem Punkt löst die Beispiel-App eine `SerializationException`-Ausnahme aus (ein Laufzeitfehler). Das heißt, die APP wählt die Daten aus, die Sie serialisieren möchten. Da Sie die APP im Debugmodus (Debugger angefügt) gestartet haben, führt die Ausnahme Unterstützung des Debuggers Sie direkt zu dem Code, der die Ausnahme ausgelöst hat, und gibt Ihnen eine hilfreiche Fehlermeldung.

![Eine SerializationException tritt auf.](../debugger/media/write-better-code-serialization-exception.png)

Die Fehlermeldung weist Sie darauf hin, dass der Wert `4o` nicht als ganze Zahl analysiert werden kann. In diesem Beispiel wissen Sie, dass die Daten schlecht sind: `4o` sollte `40` sein. Wenn Sie jedoch nicht die Kontrolle über die Daten in einem realen Szenario haben (z.b., wenn Sie es von einem Webdienst erhalten), was tun Sie damit? Wie lösen Sie dieses Problem?

Wenn Sie auf eine Ausnahme reagieren, müssen Sie eine Reihe von Fragen stellen (und beantworten):

* Handelt es sich bei dieser Ausnahme um einen Fehler, den Sie beheben können? Oder:

* Ist diese Ausnahme etwas, das Ihre Benutzer möglicherweise bemerken?

Wenn dies der erste ist, beheben Sie den Fehler. (In der Beispiel-App bedeutet das, dass die fehlerhaften Daten behoben werden müssen.) Wenn dies der zweite ist, müssen Sie möglicherweise die Ausnahme in Ihrem Code mithilfe eines `try/catch`-Blocks behandeln (im nächsten Abschnitt werden andere mögliche Strategien erläutert). Ersetzen Sie in der Beispiel-App den folgenden Code:

```csharp
users = ser.ReadObject(ms) as User[];
```

durch den folgenden:

```csharp
try
{
    users = ser.ReadObject(ms) as User[];
}
catch (SerializationException)
{
    Console.WriteLine("Give user some info or instructions, if necessary");
    // Take appropriate action for your app
}
```

Ein `try/catch`-Block hat einige Leistungseinbußen, sodass Sie Sie nur verwenden möchten, wenn Sie Sie wirklich benötigen, d. h. wo (a) Sie in der Releaseversion der APP vorkommen können, und wo (b) die Dokumentation für die Methode anzeigt, dass Sie die Ausnahme überprüfen sollten (als Das Zusammenstellen der Dokumentation ist fertiggestellt!). In vielen Fällen können Sie eine Ausnahme ordnungsgemäß behandeln, und der Benutzer muss diese nicht kennen.

Im folgenden finden Sie einige wichtige Tipps für die Ausnahmebehandlung:

* Vermeiden Sie die Verwendung eines leeren Catch-Blocks, wie z. b. `catch (Exception) {}`, der keine geeignete Aktion zum verfügbar machen oder behandeln eines Fehlers ausführt. Ein leerer oder nicht informativer catch-Block kann Ausnahmen ausblenden und die debuggingerstellung Ihres Codes erschweren.

* Verwenden Sie den `try/catch`-Block um die bestimmte Funktion, die die Ausnahme auslöst (`ReadObject` in der Beispiel-APP). Wenn Sie ihn um einen größeren Code Abschnitt herum verwenden, blenden Sie den Speicherort des Fehlers aus. Verwenden Sie z. b. den `try/catch`-Block nicht um die übergeordnete Funktion `ReadToObject`, wie hier gezeigt, oder Sie wissen nicht genau, wo die Ausnahme aufgetreten ist.

    ```csharp
    // Don't do this
    try
    {
        User[] users = ReadToObject(data);
    }
    catch (SerializationException)
    {
    }
    ```

* Für unbekannte Funktionen, die Sie in Ihre APP einschließen, insbesondere für die Interaktion mit externen Daten (z. b. eine Webanforderung), überprüfen Sie die Dokumentation, um zu sehen, welche Ausnahmen die Funktion wahrscheinlich auslöst. Dies können wichtige Informationen für die ordnungsgemäße Fehlerbehandlung und das Debuggen Ihrer APP sein.

Korrigieren Sie für die Beispiel-App den `SerializationException` in der `GetJsonData`-Methode, indem Sie `4o` in `40` ändern.

## <a name="clarify-your-code-intent-by-using-assert"></a>Verdeutlichen Sie Ihre Code Absicht mithilfe von Assert.

Klicken Sie in der Symbolleiste „Debuggen“ auf die Schaltfläche **Neu starten** ![App neu starten](../debugger/media/dbg-tour-restart.png "RestartApp") (**STRG** + **UMSCHALT** + **F5**). Dadurch wird die app in weniger Schritten neu gestartet. Im Konsolenfenster wird die folgende Ausgabe angezeigt.

![NULL-Wert in Ausgabe](../debugger/media/write-better-code-using-assert-null-output.png)

Sie können in dieser Ausgabe etwas sehen, das nicht ganz rechts ist. " **Name** " und " **LastName** " für den dritten Datensatz sind leer.

Dies ist ein guter Zeitpunkt, über eine hilfreiche Programmier Übung zu sprechen, die häufig unterausgelastet ist, um `assert`-Anweisungen in ihren Funktionen zu verwenden. Durch Hinzufügen des folgenden Codes schließen Sie eine Lauf Zeit Überprüfung ein, um sicherzustellen, dass `firstname` und `lastname` nicht `null` sind. Ersetzen Sie den folgenden Code in der `UpdateRecords`-Methode:

```csharp
if (existingUser == false)
{
    User user = new User();
    user.firstname = users[i].firstname;
    user.lastname = users[i].lastname;
```

durch diesen:

```csharp
// Also, add a using statement for System.Diagnostics at the start of the file.
Debug.Assert(users[i].firstname != null);
Debug.Assert(users[i].lastname != null);
if (existingUser == false)
{
    User user = new User();
    user.firstname = users[i].firstname;
    user.lastname = users[i].lastname;
```

Indem Sie den Funktionen während des Entwicklungsprozesses `assert`-Anweisungen wie diese hinzufügen, können Sie die Absicht Ihres Codes angeben. Im vorherigen Beispiel geben wir Folgendes an:

* Für den Vornamen ist eine gültige Zeichenfolge erforderlich.
* Für den Nachnamen ist eine gültige Zeichenfolge erforderlich.

Durch die Angabe der Absicht auf diese Weise erzwingen Sie Ihre Anforderungen. Dies ist eine einfache und praktische Methode, die Sie verwenden können, um während der Entwicklung Fehler zu beheben. (`assert`-Anweisungen werden auch als Hauptelement in Komponententests verwendet.)

Klicken Sie in der Symbolleiste „Debuggen“ auf die Schaltfläche **Neu starten** ![App neu starten](../debugger/media/dbg-tour-restart.png "RestartApp") (**STRG** + **UMSCHALT** + **F5**).

> [!NOTE]
> Der `assert`-Code ist nur in einem Debugbuild aktiv.

Wenn Sie neu starten, hält der Debugger an der `assert`-Anweisung an, da der Ausdruck `users[i].firstname != null` zu `false` anstatt `true` ausgewertet wird.

![Assert wird in false aufgelöst.](../debugger/media/write-better-code-using-assert.png)

Der Fehler "`assert`" weist darauf hin, dass ein Problem vorliegt, das Sie untersuchen müssen. `assert` kann viele Szenarien abdecken, in denen Sie nicht notwendigerweise eine Ausnahme sehen. In diesem Beispiel wird dem Benutzer keine Ausnahme angezeigt, und ein `null`-Wert wird als `firstname` in der Liste der Datensätze hinzugefügt. Dies kann später zu Problemen führen (z. b. in der Konsolenausgabe) und das Debuggen möglicherweise erschwert werden.

> [!NOTE]
> In Szenarien, in denen eine Methode für den `null`-Wert aufgerufen wird, wird ein `NullReferenceException`-Ergebnis angezeigt. Normalerweise möchten Sie die Verwendung eines `try/catch`-Blocks nicht für eine allgemeine Ausnahme vermeiden, d. h. eine Ausnahme, die nicht an die jeweilige Bibliotheksfunktion gebunden ist. Jedes Objekt kann eine `NullReferenceException` auslösen. Wenn Sie sich nicht sicher sind, lesen Sie die Dokumentation für die Bibliotheksfunktion.

Während des Debugvorgangs ist es gut, eine bestimmte `assert`-Anweisung beizubehalten, bis Sie wissen, dass Sie Sie durch eine tatsächliche Code Korrektur ersetzen müssen. Nehmen wir an, Sie entscheiden, dass der Benutzer die Ausnahme in einem Releasebuild der APP bemerken könnte. In diesem Fall müssen Sie Code umgestalten, um sicherzustellen, dass Ihre APP keine schwerwiegende Ausnahme auslöst oder zu einem anderen Fehler führt. Um diesen Code zu korrigieren, ersetzen Sie den folgenden Code:

```csharp
if (existingUser == false)
{
    User user = new User();
```

durch den folgenden:

```csharp
if (existingUser == false && users[i].firstname != null && users[i].lastname != null)
{
    User user = new User();
```

Wenn Sie diesen Code verwenden, erfüllen Sie die Code Anforderungen, und stellen Sie sicher, dass ein Datensatz mit einem `firstname`-oder `lastname`-Wert von `null` nicht zu den Daten hinzugefügt wird.

In diesem Beispiel haben wir die beiden `assert`-Anweisungen in einer-Schleife hinzugefügt. Wenn Sie `assert` verwenden, sollten Sie in der Regel `assert`-Anweisungen am Einstiegspunkt (Anfang) einer Funktion oder Methode hinzufügen. Sie sehen sich zurzeit die `UpdateRecords`-Methode in der Beispiel-APP an. Bei dieser Methode wissen Sie, dass Sie Probleme haben, wenn eines der Methodenargumente `null` ist, und überprüfen Sie beide mit einer `assert`-Anweisung am Einstiegspunkt der Funktion.

```csharp
public static void UpdateRecords(List<User> db, User[] users)
{
    Debug.Assert(db != null);
    Debug.Assert(users != null);
```

Bei den vorangehenden Anweisungen ist ihre Absicht, dass Sie vorhandene Daten (`db`) laden und neue Daten (`users`) abrufen, bevor Sie etwas aktualisieren.

Sie können `assert` mit jeder Art von Ausdruck verwenden, der in `true` oder `false` aufgelöst wird. Sie können z. b. eine `assert`-Anweisung wie die folgende hinzufügen.

```csharp
Debug.Assert(users[0].points > 0);
```

Der vorangehende Code ist nützlich, wenn Sie die folgende Absicht angeben möchten: ein neuer Punktwert, der größer als NULL (0) ist, ist erforderlich, um den Datensatz des Benutzers zu aktualisieren.

## <a name="inspect-your-code-in-the-debugger"></a>Überprüfen des Codes im Debugger

Nun, da Sie alle wichtigen Probleme korrigiert haben, die mit der Beispiel-App falsch sind, können Sie auf andere wichtige Dinge umsteigen!

Wir haben Ihnen die Ausnahme Hilfe des Debuggers gezeigt, aber der Debugger ist ein viel leistungsfähigeres Tool, mit dem Sie auch andere Aufgaben ausführen können, wie z. b. durchlaufen des Codes und Überprüfen der Variablen. Diese leistungsfähigeren Funktionen sind in vielen Szenarien nützlich, insbesondere in folgenden Fällen:

* Sie versuchen, einen Laufzeitfehler im Code zu isolieren, können ihn jedoch nicht mithilfe der zuvor beschriebenen Methoden und Tools ausführen.

* Sie möchten den Code überprüfen, d. h., während er ausgeführt wird, um sicherzustellen, dass er sich in der erwartungsgemäß verhält und was Sie möchten.

    Es ist lehrreich, den Code während der Ausführung zu überwachen. Sie können auf diese Weise mehr über Ihren Code erfahren und häufig Fehler identifizieren, bevor Sie offensichtliche Symptome manifestieren.

Informationen dazu, wie Sie die wesentlichen Features des-Debuggers verwenden, finden Sie unter [Debugging für absolute Anfänger](../debugger/debugging-absolute-beginners.md).

## <a name="fix-performance-issues"></a>Beheben der Leistungsprobleme

Zu den Fehlern einer anderen Art gehören ineffizienter Code, der bewirkt, dass Ihre APP langsam ausgeführt wird oder zu viel Speicherplatz verwendet wird. Im Allgemeinen ist die Optimierung der Leistung etwas, das Sie später in der APP-Entwicklung durchführen. Leistungsprobleme können jedoch frühzeitig auftreten (z. b. Wenn Sie sehen, dass ein Teil Ihrer APP langsam läuft), und Sie müssen Ihre APP möglicherweise frühzeitig mit den Profil Erstellungs Tools testen. Weitere Informationen zu Profil Erstellungs Tools, wie z. b. dem CPU-Auslastungs Tool und der Speicher Analyse, finden Sie unter [First Look of the profile Tools](../profiling/profiling-feature-tour.md)

## <a name="next-steps"></a>Nächste Schritte

In diesem Artikel haben Sie gelernt, wie Sie viele gängige Fehler in Ihrem Code vermeiden und beheben können, und wann der Debugger verwendet werden soll. Im nächsten Schritt erfahren Sie mehr über die Verwendung des Visual Studio-Debuggers, um Fehler zu beheben.

> [!div class="nextstepaction"]
> [Debuggen für Einsteiger](../debugger/debugging-absolute-beginners.md)
