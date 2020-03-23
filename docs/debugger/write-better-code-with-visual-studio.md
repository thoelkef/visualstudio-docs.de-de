---
title: Debugverfahren und -tools
description: Schreiben Sie besseren Code mit weniger Fehlern, indem Sie Visual Studio verwenden, um Ausnahmen zu beheben, Fehler zu beheben und Ihren Code zu verbessern
ms.custom:
- debug-experiment
- seodec18
ms.date: 02/14/2020
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2ac595098d793e44d65312a09fc8857225f150ef
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301020"
---
# <a name="debugging-techniques-and-tools-to-help-you-write-better-code"></a>Debugging-Techniken und -Tools, mit denen Sie besseren Code schreiben können

Das Beheben von Fehlern und Fehlern in Ihrem Code kann eine zeitaufwändige - und manchmal frustrierende - Aufgabe sein. Es braucht Zeit, um zu lernen, wie man effektiv debuggen kann, aber eine leistungsstarke IDE wie Visual Studio kann Ihre Arbeit viel einfacher machen. Eine IDE kann Ihnen helfen, Fehler zu beheben und Ihren Code schneller zu debuggen, und nicht nur das, aber es kann Ihnen auch helfen, besseren Code mit weniger Fehlern zu schreiben. Unser Ziel in diesem Artikel ist es, Ihnen eine ganzheitliche Ansicht des "Fehlerbehebungsprozesses" zu geben, damit Sie wissen, wann Sie den Codeanalysator verwenden, wann Sie den Debugger verwenden, wie Sie Ausnahmen beheben und wie Sie für Absichten programmieren. Wenn Sie bereits wissen, dass Sie den Debugger verwenden müssen, finden Sie weitere Informationen [unter Erster Blick auf den Debugger](../debugger/debugger-feature-tour.md).

In diesem Artikel sprechen wir über die Nutzung der IDE, um Ihre Codierungssitzungen produktiver zu machen. Wir berühren mehrere Aufgaben, wie z. B.:

* Bereiten Sie Ihren Code für das Debuggen vor, indem Sie den Codeanalysator der IDE nutzen

* Beheben von Ausnahmen (Laufzeitfehler)

* So minimieren Sie Fehler, indem Sie für Absicht codieren (mit Assert)

* Wann Sie den Debugger verwenden

Um diese Aufgaben zu veranschaulichen, zeigen wir einige der häufigsten Arten von Fehlern und Fehlern, die beim Debuggen Ihrer Apps auftreten. Obwohl es sich bei dem Beispielcode um C-Code handelt, sind die konzeptionellen Informationen allgemein auf C++, Visual Basic, JavaScript und andere Sprachen anwendbar, die von Visual Studio unterstützt werden (sofern nicht angegeben). Die Screenshots wurden in C# erstellt.

## <a name="create-a-sample-app-with-some-bugs-and-errors-in-it"></a>Erstellen einer Beispiel-App mit einigen Fehlern und Fehlern darin

Der folgende Code enthält einige Fehler, die Sie mit der Visual Studio-IDE beheben können. Die App hier ist eine einfache App, die das Abrufen von JSON-Daten aus einem Vorgang simuliert, die Daten in ein Objekt deserialisiert und eine einfache Liste mit den neuen Daten aktualisiert.

Gehen Sie wie folgt vor, um die App zu erstellen:

1. Sie müssen Visual Studio installiert und entweder die **Plattformübergreifende .NET Core-Entwicklung** oder die **.NET Desktopentwicklungsarbeitsauslastung** installiert haben, je nachdem, welchen App-Typ Sie erstellen möchten.

    Wenn Sie Visual Studio noch nicht installiert haben, wechseln Sie zur [Seite Visual Studio-Downloads,](https://visualstudio.microsoft.com/downloads/) um es kostenlos zu installieren.

    Wenn Sie die Arbeitsauslastung installieren müssen, aber bereits über Visual Studio verfügen, klicken Sie auf **Tools** > **Get Tools and Features**. Der Visual Studio-Installer wird gestartet. Wählen Sie **die plattformübergreifende .NET Core-Entwicklung** oder **.NET Desktopentwicklungsworkload** aus, und wählen Sie dann **Ändern**aus.

1. Öffnen Sie Visual Studio.

    ::: moniker range=">=vs-2019"
    Wählen Sie im Startfenster die Option **Neues Projekt erstellen**aus. Geben Sie die **Konsole** in das Suchfeld ein, und wählen Sie dann entweder **Console App (.NET Core)** oder **Console App (.NET Framework)** aus. Klicken Sie auf **Weiter**. Geben Sie einen Projektnamen wie **Console_Parse_JSON** ein, und klicken Sie auf **Erstellen**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Wählen Sie in der oberen Menüleiste **Datei** > **neues** > **Projekt**aus. Wählen Sie im linken Bereich des Dialogfelds **Neues Projekt** unter **Visual C-** die Option **Konsolen-App**aus, und wählen Sie dann im mittleren Bereich entweder **Console App (.NET Core)** oder **Console App (.NET Framework)** aus. Geben Sie einen Namen wie **Console_Parse_JSON** ein, und klicken Sie auf **OK**.
    ::: moniker-end

    Wenn die **Projektvorlage "Konsolen-App(.NET Core"** oder **"Konsolen-App"-Projektvorlage (.NET Framework)** nicht angezeigt wird, gehen Sie zu **Tools** > **Get Tools and Features**, die das Visual Studio Installer öffnet. Wählen Sie entweder die **plattformübergreifende .NET Core-Entwicklung** oder die **.NET Desktop-Entwicklungsworkload** aus, und wählen Sie dann **Ändern**aus.

    Visual Studio erstellt das Konsolenprojekt, das im Projektmappen-Explorer (rechter Bereich) angezeigt wird.

1. Ersetzen Sie den Standardcode in der *Program.cs* Datei des Projekts durch den folgenden Beispielcode.

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

## <a name="find-the-red-and-green-squiggles"></a>Finde die roten und grünen Wellen!

Bevor Sie versuchen, die Beispiel-App zu starten und den Debugger auszuführen, überprüfen Sie den Code im Code-Editor auf rote und grüne Wellen. Diese stellen Fehler und Warnungen dar, die vom Codeanalysator der IDE identifiziert werden. Bei den roten Wellenläufen handelt es sich um Kompilierungsfehler, die Sie beheben müssen, bevor Sie den Code ausführen können. Die grünen Wellen sind Warnungen. Obwohl Sie Ihre App oft ausführen können, ohne die Warnungen zu beheben, können sie eine Quelle von Fehlern sein und Sie sparen sich oft Zeit und Mühe, indem Sie sie untersuchen. Diese Warnungen und Fehler werden auch im Fenster **Fehlerliste** angezeigt, wenn Sie eine Listenansicht bevorzugen.

In der Beispiel-App sehen Sie mehrere rote Wellen, die Sie reparieren müssen, und eine grüne, die Sie sich ansehen werden. Hier ist der erste Fehler.

![Fehler, der als rote Squiggle angezeigt wird](../debugger/media/write-better-code-red-squiggle.png)

Um diesen Fehler zu beheben, sehen Sie sich ein anderes Feature der IDE an, das durch das Glühbirnensymbol dargestellt wird.

## <a name="check-the-light-bulb"></a>Überprüfen Sie die Glühbirne!

Die erste rote Squiggle stellt einen Kompilierungsfehler dar. Bewegen Sie den Mauszeiger ```The name `Encoding` does not exist in the current context```darüber, und Sie sehen die Nachricht .

Beachten Sie, dass dieser Fehler ein Glühbirnensymbol unten links zeigt. Zusammen mit dem ![Schraubendreher](../ide/media/screwdriver-icon.png)Icon Schraubendreher Symbol, stellt die Glühbirne Symbol ![](../ide/media/light-bulb-icon.png) Quick Actions, die Ihnen helfen können, zu beheben oder umgestalten Code inline. Die Glühbirne stellt Probleme dar, die Sie beheben *sollten.* Der Schraubendreher ist für Probleme, die Sie vielleicht beheben. Verwenden Sie die erste vorgeschlagene Korrektur, um diesen Fehler zu beheben, indem Sie **auf System.Text** auf der linken Seite klicken.

![Verwenden Sie die Glühbirne, um Code zu fixieren](../debugger/media/write-better-code-missing-include.png)

Wenn Sie auf dieses Element `using System.Text` klicken, fügt Visual Studio die Anweisung oben in der *Program.cs-Datei* hinzu, und die rote Wellenlinie verschwindet. (Wenn Sie nicht sicher sind, was ein vorgeschlagenes Update bewirkt, wählen Sie den Link **Vorschauänderungen** auf der rechten Seite aus, bevor Sie das Update anwenden.)

Der vorangehende Fehler ist ein häufiger Fehler, den Sie normalerweise beheben, indem Sie dem Code eine neue `using` Anweisung hinzufügen. Es gibt mehrere häufige, ähnliche Fehler ```The type or namespace `Name` cannot be found.``` wie diese Art von Fehlern können auf einen fehlenden Assemblyverweis hinweisen (Rechtsklick auf das Projekt, wählen Sie**Referenz** **hinzufügen** > ), einen falsch geschriebenen Namen oder eine fehlende Bibliothek, die Sie hinzufügen müssen (für C-Zeichen, klicken Sie mit der rechten Maustaste auf das Projekt und wählen **NuGet-Pakete verwalten).**

## <a name="fix-the-remaining-errors-and-warnings"></a>Beheben der verbleibenden Fehler und Warnungen

Es gibt noch ein paar squiggles in diesem Code zu betrachten. Hier wird ein häufiger Typkonvertierungsfehler angezeigt. Wenn Sie den Mauszeiger über die Wellenlinie bewegen, wird angezeigt, dass der Code versucht, eine Zeichenfolge in eine int zu konvertieren, die nicht unterstützt wird, es sei denn, Sie fügen expliziten Code hinzu, um die Konvertierung durchzuführen.

![Typkonvertierungsfehler](../debugger/media/write-better-code-conversion-error.png)

Da der Codeanalysator Ihre Absicht nicht erraten kann, gibt es diesmal keine Glühbirnen, die Ihnen helfen. Um diesen Fehler zu beheben, müssen Sie die Absicht des Codes kennen. In diesem Beispiel ist es nicht schwer `points` zu sehen, dass es sich um einen numerischen (ganzzahligen) Wert handelt, da Sie versuchen, `points` . `totalpoints`

Um diesen Fehler zu `points` beheben, `User` ändern Sie den Member der Klasse aus folgenden:

```csharp
[DataMember]
internal string points;
```

Und zwar in diesen Code:

```csharp
[DataMember]
internal int points;
```

Die roten Squiggly-Linien im Code-Editor verschwinden.

Als Nächstes bewegen Sie den Mauszeiger über `points` das grüne Wellenspiel in der Deklaration des Datenmembers. Der Codeanalysator teilt Ihnen mit, dass der Variablen nie ein Wert zugewiesen wird.

![Warnmeldung für nicht zugewiesene Variable](../debugger/media/write-better-code-warning-message.png)

In der Regel stellt dies ein Problem dar, das behoben werden muss. In der Beispiel-App speichern Sie jedoch `points` während des Deserialisierungsprozesses Daten in der `totalpoints` Variablen und fügen diesen Wert dann dem Datenmember hinzu. In diesem Beispiel kennen Sie die Absicht des Codes und können die Warnung sicher ignorieren. Wenn Sie die Warnung jedoch entfernen möchten, können Sie den folgenden Code ersetzen:

```csharp
item.totalpoints = users[i].points;
```

durch diesen:

```csharp
item.points = users[i].points;
item.totalpoints += users[i].points;
```

Die grüne Squiggle verschwindet.

## <a name="fix-an-exception"></a>Fix einer Ausnahme

Wenn Sie alle roten Wellen und aufgelöst - oder zumindest untersucht - alle grünen Wellengangs behoben haben, können Sie den Debugger starten und die App ausführen.

Drücken Sie **F5** (**Debug > Start Debugging**) oder die Schaltfläche **Debuggen starten** Starten Sie das ![Debuggen](../debugger/media/dbg-tour-start-debugging.png "Debuggen") in der Debugsymbolleiste.

An diesem Punkt löst die `SerializationException` Beispiel-App eine Ausnahme aus (ein Laufzeitfehler). Das heißt, die App erstickt die Daten, die sie zu serialisieren versucht. Da Sie die App im Debugmodus gestartet haben (Debugger angefügt), führt der Ausnahmehelfer des Debuggers den Code, der die Ausnahme ausgelöst hat, direkt und gibt Ihnen eine hilfreiche Fehlermeldung.

![Eine SerializationException tritt auf](../debugger/media/write-better-code-serialization-exception.png)

Die Fehlermeldung weist Sie an, `4o` dass der Wert nicht als ganzzahlige Datei analysiert werden kann. In diesem Beispiel wissen Sie also, `4o` dass `40`die Daten schlecht sind: sollte . Wenn Sie jedoch in einem realen Szenario nicht die Kontrolle über die Daten haben (z. B. von einem Webdienst erhalten), was tun Sie dagegen? Wie lösen Sie dieses Problem?

Wenn Sie eine Ausnahme treffen, müssen Sie einige Fragen stellen (und beantworten):

* Ist diese Ausnahme nur ein Fehler, den Sie beheben können? Oder

* Ist diese Ausnahme etwas, auf das Ihre Benutzer stoßen könnten?

Wenn es ersterist ist, beheben Sie den Fehler. (In der Beispiel-App bedeutet dies, dass die fehlerhaften Daten behoben werden.) Wenn es sich um Letzteres handelt, müssen Sie die `try/catch` Ausnahme in Ihrem Code möglicherweise mithilfe eines Blocks behandeln (wir sehen uns im nächsten Abschnitt andere mögliche Strategien an). Ersetzen Sie in der Beispiel-App den folgenden Code:

```csharp
users = ser.ReadObject(ms) as User[];
```

durch diesen Code:

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

Ein `try/catch` Block hat einige Leistungskosten, daher sollten Sie sie nur verwenden, wenn Sie sie wirklich benötigen, d. h. wo (a) sie in der Releaseversion der App auftreten können und wo (b) die Dokumentation für die Methode angibt, dass Sie die Ausnahme suchen sollten (vorausgesetzt, die Dokumentation ist vollständig!). In vielen Fällen können Sie eine Ausnahme entsprechend behandeln, und der Benutzer muss nie davon erfahren.

Hier sind einige wichtige Tipps für die Ausnahmebehandlung:

* Vermeiden Sie die Verwendung `catch (Exception) {}`eines leeren catch-Blocks, z. B. , der keine geeigneten Aktionen zum Offensetzen oder Behandeln eines Fehlers ergreift. Ein leerer oder nicht informativer Catch-Block kann Ausnahmen ausblenden und das Debuggen des Codes erschweren, anstatt ihn zu vereinfachen.

* Verwenden `try/catch` Sie den Block um die`ReadObject`spezifische Funktion, die die Ausnahme ( in der Beispiel-App) auslöst. Wenn Sie es um einen größeren Codeabschnitt herum verwenden, werden die Speicherorte des Fehlers ausgeblendet. Verwenden Sie z. B. nicht den `try/catch` Block `ReadToObject`um den Aufruf der übergeordneten Funktion , der hier angezeigt wird, oder Sie wissen nicht genau, wo die Ausnahme aufgetreten ist.

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

* Überprüfen Sie in der Dokumentation, welche Ausnahmen die Funktion auslösen kann, um unbekannte Funktionen, die Sie in Ihre App aufnehmen, insbesondere funktionen, die mit externen Daten interagieren (z. B. eine Webanforderung). Dies können wichtige Informationen für die ordnungsgemäße Fehlerbehandlung und das Debuggen Ihrer App sein.

Beheben Sie für die `SerializationException` Beispiel-App die in der `GetJsonData` Methode, indem Sie zu ändern. `4o` `40`

## <a name="clarify-your-code-intent-by-using-assert"></a>Verdeutlichn Sie Ihre Codeabsicht mithilfe von Assert

Klicken Sie auf der Symbolleiste „Debuggen“ auf die Schaltfläche **Neu starten ** ![App neu starten](../debugger/media/dbg-tour-restart.png "RestartApp") (**STRG** + **UMSCHALT** + **F5**). Dadurch wird die App in weniger Schritten neu gestartet. Die folgende Ausgabe wird im Konsolenfenster angezeigt.

![Nullwert in der Ausgabe](../debugger/media/write-better-code-using-assert-null-output.png)

Sie können etwas in dieser Ausgabe sehen, das nicht ganz richtig ist. **Name** und **Nachname** für den dritten Datensatz sind leer!

Dies ist ein guter Zeitpunkt, um über eine hilfreiche Codierungspraxis zu sprechen, die oft nicht ausgelastet ist, d. h. Anweisungen in Ihren Funktionen zu verwenden. `assert` Durch Hinzufügen des folgenden Codes fügen Sie eine `firstname` Laufzeitprüfung ein, um sicherzustellen, dass und `lastname` nicht `null`. Ersetzen Sie den `UpdateRecords` folgenden Code in der Methode:

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

Wenn `assert` Sie Anweisungen wie diese während des Entwicklungsprozesses zu Ihren Funktionen hinzufügen, können Sie die Absicht des Codes angeben. Im vorherigen Beispiel geben wir Folgendes an:

* Für den Vornamen ist eine gültige Zeichenfolge erforderlich.
* Für den Nachnamen ist eine gültige Zeichenfolge erforderlich.

Indem Sie die Absicht auf diese Weise angeben, erzwingen Sie Ihre Anforderungen. Dies ist eine einfache und praktische Methode, die Sie verwenden können, um Fehler während der Entwicklung zu beschaffen. (`assert` Anweisungen werden auch als Hauptelement in Komponententests verwendet.)

Klicken Sie auf der Symbolleiste „Debuggen“ auf die Schaltfläche **Neu starten ** ![App neu starten](../debugger/media/dbg-tour-restart.png "RestartApp") (**STRG** + **UMSCHALT** + **F5**).

> [!NOTE]
> Der `assert` Code ist nur in einem Debugbuild aktiv.

Beim Neustart wird der Debugger `assert` für die Anweisung `users[i].firstname != null` angehalten, `false` da `true`der Ausdruck anstelle von ausgewertet wird.

![Assert löst sich auf false auf](../debugger/media/write-better-code-using-assert.png)

Der `assert` Fehler weist darauf hin, dass es ein Problem gibt, das Sie untersuchen müssen. `assert`kann viele Szenarien abdecken, in denen Sie nicht unbedingt eine Ausnahme sehen. In diesem Beispiel wird dem Benutzer keine Ausnahme `null` angezeigt, `firstname` und ein Wert wird wie in der Datensatzliste hinzugefügt. Dies kann später zu Problemen führen (wie sie in der Konsolenausgabe angezeigt werden) und kann schwieriger zu debuggen sein.

> [!NOTE]
> In Szenarien, in denen `null` Sie eine `NullReferenceException` Methode für den Wert aufrufen, wird ein Ergebnis erzielt. Normalerweise möchten Sie vermeiden, einen `try/catch` Block für eine allgemeine Ausnahme zu verwenden, d. h. eine Ausnahme, die nicht an die bestimmte Bibliotheksfunktion gebunden ist. Jedes Objekt kann `NullReferenceException`eine auslösen. Überprüfen Sie die Dokumentation für die Bibliotheksfunktion, wenn Sie sich nicht sicher sind.

Während des Debugvorgangs ist es gut, `assert` eine bestimmte Anweisung beizubehalten, bis Sie wissen, dass Sie sie durch eine tatsächliche Codekorrektur ersetzen müssen. Angenommen, Sie entscheiden, dass der Benutzer die Ausnahme in einem Releasebuild der App auftreten könnte. In diesem Fall müssen Sie Code umgestalten, um sicherzustellen, dass Ihre App keine schwerwiegende Ausnahme auslöst oder zu einem anderen Fehler führt. Um diesen Code zu beheben, ersetzen Sie den folgenden Code:

```csharp
if (existingUser == false)
{
    User user = new User();
```

durch diesen Code:

```csharp
if (existingUser == false && users[i].firstname != null && users[i].lastname != null)
{
    User user = new User();
```

Mit diesem Code erfüllen Sie Ihre Codeanforderungen und stellen `firstname` `lastname` sicher, `null` dass den Daten kein Datensatz mit einem oder einem Wert von hinzugefügt wird.

In diesem Beispiel haben `assert` wir die beiden Anweisungen innerhalb einer Schleife hinzugefügt. In der `assert`Regel ist es bei `assert` der Verwendung von , Anweisungen am Einstiegspunkt (Anfang) einer Funktion oder Methode hinzuzufügen. Sie betrachten derzeit `UpdateRecords` die Methode in der Beispiel-App. Bei dieser Methode wissen Sie, dass Sie in `null`Schwierigkeiten sind, wenn `assert` eines der Methodenargumente ist, also überprüfen Sie beide mit einer Anweisung am Einstiegspunkt der Funktion.

```csharp
public static void UpdateRecords(List<User> db, User[] users)
{
    Debug.Assert(db != null);
    Debug.Assert(users != null);
```

Für die vorherigen Anweisungen ist Es Ihre`db`Absicht, vorhandene Daten`users`( ) zu laden und neue Daten ( ) abzurufen, bevor Sie etwas aktualisieren.

Sie können `assert` mit jeder Art von `true` Ausdruck `false`verwenden, der in oder aufgelöst wird. Sie können also z. `assert` B. eine solche Anweisung hinzufügen.

```csharp
Debug.Assert(users[0].points > 0);
```

Der vorangehende Code ist nützlich, wenn Sie die folgende Absicht angeben möchten: Zum Aktualisieren des Benutzerdatensatzes ist ein neuer Punktwert größer als Null (0) erforderlich.

## <a name="inspect-your-code-in-the-debugger"></a>Überprüfen des Codes im Debugger

OK, jetzt, da Sie alles kritische behoben haben, was mit der Beispiel-App falsch ist, können Sie auf andere wichtige Dinge umsteigen!

Wir haben Ihnen den Ausnahmehelfer des Debuggers gezeigt, aber der Debugger ist ein viel leistungsfähigeres Tool, mit dem Sie auch andere Dinge wie den Schritt durch Ihren Code ausführen und seine Variablen überprüfen können. Diese leistungsstärkeren Funktionen sind in vielen Szenarien nützlich, insbesondere in den folgenden:

* Sie versuchen, einen Laufzeitfehler in Ihrem Code zu isolieren, können dies jedoch nicht mit den zuvor beschriebenen Methoden und Tools durchführen.

* Sie möchten Ihren Code überprüfen, d. h. ihn während der Laufzeit überprüfen, um sicherzustellen, dass er sich so verhält, wie Sie es erwarten, und das tun, was Sie möchten.

    Es ist lehrreich, Ihren Code während der Laufzeit zu beobachten. Sie können mehr über Ihren Code auf diese Weise erfahren und oft Fehler identifizieren, bevor sie offensichtliche Symptome manifestieren.

Informationen zur Verwendung der wesentlichen Funktionen des Debuggers finden Sie unter [Debuggen für absolute Anfänger](../debugger/debugging-absolute-beginners.md).

## <a name="fix-performance-issues"></a>Beheben der Leistungsprobleme

Fehler anderer Art sind ineffizienter Code, der dazu führt, dass Ihre App langsam ausgeführt wird oder zu viel Arbeitsspeicher verwendet. Im Allgemeinen ist die Optimierung der Leistung etwas, was Sie später in Ihrer App-Entwicklung tun. Sie können jedoch frühzeitig auf Leistungsprobleme stoßen (z. B. sehen Sie, dass ein Teil Ihrer App langsam ausgeführt wird), und Sie müssen Ihre App möglicherweise frühzeitig mit den Profilerstellungstools testen. Weitere Informationen zu Profilerstellungstools wie dem CPU-Auslastungstool und dem Speicheranalysator finden Sie unter [Erste Informationen zu den Profilerstellungstools](../profiling/profiling-feature-tour.md).

## <a name="next-steps"></a>Nächste Schritte

In diesem Artikel haben Sie gelernt, wie Sie viele häufige Fehler in Ihrem Code vermeiden und beheben und wann Sie den Debugger verwenden können. Weitere Informationen zur Verwendung des Visual Studio-Debuggers zum Beheben von Fehlern.

> [!div class="nextstepaction"]
> [Debuggen für Einsteiger](../debugger/debugging-absolute-beginners.md)
