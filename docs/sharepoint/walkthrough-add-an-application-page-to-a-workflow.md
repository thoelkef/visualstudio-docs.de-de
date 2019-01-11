---
title: 'Exemplarische Vorgehensweise: Hinzufügen eine Anwendungsseite zu einem Workflow | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, adding applications page to workflow
- application page [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: cb0dfa7212cae1dd4e7c62f71f423c0f8fd275d9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53938198"
---
# <a name="walkthrough-add-an-application-page-to-a-workflow"></a>Exemplarische Vorgehensweise: Hinzufügen einer Anwendungsseite zu einem workflow
  Diese exemplarische Vorgehensweise veranschaulicht, wie Sie eine Anwendungsseite hinzufügen, die zu einem Workflowprojekt von einem Workflow abgeleitete Daten angezeigt werden. Er baut auf das Projekt, das in diesem Thema beschriebenen [Exemplarische Vorgehensweise: Erstellen eines Workflows mit Zuordnungs-und Initiierungsformularen](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).

 Diese exemplarische Vorgehensweise enthält die folgenden Aufgaben:

- Hinzufügen einer ASPX-Anwendungsseite zu einem SharePoint-Workflowprojekt.

- Abrufen von Daten aus dem Workflowprojekt, und bearbeiten es.

- Anzeigen von Daten in eine Tabelle auf der Seite "Anwendung" aus.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Vorraussetzungen
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:

-   Unterstützte Editionen von [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] und SharePoint.

-   Visual Studio.

-   Müssen Sie auch das Projekt in das Thema abschließen [Exemplarische Vorgehensweise: Erstellen eines Workflows mit Zuordnungs-und Initiierungsformularen](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).

## <a name="ammend-the-workflow-code"></a>Ammend Workflowcode
 Fügen Sie zunächst eine einzige Zeile Code an den Workflow, den Wert der Ergebnisspalte angezeigt, der den Betrag der Spesenabrechnung festzulegen. Dieser Wert wird weiter unten in der Expense Report Zusammenfassung Berechnung verwendet.

#### <a name="to-set-the-value-of-the-outcome-column-in-the-workflow"></a>Den Wert der Ergebnisspalte angezeigt im Workflow festgelegt

1.  Laden Sie das abgeschlossene Projekt aus dem Thema [Exemplarische Vorgehensweise: Erstellen eines Workflows mit Zuordnungs- und Initiierungsformularen](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md) in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2.  Öffnen Sie den Code für *Workflow1.cs* oder *Workflow1.vb* (abhängig von der Programmiersprache).

3.  Am unteren Rand der `createTask1_MethodInvoking` -Methode, fügen Sie den folgenden Code hinzu:

    ```vb
    createTask1_TaskProperties1.ExtendedProperties("Outcome") =
      workflowProperties.InitiationData
    ```

    ```csharp
    createTask1_TaskProperties1.ExtendedProperties["Outcome"] =
      workflowProperties.InitiationData;
    ```

## <a name="create-an-application-page"></a>Erstellen einer Anwendungsseite
 Fügen Sie anschließend eine ASPX-Webformular, für das Projekt. Dieses Formular wird aus das Expense Report-Workflowprojekt abgerufene Daten angezeigt. Zu diesem Zweck fügen Sie eine Anwendungsseite. Eine Anwendungsseite verwendet dieselbe Masterseite als andere SharePoint-Seiten, was bedeutet, dass es anderen Seiten auf der SharePoint-Website ähnelt.

#### <a name="to-add-an-application-page-to-the-project"></a>Hinzufügen eine Anwendungsseite zum Projekt

1.  Wählen Sie das Projekt "ExpenseReport" und dann auf der Menüleiste die Option **Projekt** > **neues Element hinzufügen**.

2.  In der **Vorlagen** Bereich Wählen Sie die **Seite "Anwendung"** Vorlage verwenden Sie den Standardnamen für das Projektelement (**ApplicationPage1.aspx**), und wählen Sie die **Hinzufügen** Schaltfläche.

3.  In der [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] von ApplicationPage1.aspx, ersetzen die `PlaceHolderMain` -Abschnitt folgendermaßen:

    ```aspx-csharp
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">
        <asp:Label ID="Label1" runat="server" Font-Bold="True"
            Text="Expenses that exceeded allotted amount" Font-Size="Medium"></asp:Label>
        <br />
        <asp:Table ID="Table1" runat="server">
        </asp:Table>
    </asp:Content>
    ```

     Dieser Code Fügt eine Tabelle auf der Seite zusammen mit einem Titel.

4.  Fügen Sie einen Titel auf der Seite "Anwendung" hinzu, indem Sie ersetzt die `PlaceHolderPageTitleInTitleArea` -Abschnitt folgendermaßen:

    ```aspx-csharp
    <asp:Content ID="PageTitleInTitleArea" ContentPlaceHolderID="PlaceHolderPageTitleInTitleArea" runat="server" >
        Expense Report Summary
    </asp:Content>
    ```

## <a name="code-the-application-page"></a>Code der Seite "Anwendung"
 Als Nächstes fügen Sie Code hinzu, um die Zusammenfassung der Anwendung für die Spesenabrechnungsseite. Wenn Sie die Seite zu öffnen, durchsucht der Code die Aufgabenliste in SharePoint für Ausgaben, die das zugeordnete Ausgabenlimit überschritten haben. Der Bericht listet jedes Element zusammen mit der Summe der Ausgaben.

#### <a name="to-code-the-application-page"></a>Code der Seite "Anwendung"

1.  Wählen Sie die **ApplicationPage1.aspx** Knoten und anschließend auf der Menüleiste die Optionen **Ansicht** > **Code** um den Code hinter der Seite "Anwendung" anzuzeigen.

2.  Ersetzen Sie die **mit** oder **Import** Anweisungen (abhängig von der Programmiersprache) am Anfang der Klasse durch den folgenden:

    ```vb
    Imports System
    Imports Microsoft.SharePoint
    Imports Microsoft.SharePoint.WebControls
    Imports System.Collections
    Imports System.Data
    Imports System.Web.UI
    Imports System.Web.UI.WebControls
    Imports System.Web.UI.WebControls.WebParts
    Imports System.Drawing
    Imports Microsoft.SharePoint.Navigation
    ```

    ```csharp
    using System;
    using Microsoft.SharePoint;
    using Microsoft.SharePoint.WebControls;
    using System.Collections;
    using System.Data;
    using System.Web.UI;
    using System.Web.UI.WebControls;
    using System.Web.UI.WebControls.WebParts;
    using System.Drawing;
    using Microsoft.SharePoint.Navigation;
    ```

3.  Fügen Sie der `Page_Load`-Methode folgenden Code hinzu:

    ```vb
    Try
        ' Reference the Tasks list on the SharePoint site.
        ' Replace "TestServer" with a valid SharePoint server name.
        Dim site As SPSite = New SPSite("http://TestServer")
        Dim list As SPList = site.AllWebs(0).Lists("Tasks")
        ' string text = "";
        Dim sum As Integer = 0
        Table1.Rows.Clear()
        ' Add table headers.
        Dim hr As TableHeaderRow = New TableHeaderRow
        hr.BackColor = Color.LightBlue
        Dim hc1 As TableHeaderCell = New TableHeaderCell
        Dim hc2 As TableHeaderCell = New TableHeaderCell
        hc1.Text = "Expense Report Name"
        hc2.Text = "Amount Exceeded"
        hr.Cells.Add(hc1)
        hr.Cells.Add(hc2)
        ' Add the TableHeaderRow as the first item
        ' in the Rows collection of the table.
        Table1.Rows.AddAt(0, hr)
        ' Iterate through the tasks in the Task list and collect those
        ' that have values in the "Related Content" and "Outcome" fields
        ' - the fields written to when expense approval is required.
        For Each item As SPListItem In list.Items
            Dim s_relContent As String = ""
            Dim s_outcome As String = ""
            Try
                ' Task has the fields - treat as expense report.
                s_relContent = item.GetFormattedValue("Related Content")
                s_outcome = item.GetFormattedValue("Outcome")
            Catch erx As System.Exception
                ' Task does not have fields - skip it.
                Continue For
            End Try
            ' Convert amount to an int and keep a running total.
            If (Not String.IsNullOrEmpty(s_relContent) And Not
              String.IsNullOrEmpty(s_outcome)) Then
                sum = (sum + Convert.ToInt32(s_outcome))
                Dim relContent As TableCell = New TableCell
                relContent.Text = s_relContent
                Dim outcome As TableCell = New TableCell
                outcome.Text = ("$" + s_outcome)
                Dim dataRow2 As TableRow = New TableRow
                dataRow2.Cells.Add(relContent)
                dataRow2.Cells.Add(outcome)
                Table1.Rows.Add(dataRow2)
            End If
        Next
        ' Report the sum of the reports in the table footer.
        Dim tfr As TableFooterRow = New TableFooterRow
        tfr.BackColor = Color.LightGreen
        ' Create a TableCell object to contain the
        ' text for the footer.
        Dim ftc1 As TableCell = New TableCell
        Dim ftc2 As TableCell = New TableCell
        ftc1.Text = "TOTAL: "
        ftc2.Text = ("$" + Convert.ToString(sum))
        ' Add the TableCell object to the Cells
        ' collection of the TableFooterRow.
        tfr.Cells.Add(ftc1)
        tfr.Cells.Add(ftc2)
        ' Add the TableFooterRow to the Rows
        ' collection of the table.
        Table1.Rows.Add(tfr)
    Catch errx As Exception
        System.Diagnostics.Debug.WriteLine(("Error: " + errx.ToString))
    End Try
    ```

    ```csharp
    try
    {
        // Reference the Tasks list on the SharePoint site.
        // Replace "TestServer" with a valid SharePoint server name.
        SPSite site = new SPSite("http://TestServer");
        SPList list = site.AllWebs[0].Lists["Tasks"];

        // string text = "";
        int sum = 0;

        Table1.Rows.Clear();

        // Add table headers.
        TableHeaderRow hr = new TableHeaderRow();
        hr.BackColor = Color.LightBlue;
        TableHeaderCell hc1 = new TableHeaderCell();
        TableHeaderCell hc2 = new TableHeaderCell();
        hc1.Text = "Expense Report Name";
        hc2.Text = "Amount Exceeded";
        hr.Cells.Add(hc1);
        hr.Cells.Add(hc2);
        // Add the TableHeaderRow as the first item
        // in the Rows collection of the table.
        Table1.Rows.AddAt(0, hr);

        // Iterate through the tasks in the Task list and collect those
        // that have values in the "Related Content" and "Outcome"
        // fields - the fields written to when expense approval is
        // required.
        foreach (SPListItem item in list.Items)
        {
            string s_relContent = "";
            string s_outcome = "";

            try
            {
                // Task has the fields - treat as expense report.
                s_relContent = item.GetFormattedValue("Related
                  Content");
                s_outcome = item.GetFormattedValue("Outcome");
            }
            catch
            {
                // Task does not have fields - skip it.
                continue;
            }

            if (!String.IsNullOrEmpty(s_relContent) &&
              !String.IsNullOrEmpty(s_outcome))
            {
                // Convert amount to an int and keep a running total.
                sum += Convert.ToInt32(s_outcome);
                TableCell relContent = new TableCell();
                relContent.Text = s_relContent;
                TableCell outcome = new TableCell();
                outcome.Text = "$" + s_outcome;
                TableRow dataRow2 = new TableRow();
                dataRow2.Cells.Add(relContent);
                dataRow2.Cells.Add(outcome);
                Table1.Rows.Add(dataRow2);
            }
        }

        // Report the sum of the reports in the table footer.
           TableFooterRow tfr = new TableFooterRow();
        tfr.BackColor = Color.LightGreen;

        // Create a TableCell object to contain the
        // text for the footer.
        TableCell ftc1 = new TableCell();
        TableCell ftc2 = new TableCell();
        ftc1.Text = "TOTAL: ";
        ftc2.Text = "$" + Convert.ToString(sum);

        // Add the TableCell object to the Cells
        // collection of the TableFooterRow.
        tfr.Cells.Add(ftc1);
        tfr.Cells.Add(ftc2);

        // Add the TableFooterRow to the Rows
        // collection of the table.
        Table1.Rows.Add(tfr);
    }

    catch (Exception errx)
    {
        System.Diagnostics.Debug.WriteLine("Error: " + errx.ToString());
    }
    ```

    > [!WARNING]
    >  Achten Sie darauf, dass "TestServer" im Code mit dem Namen eines gültigen Servers ersetzen, auf dem SharePoint ausgeführt wird.

## <a name="test-the-application-page"></a>Testen Sie die Seite "Anwendung"
 Als Nächstes zu bestimmen, ob die Seite "Anwendung" der Ausgabedaten ordnungsgemäß angezeigt.

#### <a name="to-test-the-application-page"></a>So testen Sie die Anwendungsseite

1. Wählen Sie die **F5** Schlüssel ausführen und Bereitstellen des Projekts in SharePoint.

2. Wählen Sie die **Startseite** Schaltfläche, und wählen Sie dann die **freigegebene Dokumente** Link auf der Schnellstartleiste auf die Liste Freigegebene Dokumente auf SharePoint-Website angezeigt.

3. Hochladen von zur Darstellung von spesenabrechnungen für dieses Beispiel einige neue Dokumente in die Liste der Dokumente durch Auswählen der **Dokumente** auf einen link auf die **LibraryTools** Registerkarte am oberen Rand der Seite auswählen und dann die  **Dokument hochladen** Schaltfläche im Menüband des Tools.

4. Nachdem Sie einige Dokumente hochladen, instanziieren Sie den Workflow durch Auswahl der **Bibliothek** auf einen link auf die **LibraryTools** Registerkarte am oberen Rand der Seite auswählen und dann die **Bibliothekseinstellungen**Schaltfläche im Menüband des Tools.

5. In der **Dokumentbibliothekseinstellungen** Seite die **Workfloweinstellungen** -link in der **Berechtigungen und Verwaltung** Abschnitt.

6. In der **Workfloweinstellungen** Seite die **fügen Sie einen Workflow** Link.

7. In der **fügen Sie einen Workflow** Seite die **ExpenseReport - Workflow1** Workflow, geben Sie einen Namen für den Workflow, z. B. **ExpenseTest**, und wählen Sie dann die **Weiter** Schaltfläche.

    Die Workflowzuordnungsformular wird angezeigt. Verwenden sie zum Melden der Ausgaben an.

8. Geben Sie im Formular Zuordnung **1000** in die **automatisch Genehmigungsgrenzwert** ein, und wählen Sie dann die **Workflow zuordnen** Schaltfläche.

9. Wählen Sie die **Home** Schaltfläche, um auf die SharePoint-Startseite zurückzukehren.

10. Wählen Sie die **freigegebene Dokumente** Link auf der Schnellstartleiste.

11. Wählen Sie eine der hochgeladenen Dokumente, um eine Dropdown-Pfeil angezeigt, wählen Sie diese, und wählen Sie dann die **Workflows** Element.

12. Wählen Sie das Image neben ExpenseTest, um den Workflow Initiierungsformular anzuzeigen.

13. In der **Expense Total** im Textfeld Geben Sie einen Wert, der größer als 1000 ist, und wählen Sie dann die **Workflow starten** Schaltfläche.

     Wenn eine gemeldete Ausgabe der zugeordneten Gesamtausgaben überschreitet, wird eine Aufgabe zur Aufgabenliste hinzugefügt. Eine Spalte namens **ExpenseTest** mit dem Wert **abgeschlossen** wird auch das Kosten-Berichtselement in der Liste Freigegebene Dokumente hinzugefügt.

14. Wiederholen Sie die Schritte 11 bis 13 mit anderen Dokumenten in der Liste Freigegebene Dokumente. (Die genaue Anzahl von Dokumenten ist nicht wichtig.)

15. Die Spesenabrechnungsseite für die Zusammenfassung der Anwendung anzeigen, indem Sie die folgende URL in einem Webbrowser öffnen: **http://**<em>SystemName</em>**/_layouts/ExpenseReport/ApplicationPage1.aspx**.

     Die Spesenabrechnungsseite Zusammenfassung zeigt eine Liste aller für die spesenabrechnungen, die die zugewiesene Menge überschritten, die Menge, die, der Sie von überschritten, und den Gesamtbetrag für alle Berichte.

## <a name="next-steps"></a>Nächste Schritte
 Weitere Informationen zu SharePoint-Anwendungsseiten, finden Sie unter [Erstellen von Anwendungsseiten für SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

 Erfahren Sie mehr über das SharePoint-Seiteninhalten zu entwerfen, indem Sie mit dem Visual Web Designer in Visual Studio in den folgenden Themen:

-   [Erstellen von Webparts für SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).

-   [Erstellen von wiederverwendbaren Steuerelementen für Webparts oder Anwendungsseiten](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).

## <a name="see-also"></a>Siehe auch

- [Exemplarische Vorgehensweise: Erstellen eines Workflows mit Zuordnungs-und Initiierungsformularen](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)
- [Vorgehensweise: Erstellen einer Anwendungsseite](../sharepoint/how-to-create-an-application-page.md)
- [Erstellen von Anwendungsseiten für SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)
- [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)