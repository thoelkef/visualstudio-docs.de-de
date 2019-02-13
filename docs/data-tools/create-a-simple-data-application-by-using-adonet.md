---
title: Erstellen einer einfachen Datenanwendung mit ADO.NET
ms.date: 08/23/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 2222841f-e443-4a3d-8c70-4506aa905193
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 36fc5dd306782779f553d4144c272c91c7e0f0af
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55929400"
---
# <a name="create-a-simple-data-application-by-using-adonet"></a>Erstellen einer einfachen Datenanwendung mit ADO.NET

Wenn Sie eine Anwendung erstellen, die Daten in einer Datenbank bearbeitet, führen Sie grundlegende Aufgaben aus wie Definieren von Verbindungszeichenfolgen, Einfügen von Daten und Ausführen gespeicherter Prozeduren. Befolgen Sie in diesem Thema, Sie können ermitteln, wie Sie mit einer Datenbank in einer einfachen Windows Forms "Forms over Data"-Anwendung zu interagieren, mithilfe von Visual C# oder Visual Basic und ADO.NET.  Alle .NET Data-Technologien, einschließlich Datasets, LINQ to SQL und Entity Framework – letztendlich Schritte, die in diesem Artikel gezeigten sehr ähnlich sind.

Dieser Artikel veranschaulicht eine einfache Möglichkeit zum Abrufen von Daten aus der Datenbank auf schnelle Weise. Wenn Ihre Anwendung muss Daten auf nicht trivialen Weise ändern und die Datenbank zu aktualisieren, sollten Sie sich mithilfe von Entity Framework und mithilfe der Datenbindung an um Steuerelemente der Benutzeroberfläche auf Änderungen in den zugrunde liegenden Daten automatisch zu synchronisieren.

> [!IMPORTANT]
> Der Code enthält keine produktionsbereite Ausnahmebehandlung, um ihn einfach zu halten.

## <a name="prerequisites"></a>Erforderliche Komponenten

Zum Erstellen der Anwendung benötigen Sie:

-   Visual Studio.

-   SQL Server Express LocalDB. Wenn Sie SQL Server Express LocalDB nicht haben, können Sie installieren, von der [Downloadseite für SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express).

In diesem Thema wird davon ausgegangen, dass Sie mit den grundlegenden Funktionen von Visual Studio-IDE vertraut, und eine Windows Forms-Anwendung erstellen, hinzufügen, dass das Projekt, und fügen Schaltflächen und andere Steuerelemente auf die Formulare, Formulare Eigenschaften der Steuerelemente und einfache Ereignisse programmieren festgelegt. Wenn Sie nicht mit diesen Aufgaben vertraut sind, empfiehlt es sich, dass Sie beim Ausführen der [erste Schritte mit Visual C# und Visual Basic](../ide/quickstart-visual-basic-console.md) Thema, bevor Sie in dieser exemplarischen Vorgehensweise beginnen.

## <a name="set-up-the-sample-database"></a>Die Beispieldatenbank einrichten

Erstellen der Beispieldatenbank mit folgenden Schritten:

1. Öffnen Sie in Visual Studio die **Server-Explorer** Fenster.

2. Mit der rechten Maustaste auf **Datenverbindungen** , und wählen Sie **neue SQL Server-Datenbank erstellen**.

3. In der **Servernamen** Text geben **(Localdb) \mssqllocaldb**.

4. In der **neuen Datenbanknamen** Text geben **Sales**, wählen Sie dann **OK**.

     Die leere **Sales** Datenbank erstellt und der Knoten "Datenverbindungen" im Server-Explorer hinzugefügt wird.

5. Mit der rechten Maustaste auf die **Sales** Datenverbindung, und wählen **neue Abfrage**.

     Ein Abfrage-Editor-Fenster wird geöffnet.

6. Kopieren der [Sales Transact-SQL-Skript](https://github.com/MicrosoftDocs/visualstudio-docs/raw/master/docs/data-tools/samples/sales.sql) in die Zwischenablage.

7. Fügen Sie das T-SQL-Skript im Abfrage-Editor, und wählen Sie dann die **Execute** Schaltfläche.

     Nach kurzer Zeit die Ausführung die Abfrage abgeschlossen ist, und die Datenbankobjekte erstellt werden. Die Datenbank enthält zwei Tabellen: Kunden und Bestellungen. Diese Tabellen enthalten Anfangs keine Daten, aber Sie können Daten hinzufügen, wenn Sie die Anwendung ausführen, die Sie erstellen. Die Datenbank enthält auch vier einfache gespeicherte Prozeduren.

## <a name="create-the-forms-and-add-controls"></a>Die Formulare erstellen und Steuerelemente hinzufügen

1. Erstellen Sie ein Projekt für eine Windows Forms-Anwendung, und nennen Sie es **SimpleDataApp**.

    Visual Studio erstellt das Projekt und mehrere Dateien, einschließlich eines leeren Windows-Formulars namens **Form1**.

2. Fügen Sie dem Projekt zwei Windows-Formulare hinzu, sodass es drei Formulare enthält, und geben Sie ihnen die folgenden Namen:

   -   **Navigation**

   -   **NewCustomer**

   -   **FillOrCancel**

3. Fügen Sie für jedes Formular die Textfelder, Schaltflächen und anderen Steuerelementen hinzu, die in der folgenden Abbildung dargestellt werden. Legen Sie für jedes Steuerelement die Eigenschaften fest, die in den Tabellen beschrieben werden.

   > [!NOTE]
   > Das Gruppenfeld und die Bezeichnungsfelder sorgen für Klarheit, werden im Code jedoch nicht verwendet.

   **Navigationsformular**

   ![Dialogfeld "Navigation"](../data-tools/media/simpleappnav.png)

|Steuerelemente für das Navigationsformular|Eigenschaften|
| - |----------------|
|Schaltfläche|Name = btnGoToAdd|
|Schaltfläche|Name = btnGoToFillOrCancel|
|Schaltfläche|Name = btnExit|

 **NewCustomer-Formular**

 ![Neuen Kunden hinzufügen und eine Bestellung aufgeben](../data-tools/media/simpleappnewcust.png)

|Steuerelemente für das NewCustomer-Formular|Eigenschaften|
| - |----------------|
|TextBox|Name = txtCustomerName|
|TextBox|Name = txtCustomerID<br /><br /> Readonly = True|
|Schaltfläche|Name = btnCreateAccount|
|NumericUpdown|DecimalPlaces = 0<br /><br /> Maximum = 5000<br /><br /> Name = numOrderAmount|
|DateTimePicker|Format = Short<br /><br /> Name = dtpOrderDate|
|Schaltfläche|Name = btnPlaceOrder|
|Schaltfläche|Name = btnAddAnotherAccount|
|Schaltfläche|Name = btnAddFinish|

 **FillOrCancel-Formular**

 ![Bestellungen erfüllen oder widerrufen](../data-tools/media/simpleappcancelfill.png)

|Steuerelemente für das FillOrCancel-Formular|Eigenschaften|
| - |----------------|
|TextBox|Name = txtOrderID|
|Schaltfläche|Name = btnFindByOrderID|
|DateTimePicker|Format = Short<br /><br /> Name = dtpFillDate|
|DataGridView|Name = dgvCustomerOrders<br /><br /> Readonly = True<br /><br /> RowHeadersVisible = False|
|Schaltfläche|Name = btnCancelOrder|
|Schaltfläche|Name = btnFillOrder|
|Schaltfläche|Name = btnFinishUpdates|

## <a name="store-the-connection-string"></a>Die Verbindungszeichenfolge speichern
 Wenn die Anwendung versucht, eine Verbindung zur Datenbank zu öffnen, muss die Anwendung Zugriff auf die Verbindungszeichenfolge haben. Um zu vermeiden, die Zeichenfolge in jedem Formular manuell einzugeben, speichern Sie die Zeichenfolge in die *"App.config"* -Datei in Ihrem Projekt, und erstellen Sie eine Methode, die die Zeichenfolge zurückgibt, wenn die Methode über ein beliebiges Formular in Ihrer Anwendung aufgerufen wird.

 Sie finden die Verbindungszeichenfolge, indem Sie mit der rechten Maustaste auf die **Sales** Datenverbindung in **Server-Explorer** und **Eigenschaften**. Suchen Sie die **"ConnectionString"** -Eigenschaft verwenden, klicken Sie dann **STRG**+**ein**, **STRG**+**C**  auswählen und kopieren Sie die Zeichenfolge in die Zwischenablage.

1.  Bei Verwendung von C#im **Projektmappen-Explorer**, erweitern Sie die **Eigenschaften** Knoten unter dem Projekt, und öffnen Sie dann die **Settings.settings** Datei.
    Wenn Sie in Visual Basic verwenden **Projektmappen-Explorer**, klicken Sie auf **alle Dateien anzeigen**, erweitern Sie die **Mein Projekt** Knoten, und öffnen Sie die **Settings.settings** Datei.

2.  In der **Namen** Spalte Geben Sie `connString`.

3.  In der **Typ** Liste **(Verbindungszeichenfolge)**.

4.  In der **Bereich** Liste **Anwendung**.

5.  In der **Wert** Spalte Geben Sie Ihre Verbindungszeichenfolge (ohne außerhalb der Anführungszeichen), und speichern Sie Ihre Änderungen.

> [!NOTE]
> In einer realen Anwendung sollten Sie sicher, wie beschrieben in der Verbindungszeichenfolge speichern [Verbindungszeichenfolgen und Konfigurationsdateien](/dotnet/framework/data/adonet/connection-strings-and-configuration-files).

##  <a name="write-the-code-for-the-forms"></a>Den Code für die Formulare schreiben

Dieser Abschnitt enthält kurze Übersichten über die Funktionsweise der einzelnen Formulare. Darüber hinaus den Code, der die zugrunde liegende Logik definiert werden, wenn eine Formular auf die Schaltfläche geklickt wird.

### <a name="navigation-form"></a>Navigationsformular

Das Navigationsformular wird geöffnet, wenn Sie die Anwendung ausführen. Die Schaltfläche **Konto hinzufügen** öffnet das NewCustomer-Formular. Die Schaltfläche **Auftrag ausfüllen oder abbrechen** öffnet das FillOrCancel-Formular. Die Schaltfläche **Beenden** schließt die Anwendung.

#### <a name="make-the-navigation-form-the-startup-form"></a>Das Navigationsformular als Startformular festlegen

Wenn Sie C# verwenden, öffnen Sie **Program.cs** im **Projektmappen-Explorer** und ändern die Zeile `Application.Run` in `Application.Run(new Navigation());`.

Wenn Sie in Visual Basic verwenden **Projektmappen-Explorer**öffnen die **Eigenschaften** wählen Sie im Fenster der **Anwendung** Registerkarte, und wählen Sie dann  **"Simpledataapp.Navigation"** in die **Startformular** Liste.

#### <a name="create-auto-generated-event-handlers"></a>Erstellen von automatisch generierten Ereignishandlern

Doppelklicken Sie auf die drei Schaltflächen für das Navigationsformular leere Ereignishandlermethoden erstellen. Durch Doppelklicken auf die Schaltflächen fügt automatisch generierten Code auch in der Designer-Codedatei, die einen Klick auf ein Ereignis auslösen kann.

#### <a name="add-code-for-the-navigation-form-logic"></a>Fügen Sie Code für die Navigationslogik-Formular hinzu

In der Codepage für das Navigationsformular klicken Sie auf vollständige den Text für die Schaltfläche mit den drei Ereignishandler wie im folgenden Code gezeigt.

[!code-csharp[Navigation#1](../data-tools/codesnippet/CSharp/SimpleDataApp/Navigation.cs#1)]
[!code-vb[Navigation#1](../data-tools/codesnippet/VisualBasic/SimpleDataApp/Navigation.vb#1)]

### <a name="newcustomer-form"></a>NewCustomer-Formular

Wenn Sie einen Kundennamen eingeben, und wählen Sie dann die **Kontoerstellung** Schaltfläche das NewCustomer-Formular erstellt, ein Kundenkonto und SQL Server gibt einen Identitätswert als neue Kunden-ID zurück. Sie können dann eine Bestellung für das neue Konto setzen, indem Sie eine Menge und ein Bestelldatum angeben und Auswählen der **Bestellung aufgeben** Schaltfläche.

#### <a name="create-auto-generated-event-handlers"></a>Erstellen von automatisch generierten Ereignishandlern

Erstellen Sie einen leeren Click-Ereignishandler für jede Schaltfläche auf das NewCustomer-Formular durch Doppelklicken auf jede der vier Schaltflächen. Durch Doppelklicken auf die Schaltflächen fügt automatisch generierten Code auch in der Designer-Codedatei, die einen Klick auf ein Ereignis auslösen kann.

#### <a name="add-code-for-the-newcustomer-form-logic"></a>Fügen Sie Code für die Logik der NewCustomer-Formular hinzu

Gehen Sie folgendermaßen vor, um die Logik der NewCustomer-Formular abzuschließen.

1. Schalten Sie die `System.Data.SqlClient` Namespace in den Bereich, damit Sie auf vollständig nicht qualifizierte Namen der Member.

     ```csharp
     using System.Data.SqlClient;
     ```
     ```vb
     Imports System.Data.SqlClient
     ```

2. Fügen Sie einige Variablen und die Hilfsmethoden der Klasse, wie im folgenden Code gezeigt.

     [!code-csharp[NewCustomer#1](../data-tools/codesnippet/CSharp/SimpleDataApp/NewCustomer.cs#1)]
     [!code-vb[NewCustomer#1](../data-tools/codesnippet/VisualBasic/SimpleDataApp/NewCustomer.vb#1)]

3. Vollständige klicken Sie auf der der Text für die Schaltfläche "vier"-Ereignishandler wie im folgenden Code gezeigt.

     [!code-csharp[NewCustomer#2](../data-tools/codesnippet/CSharp/SimpleDataApp/NewCustomer.cs#2)]
     [!code-vb[NewCustomer#2](../data-tools/codesnippet/VisualBasic/SimpleDataApp/NewCustomer.vb#2)]

### <a name="fillorcancel-form"></a>FillOrCancel-Formular

Das FillOrCancel-Formular führt eine Abfrage aus, um einen Auftrag zurückzugeben, wenn Sie eine Auftrags-ID eingeben, und klicken Sie dann auf die **Auftrag suchen** Schaltfläche. Die zurückgegebene Zeile wird in einem schreibgeschützten Datenraster angezeigt. Sie können den Auftrag als abgebrochen (X) kennzeichnen, bei Auswahl der **Auftrag stornieren** Schaltfläche, oder Sie können die Reihenfolge als markieren ausgefüllten (F) bei Auswahl der **Auftrag ausfüllen** Schaltfläche. Bei Auswahl der **Auftrag suchen** Schaltfläche in diesem Fall die aktualisierte Zeile angezeigt.

#### <a name="create-auto-generated-event-handlers"></a>Erstellen von automatisch generierten Ereignishandlern

Erstellen Sie leere-Ereignishandlern für die vier Schaltflächen für das FillOrCancel-Formular durch Doppelklicken auf die Schaltflächen klicken. Durch Doppelklicken auf die Schaltflächen fügt automatisch generierten Code auch in der Designer-Codedatei, die einen Klick auf ein Ereignis auslösen kann.

#### <a name="add-code-for-the-fillorcancel-form-logic"></a>Fügen Sie Code für die Logik der FillOrCancel-Formular hinzu

Um die Logik der FillOrCancel-Formular abgeschlossen haben, gehen Sie wie folgt vor.

1. Schalten Sie die folgenden beiden Namespaces in den Bereich, damit Sie nicht die Namen der Elemente vollständig zu qualifizieren.

     ```csharp
     using System.Data.SqlClient;
     using System.Text.RegularExpressions;
     ```
     ```vb
     Imports System.Data.SqlClient
     Imports System.Text.RegularExpressions
     ```

2. Fügen Sie eine Variable und Hilfsprogramm-Methode der Klasse an, wie im folgenden Code gezeigt.

     [!code-csharp[FillOrCancel#1](../data-tools/codesnippet/CSharp/SimpleDataApp/FillOrCancel.cs#1)]
     [!code-vb[FillOrCancel#1](../data-tools/codesnippet/VisualBasic/SimpleDataApp/FillOrCancel.vb#1)]

3. Vollständige klicken Sie auf der der Text für die Schaltfläche "vier"-Ereignishandler wie im folgenden Code gezeigt.

     [!code-csharp[FillOrCancel#2](../data-tools/codesnippet/CSharp/SimpleDataApp/FillOrCancel.cs#2)]
     [!code-vb[FillOrCancel#2](../data-tools/codesnippet/VisualBasic/SimpleDataApp/FillOrCancel.vb#2)]

## <a name="test-your-application"></a>Die Anwendung testen

Drücken Sie die **F5**-Taste, um die Anwendung zu erstellen und zu testen, nachdem Sie die einzelnen Click-Ereignishandler programmiert und die Programmierung beendet haben.

## <a name="see-also"></a>Siehe auch

- [Visual Studio-Datentools für .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
