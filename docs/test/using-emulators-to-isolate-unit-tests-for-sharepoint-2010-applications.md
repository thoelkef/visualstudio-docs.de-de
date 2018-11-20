---
title: Verwenden Emulatoren zum Insolieren von Komponententests für SharePoint 2010-Anwendungen
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: baa1ebbc63f0e9649e1601bbcb6220ef8bc5f5b5
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296059"
---
# <a name="using-emulators-to-isolate-unit-tests-for-sharepoint-2010-applications"></a>Verwenden Emulatoren zum Insolieren von Komponententests für SharePoint 2010-Anwendungen

Das Microsoft.SharePoint.Emulators-Paket stellt eine Reihe von Bibliotheken bereit, die Ihnen helfen, isolierte Komponententests für Microsoft SharePoint 2010-Anwendungen zu erstellen. Emulatoren verwenden [Shims](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md) aus dem Isolationsframework [Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md), um einfache Objekte im Arbeitsspeicher zu erstellen, die die gängigsten Objekte und Methoden der SharePoint-API imitieren. Wenn eine SharePoint-Methode nicht emuliert wird oder wenn Sie das Standardverhalten eines Emulators ändern möchten, können Sie Fakes-Shims erstellen, um die gewünschten Ergebnisse bereitzustellen.

Vorhandene Testmethoden und Klassen können problemlos konvertiert werden, um im Emulatorkontext ausgeführt zu werden. Diese Funktion ermöglicht die Erstellung von zweifach verwendbarenTests. Ein zweifach verwendbarer Test kann zwischen Integrationstests für die tatsächliche SharePoint-API und isolierten Komponententests wechseln, die die Emulatoren verwenden.

##  <a name="BKMK_Requirements"></a> Anforderungen

-   Microsoft SharePoint 2010 (SharePoint 2010 Server oder SharePoint 2010 Foundation)

-   Microsoft Visual Studio Enterprise

-   Microsoft SharePoint Emulators-NuGet-Paket

Sie sollten außerdem mit den [Grundlagen von Unittests in Visual Studio](../test/unit-test-basics.md) vertraut sein und einige Kenntnisse über [Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md) mitbringen.

##  <a name="BKMK_The_AppointmentsWebPart_example"></a> Das Beispiel „AppointmentsWebPart“

AppointmentsWebPart ermöglicht Ihnen die Anzeige und Verwaltung einer SharePoint-Liste Ihrer Termine.

![Termin-Webpart](../test/media/ut_emulators_appointmentswebpart.png)

In diesem Beispiel werden Methoden des Webparts getestet:

-   Die `ScheduleAppointment`-Methode überprüft die Listenelementwerte, die an die Methode übergeben werden, und erstellt einen neuen Eintrag in einer Liste in einem angegebenen SharePoint-Web.

-   Die `GetAppointmentsForToday`-Methode gibt den Details der heutigen Termine zurück.

##  <a name="convert-an-existing-test"></a>Konvertieren eines vorhandenen Tests

In einem typischen Test einer Methode in einer SharePoint-Komponente, erstellt die Testmethode eine temporäre Site in SharePoint Foundation und fügt die SharePoint-Komponenten zu der Website hinzu, die der zu testende Code erfordert. Die Testmethode erstellt anschließend eine Instanz der Komponente und führt sie aus. Am Ende des Tests, wird die Site aufgelöst.

Die `ScheduleAppointment`-Methode des getesteten Codes ist wahrscheinlich eine der ersten Methoden, die für die Komponente geschrieben werden:

```csharp
// method under test
public bool ScheduleAppointment(SPWeb web, string listName, string name,
    string phone, string email, string age, DateTime date, out string errorMsg)
{
    errorMsg = string.Empty;
    var badFormat = this.checkInput(name, phone, email, age);
    if (badFormat)
    {
        errorMsg = "Bad Format";
        return false;
    }
    var exists = this.CheckDuplicate(listName, web, name, phone, email, age, date);
    if (exists)
    {
        errorMsg = "Item already exists";
        return false;
    }
    SPListItemCollection items = web.Lists[listName].Items;
    // create item and populate fields
    SPListItem item = items.Add();
    item["Name"] = name;
    item["Phone"] = phone;
    item["Email"] = email;
    item["Age"] = age;
    item["Date"] = date.ToString("D");
    item.Update();
    return true;
}
```

Der erste Funktionstest in der `ScheduleAppointment`-Methode kann folgendermaßen aussehen:

```csharp
[TestMethod]
public void ScheduleAppointmentReturnsTrueWhenNewAppointmentIsCreated()
{
    using( var site = new SPSite("http://localhost"))
    using (var webPart = new BookAnAppointmentWebPart())
    {
        // Arrange
        string errorMsg = string.Empty;
        DateTime date = DateTime.Now;
        SPList list = AddListToSiteHelper(site);

        // Act
        bool success = webPart.ScheduleAppointment(site.RootWeb, list.Title,
            "Raisa Pokrovskaya", "425-555-0163", "raisa@outlook.com", "55", date,
            out errorMsg);
        list.Delete();

        // Assert
        Assert.IsTrue(success);
    }
}
```

Obwohl diese Testmethode überprüft, ob die `ScheduleAppointment`-Methode der Liste einen neuen Eintrag ordnungsgemäß hinzufügt, handelt es sich eher um einen Integrationstest des Webparts als um einen Test des spezifischen Verhaltens des Codes. Die externen Abhängigkeiten zu SharePoint und die SharePoint-API können dazu führen, dass der Test aus anderen Gründen als dem Benutzercode in der `ScheduleAppointment`-Methode fehlschlägt. Der Mehraufwand bei der Erstellung und Auflösung der SharePoint-Website kann dazu führen, dass der Test zu langsam ist, um als regulärer Teil des Codierungsprozesses ausgeführt zu werden. Die Ausführung des Setups und die Zerstörung der Site für jede Testmethode verschlimmert das Problem der Erstellung effizienter Entwicklerkomponententests.

Microsoft SharePoint-Emulatoren stellen einen Satz von Objekt- und Methoden-"Doubles" bereit, die das Verhalten der gängigsten SharePoint-APIs imitieren. Die emulierten Methoden sind einfache Implementierungen der SharePoint-API, die keine Ausführung von SharePoint erfordern. Wenn Sie Microsoft Fakes verwenden, um Aufrufe an die SharePoint-API an die Methoden-Doubles von SharePoint-Emulatoren umzuleiten, isolieren Sie die Tests, und stellen Sie sicher, dass Sie den gewünschten Code testen. Wenn Sie SharePoint-Methoden aufrufen, die nicht emuliert werden, können Sie Fakes direkt verwenden, um das gewünschte Verhalten zu erstellen.

###  <a name="BKMK_Adding_the_Emulators_package_to_a_test_project"></a> Hinzufügen des Emulatorpakets zu einem Testprojekt

So fügen Sie den SharePoint-Emulatoren ein Testprojekt hinzu:

1.  Wählen Sie das Testprojekt im **Projektmappen-Explorer** aus.

2.  Wählen Sie im Kontextmenü **NuGet-Pakete verwalten** aus.

3.  Suchen Sie die **Online**-Kategorie für `Microsoft.SharePoint.Emulators`, und wählen Sie dann **Installieren** aus.

![SharePoint Emulators-NuGet-Paket](../test/media/ut_emulators_nuget.png)

###  <a name="BKMK__Running_a_test_method_in_the_emulation_context"></a> Ausführen einer Testmethode mit Emulation

Durch das Installieren des Pakets werden den Projekten Verweise auf die erforderlichen Bibliotheken hinzugefügt. Um die Verwendung von Emulatoren in einer vorhandenen Testklasse zu vereinfachen, fügen Sie den Namespaces `Microsoft.SharePoint.Emulators` und `Microsoft.QualityTools.Testing.Emulators` hinzu.

Um die Emulation in den Testmethoden zu ermöglichen, binden Sie den Methodentext in einer `using`-Anweisung ein, die ein `SharePointEmulationScope`-Objekt erstellt. Zum Beispiel:

```csharp
[TestMethod]
public void ScheduleAppointmentReturnsTrueWhenNewAppointmentIsCreated()
{
    // create the emulation scope with a using statement
    using (new SharePointEmulationScope())
    using( var site = new SPSite("http://localhost"))
    using (var webPart = new BookAnAppointmentWebPart())
    {
        // Arrange
        string errorMsg = string.Empty;
        DateTime date = DateTime.Now;
        SPList list = AddListToSiteHelper(site);

        // Act
        bool success = webPart.ScheduleAppointment(site.RootWeb, list.Title,
            "Raisa Pokrovskaya", "425-555-0163", "raisa@outlook.com", "55", date,
            out errorMsg);
        list.Delete();

        // Assert
        Assert.IsTrue(success);
    }
}
```

Wenn die Testmethode ausgeführt wird, ruft die Emulator-Laufzeit Microsoft Fakes auf, um Code dynamisch in SharePoint-Methoden einzufügen, um die Aufrufe an diese Methoden an Delegaten umzuleiten, die in *Microsoft.SharePoint.Fakes.dll* deklariert werden. *Microsoft.SharePoint.Emulators.dll* implementiert die Delegaten für emulierte Methoden, wobei das tatsächliche SharePoint-Verhalten genau simuliert wird. Wenn die Testmethode oder die getestete Komponente eine SharePoint-Methode aufruft, entspricht das daraus resultierende Verhalten der Emulation.

![Emulatorausführungsfluss](../test/media/ut_emulators_flowchart.png)

##  <a name="create-dual-use-classes-and-methods"></a>Erstellen von zweifach verwendbaren Klassen und Methoden

Um Methoden zu erstellen, die für beide Integrationstests für die SharePoint-API und die isolierten Komponententests verwendet werden können, verwenden Sie den überladenen Konstruktor `SharePointEmulationScope(EmulationMode)`, um den Code der Testmethode zu umschließen. Die beiden Werte der `EmulationMode`-Enumeration geben an, ob der Bereich Emulatoren (`EmulationMode.Enabled`) oder die SharePoint-API (`EmulationMode.Passthrough`) verwendet.

So können Sie beispielsweise den vorherigen Test ändern, damit er zweifach verwendbar ist:

```csharp
// class level field specifies emulation mode
private const EmulationMode emulatorMode = EmulationMode.Enabled;

[TestMethod]
public void ScheduleAppointmentReturnsTrueWhenNewAppointmentIsCreated()
{
    // emulation scope determined by emulatorMode
    using( SharePointEmulationScope(emulatorMode))
    using( var site = new SPSite("http://localhost"))
    using (var webPart = new BookAnAppointmentWebPart())
    {
        // Arrange
        string errorMsg = string.Empty;
        DateTime date = DateTime.Now;
        SPList list = AddListToSiteHelper(site);

        // Act
        bool success = webPart.ScheduleAppointment(site.RootWeb, list.Title,
            "Raisa Pokrovskaya", "425-555-0163", "raisa@outlook.com", "55", date,
            out errorMsg);
        list.Delete();

        // Assert
        Assert.IsTrue(success);
    }
}
```

## <a name="use-testinitialize-and-testcleanup-attributes-to-create-a-dual-use-test-class"></a>Verwenden der Attribute „TestInitialize“ und „TestCleanup“ zur Erstellung einer zweifach verwendbaren Testklasse

Wenn Sie alle bzw. die meisten Tests in einer Klasse mit `SharePointEmulationScope` ausführen, können Sie Techniken auf Klassenebene nutzen, um den Emulationsmodus festzulegen.

-   Testklassenmethoden, die mit <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute> und <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute> attributiert sind, können den Bereich erstellen und zerstören.

-   Durch Festlegen von `EmulationMode` auf Klassenebene kann die Modusänderung zwischen `EmulationMode.Enabled` und `EmulationMode.Passthrough` automatisiert werden.

Eine Klassemethode, die mit `[TestInitialize]` attributiert ist, wird beim Starten jeder Testmethode ausgeführt, und eine Methode, die mit `[TestCleanup]` attributiert ist, wird beim Beenden jeder Testmethode ausgeführt. Sie können ein privates Feld für das `SharePointEmulationScope`-Objekt auf Klassenebene deklarieren, es in der mit dem `TestInitialize`-Attribut versehenen Methode initialisieren und anschließend das Objekt in der mit dem `TestCleanup`-Attribut versehenen Methode löschen.

Sie können jede Methode verwenden, die Sie auswählen, um die Auswahl von `EmulationMode` zu automatisieren. Eine Möglichkeit besteht darin, anhand von Präprozessordirektiven zu prüfen, ob ein Symbol vorhanden ist. Um beispielsweise die Testmethoden in einer Klasse mit Emulatoren auszuführen, können Sie ein Symbol wie `USE_EMULATION` in der Testprojektdatei oder in der Buildbefehlszeile definieren. Wenn das Symbol definiert ist, wird eine `EmulationMode`-Konstante auf Klassenebene deklariert und auf `Enabled` festgelegt. Andernfalls wird die Konstante auf `Passthrough` festgelegt.

Im Folgenden Beispiel der Testklasse wird veranschaulicht, wie Präprozessordirektiven und die mit `TestInitialize` und `TestCleanup` attributierten Methoden verwendet werden, um den Emulationsmodus festzulegen.

```csharp
//namespace declarations
...

namspace MySPAppTests
{
    [TestClass]
    public class BookAnAppointmentWebPartTests
    {

        // emulationScope is a class level field
        private SharePointEmulationScope emulationScope;

        // preprocessor directives determine the value of emulatorMode
        #if USE_EMULATIONprivate const EmulationMode emulatorMode = EmulationMode.Enabled;#elseprivate const EmulationMode emulatorMode = EmulationMode.Passthrough;#endif

        // InitializeTest sets the emulation scope at the beginning of each test method
        [TestInitialize]public void InitializeTest(){this.emulationScope = new SharePointEmulationScope(emulatorMode);}

        // CleanupTest disposes the emulation scope at the end of each test method
        [TestCleanup]public void CleanupTest(){this.emulationScope.Dispose();}

        [TestMethod]
        public void ScheduleAppointmentReturnsTrueWhenNewAppointmentIsCreated()
        {
            // remove the SharePointEmulationScope using statement from the method
            using( var site = new SPSite("http://localhost"))
            using (var webPart = new BookAnAppointmentWebPart())
            {
                // Arrange
                string errorMsg = string.Empty;
                DateTime date = DateTime.Now;
                SPList list = AddListToSiteHelper(site);

                // Act
                bool success = webPart.ScheduleAppointment(site.RootWeb, list.Title,
                    "Raisa Pokrovskaya", "425-555-0163", "raisa@outlook.com", "55", date,
                    out errorMsg);
                list.Delete()

                // Assert
                Assert.IsTrue(success);
            }
        }

        ...// More tests

    }
}
```

##  <a name="handle-non-emulated-sharepoint-methods"></a>Arbeiten mit nicht emulierten SharePoint-Methoden

Nicht alle SharePoint-Typen werden emuliert und nicht alle Methoden in einigen emulierten Typen werden emuliert. Wenn der zu testenden Code eine SharePoint-Methode aufruft, die nicht emuliert wird, löst die Methode eine `NotSupportedException`-Ausnahme aus. Wenn eine Ausnahme auftritt, fügen Sie Fakes für die SharePoint-Methode hinzu.

**Einrichten von SharePoint Fakes**

So werden Microsoft Fakes-Shims explizit aufgerufen:

1.  Wenn Sie ein Shim für eine SharePoint-Klasse verwenden möchten, die nicht emuliert wird, bearbeiten Sie die Datei *Microsoft.SharePoint.fakes*, und fügen Sie die Klasse zur Liste der Shim-Klassen hinzu. Weitere Informationen finden Sie im Abschnitt [Konfigurieren der Codegenerierung von Stubs](code-generation-compilation-and-naming-conventions-in-microsoft-fakes.md#configure-code-generation-of-stubs) unter [Codegenerierung, Kompilierung und Benennungskonventionen in Microsoft Fakes](../test/code-generation-compilation-and-naming-conventions-in-microsoft-fakes.md).

     ![Fakes-Ordner im Projektmappen-Explorer](../test/media/ut_emulators_fakesfilefolder.png)

2.  Erstellen Sie das Testprojekt mindestens einmal neu, nachdem Sie das Microsoft SharePoint-Emulatorpaket installiert und die Datei *Microsoft.SharePoint.Fakes* bearbeitet haben. Beim Erstellen des Projekts wird ein **FakesAssembly**-Ordner im Stammordner des Projekts auf dem Datenträger erstellt und gefüllt.

     ![FakesAssembly-Ordner](../test/media/ut_emulators_fakesassemblyfolder.png)

3.  Hinzufügen eines Verweises auf die **Microsoft.SharePoint.14.0.0.0.Fakes.dll**-Assembly, die im Ordner **FakesAssembly** gespeichert ist.

4.  (Optional) Fügen Sie die Namespacedirektive der Testklasse für `Microsoft.QualityTools.Testing.Fakes`, `Microsoft.SharePoint.Fakes` und jeden geschachtelten Namespace von `Microsoft.SharePoint.Fakes` hinzu, den Sie verwenden möchten.

**Implementieren des Shim-Delegaten für eine SharePoint-Methode**

In diesem Beispielprojekt ruft die `GetAppointmentsForToday`-Methode die SharePoint-API-Methode [SPList.GetItems (SPQuery)](xref:Microsoft.SharePoint.SPList.GetItems%2A) auf.

```csharp
// method under test
public string GetAppointmentsForToday(string listName, SPWeb web)
{
    SPList list = web.Lists[listName];
    DateTime today = DateTime.Now;
    var listQuery = new SPQuery{Query = String.Format("<Where><Eq><FieldRef Name='Date'/>" +"<Value Type='Text'>{0}</Value>" +"</Eq></Where>", today.ToString("D"))};
    var result = new System.Text.StringBuilder();
    foreach (SPListItem item in list.GetItems(listQuery))
    {
        result.AppendFormat("Name: {0}, Phone: {1}, Email: {2}, Age: {3}, Date: {4}\n",
            item["Name"], item["Phone"], item["Email"], item["Age"], item["Date"]);
    }
    return result.ToString();
}
```

Die `SPList.GetItems(SPQuery)`-Version der überladenen `GetItems`-Methode wird nicht emuliert. Daher würde das Umschließen eines vorhandenen Tests für `GetAppointmentsForToday` in `SharePoint.Emulation.Scope` fehlschlagen. Um einen funktionierenden Test zu erstellen, müssen Sie eine Implementierung des Fakedelegaten `ShimSPList.GetItemsSPQuery` schreiben, der die Ergebnisse zurückgibt, die Sie testen möchten.

Im Folgenden finden Sie eine Änderung der vorhandenen Testmethode `GetAppointmentsForTodayReturnsOnlyTodaysAppointments`, die einen Fälschungsdelegaten implementiert. Die erforderlichen Änderungen werden in den Kommentaren gekennzeichnet:

> [!IMPORTANT]
> Testmethoden, die explizit Fakes-Shims erstellen, lösen eine `ShimNotSupported`-Ausnahme aus, wenn der Test im `EmulationMode.Passthrough`-Kontext ausgeführt wird. Um dieses Problem zu vermeiden, verwenden Sie eine Variable, um den `EmulationMode`-Wert festzulegen und jeden Fakes-Code in eine `if`-Anweisung einzubinden, die den Wert testet.

```csharp
// class level field to set emulation mode
private const EmulationMode emulatorMode = EmulationMode.Enabled

[TestMethod]
public void GetAppointmentsForTodayReturnsOnlyTodaysAppointments()
{

    // create the emulation scope with a using statement
    using (var emulationScope = new SharePointEmulationScope(emulatorMode))
    using( var site = new SPSite("http://localhost"))
    using (var webPart = new BookAnAppointmentWebPart())
    {
        // Arrange
        DateTime date = DateTime.Now;
        SPList list = AddListToSiteHelper(site);
        // insert 2 items into list
        AddItemsToListHelper(list, new string[] {"Raisa Pokrovskaya", "425-555-0163",
            "raisa@outlook.com", "55", date.ToString("D") });
        AddItemsToListHelper(list, new string[] {"Francis Totten", "313-555-0100",
            "francis@contoso.com", "42", date.AddDays(1).ToString("D") });

        // use Fakes shims only if emulation is enabled
        if (emulatorMode == EmulationMode.Enabled){var sList = new ShimSPList(list);sList.GetItemsSPQuery = (query) =>{var shim = new ShimSPListItemCollection();shim.Bind(new[] { list.Items[0] });return shim.Instance;}}

        // Act
        string result = webPart.GetAppointmentsForToday(list.Title, site.RootWeb);
        list.Delete();

        // Assert
        Assert.IsTrue(result.Contains(String.Format(
            "Name: Raisa Pokrovskaya, Phone: 425-555-0163, Email: raisa@outlook.com," +
            "Age: 55, Date: {0}", date.ToString("D"))));
        Assert.IsFalse(result.Contains("Name: Francis Totten"));
    }
}
```

In dieser Methode testen wir zuerst, ob die Emulation aktiviert ist. Wenn dies der Fall ist, erstellen wir ein Fakes-Shim-Objekt für die `SPList`-Liste und erstellen dann eine Methode und weisen Sie dem zugehörigen `GetItemsSPQuery`-Delegaten zu. Der Delegat verwendet die `Bind`-Methode für Fakes, um das richtige Listenelement zur `ShimSPListItemCollection` hinzuzufügen, die an den Aufrufer zurückgegeben wird.

##  <a name="write-emulation-tests-from-scratch-and-a-summary"></a>Schreiben neuer Emulationstests; Zusammenfassung

Obwohl die Verfahren zum Erstellen von Emulations- und zweifach verwendbaren Tests, die in den vorangehenden Abschnitten beschrieben werden, davon ausgehen, dass Sie vorhandene Tests konvertieren, können Sie die Verfahren auch verwenden, um Tests von Grund auf neu zu schreiben. In der folgenden Liste werden diese Techniken zusammengefasst:

-   Um Emulatoren in einem Testprojekt zu verwenden, fügen Sie dem Projekt das Microsoft.SharePoint.Emulators-NuGet-Paket hinzu.

-   Um Emulatoren in einer Testmethode zu verwenden, erstellen Sie ein `SharePointEmulationScope`-Objekt am Anfang der Methode. Alle unterstützten SharePoint-APIs werden emuliert werden, bis der Bereich freigegeben ist.

-   Schreiben Sie den Testcode, als ob Sie ihn für die tatsächliche SharePoint-API schreiben würden. Der Emulationskontext leitet die Aufrufe von SharePoint-Methoden automatisch an ihre Emulatoren um.

-   Nicht alle SharePoint-Objekte werden emuliert und nicht alle Methoden einiger emulierter Objekte werden emuliert. Eine `NotSupportedException`-Ausnahme wird ausgelöst, wenn Sie ein nicht emuliertes Objekt oder eine Methode verwenden. Wenn dies auftritt, erstellen Sie explizit einen Fakes-Shim-Delegaten für die Methode, um das erforderliche Verhalten zurückzugeben.

-   Um zweifach verwendbare Tests zu erstellen, verwenden Sie den `SharePointEmulationScope(EmulationMode)`-Konstruktor um das Emulationsbereichsobjekt zu erstellen. Der `EmulationMode`-Wert gibt an, ob die SharePoint-Aufrufe für eine echte SharePoint-Website emuliert oder ausgeführt werden.

-   Wenn alle oder die meisten Testmethoden in einer Testklasse im Emulationskontext ausgeführt werden, können Sie eine mit dem Attribut `TestInitialize` versehene Methode auf Klassenebene verwenden, um das `SharePointEmulationScope`-Objekt und ein Feld auf Klassenebene zum Festlegen des Emulationsmodus zu erstellen. Dies hilft Ihnen, die Änderung des Emulationsmodus zu automatisieren. Verwenden Sie dann eine mit dem Attribut `TestCleanup` versehene Methode, um das Bereichsobjekt freizugeben.

##  <a name="BKMK_Example"></a> Beispiel

Im Folgenden finden Sie ein letztes Beispiel, das die SharePoint-Emulatortechniken enthält, die oben beschrieben werden:

```csharp
using System;
//other namespace declarations
...
// code under test
using MySPApps;
using Microsoft.SharePoint;
// unit testing and emulators
using Microsoft.VisualStudio.TestTools.UnitTesting;
using Microsoft.QualityTools.Testing.Emulators;
using Microsoft.SharePoint.Emulators;
// explicit Fakes shims
using Microsoft.QualityTools.Testing.Fakes;
using Microsoft.SharePoint.Fakes

namspace MySPAppTests
{
    [TestClass]
    public class BookAnAppointmentWebPartTests
    {

        // emulationScope is a class level field
        private SharePointEmulationScope emulationScope;

        // preprocessor directives determine the value of emulatorMode
        #if USE_EMULATION
            private const EmulationMode emulatorMode = EmulationMode.Enabled;
        #else
            private const EmulationMode emulatorMode = EmulationMode.Passthrough;
        #endif

        // InitializeTest sets the emulation scope at the beginning of each test method
        [TestInitialize]
        public void InitializeTest()
        {
            this.emulationScope = new SharePointEmulationScope(emulatorMode);
        }

        // CleanupTest disposes the emulation scope at the end of each test method
        [TestCleanup]
        public void Cleanup()
        {
            this.emulationScope.Dispose();
        }

        [TestMethod]
        public void ScheduleAppointmentReturnsTrueWhenNewAppointmentIsCreated()
        {
            // remove the SharePointEmulationScope using statement from the method
            using( var site = new SPSite("http://localhost"))
            using (var webPart = new BookAnAppointmentWebPart())
            {
                // Arrange
                string errorMsg = string.Empty;
                DateTime date = DateTime.Now;
                SPList list = AddListToSiteHelper(site);

                // Act
                bool success = webPart.ScheduleAppointment(site.RootWeb, list.Title,
                    "Raisa Pokrovskaya", "425-555-0163", "raisa@outlook.com", "55", date,
                    out errorMsg);
                list.Delete()

                // Assert
                Assert.IsTrue(success);
            }
        }

        [TestMethod]
        public void GetAppointmentsForTodayReturnsOnlyTodaysAppointments()
        {

            // remove the SharePointEmulationScope using statement from the method
            using( var site = new SPSite("http://localhost"))
            using (var webPart = new BookAnAppointmentWebPart())
            {
                // Arrange
                DateTime date = DateTime.Now;
                SPList list = AddListToSiteHelper(site);
                // insert 2 items into list
                AddItemsToListHelper(list, new string[] {"Raisa Pokrovskaya", "425-555-0163",
                    "raisa@outlook.com", "55", date.ToString("D") });
                AddItemsToListHelper(list, new string[] {"Francis Totten", "313-555-0100",
                    "francis@contoso.com", "42", date.AddDays(1).ToString("D") });

                // use Fakes shims only if emulation is enabled
                if (emulatorMode == EmulationMode.Enabled)
                {
                    var sList = new ShimSPList(list);

                    sList.GetItemsSPQuery = (query) =>
                    {
                        var shim = new ShimSPListItemCollection();
                        shim.Bind(new[] { list.Items[0] });
                        return shim.Instance;
                    }
                }

                // Act
                string result = webPart.GetAppointmentsForToday(list.Title, site.RootWeb);
                list.Delete();

                // Assert
                Assert.IsTrue(result.Contains(String.Format(
                    "Name: Raisa Pokrovskaya, Phone: 425-555-0163, Email: raisa@outlook.com," +
                    "Age: 55, Date: {0}", date.ToString("D"))));
                Assert.IsFalse(result.Contains("Name: Francis Totten"));
            }
        }

        ...// More tests

    }
}
```

##  <a name="BKMK_Emulated_SharePoint_types"></a> Emulierte SharePoint-Typen

 <xref:Microsoft.SharePoint.SPField?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPFieldIndex?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPFieldIndexCollection?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPFieldLink?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPFieldLinkCollection?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPFieldUrlValue?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPFile?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPFileCollection?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPFolder?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPFolderCollection?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPItem?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPItemEventDataCollection?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPItemEventProperties?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPList?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPListCollection?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPListEventProperties?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPListItem?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPListItemCollection?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPQuery?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPRoleAssignment?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPRoleAssignmentCollection?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPSecurableObject?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPSecurity?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPSite?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPUser?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPUserCollection?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPView?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPViewCollection?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPViewContext?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPWeb?displayProperty=nameWithType>

 <xref:Microsoft.SharePoint.SPWebCollection?displayProperty=nameWithType>

## <a name="see-also"></a>Siehe auch

- [Ausführen von Komponententests für Code](../test/unit-test-your-code.md)
- [Testen von SharePoint 2010-Anwendungen mit Tests der programmierten UI](../test/testing-sharepoint-2010-applications-with-coded-ui-tests.md)
- [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)
