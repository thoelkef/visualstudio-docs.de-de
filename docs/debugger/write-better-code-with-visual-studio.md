---
title: Debugverfahren und -tools
description: Schreiben von besserem Code mit weniger Fehlern mit Visual Studio zum Beheben von Ausnahmen, Fehler beheben und Verbessern Ihres Codes
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
ms.openlocfilehash: 6bfbcf9a63a01d391cbbc65067793d75d42899c1
ms.sourcegitcommit: d4bea2867a4f0c3b044fd334a54407c0fe87f9e8
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 04/01/2019
ms.locfileid: "58790328"
---
# <a name="debugging-techniques-and-tools-to-help-you-write-better-code"></a>Debuggen von Techniken und Tools zum Schreiben von besserem code

Beheben von Fehlern und Fehler in Ihrem Code kann ein zeitraubender – und manchmal frustrierend--Task. Dauert einige Zeit, zu erfahren, wie auf effiziente Weise zu debuggen kann, aber eine leistungsfähige IDE wie Visual Studio Ihr Auftrag viel einfacher. Eine IDE können Sie das Beheben von Fehlern und Debuggen Sie Ihren Code schneller und nicht, aber es kann auch helfen, die Sie besseren Code mit weniger Fehlern schreiben. Unser Ziel in diesem Artikel ist, erhalten Sie einen ganzheitlichen Überblick über den Prozess "Fehlerbehebung", damit Sie bei Verwendung des Code-Analyzer, wissen, verwenden Sie den Debugger, um Ausnahmen zu beheben, und das Absicht code. Wenn Sie bereits kennen, müssen Sie den Debugger verwenden, finden Sie unter [ein erster Blick auf der Debugger](../debugger/debugger-feature-tour.md).

In diesem Artikel sprechen wir über die IDE, um Ihre Codierung Sitzungen produktiver nutzen. Wir angeschnitten mehrere Tasks ein, z. B. ein:

* Vorbereiten des Codes für das Debuggen durch die Nutzung der IDE, Code-analyzer

* Gewusst wie: Beheben von Ausnahmen (Laufzeitfehler)

* Wie Sie Fehler minimieren, indem Sie die Codierung für beabsichtigte Lesevorgänge (mithilfe der Assert)

* Wenn Sie den Debugger verwenden

Um diese Aufgaben zu demonstrieren, zeigen wir nur einige der am häufigsten verwendeten Typen von Fehlern und Fehlern, die Sie beim Debuggen Ihrer apps begegnen. Obwohl der Beispielcode ist C#konzeptuelle Informationen gilt im Allgemeinen in C++, Visual Basic, JavaScript und anderen Sprachen, die von Visual Studio (außer den) unterstützt. Die Screenshots wurden in C# erstellt.

## <a name="create-a-sample-app-with-some-bugs-and-errors-in-it"></a>Erstellen Sie eine Beispiel-app mit einigen Fehlern und die Fehler darin

Der folgende Code verfügt über einige Fehler, die Sie beheben können, mit der Visual Studio-IDE. Hier der app handelt es sich um eine einfache app, die JSON-Daten aus einen Vorgang, Deserialisieren der Daten auf ein Objekt, und aktualisieren eine einfache Liste mit den neuen Daten simuliert.

So erstellen Sie die App:

1. Öffnen Sie Visual Studio, und wählen Sie **Datei** > **neu** > **Projekt**. Klicken Sie unter **Visual C#** , wählen Sie **Windows Desktop** oder **.NET Core**, und wählen Sie dann im mittleren Bereich eine **Konsolen-App**.

    > [!NOTE]
    > Wenn Ihnen die Projektvorlage **Konsolenanwendung** nicht angezeigt wird, klicken Sie im linken Bereich des Dialogfelds **Neues Projekt** auf den Link **Visual Studio-Installer öffnen**. Der Visual Studio-Installer wird gestartet. Wählen Sie die Workload **.NET-Desktopentwicklung** oder **Plattformübergreifende .NET Core-Entwicklung** aus, und klicken Sie dann auf **Anpassen**.

2. In der **Namen** Feld **Console_Parse_JSON** , und klicken Sie auf **OK**. Visual Studio erstellt daraufhin das Projekt.

3. Ersetzen Sie den Standardcode des Projekts *"Program.cs"* -Datei mit den unten stehenden Beispielcode.

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

## <a name="find-the-red-and-green-squiggles"></a>Suchen Sie die roten und grünen Wellenlinien!

Bevor Sie versuchen, die die Beispielapp zu starten und den Debugger ausführen, überprüfen Sie den Code im Code-Editor für den roten und grünen Wellenlinien. Diese repräsentieren die Fehler und Warnungen, die von der IDE, Code-Analyzer identifiziert werden. Die roten Wellenlinien werden Kompilierungsfehler, die Sie beheben müssen, bevor Sie den Code ausführen kann. Die grünen Wellenlinien sind Warnungen. Obwohl Sie Ihre app häufig ausführen können, ohne die Warnungen beheben, können sie eine Quelle von Fehlern sein und Sie häufig speichern selbst Zeit und Aufwand durch Untersuchen sie. Diese Warnungen und Fehler auch angezeigt der **Fehlerliste** Fenster, wenn Sie eine Listenansicht bevorzugen.

In der Beispiel-app mehrere rote Wellenlinien, die Sie korrigieren müssen, und eine grüne Kabel, die Sie sich ansehen, werden angezeigt. Hier ist der erste Fehler aus.

![Fehler, die als eine rote Wellenlinie angezeigt](../debugger/media/write-better-code-red-squiggle.png)

Um diesen Fehler zu beheben, betrachten Sie ein weiteres Feature von der IDE vornehmen, durch das Glühbirnensymbol klicken dargestellt wird.

## <a name="check-the-light-bulb"></a>Überprüfen Sie die Glühbirne!

Die erste rote Wellenlinie stellt einen Fehler während der Kompilierung dar. Zeigen Sie darauf, und die Meldung ```The name `Encoding` does not exist in the current context```.

Beachten Sie, dass dieser Fehler Glühbirnen-Symbol auf der linken unteren Ecke angezeigt. Zusammen mit dem Schraubendreher Symbol ![schraubendrehersymbol klicken](../ide/media/screwdriver-icon.png), das Glühbirnensymbol klicken ![Glühbirnensymbol](../ide/media/light-bulb-icon.png) stellt Schnellaktionen, die Ihnen helfen kann, beheben oder Umgestalten von code Inline. Die Glühbirne stellt Probleme, die Sie *sollten* zu beheben. Die Schraubendreher ist für Probleme, die Sie auswählen können, um zu beheben. Verwenden Sie die erste vorgeschlagene Korrektur, um diesen Fehler zu beheben, indem Sie auf **mit System.Text** auf der linken Seite.

![Verwenden Sie die Glühbirne verlagert, um Code zu korrigieren](../debugger/media/write-better-code-missing-include.png)

Wenn Sie dieses Element klicken, fügt Visual Studio die `using System.Text` Anweisung am Anfang der *"Program.cs"* -Datei und die rote Wellenlinie wird nicht mehr angezeigt. (Wenn Sie nicht sicher sind, was eine empfohlene problemlösung durchgeführt wird, wählen Sie die **Vorschau der Änderungen** Link auf der rechten Seite vor dem Anwenden des Fixes.)

Die vorherige Fehler ist allgemein bekannt, die Sie in der Regel beheben, indem er ein neues `using` Anweisung, um Ihren Code. Es gibt mehrere allgemeine, ähnliche Fehler für diesen Artikel wie ```The type or namespace `Name` cannot be found.``` diese Art von Fehler deuten auf einen fehlenden Assemblyverweis (mit der rechten Maustaste in des Projekts, wählen Sie **hinzufügen** > **Verweis**), einen falsch geschriebenen Namen oder eine fehlende Bibliothek, die Sie hinzufügen möchten (für C#mit der rechten Maustaste auf das Projekt, und wählen Sie **NuGet-Pakete verwalten**).

## <a name="fix-the-remaining-errors-and-warnings"></a>Beheben Sie die übrigen Fehler und Warnungen

Es gibt einigen Weitere Wellenlinien in diesem Code zu betrachten. Hier sehen Sie eine allgemeine Typkonvertierungsfehler. Wenn Sie auf die Wellenlinie zeigen, sehen Sie sich, dass der Code versucht wird, zum Konvertieren einer Zeichenfolge in einen ganzzahligen Typ, der nicht unterstützt wird, es sei denn, Sie fügen Sie die Konvertierung explizit Code hinzu.

![Typkonvertierungsfehler](../debugger/media/write-better-code-conversion-error.png)

Da der Code-Analyzer Ihre Absicht nicht wissen kann, sind keine Glühbirnen können Sie sich dieses Mal. Um diesen Fehler zu beheben, müssen Sie die Absicht des Codes kennen. In diesem Beispiel ist es nicht schwierig zu erkennen, die `points` muss ein numerischen (Integer)-Wert, da Sie hinzufügen möchten `points` zu `totalpoints`.

Um diesen Fehler zu beheben, Ändern der `points` Mitglied der `User` Klasse aus diesem:

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

Zeigen Sie als Nächstes, auf die grüne Wellenlinie in der Deklaration der `points` -Datenmember. Der Code-Analyzer teilt Ihnen mit, dass die Variable nie ein Wert zugewiesen wird.

![Warnmeldung für den nicht zugewiesenen Variablen](../debugger/media/write-better-code-warning-message.png)

In der Regel stellt dies ein Problem, das behoben werden muss. Allerdings in der Beispiel-app in der Tat speichern Sie Daten in die `points` Variablen während der Deserialisierung und zum anschließenden Hinzufügen dieses Werts, damit die `totalpoints` -Datenmember. In diesem Beispiel müssen Sie wissen, die Absicht des Codes und können die Warnung gefahrlos ignorieren. Wenn Sie die Warnung zu vermeiden möchten, können Sie jedoch den folgenden Code ersetzen:

```csharp
item.totalpoints = users[i].points;
```

durch diesen:

```csharp
item.points = users[i].points;
item.totalpoints += users[i].points;
```

Die grüne Wellenlinie verschwindet.

## <a name="fix-an-exception"></a>Eine Ausnahme beheben

Wenn Sie alle roten Wellenlinien behoben und behoben – oder mindestens untersucht: sind die grünen Wellenlinien Sie möchten Sie den Debugger zu starten, und führen Sie die app.

Drücken Sie die Taste **F5** (**Debuggen > Debuggen starten**), oder klicken Sie in der Symbolleiste „Debuggen“ auf die Schaltfläche **Debuggen starten** ![Debuggen starten](../debugger/media/dbg-tour-start-debugging.png "Start Debugging").

An diesem Punkt die Beispiel-app löst eine `SerializationException` Ausnahme (Common Language Runtime-Fehler). Unterfüllt, also die app, auf die Daten, die sie versuchen zu serialisieren. Da Sie die app im Debugmodus (angefügten Debugger) gestartet, führt des datenschnellansichten des Debuggers Ausnahmen-Hilfe Sie direkt auf den Code, der die Ausnahme ausgelöst hat, und bietet Ihnen eine nützliche Fehlermeldung an.

![Eine SerializationException auftritt.](../debugger/media/write-better-code-serialization-exception.png)

Die Fehlermeldung werden Sie angewiesen, den Wert `4o` kann nicht als ganze Zahl analysiert werden. In diesem Beispiel also die Daten ist ungültig: `4o` muss `40`. Aber wenn Sie keine Kontrolle über die Daten in einem realen Szenario (z. B. Sie es von einem Webdienst abrufen), wie gehen Sie dazu vor? Wie lösen Sie dieses Problem?

Wenn eine Ausnahme erreicht wird, müssen Sie ein paar Fragen gestellt (und beantwortet):

* Ist diese Ausnahme wird nur auf einen Fehler, den Sie beheben können? Oder:

* Ist diese Ausnahme, die auftreten können, dass Sie Ihre Benutzer?

Wenn dies der erste Wert ist, korrigieren Sie den Fehler. (In der Beispiel-app bedeutet, dass die ungültigen Daten zu beheben.) Wenn sie die zweite ist, möglicherweise müssen Sie zur Behandlung von Ausnahmen in Ihrem Code mithilfe einer `try/catch` Block (wir sehen Sie sich andere möglichen Strategien im nächsten Abschnitt). Ersetzen Sie in der Beispiel-app den folgenden Code ein:

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

Ein `try/catch` Block weist einige Leistungseinbußen, damit Sie nur verwenden, wenn Sie diese, also wirklich benötigen, in denen (a) sie können in der Releaseversion der app auftreten möchten und wo (b) die Dokumentation für die Methode gibt an, dass Sie überprüfen sollten die die Ausnahme (vorausgesetzt, dass die Dokumentation abgeschlossen ist!). In vielen Fällen können Sie die Ausnahme ordnungsgemäß behandeln, und der Benutzer nicht kennen muss.

Hier sind ein paar wichtige Tipps für die Ausnahmebehandlung:

* Verwenden Sie einen leeren Catch-Block, z. B. `catch (Exception) {}`, das ist keine Maßnahmen verfügbar zu machen oder einen Fehler behandeln. Ein leerer oder nicht informativ Catch-Block kann kann Ausnahmen ausblenden und Ihren Code schwieriger sein statt einfacher zu debuggen.

* Verwenden der `try/catch` -Block um die bestimmte Funktion, die die Ausnahme auslöst (`ReadObject`, in der Beispiel-app). Wenn Sie es auf einem größeren Block des Codes verwenden, erhalten Sie durch das Ausblenden der Position des Fehlers. Beispielsweise verwenden Sie nicht die `try/catch` Block rund um den Aufruf der übergeordneten Funktion `ReadToObject`, hier, oder Sie wissen nicht, genau, wo die Ausnahme aufgetreten ist.

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

* Überprüfen Sie für nicht vertraut sind Funktionen, die Sie in Ihrer app Expecially Interaktion mit externen Daten (z. B. eine webanforderung) enthält die Dokumentation, um zu sehen, welche Ausnahmen die Funktion auslösen. Dies kann es sich um wichtige Informationen für die richtige Fehlerbehandlung und zum Debuggen Ihrer app sein.

Beheben Sie die Beispiel-app, die `SerializationException` in die `GetJsonData` Methode ändern `4o` zu `40`.

## <a name="clarify-your-code-intent-by-using-assert"></a>Verdeutlichen Sie Ihre Absicht Code mithilfe der assert

Klicken Sie in der Symbolleiste „Debuggen“ auf die Schaltfläche **Neu starten** ![App neu starten](../debugger/media/dbg-tour-restart.png "RestartApp") (**STRG** + **UMSCHALT** + **F5**). Die app in weniger Schritten neu gestartet. Daraufhin wird die folgende Ausgabe im Konsolenfenster angezeigt.

![NULL-Wert in der Ausgabe](../debugger/media/write-better-code-using-assert-null-output.png)

Sie können etwas in dieser Ausgabe sehen, die nicht ganz richtig ist. **Namen** und **"LastName"** für die dritte Datensatz leer sind.

Dies ist ein guter Zeitpunkt für die Kommunikation über eine hilfreiche codierungspraxis, oftmals zu selten genutzt, ist die Verwendung `assert` -Anweisungen in Ihrer Funktionen. Durch den folgenden Code hinzufügen, enthalten Sie eine Überprüfung zur Laufzeit, um sicherzustellen, dass `firstname` und `lastname` nicht `null`. Ersetzen Sie den folgenden Code in die `UpdateRecords` Methode:

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

Durch Hinzufügen von `assert` Anweisungen wie folgt an Ihre Funktionen während des Entwicklungsprozesses, Sie können die Absicht des Codes anzugeben. Im vorhergehenden Beispiel geben wir Folgendes an:

* Eine gültige Zeichenfolge ist für den ersten Namen erforderlich
* Eine gültige Zeichenfolge ist für den Nachnamen erforderlich

Mit Absicht auf diese Weise zu verwenden, erzwingen Sie Ihren Anforderungen. Dies ist eine einfache und praktische Methode, mit denen Sie Surface-Fehler während der Entwicklung. (`assert` Anweisungen sind auch als das Hauptelement in Komponententests verwendet.)

Klicken Sie in der Symbolleiste „Debuggen“ auf die Schaltfläche **Neu starten** ![App neu starten](../debugger/media/dbg-tour-restart.png "RestartApp") (**STRG** + **UMSCHALT** + **F5**).

> [!NOTE]
> Die `assert` Code nur in einem Debugbuild aktiv ist.

Wenn Sie neu starten, hält der Debugger bei der `assert` -Anweisung, da der Ausdruck `users[i].firstname != null` ergibt `false` anstelle von `true`.

![Assert-aufgelöst wird, auf "false"](../debugger/media/write-better-code-using-assert.png)

Die `assert` Fehler gibt an, dass ein Problem auftritt, die Sie untersuchen möchten. `assert` können viele Szenarien abdecken, in dem Sie unbedingt eine Ausnahme nicht angezeigt. In diesem Beispiel wird nicht dem Benutzer angezeigt, eine Ausnahme aus, und ein `null` Wert wird als hinzugefügt `firstname` in Ihrer Liste mit Datensätzen. Dies kann zu Problemen führen später (z. B. in der Konsolenausgabe angezeigt) und möglicherweise schwieriger zu debuggen.

> [!NOTE]
> In Szenarien, in dem Sie eine Methode aufrufen, auf, die `null` Wert eine `NullReferenceException` Ergebnisse. Der Regel sollten Sie vermeiden Sie mithilfe einer `try/catch` block für eine allgemeine Ausnahme ist, d. h. eine Ausnahme, die nicht an die Funktion für die Bibliothek gebunden ist. Jedes Objekt kann Auslösen einer `NullReferenceException`. Überprüfen Sie die Dokumentation für die Bibliotheksfunktion, wenn Sie nicht sicher sind.

Während des Debuggens, es ist ratsam, einen bestimmten halten `assert` Anweisung aus, bis Sie wissen, müssen Sie ihn durch einen tatsächlichen Codefehlerbehebung zu ersetzen. Nehmen wir an, dass Sie entscheiden, dass der Benutzer die Ausnahme in einem Releasebuild der app auftreten kann. In diesem Fall müssen Sie Code, um sicherzustellen, dass Ihre app keine schwerwiegende Ausnahme auslösen oder ein anderer Fehler dazu führen, Umgestalten. Also, um diesen Code zu beheben, ersetzen Sie den folgenden Code ein:

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

Mit diesem Code können Sie Ihren codeanforderungen zu erfüllen, und stellen Sie sicher, dass ein Datensatz mit einem `firstname` oder `lastname` Wert `null` wird nicht auf die Daten hinzugefügt.

In diesem Beispiel wir die beiden hinzugefügt `assert` Anweisungen innerhalb einer Schleife. In der Regel bei Verwendung `assert`, es wird empfohlen, Sie fügen `assert` Anweisungen auf den Einstiegspunkt (Anfang), einer Funktion oder Methode. Sie gerade betrachten die `UpdateRecords` -Methode in der Beispiel-app. Bei dieser Methode Sie wissen, Sie sind Probleme, wenn entweder der Methodenargumente `null`, überprüfen Sie daher sie beide mit einem `assert` Anweisung am Einstiegspunkt der Funktion.

```csharp
public static void UpdateRecords(List<User> db, User[] users)
{
    Debug.Assert(db != null);
    Debug.Assert(users != null);
```

Für die vorhergehenden Anweisungen aus, Ihre Absicht darin besteht, dass Sie vorhandene Daten zu laden (`db`) und neue Daten (`users`) vor dem Update nichts.

Sie können `assert` mit jeder Art von Ausdruck, der aufgelöst wird `true` oder `false`. Also z. B. Sie konnte Hinzufügen einer `assert` Anweisung wie folgt.

```csharp
Debug.Assert(users[0].points > 0);
```

Der vorangehende Code ist hilfreich, wenn Sie den folgenden Zweck angeben möchten: einen neuen Punktwert, der größer als 0 (null) erforderlich, um den Datensatz des Benutzers zu aktualisieren.

## <a name="inspect-your-code-in-the-debugger"></a>Überprüfen von Code im debugger

OK, nun, dass Sie alles wichtige, das Problem mit der Beispiel-app ist behoben haben, können Sie auf andere wichtige Details verschieben!

Ich habe Ihnen gezeigt des datenschnellansichten des Debuggers Ausnahmen-Hilfe, aber der Debugger ist einem viel leistungsfähigeren Tool, mit der Sie die anderen Aufgaben wie das Durchlaufen des Codes und untersuchen Sie die Variablen auch. Diese leistungsstarken Funktionen sind in vielen Fällen, insbesondere die folgenden nützlich:

* Sie versuchen, einen Common Language Runtime-Fehler in Ihrem Code zu isolieren, aber Sie können diesen Schritt mit Methoden und Tools, die zuvor erläutert.

* Überprüfen von Code, d. h., während es ausgeführt wird, um sicherzustellen, dass dabei handelt es sich auf die gewünschten Weise verhält tun, was soll ansehen möchten.

    Es ist hilfreich zu Ihrem Code sehen Sie sich während der Ausführung. Sie können erfahren Sie mehr über Ihren Code auf diese Weise und Fehler können häufig identifiziert werden, bevor sie offensichtlich keine derartigen Symptome manifest.

Gewusst wie: Verwenden Sie die wichtigsten Funktionen des Debuggers finden Sie unter [Debuggen für absolute Anfänger](../debugger/debugging-absolute-beginners.md).

## <a name="fix-performance-issues"></a>Beheben der Leistungsprobleme

Fehler mit einer anderen Art enthalten, ineffizienten Code, der bewirkt, dass Ihre app langsam ausgeführt oder zu viel Arbeitsspeicher verwendet wird. Im Allgemeinen ist das Optimieren der Leistung von etwas, das Sie später in der app-Entwicklung durchführen. Sie können jedoch ausführen auf Leistungsprobleme frühzeitig (z. B. angezeigt, dass ein Teil Ihrer app langsam ausgeführt wird), und Sie müssen möglicherweise Ihre app mit den Profilerstellungstools frühzeitig zu testen. Weitere Informationen über Tools wie z. B. die CPU-auslastungstool und der Speicheranalyse zur profilerstellung finden Sie unter [ein erster Blick auf die Profilerstellungstools](../profiling/profiling-feature-tour.md).

## <a name="next-steps"></a>Nächste Schritte

In diesem Artikel haben Sie gelernt, wie zu vermeiden, und beheben viele häufige Fehler in Ihrem Code und wann Sie den Debugger verwenden. Als Nächstes erfahren Sie mehr über die Verwendung von Visual Studio-Debugger, um Fehler zu beheben.

> [!div class="nextstepaction"]
> [Debuggen für Einsteiger](../debugger/debugging-absolute-beginners.md)
