---
title: Erstellen einer einfachen Daten Anwendung mit ADO.net | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
ms.assetid: 2222841f-e443-4a3d-8c70-4506aa905193
caps.latest.revision: 46
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b524c9d630f30edd226265ac150ef7ec4f6c60d8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651078"
---
# <a name="create-a-simple-data-application-by-using-adonet"></a>Erstellen einer einfachen Datenanwendung mit ADO.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie eine Anwendung erstellen, die Daten in einer Datenbank bearbeitet, führen Sie grundlegende Aufgaben aus, beispielsweise Definieren von Verbindungszeichenfolgen, Einfügen von Daten und Ausführen gespeicherter Prozeduren. In diesem Thema erfahren Sie, wie Sie über eine einfache Windows Forms "Forms over Data"-Anwendung mit einer Datenbank interagieren, indem Sie Visual C# oder Visual Basic und ADO.NET verwenden.  Alle .NET-Daten Technologien – einschließlich Datasets, LINQ to SQL und Entity Framework – führen letztendlich Schritte aus, die den in diesem Artikel gezeigten ähneln.

 Dieser Artikel veranschaulicht eine einfache Methode, um Daten aus einer Datenbank sehr schnell zu erhalten. Wenn Ihre Anwendung Daten auf nicht triviale Weise ändern und die Datenbank aktualisieren muss, sollten Sie die Verwendung von Entity Framework und die Verwendung der Datenbindung in Erwägung gezogen, um die Benutzeroberflächen-Steuerelemente automatisch mit Änderungen in den zugrunde liegenden Daten zu synchronisieren.

> [!IMPORTANT]
> Um den Code einfach zu halten, enthält er keine produktionsbereite Ausnahmebehandlung.

 **Inhalt**

- [Einrichten der Beispieldatenbank](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_setupthesampledatabase)

- [Erstellen der Formulare und Hinzufügen von Steuerelementen](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_createtheformsandaddcontrols)

- [Speichern der Verbindungs Zeichenfolge](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_storetheconnectionstring)

- [Abrufen der Verbindungs Zeichenfolge](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_retrievetheconnectionstring)

- [Schreiben des Codes für die Formulare](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_writethecodefortheforms)

- [Testen der Anwendung](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_testyourapplication)

## <a name="prerequisites"></a>Erforderliche Voraussetzungen
 Zum Erstellen der Anwendung benötigen Sie:

- Visual Studio Community Edition.

- SQL Server Express LocalDB.

- Die kleine Beispieldatenbank, die Sie erstellen, indem Sie die Schritte unter [Erstellen einer SQL-Datenbank mithilfe eines Skripts ausführen](../data-tools/create-a-sql-database-by-using-a-script.md).

- Die Verbindungszeichenfolge für die Datenbank, nachdem Sie sie eingerichtet haben. Sie finden diesen Wert, indem Sie **SQL Server-Objekt-Explorer**öffnen, das Kontextmenü für die Datenbank öffnen, **Eigenschaften**auswählen und dann einen Bildlauf zur **ConnectionString** -Eigenschaft durchführen.

  In diesem Thema wird davon ausgegangen, dass Sie mit der grundlegenden Funktionalität der Visual Studio IDE vertraut sind und eine Windows Forms-Anwendung erstellen, diesem Projekt Formulare hinzufügen, Schaltflächen und andere Steuerelemente in diesen Formularen einfügen, Eigenschaften für diese Steuerelemente einrichten und einfache Ereignisse programmieren können. Wenn Sie mit diesen Aufgaben nicht vertraut sind, empfehlen wir Ihnen, die ersten Schritte [mit Visual C# und Visual Basic](../ide/getting-started-with-visual-csharp-and-visual-basic.md) abzuschließen, bevor Sie mit diesem Thema beginnen.

## <a name="BKMK_setupthesampledatabase"></a>Einrichten der Beispieldatenbank
 Die Beispieldatenbank für diese exemplarische Vorgehensweise besteht aus den Tabellen "Customer" und "Orders". Die Tabellen enthalten anfangs keine Daten, aber Sie fügen Daten hinzu, wenn Sie die von Ihnen erstellte Anwendung ausführen. Die Datenbank hat auch fünf einfache gespeicherte Prozeduren. [Erstellen einer SQL-Datenbank mithilfe eines Skripts](../data-tools/create-a-sql-database-by-using-a-script.md) enthält ein Transact-SQL-Skript, mit dem die Tabellen, die Primär-und Fremdschlüssel, die Einschränkungen und die gespeicherten Prozeduren erstellt werden.

## <a name="BKMK_createtheformsandaddcontrols"></a>Erstellen der Formulare und Hinzufügen von Steuerelementen

1. Erstellen Sie ein Projekt für eine Windows Forms Anwendung, und nennen Sie es simpledataapp.

    Visual Studio erstellt das Projekt und mehrere Dateien, einschließlich eines leeren Windows-Formulars namens "Form1".

2. Fügen Sie dem Projekt zwei Windows-Formulare hinzu, sodass es drei Formulare enthält, und geben Sie ihnen die folgenden Namen:

   - Navigation

   - NewCustomer

   - FillOrCancel

3. Fügen Sie für jedes Formular die Textfelder, Schaltflächen und anderen Steuerelementen hinzu, die in der folgenden Abbildung dargestellt werden. Legen Sie für jedes Steuerelement die Eigenschaften fest, die in den Tabellen beschrieben werden.

   > [!NOTE]
   > Das Gruppenfeld und die Bezeichnungsfelder sorgen für Klarheit, werden im Code jedoch nicht verwendet.

   **Navigationsformular**

   ![Navigations Dialogfeld](../data-tools/media/simpleappnav.png "Simpleappnav")

|Steuerelemente für das Navigationsformular|Eigenschaften|
|--------------------------------------|----------------|
|Schaltfläche|Name = btnGoToAdd|
|Schaltfläche|Name = btnGoToFillOrCancel|
|Schaltfläche|Name = btnExit|

 **NewCustomer-Formular**

 ![Neuen Kunden hinzufügen und eine Bestellung aufgeben](../data-tools/media/simpleappnewcust.png "Simpleappnewcust")

|Steuerelemente für das NewCustomer-Formular|Eigenschaften|
|---------------------------------------|----------------|
|TextBox|Name = txtCustomerName|
|TextBox|Name = txtCustomerID<br /><br /> Readonly = True|
|Schaltfläche|Name = btnCreateAccount|
|NumericUpdown|DecimalPlaces = 0<br /><br /> Maximum = 5000<br /><br /> Name = numOrderAmount|
|DateTimePicker|Format = Short<br /><br /> Name = dtpOrderDate|
|Schaltfläche|Name = btnPlaceOrder|
|Schaltfläche|Name = btnAddAnotherAccount|
|Schaltfläche|Name = btnAddFinish|

 **FillOrCancel-Formular**

 ![ausfüllen oder Abbrechen von Aufträgen](../data-tools/media/simpleappcancelfill.png "Simpleappcancelfill")

|Steuerelemente für das FillOrCancel-Formular|Eigenschaften|
|----------------------------------------|----------------|
|TextBox|Name = txtOrderID|
|Schaltfläche|Name = btnFindByOrderID|
|DateTimePicker|Format = Short<br /><br /> Name = dtpFillDate|
|DataGridView|Name = dgvCustomerOrders<br /><br /> Readonly = True<br /><br /> RowHeadersVisible = False|
|Schaltfläche|Name = btnCancelOrder|
|Schaltfläche|Name = btnFillOrder|
|Schaltfläche|Name = btnFinishUpdates|

## <a name="BKMK_storetheconnectionstring"></a>Speichern der Verbindungs Zeichenfolge
 Wenn die Anwendung versucht, eine Verbindung zur Datenbank zu öffnen, muss die Anwendung Zugriff auf die Verbindungszeichenfolge haben. Speichern Sie die Zeichenfolge in der APP-Konfigurationsdatei in Ihrem Projekt, und erstellen Sie eine Methode, die die Zeichenfolge zurückgibt, wenn die Methode von einem beliebigen Formular in der Anwendung aufgerufen wird, um zu vermeiden, dass die Zeichenfolge manuell eingegeben wird.

 Sie können die Verbindungs Zeichenfolge in **SQL Server-Objekt-Explorer** finden, indem Sie mit der rechten Maustaste auf die Datenbank klicken, **Eigenschaften**auswählen und dann die ConnectionString-Eigenschaft suchen. Verwenden Sie STRG + A, um die Zeichenfolge auszuwählen.

1. Wählen Sie in **Projektmappen-Explorer**den Knoten **Eigenschaften** unter dem Projekt aus, und wählen Sie dann **Settings. Settings**aus.

2. Geben Sie in der Spalte **Name** `connString` ein.

3. Wählen Sie in der Liste **Typ** die Option **(Verbindungs Zeichenfolge)** aus.

4. Wählen Sie in der Liste **Bereich den Bereich** **Anwendung**aus.

5. Geben Sie in der Spalte **Wert** die Verbindungs Zeichenfolge (ohne äußere Anführungszeichen) ein, und speichern Sie die Änderungen.

> [!NOTE]
> In einer realen Anwendung sollten Sie die Verbindungs Zeichenfolge sicher speichern, wie in Verbindungs Zeichenfolgen [und Konfigurationsdateien](https://msdn.microsoft.com/library/37df2641-661e-407a-a3fb-7bf9540f01e8)beschrieben.

## <a name="BKMK_retrievetheconnectionstring"></a>Abrufen der Verbindungs Zeichenfolge

1. Wählen Sie in der Menüleiste **Projekt**  > **Verweis hinzufügen**aus, und fügen Sie dann einen Verweis auf "System. Configuration. dll" hinzu.

2. Wählen Sie in der Menüleiste **Projekt**  > **Klasse hinzufügen** aus, um dem Projekt eine Klassendatei hinzuzufügen, und benennen Sie die Datei `Utility`.

     Visual Studio erstellt die Datei und zeigt Sie in **Projektmappen-Explorer**an.

3. Ersetzen Sie den Platzhaltercode in der Datei "Utility" durch folgenden Code. Beachten Sie die nummerierten Kommentare (mit vorangestelltem "Uti-"), die die Abschnitte des Codes kennzeichnen. In der Tabelle, die unter dem Code steht, werden wesentliche Punkte aufgeführt.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Text;
    using System.Threading.Tasks;
    //Util-1 More namespaces.
    using System.Configuration;

    namespace SimpleDataApp
    {
        internal class Utility
        {

            //Get the connection string from App config file.
            internal static string GetConnectionString()
            {
                //Util-2 Assume failure.
                string returnValue = null;

                //Util-3 Look for the name in the connectionStrings section.
                ConnectionStringSettings settings =
                ConfigurationManager.ConnectionStrings["SimpleDataApp.Properties.Settings.connString"];

                //If found, return the connection string.
                if (settings != null)
                    returnValue = settings.ConnectionString;

                return returnValue;
            }
        }
    }
    ```

    ```vb
    Imports System
    Imports System.Collections.Generic
    Imports System.Linq
    Imports System.Text
    Imports System.Threading.Tasks
    ' Util-1 More namespaces.
    Imports System.Configuration

    Namespace SimpleDataApp
        Friend Class Utility

            ' Get connection string from App config file.
            Friend Shared Function GetConnectionString() As String

                ' Util-2 Assume failure.
                Dim returnValue As String = Nothing

                ' Util-3 Look for the name in the connectionStrings section.
                Dim settings As ConnectionStringSettings = ConfigurationManager.ConnectionStrings("SimpleDataApp.My.MySettings.connString")

                ' If found, return the connection string.
                If settings IsNot Nothing Then
                    returnValue = settings.ConnectionString
                End If

                Return returnValue
            End Function
        End Class
    End Namespace
    ```

    |Kommentar|Beschreibung|
    |-------------|-----------------|
    |Util-1|Fügen Sie den `System.Configuration` -Namespace hinzu.|
    |Util-2|Definieren Sie die Variable `returnValue`, und initialisieren Sie sie mit `null` (C#) oder `Nothing` (Visual Basic).|
    |Util-3|Obwohl Sie im **Eigenschaften** Fenster `connString` als Namen der Verbindungs Zeichenfolge eingegeben haben, müssen Sie `"SimpleDataApp.Properties.Settings.connString"` (C#) oder `"SimpleDataApp.My.MySettings.connString"` (Visual Basic) im Code angeben.|

## <a name="BKMK_writethecodefortheforms"></a>Schreiben des Codes für die Formulare
 Dieser Abschnitt enthält kurze Übersichten über den Zweck der einzelnen Formulare sowie den Code, der die Formulare erstellt. Nummerierte Kommentare kennzeichnen die Codeabschnitte.

### <a name="navigation-form"></a>Navigationsformular
 Das Navigationsformular wird geöffnet, wenn Sie die Anwendung ausführen. Die Schaltfläche **Konto hinzufügen** öffnet das NewCustomer-Formular. Die Schaltfläche **Auftrag ausfüllen oder abbrechen** öffnet das FillOrCancel-Formular. Die Schaltfläche **Beenden** schließt die Anwendung.

#### <a name="make-the-navigation-form-the-startup-form"></a>Das Navigationsformular als Startformular festlegen
 Wenn Sie verwenden C#, öffnen Sie in **Projektmappen-Explorer**Program.cs, und ändern Sie dann die `Application.Run` Zeile in this: `Application.Run(new Navigation());`

 Wenn Sie Visual Basic verwenden, öffnen Sie in **Projektmappen-Explorer**das Fenster **Eigenschaften** , wählen Sie die Registerkarte **Anwendung** aus, und wählen Sie dann **simpledataapp. Navigation** in der Liste **Start Formular** aus.

#### <a name="create-event-handlers"></a>Ereignishandler erstellen
 Doppelklicken Sie auf die drei Schaltflächen im Formular, um leere Ereignishandlermethoden zu erstellen.

#### <a name="create-code-for-navigation"></a>Code für "Navigation" erstellen
 Ersetzen Sie im Navigationsformular den vorhandenen Code durch den folgenden Code.

```csharp
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace SimpleDataApp
{
    public partial class Navigation : Form
    {
        public Navigation()
        {
            InitializeComponent();
        }

        //Open the NewCustomer form as a dialog box, which will return focus to the calling form when it closes.
        private void btnGoToAdd_Click(object sender, EventArgs e)
        {
            Form frm = new NewCustomer();
            frm.Show();
        }

        //Open the FillorCancel form as a dialog box.
        private void btnGoToFillOrCancel_Click(object sender, EventArgs e)
        {
            Form frm = new FillOrCancel();
            frm.ShowDialog();
        }

        //Close the application, not just the Navigation form.
        private void btnExit_Click(object sender, EventArgs e)
        {
            this.Close();
        }
    }
}
```

```vb
Imports System
Imports System.Collections.Generic
Imports System.ComponentModel
Imports System.Data
Imports System.Drawing
Imports System.Linq
Imports System.Text
Imports System.Threading.Tasks
Imports System.Windows.Forms

Namespace SimpleDataApp
    Partial Public Class Navigation
        Inherits Form
        Public Sub New()
            InitializeComponent()
        End Sub

        ' Open the NewCustomer form as a dialog box, which will return focus to the calling form when it closes.
        Private Sub btnGoToAdd_Click() Handles btnGoToAdd.Click
            Dim frm As Form = New NewCustomer()
            frm.Show()
        End Sub

        ' Open the FillorCancel form as a dialog box.
        Private Sub btnGoToFillOrCancel_Click() Handles btnGoToFillOrCancel.Click
            Dim frm As Form = New FillOrCancel()
            frm.ShowDialog()
        End Sub

        ' Close the application, not just the Navigation form.
        Private Sub btnExit_Click() Handles btnExit.Click
            Me.Close()
        End Sub
    End Class
End Namespace

```

### <a name="newcustomer-form"></a>NewCustomer-Formular
 Wenn Sie einen Kundennamen eingeben und dann auf die Schaltfläche **Konto erstellen** klicken, erstellt das NewCustomer-Formular ein Kundenkonto, und SQL Server einen Identitäts Wert als neue Kontonummer zurück. Anschließend legen Sie eine Bestellung für das neue Konto fest, indem Sie einen Betrag und ein Bestelldatum angeben und die Schaltfläche **Bestellung platzieren** auswählen.

#### <a name="create-event-handlers"></a>Ereignishandler erstellen
 Erstellen Sie einen leeren Click-Ereignishandler für jede Schaltfläche im Formular.

#### <a name="create-code-for-newcustomer"></a>Code für "NewCustomer" erstellen
 Fügen Sie dem NewCustomer-Formular folgenden Code hinzu. Führen Sie jeden Codeblock schrittweise aus, und verwenden Sie dazu die nummerierten Kommentare und die Tabelle unter dem Code.

```csharp
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;
//NC-1 More namespaces.
using System.Data.SqlClient;
using System.Configuration;

namespace SimpleDataApp
{
    public partial class NewCustomer : Form
    {
        //NC-2 Storage for IDENTITY values returned from database.
        private int parsedCustomerID;
        private int orderID;

        //NC-3 Specify a connection string.
        string connstr = SimpleDataApp.Utility.GetConnectionString();

        public NewCustomer()
        {
            InitializeComponent();
        }

        //NC-4 Create account.
        private void btnCreateAccount_Click(object sender, EventArgs e)
        {
            //NC-5 Set up and run stored procedure only if Customer Name is present.
            if (isCustomerName())
            {

                //NC-6 Create the connection.
                SqlConnection conn = new SqlConnection(connstr);

                //NC-7 Create a SqlCommand, and identify it as a stored procedure.
                SqlCommand cmdNewCustomer = new SqlCommand("Sales.uspNewCustomer", conn);
                cmdNewCustomer.CommandType = CommandType.StoredProcedure;

                //NC-8 Add input parameter from the stored procedure and specify what to use as its value.
                cmdNewCustomer.Parameters.Add(new SqlParameter("@CustomerName", SqlDbType.NVarChar, 40));
                cmdNewCustomer.Parameters["@CustomerName"].Value = txtCustomerName.Text;

                //NC-9 Add output parameter.
                cmdNewCustomer.Parameters.Add(new SqlParameter("@CustomerID", SqlDbType.Int));
                cmdNewCustomer.Parameters["@CustomerID"].Direction = ParameterDirection.Output;

                //NC-10 try-catch-finally
                try
                {
                    //NC-11 Open the connection.
                    conn.Open();

                    //NC-12 Run the stored procedure.
                    cmdNewCustomer.ExecuteNonQuery();

                    //NC-13 Customer ID is an IDENTITY value from the database.
                    this.parsedCustomerID = (int)cmdNewCustomer.Parameters["@CustomerID"].Value;
                    this.txtCustomerID.Text = Convert.ToString(parsedCustomerID);

                }
                catch
                {
                    //NC-14 A simple catch.

                    MessageBox.Show("Customer ID was not returned. Account could not be created.");
                }
                finally
                {
                    //NC-15 Close the connection.
                    conn.Close();
                }
            }
        }

        //NC-16 Verify that Customer Name is present.
        private bool isCustomerName()
        {
            if (txtCustomerName.Text == "")
            {
                MessageBox.Show("Please enter a name.");
                return false;
            }
            else
            {
                return true;
            }
        }

        //NC-17 Place order.
        private void btnPlaceOrder_Click(object sender, EventArgs e)
        {
            //NC-18 Set up and run stored procedure only if required input is present.
            if (isPlaceOrderReady())
            {
                // Create the connection.
                SqlConnection conn = new SqlConnection(connstr);

                //NC-19 Create SqlCommand and identify it as a stored procedure.
                SqlCommand cmdNewOrder = new SqlCommand("Sales.uspPlaceNewOrder", conn);
                cmdNewOrder.CommandType = CommandType.StoredProcedure;

                //NC-20 @CustomerID, which was an output parameter from uspNewCustomer.
                cmdNewOrder.Parameters.Add(new SqlParameter("@CustomerID", SqlDbType.Int));
                cmdNewOrder.Parameters["@CustomerID"].Value = this.parsedCustomerID;

                //NC-21 @OrderDate.
                cmdNewOrder.Parameters.Add(new SqlParameter("@OrderDate", SqlDbType.DateTime, 8));
                cmdNewOrder.Parameters["@OrderDate"].Value = dtpOrderDate.Value;

                //NC-22 @Amount.
                cmdNewOrder.Parameters.Add(new SqlParameter("@Amount", SqlDbType.Int));
                cmdNewOrder.Parameters["@Amount"].Value = numOrderAmount.Value;

                //NC-23 @Status. For a new order, the status is always O (open).
                cmdNewOrder.Parameters.Add(new SqlParameter("@Status", SqlDbType.Char, 1));
                cmdNewOrder.Parameters["@Status"].Value = "O";

                //NC-24 Add return value for stored procedure, which is orderID.
                cmdNewOrder.Parameters.Add(new SqlParameter("@RC", SqlDbType.Int));
                cmdNewOrder.Parameters["@RC"].Direction = ParameterDirection.ReturnValue;

                //try-catch-finally
                try
                {
                    //Open connection.
                    conn.Open();

                    //Run the stored procedure.
                    cmdNewOrder.ExecuteNonQuery();

                    //NC-25 Display the order number.
                    this.orderID = (int)cmdNewOrder.Parameters["@RC"].Value;
                    MessageBox.Show("Order number " + this.orderID + " has been submitted.");
                }
                catch
                {
                    //A simple catch.
                    MessageBox.Show("Order could not be placed.");
                }
                finally
                {
                    //Close connection.
                    conn.Close();
                }
            }
        }

        //NC-26 Verify that order data is ready.
        private bool isPlaceOrderReady()
        {
            // Verify that CustomerID is present.
            if (txtCustomerID.Text == "")
            {
                MessageBox.Show("Please create customer account before placing order.");
                return false;
            }

            // Verify that Amount isn't 0.
            else if ((numOrderAmount.Value < 1))
            {
                MessageBox.Show("Please specify an order amount.");
                return false;
            }
            else
            {
                // Order can be submitted.
                return true;
            }
        }

        //NC-27 Reset the form for another new account.
        private void btnAddAnotherAccount_Click(object sender, EventArgs e)
        {
            this.ClearForm();
        }

        //NC-28 Clear values from controls.
        private void ClearForm()
        {
            txtCustomerName.Clear();
            txtCustomerID.Clear();
            dtpOrderDate.Value = DateTime.Now;
            numOrderAmount.Value = 0;
            this.parsedCustomerID = 0;
        }

        //NC-29 Close the form.
        private void btnAddFinish_Click(object sender, EventArgs e)
        {
            this.Close();
        }

    }
}

```

```vb
Imports System
Imports System.Collections.Generic
Imports System.ComponentModel
Imports System.Data
Imports System.Drawing
Imports System.Linq
Imports System.Text
Imports System.Threading.Tasks
Imports System.Windows.Forms
' NC-1 More namespaces.
Imports System.Data.SqlClient
Imports System.Configuration

Namespace SimpleDataApp
    Partial Public Class NewCustomer
        Inherits Form

        ' NC-2 Storage for IDENTITY values returned from database.
        Private parsedCustomerID As Integer
        Private orderID As Integer

        ' NC-3 Specify a connection string.
        Private connstr As String = SimpleDataApp.Utility.GetConnectionString()

        Public Sub New()
            InitializeComponent()
        End Sub

        ' NC-4 Create account.
        Private Sub btnCreateAccount_Click() Handles btnCreateAccount.Click

            ' NC-5 Set up and run stored procedure only if Customer Name is present.
            If isCustomerName() Then

                ' NC-6 Create the connection.
                Dim conn As New SqlConnection(connstr)

                ' NC-7 Create a SqlCommand, and identify it as a stored procedure.
                Dim cmdNewCustomer As New SqlCommand("Sales.uspNewCustomer", conn)
                cmdNewCustomer.CommandType = CommandType.StoredProcedure

                ' NC-8 Add input parameter from the stored procedure and specify what to use as its value.
                cmdNewCustomer.Parameters.Add(New SqlParameter("@CustomerName", SqlDbType.NVarChar, 40))
                cmdNewCustomer.Parameters("@CustomerName").Value = txtCustomerName.Text

                ' NC-9 Add output parameter.
                cmdNewCustomer.Parameters.Add(New SqlParameter("@CustomerID", SqlDbType.Int))
                cmdNewCustomer.Parameters("@CustomerID").Direction = ParameterDirection.Output

                ' NC-10 try-catch-finally
                Try
                    ' NC-11 Open the connection.
                    conn.Open()

                    ' NC-12 Run the stored procedure.
                    cmdNewCustomer.ExecuteNonQuery()

                    ' NC-13 Customer ID is an IDENTITY value from the database.
                    Me.parsedCustomerID = CInt(cmdNewCustomer.Parameters("@CustomerID").Value)
                    Me.txtCustomerID.Text = Convert.ToString(parsedCustomerID)

                Catch
                    ' NC-14 A simple catch.
                    MessageBox.Show("Customer ID was not returned. Account could not be created.")
                Finally
                    ' NC-15 Close the connection.
                    conn.Close()
                End Try
            End If
        End Sub

        ' NC-16 Verify that Customer Name is present.
        Private Function isCustomerName() As Boolean
            If txtCustomerName.Text = "" Then
                MessageBox.Show("Please enter a name.")
                Return False
            Else
                Return True
            End If
        End Function

        ' NC-17 Place order.
        Private Sub btnPlaceOrder_Click() Handles btnPlaceOrder.Click

            ' NC-18 Set up and run stored procedure only if necessary input is present.
            If isPlaceOrderReady() Then

                ' Create the connection.
                Dim conn As New SqlConnection(connstr)

                ' NC-19 Create SqlCommand and identify it as a stored procedure.
                Dim cmdNewOrder As New SqlCommand("Sales.uspPlaceNewOrder", conn)
                cmdNewOrder.CommandType = CommandType.StoredProcedure

                ' NC-20 @CustomerID, which was an output parameter from uspNewCustomer.
                cmdNewOrder.Parameters.Add(New SqlParameter("@CustomerID", SqlDbType.Int))
                cmdNewOrder.Parameters("@CustomerID").Value = Me.parsedCustomerID

                ' NC-21 @OrderDate.
                cmdNewOrder.Parameters.Add(New SqlParameter("@OrderDate", SqlDbType.DateTime, 8))
                cmdNewOrder.Parameters("@OrderDate").Value = dtpOrderDate.Value

                ' NC-22 @Amount.
                cmdNewOrder.Parameters.Add(New SqlParameter("@Amount", SqlDbType.Int))
                cmdNewOrder.Parameters("@Amount").Value = numOrderAmount.Value

                ' NC-23 @Status. For a new order, the status is always O (open).
                cmdNewOrder.Parameters.Add(New SqlParameter("@Status", SqlDbType.[Char], 1))
                cmdNewOrder.Parameters("@Status").Value = "O"

                ' NC-24 Add return value for stored procedure, which is orderID.
                cmdNewOrder.Parameters.Add(New SqlParameter("@RC", SqlDbType.Int))
                cmdNewOrder.Parameters("@RC").Direction = ParameterDirection.ReturnValue

                ' try-catch-finally
                Try
                    ' Open connection.
                    conn.Open()

                    ' Run the stored procedure.
                    cmdNewOrder.ExecuteNonQuery()

                    ' NC-25 Display the order number.
                    Me.orderID = CInt(cmdNewOrder.Parameters("@RC").Value)
                    MessageBox.Show("Order number " & (Me.orderID).ToString & " has been submitted.")

                Catch
                    ' A simple catch.
                    MessageBox.Show("Order could  not be placed.")

                Finally
                    ' Close connection.
                    conn.Close()
                End Try
            End If
        End Sub

        ' NC-26 Verify that order data is ready.
        Private Function isPlaceOrderReady() As Boolean

            ' Verify that CustomerID is present.
            If txtCustomerID.Text = "" Then
                MessageBox.Show("Please create customer account before placing order.")
                Return False

                ' Verify that Amount isn't 0.
            ElseIf (numOrderAmount.Value < 1) Then

                MessageBox.Show("Please specify an order amount.")
                Return False
            Else
                ' Order can be submitted.
                Return True
            End If
        End Function

        ' NC-27 Reset the form for another new account.
        Private Sub btnAddAnotherAccount_Click() Handles btnAddAnotherAccount.Click
            Me.ClearForm()
        End Sub

        ' NC-28 Clear values from controls.
        Private Sub ClearForm()
            txtCustomerName.Clear()
            txtCustomerID.Clear()
            dtpOrderDate.Value = DateTime.Now
            numOrderAmount.Value = 0
            Me.parsedCustomerID = 0
        End Sub

        ' NC-29 Close the form.
        Private Sub btnAddFinish_Click() Handles btnAddFinish.Click
            Me.Close()
        End Sub

    End Class
End Namespace
```

|Kommentar|Beschreibung|
|-------------|-----------------|
|NC-1|Fügen Sie der Liste der Namespaces `System.Data.SqlClient` und `System.Configuration` hinzu.|
|NC-2|Deklarieren Sie die Variablen `parsedCustomerID` und `orderID`, die später verwendet werden.|
|NC-3|Rufen Sie die `GetConnectionString`-Methode auf, um die Verbindungszeichenfolge aus der Datei "App.config" abzurufen, und speichern Sie den Wert in der Zeichenfolgenvariablen `connstr`.|
|NC-4|Fügen Sie dem Click-Ereignishandler den Code für die Schaltfläche `btnCreateAccount` hinzu.|
|NC-5|Umschließen Sie den Code des Click-Ereignisses mit dem Aufruf von `isCustomerName`, sodass `uspNewCustomer` nur ausgeführt wird, wenn ein Kundenname vorhanden ist.|
|NC-6|Erstellen Sie ein `SqlConnection`-Objekt (`conn`), und übergeben Sie die Verbindungszeichenfolge an `connstr`.|
|NC-7|Erstellen Sie das `SqlCommand`-Objekt `cmdNewCustomer`.<br /><br /> -Geben Sie `Sales.uspNewCustomer` als gespeicherte Prozedur an, die ausgeführt werden soll.<br />-Verwenden Sie die `CommandType`-Eigenschaft, um anzugeben, dass der Befehl eine gespeicherte Prozedur ist.|
|NC-8|Fügen Sie den Eingabeparameter `@CustomerName` aus der gespeicherten Prozedur ein.<br /><br /> -Parameter der `Parameters` Auflistung hinzufügen.<br />-Verwenden Sie die `SqlDbType`-Enumeration, um den Parametertyp als nvarchar (40) anzugeben.<br />-Geben Sie `txtCustomerName.Text` als Quelle an.|
|NC-9|Fügen Sie den Ausgabeparameter aus der gespeicherten Prozedur ein.<br /><br /> -Parameter der `Parameters` Auflistung hinzufügen.<br />-Verwenden Sie `ParameterDirection.Output`, um den Parameter als Ausgabe zu identifizieren.|
|NC-10|Fügen Sie einen try-catch-then-Block hinzu, um die Verbindung zu öffnen, führen Sie die gespeicherte Prozedur aus, behandeln Sie Ausnahmen, und schließen Sie dann die Verbindung.|
|NC-11|Öffnen Sie die Verbindung (`conn`), die Sie unter NC-6 erstellt haben.|
|NC-12|Verwenden Sie die `ExecuteNonQuery`-Methode für die `cmdNewCustomer`, um die gespeicherte Prozedur `Sales.uspNewCustomer` auszuführen. Diese gespeicherte Prozedur führt eine `INSERT`-Anweisung und keine-Abfrage aus.|
|NC-13|Der `@CustomerID`-Wert wird als Identitätswert aus der Datenbank zurückgegeben. Da es sich um eine ganze Zahl handelt, müssen Sie Sie in eine Zeichenfolge konvertieren, um Sie im Textfeld **Customer ID** anzuzeigen.<br /><br /> -Sie haben `parsedCustomerID` bei NC-2 deklariert.<br />: Speichert den `@CustomerID` Wert für die spätere Verwendung in `parsedCustomerID`.<br />-Konvertieren Sie die zurückgegebene Kunden-ID in eine Zeichenfolge, und fügen Sie Sie in `txtCustomerID.Text` ein.|
|NC-14|Fügen Sie für dieses Beispiel eine einfache catch-Klausel (nicht Produktionsqualität) hinzu.|
|NC-15|Schließen Sie eine Verbindung immer, wenn Sie sie nicht mehr verwenden, sodass sie für den Verbindungspool freigegeben werden kann. Weitere Informationen finden Sie unter [SQL Server Verbindungs Pooling (ADO.net)](https://msdn.microsoft.com/library/8xx3tyca\(l=en-us,v=VS.110\).aspx).|
|NC-16|Definieren Sie eine Methode, um zu überprüfen, ob ein Kundenname vorhanden ist.<br /><br /> -Wenn das Textfeld leer ist, wird eine Meldung angezeigt, und es wird `false` zurückgegeben, da zum Erstellen des Kontos ein Name erforderlich ist.<br />Wenn das Textfeld nicht leer ist, wird `true` zurückgegeben.|
|NC-17|Fügen Sie dem Click-Ereignishandler den Code für die Schaltfläche `btnPlaceOrder` hinzu.|
|NC-18|Umschließen Sie den Ereigniscode `isPlaceOrderReady` mit dem Aufruf von `btnPlaceOrder_Click`, sodass `uspPlaceNewOrder` nicht ausgeführt wird, wenn die erforderliche Eingabe fehlt.|
|NC-19 bis NC-25|Diese Codeabschnitte ähneln dem Code, den Sie für den Ereignishandler `btnCreateAccount_Click` hinzugefügt haben.<br /><br /> -NC-19. Erstellen Sie das `SqlCommand`-Objekt `cmdNewOrder`, und geben Sie `Sales.uspPlaceOrder` als die gespeicherte Prozedur an.<br />-NC-20 bis NC-23 sind die Eingabeparameter für die gespeicherte Prozedur.<br />-NC-24. `@RC` enthält einen Rückgabewert, der die generierte Auftrags-ID aus der Datenbank ist. Die Richtung dieses Parameters wird als `ReturnValue` angegeben.<br />-NC-25. Speichern Sie den Wert der Auftrags-ID in der Variablen `orderID`, die Sie unter NC-2 deklariert haben, und zeigen Sie den Wert in einem Meldungsfeld an.|
|NC-26|Definieren Sie eine Methode, um zu überprüfen, ob eine Kunden-ID vorhanden ist und ob in `numOrderAmount` eine Menge angegeben wurde.|
|NC-27|Rufen Sie die `ClearForm`-Methode im Click-Ereignishandler `btnAddAnotherAccount` auf.|
|NC-28|Erstellen Sie die `ClearForm`-Methode, um Werte aus dem Formular zu löschen, wenn Sie einen weiteren Kunden hinzufügen möchten.|
|NC-29|Schließen Sie das NewCustomer-Formular, und geben Sie den Fokus an das Navigationsformular zurück.|

### <a name="fillorcancel-form"></a>FillOrCancel-Formular
 Das Formular "fllorcancel" führt eine Abfrage aus, um eine Bestellung zurückzugeben, wenn Sie eine Bestell-ID eingeben und die Schaltfläche " **Auftrag suchen** " auswählen Die zurückgegebene Zeile wird in einem schreibgeschützten Datenraster angezeigt. Sie können die Bestellung als abgebrochen (X) markieren, wenn Sie die Schaltfläche **Bestellung abbrechen** auswählen, oder Sie können die Bestellung als ausgefüllt markieren (F), wenn Sie die Schaltfläche Reihen **Folge ausfüllen** auswählen. Wenn Sie die Schaltfläche " **Bestellung suchen** " erneut auswählen, wird die aktualisierte Zeile angezeigt.

#### <a name="create-event-handlers"></a>Ereignishandler erstellen
 Erstellen Sie leere Click-Ereignishandler für die vier Schaltflächen in dem Formular.

#### <a name="create-code-for-fillorcancel"></a>Erstellen Sie Code für "FillOrCancel".
 Fügen Sie dem FillOrCancel-Formular folgenden Code hinzu. Führen Sie die Codeblöcke schrittweise aus, indem Sie die nummerierten Kommentare und die Tabelle verwenden, die unter dem Code steht.

```csharp
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;
//FC-1 More namespaces.
using System.Text.RegularExpressions;
using System.Data.SqlClient;
using System.Configuration;

namespace SimpleDataApp
{
    public partial class FillOrCancel : Form
    {
        //FC-2 Storage for OrderID.
        private int parsedOrderID;

        //FC-3 Specify a connection string.
        string connstr = SimpleDataApp.Utility.GetConnectionString();

        public FillOrCancel()
        {
            InitializeComponent();
        }

        //FC-4 Find an order.
        private void btnFindByOrderID_Click(object sender, EventArgs e)
        {
            //FC-5 Prepare the connection and the command.
            if (isOrderID())
            {
                //Create the connection.
                SqlConnection conn = new SqlConnection(connstr);

                //Define a query string that has a parameter for orderID.
                string sql = "select * from Sales.Orders where orderID = @orderID";

                //Create a SqlCommand object.
                SqlCommand cmdOrderID = new SqlCommand(sql, conn);

                //Define the @orderID parameter and its value.
                cmdOrderID.Parameters.Add(new SqlParameter("@orderID", SqlDbType.Int));
                cmdOrderID.Parameters["@orderID"].Value = parsedOrderID;

                //try-catch-finally
                try
                {
                    //FC-6 Run the command and display the results.
                    //Open the connection.
                    conn.Open();

                    //Run the command by using SqlDataReader.
                    SqlDataReader rdr = cmdOrderID.ExecuteReader();

                    //Create a data table to hold the retrieved data.
                    DataTable dataTable = new DataTable();

                    //Load the data from SqlDataReader into the data table.
                    dataTable.Load(rdr);

                    //Display the data from the data table in the data grid view.
                    this.dgvCustomerOrders.DataSource = dataTable;

                    //Close the SqlDataReader.
                    rdr.Close();
                }
                catch
                {
                    //A simple catch.
                    MessageBox.Show("The requested order could not be loaded into the form.");
                }
                finally
                {
                    //Close the connection.
                    conn.Close();
                }
            }
        }

        //FC-7 Cancel an order.
        private void btnCancelOrder_Click(object sender, EventArgs e)
        {
            //Set up and run stored procedure only if OrderID is ready.
            if (isOrderID())
            {
                //Create the connection.
                SqlConnection conn = new SqlConnection(connstr);

                // Create command and identify it as a stored procedure.
                SqlCommand cmdCancelOrder = new SqlCommand("Sales.uspCancelOrder", conn);
                cmdCancelOrder.CommandType = CommandType.StoredProcedure;

                cmdCancelOrder.Parameters.Add(new SqlParameter("@orderID", SqlDbType.Int));
                cmdCancelOrder.Parameters["@orderID"].Value = parsedOrderID;

                // try-catch-finally
                try
                {
                    // Open the connection.
                    conn.Open();

                    // Run the cmdCancelOrder command.
                    cmdCancelOrder.ExecuteNonQuery();
                }
                // A simple catch.
                catch
                {
                    MessageBox.Show("The cancel operation was not completed.");
                }
                finally
                {
                    //Close connection.
                    conn.Close();
                }
            }
        }

        //FC-8 Fill an order.
        private void btnFillOrder_Click(object sender, EventArgs e)
        {
            //Set up and run stored procedure only if OrderID is ready.
            if (isOrderID())
            {
                //Create the connection.
                SqlConnection conn = new SqlConnection(connstr);

                //Create command and identify it as a stored procedure.
                SqlCommand cmdFillOrder = new SqlCommand("Sales.uspFillOrder", conn);
                cmdFillOrder.CommandType = CommandType.StoredProcedure;

                // Add input parameter from the stored procedure.
                cmdFillOrder.Parameters.Add(new SqlParameter("@orderID", SqlDbType.Int));
                cmdFillOrder.Parameters["@orderID"].Value = parsedOrderID;

                //Add the second input parameter.
                cmdFillOrder.Parameters.Add(new SqlParameter("@FilledDate", SqlDbType.DateTime, 8));
                cmdFillOrder.Parameters["@FilledDate"].Value = dtpFillDate.Value;

                //try-catch-finally
                try
                {
                    //Open the connection.
                    conn.Open();

                    //Run the cmdFillOrder command.
                    cmdFillOrder.ExecuteNonQuery();
                }
                catch
                {
                    //A simple catch.
                    MessageBox.Show("The fill operation was not completed.");
                }
                finally
                {
                    //Close the connection.
                    conn.Close();
                }
            }
        }

        //FC-9 Verify that OrderID is ready.
        private bool isOrderID()
        {

            //Check for input in the Order ID text box.
            if (txtOrderID.Text == "")
            {
                MessageBox.Show("Please specify the Order ID.");
                return false;
            }

            // Check for characters other than integers.
            else if (Regex.IsMatch(txtOrderID.Text, @"^\D*$"))
            {
               //Show message and clear input.
                MessageBox.Show("Please specify integers only.");
                txtOrderID.Clear();
                return false;
            }
            else
            {
                //Convert the text in the text box to an integer to send to the database.
                parsedOrderID = Int32.Parse(txtOrderID.Text);
                return true;
            }
        }

        //Close the form.
        private void btnFinishUpdates_Click(object sender, EventArgs e)
        {
            this.Close();
        }
    }
}
```

```vb
Imports System
Imports System.Collections.Generic
Imports System.ComponentModel
Imports System.Data
Imports System.Drawing
Imports System.Linq
Imports System.Text
Imports System.Threading.Tasks
Imports System.Windows.Forms
' FC-1 More namespaces.
Imports System.Text.RegularExpressions
Imports System.Data.SqlClient
Imports System.Configuration

Namespace SimpleDataApp
    Partial Public Class FillOrCancel
        Inherits Form
        ' FC-2 Storage for OrderID.
        Private parsedOrderID As Integer

        ' FC-3 Specify a connection string.
        Private connstr As String = SimpleDataApp.Utility.GetConnectionString()

        Public Sub New()
            InitializeComponent()
        End Sub

        ' FC-4 Find an order.
        Private Sub btnFindByOrderID_Click() Handles btnFindByOrderID.Click

            ' FC-5 Prepare the connection and the command.

            If isOrderID() Then
                ' Create the connection.
                Dim conn As New SqlConnection(connstr)

                ' Define the query string that has a parameter for orderID.
                Dim sql As String = "select * from Sales.Orders where orderID = @orderID"

                ' Create a SqlCommand object.
                Dim cmdOrderID As New SqlCommand(sql, conn)

                ' Define the @orderID parameter and its value.
                cmdOrderID.Parameters.Add(New SqlParameter("@orderID", SqlDbType.Int))
                cmdOrderID.Parameters("@orderID").Value = parsedOrderID

                ' try-catch-finally
                Try
                    ' FC-6 Run the command and display the results.
                    ' Open connection.
                    conn.Open()

                    ' Run the command by using SqlDataReader.
                    Dim rdr As SqlDataReader = cmdOrderID.ExecuteReader()

                    ' Create a data table to hold the retrieved data.
                    Dim dataTable As New DataTable()

                    ' Load the data from SqlDataReader into the data table.
                    dataTable.Load(rdr)

                    ' Display the data from the data table in the data grid view.
                    Me.dgvCustomerOrders.DataSource = dataTable

                    ' Close the SqlDataReader.
                    rdr.Close()
                Catch
                    ' A simple catch.
                    MessageBox.Show("The requested order could not be loaded into the form.")
                Finally
                    ' Close the connection.
                    conn.Close()
                End Try
            End If
        End Sub

        ' FC-7 Cancel an order.
        Private Sub btnCancelOrder_Click() Handles btnCancelOrder.Click

            ' Set up and run stored procedure only if OrderID is ready.
            If isOrderID() Then

                ' Create the connection.
                Dim conn As New SqlConnection(connstr)

                ' Create the command and identify it as a stored procedure.
                Dim cmdCancelOrder As New SqlCommand("Sales.uspCancelOrder", conn)
                cmdCancelOrder.CommandType = CommandType.StoredProcedure

                ' Add input parameter from the stored procedure.
                cmdCancelOrder.Parameters.Add(New SqlParameter("@orderID", SqlDbType.Int))
                cmdCancelOrder.Parameters("@orderID").Value = parsedOrderID

                ' try-catch-finally
                Try
                    ' Open the connection.
                    conn.Open()

                    ' Run the cmdCancelOrder command.
                    cmdCancelOrder.ExecuteNonQuery()
                Catch
                    ' A simple catch.
                    MessageBox.Show("The cancel operation was not completed.")
                Finally
                    ' Close connection.
                    conn.Close()
                End Try
            End If
        End Sub

        ' FC-8 Fill an order.
        Private Sub btnFillOrder_Click() Handles btnFillOrder.Click

            ' Set up and run stored procedure only if OrderID is ready.
            If isOrderID() Then

                ' Create the connection.
                Dim conn As New SqlConnection(connstr)

                ' Create command and identify it as a stored procedure.
                Dim cmdFillOrder As New SqlCommand("Sales.uspFillOrder", conn)
                cmdFillOrder.CommandType = CommandType.StoredProcedure

                ' Add input parameter from the stored procedure.
                cmdFillOrder.Parameters.Add(New SqlParameter("@orderID", SqlDbType.Int))
                cmdFillOrder.Parameters("@orderID").Value = parsedOrderID

                ' Add second input parameter.
                cmdFillOrder.Parameters.Add(New SqlParameter("@FilledDate", SqlDbType.DateTime, 8))
                cmdFillOrder.Parameters("@FilledDate").Value = dtpFillDate.Value

                ' try-catch-finally
                Try
                    ' Open the connection.
                    conn.Open()

                    ' Run the cmdFillOrder command.
                    cmdFillOrder.ExecuteNonQuery()
                Catch
                    ' A simple catch.
                    MessageBox.Show("The fill operation was not completed.")
                Finally
                    ' Close the connection.
                    conn.Close()
                End Try
            End If
        End Sub

        ' FC-9 Verify that OrderID is ready.
        Private Function isOrderID() As Boolean

            ' Check for input in the Order ID text box.
            If txtOrderID.Text = "" Then
                MessageBox.Show("Please specify the Order ID.")
                Return False

                ' Check for characters other than integers.
            ElseIf Regex.IsMatch(txtOrderID.Text, "^\D*$") Then

                ' Show message and clear input.
                MessageBox.Show("Please specify integers only.")
                txtOrderID.Clear()
                Return False

            Else
                ' Convert the text in the text box to an integer to send to the database.
                parsedOrderID = Int32.Parse(txtOrderID.Text)
                Return True

            End If
        End Function

        ' Close the form.
        Private Sub btnFinishUpdates_Click() Handles btnFinishUpdates.Click
            Me.Close()
        End Sub
    End Class
End Namespace
```

|Kommentar|Beschreibung|
|-------------|-----------------|
|FC-1|Fügen Sie der Liste der Namespaces `System.Data.SqlClient`, `System.Configuration` und `System.Text.RegularExpressions` hinzu.|
|FC-2|Deklarieren Sie die Variable `parsedOrderID`.|
|FC-3|Rufen Sie die `GetConnectionString`-Methode auf, um die Verbindungszeichenfolge aus der Datei "App.config" abzurufen, und speichern Sie den Wert in der Zeichenfolgenvariablen `connstr`.|
|FC-4|Fügen Sie dem Click-Ereignishandler den Code für `btnFindOrderByID` hinzu.|
|FC-5|Diese Aufgaben sind erforderlich, bevor Sie versuchen, eine SQL-Anweisung oder eine gespeicherte Prozedur auszuführen.<br /><br /> -Erstellen Sie ein `SqlConnection`-Objekt.<br />-Definieren Sie die SQL-Anweisung, oder geben Sie den Namen der gespeicherten Prozedur an. (In diesem Fall führen Sie eine `SELECT`-Anweisung aus.)<br />-Erstellen Sie ein `SqlCommand`-Objekt.<br />-Definieren Sie alle Parameter für die SQL-Anweisung oder die gespeicherte Prozedur.|
|FC-6|Dieser Code verwendet `SqlDataReader` und `DataTable`, um das Abfrageergebnis abzurufen und anzuzeigen.<br /><br /> -Öffnen Sie die Verbindung.<br />-Erstellen Sie ein `SqlDataReader` Objekt `rdr`, indem Sie die `ExecuteReader`-Methode für `cmdOrderID` ausführen.<br />-Erstellen Sie ein `DataTable` Objekt, das die abgerufenen Daten enthält.<br />Laden Sie die Daten aus dem `SqlDataReader`-Objekt in das `DataTable`-Objekt.<br />-Zeigen Sie die Daten in der Datenraster Ansicht an, indem Sie `DataTable` als `DataSource` für die Datenraster Ansicht angeben.<br />-Schließen Sie `SqlDataReader`.|
|FC-7|Fügen Sie dem Click-Ereignishandler den Code für `btnCancelOrder` hinzu. Dieser Code führt die gespeicherte Prozedur `Sales.uspCancelOrder` aus.|
|FC-8|Fügen Sie dem Click-Ereignishandler den Code für `btnFillOrder` hinzu. Dieser Code führt die gespeicherte Prozedur `Sales.uspFillOrder` aus.|
|FC-9|Erstellen Sie eine-Methode, um zu überprüfen, ob `OrderID` bereit ist, als Parameter an das `SqlCommand`-Objekt zu senden.<br /><br /> -Stellen Sie sicher, dass eine ID in `txtOrderID` eingegeben wurde.<br />-Verwenden Sie `Regex.IsMatch`, um eine einfache Überprüfung auf nicht ganzzahlige Zeichen zu definieren.<br />-Sie haben die `parsedOrderID`-Variable bei FC-2 deklariert.<br />-Wenn die Eingabe gültig ist, konvertieren Sie den Text in eine ganze Zahl, und speichern Sie den Wert in der `parsedOrderID`-Variablen.<br />-Umschließen Sie die `isOrderID`-Methode um die `btnFindByOrderID`, `btnCancelOrder` und `btnFillOrder` Click-Ereignishandler.|

## <a name="BKMK_testyourapplication"></a>Testen der Anwendung
 Drücken Sie die Taste F5, um die Anwendung zu erstellen und zu testen, nachdem Sie jeden Click-Ereignishandler codiert haben, und nachdem Sie die Codierung abgeschlossen haben.
