---
title: "Exemplarische Vorgehensweise: Hinzuf&#252;gen einer Anwendungsseite zu einem Workflow | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Anwendungsseite [SharePoint-Entwicklung in Visual Studio]"
  - "SharePoint-Entwicklung in Visual Studio, Hinzufügen einer Anwendungsseite zu einem Workflow"
ms.assetid: e4845d07-917b-45cb-a569-4ecdd602fbd9
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# Exemplarische Vorgehensweise: Hinzuf&#252;gen einer Anwendungsseite zu einem Workflow
  In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie einem Workflowprojekt eine Anwendungsseite hinzugefügt wird, auf der von einem Workflow abgeleitete Daten angezeigt werden.  Grundlage ist das im Thema [Exemplarische Vorgehensweise: Erstellen eines Workflows mit Zuordnungs- und Initiierungsformularen](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md) beschriebene Projekt.  
  
 Diese exemplarische Vorgehensweise enthält die folgenden Aufgaben:  
  
-   Hinzufügen einer ASPX\-Anwendungsseite zu einem SharePoint\-Workflowprojekt.  
  
-   Abrufen von Daten aus dem Workflowprojekt und Bearbeiten dieser Daten.  
  
-   Anzeigen von Daten in einer Tabelle auf der Anwendungsseite.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   Unterstützte Editionen von [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] und SharePoint.  Weitere Informationen finden Sie unter [Anforderungen für die Entwicklung von SharePoint-Lösungen](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
-   Außerdem müssen Sie das Projekt im Thema [Exemplarische Vorgehensweise: Erstellen eines Workflows mit Zuordnungs- und Initiierungsformularen](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md) abgeschlossen haben.  
  
## Ergänzen des Workflowcodes  
 Fügen Sie dem Workflow zunächst eine Codezeile hinzu, um den Wert der Spalte Ergebnis auf den Betrag der Spesenabrechnung festzulegen.  Dieser Wert wird später in der Zusammenfassungsberechnung der Spesenabrechnung verwendet.  
  
#### So legen Sie den Wert der Spalte Ergebnis im Workflow fest  
  
1.  Laden Sie das abgeschlossene Projekt aus dem Thema [Exemplarische Vorgehensweise: Erstellen eines Workflows mit Zuordnungs- und Initiierungsformularen](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md) in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Öffnen Sie den Code für Workflow1.cs oder Workflow1.vb \(abhängig von der Programmiersprache\).  
  
3.  Fügen Sie am unteren Rand der `createTask1_MethodInvoking`\-Methode den folgenden Code hinzu:  
  
    ```vb  
    createTask1_TaskProperties1.ExtendedProperties("Outcome") =   
      workflowProperties.InitiationData  
    ```  
  
    ```csharp  
    createTask1_TaskProperties1.ExtendedProperties["Outcome"] =   
      workflowProperties.InitiationData;  
    ```  
  
## Erstellen einer Anwendungsseite  
 Fügen Sie dem Projekt jetzt ein ASPX\-Formular hinzu.  In diesem Formular werden Daten angezeigt, die aus dem Workflowprojekt der Spesenabrechnung abgerufen werden.  Hierzu fügen Sie eine Anwendungsseite hinzu.  Eine Anwendungsseite verwendet dieselbe Gestaltungsvorlage wie andere SharePoint\-Seiten. Dies bedeutet, dass sie anderen Seiten auf der SharePoint\-Website ähnelt.  
  
#### So fügen Sie dem Projekt eine Anwendungsseite hinzu  
  
1.  Wählen Sie das Projekt ExpenseReport, und dann, auf der Menüleiste aus, wählen Sie **Neues Element hinzufügen**, **Projekt** aus.  
  
2.  Im Bereich **Vorlagen** wählen Sie die Vorlage **Anwendungsseite**, verwenden die Standardnamen für das Projektelement \(**ApplicaitonPage1.aspx**\) und die Schaltfläche **Hinzufügen** aus.  
  
3.  Ersetzen Sie im [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]\-Code von "ApplicationPage1.aspx" den Abschnitt `PlaceHolderMain` durch Folgendes:  
  
    ```  
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">  
        <asp:Label ID="Label1" runat="server" Font-Bold="True"   
            Text="Expenses that exceeded allotted amount" Font-Size="Medium"></asp:Label>  
        <br />  
        <asp:Table ID="Table1" runat="server">  
        </asp:Table>  
    </asp:Content>  
    ```  
  
     Durch diesen Code wird der Seite eine Tabelle zusammen mit einem Titel hinzugefügt.  
  
4.  Fügen Sie der Anwendungsseite einen Titel hinzu, indem Sie den Abschnitt `PlaceHolderPageTitleInTitleArea` durch Folgendes ersetzen:  
  
    ```  
    <asp:Content ID="PageTitleInTitleArea" ContentPlaceHolderID="PlaceHolderPageTitleInTitleArea" runat="server" >  
        Expense Report Summary  
    </asp:Content>  
    ```  
  
## Hinzufügen von Code zur Anwendungsseite  
 Fügen Sie der Anwendungsseite mit der Spesenabrechnungszusammenfassung dann Code hinzu.  Wenn Sie die Seite öffnen, wird im Code die Aufgabenliste in SharePoint nach Ausgaben gesucht, die die zugeordnete Ausgabengrenze überschritten haben.  Im Bericht wird jedes Element zusammen mit der Summe der Ausgaben aufgeführt.  
  
#### So fügen Sie Code zur Anwendungsseite hinzu  
  
1.  Wählen Sie den Knoten **ApplicationPage1.aspx**, und dann, auf der Menüleiste aus, wählen Sie **Code**, **Ansicht**, um den Code hinter der Anwendungsseite anzuzeigen.  
  
2.  Ersetzen Sie die **using**\-Anweisung oder die **Import**\-Anweisung \(abhängig von der Programmiersprache\) am oberen Rand der Klasse durch Folgendes:  
  
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
  
3.  Fügen Sie der `Page_Load`\-Methode folgenden Code hinzu:  
  
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
    >  Stellen Sie sicher, "TestServer" im Code durch den Namen eines gültigen Servers zu ersetzen, auf dem SharePoint ausgeführt wird.  
  
## Testen der Anwendungsseite  
 Bestimmen Sie danach, ob auf der Anwendungsseite die Ausgabedaten ordnungsgemäß angezeigt werden.  
  
#### So testen Sie die Anwendungsseite  
  
1.  Drücken Sie die F5\-TASTE, um das Projekt in SharePoint auszuführen und bereitzustellen.  
  
2.  Wählen Sie die Schaltfläche **Startseite** aus, und wählen Sie anschließend den Link **Freigegebene Dokumente** auf der Schnellstartleiste, um die Liste Freigegebene Dokumente auf der SharePoint\-Website anzuzeigen.  
  
3.  Um für dieses Beispiel zum Darstellen von Spesenabrechnungen, laden Sie einige neue Dokumente in die Liste "Dokumente" hoch indem Sie den Link **Dokumente** auf der Registerkarte **LibraryTools** am Anfang der Seite auswählen und dann die Schaltfläche **Dokument hochladen** im Toolmenüband auswählen.  
  
4.  Nachdem Sie einige Dokumente hochgeladen haben, instanziieren Sie den Workflow, indem Sie den Link **Bibliothek** auf der Registerkarte **LibraryTools** am Anfang der Seite auswählen und dann die Schaltfläche **Bibliothekeinstellungen** im Toolmenüband auswählen.  
  
5.  Auf der Seite **Einstellungen Dokumentbibliothek** Wählen Sie den Link **Workfloweinstellungen** im Abschnitt **Berechtigungen und Verwaltung** aus.  
  
6.  Auf der Seite **Workfloweinstellungen** Wählen Sie den Link **Workflow hinzufügen** aus.  
  
7.  Auf der Seite **Workflow hinzufügen** wählen Sie den Workflow **ExpenseReport \- Workflow1** aus, geben Sie einen Namen für den Workflow, z "ExpenseTest" ein, und wählen Sie dann die Schaltfläche **Weiter** aus.  
  
     Das Workflowzuordnungsformular wird angezeigt.  Geben Sie hier den Höchstbetrag für Ausgaben an.  
  
8.  In Geben Sie im Zuordnungsformular **1000** in das Feld **Automatische Genehmigungsgrenze** ein, und wählen Sie dann die Schaltfläche **Workflow zuordnen** aus.  
  
9. Wählen Sie die Schaltfläche **Startseite**, um zur SharePoint\-Homepage zurückzukehren.  
  
10. Wählen Sie den Link **Freigegebene Dokumente** auf der Schnellstartleiste aus.  
  
11. Wählen Sie eines der hochgeladenen Dokumente, um einen Dropdownpfeil anzuzeigen, wählen Sie es aus und wählen Sie das Element **Workflows** aus.  
  
12. Wählen Sie das Bild neben ExpenseTest, um das Workflowinitiierungsformular anzuzeigen.  
  
13. Im Textfeld **Gesamtausgaben** geben Sie einen Wert, der größer als 1000 ist, und wählen Sie dann die Schaltfläche **Workflow starten** aus.  
  
     Wenn eine gemeldete Ausgabe den zugeordneten Höchstbetrag überschreitet, wird der Aufgabenliste eine Aufgabe hinzugefügt.  Außerdem wird dem Spesenabrechnungselement in der Liste Freigegebene Dokumente eine Spalte namens **ExpenseTest** mit dem Wert **Abgeschlossen** hinzugefügt.  
  
14. Wiederholen Sie die Schritte 11 \- 13 mit den anderen Dokumenten in der Liste Freigegebene Dokumente. \(Die genaue Anzahl von Dokumenten ist nicht wichtig.\)  
  
15. Zeigen Sie die Anwendungsseite mit der Spesenabrechnungszusammenfassung an, indem Sie die folgende URL in einem Webbrowser öffnen: **http:\/\/***SystemName***\/\_layouts\/ExpenseReport\/ApplicationPage1.aspx**.  
  
     Auf der Seite mit der Spesenabrechnungszusammenfassung sind alle Spesenabrechnungen aufgeführt, die den zugeordneten Betrag überschritten haben. Außerdem wird aufgeführt, um welchen Betrag der Höchstbetrag überschritten wurde, und der Gesamtbetrag aller Abrechnungen wird angezeigt.  
  
## Nächste Schritte  
 Weitere Informationen über SharePoint\-Anwendungsseiten finden Sie unter [Erstellen von Anwendungsseiten für SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
 Weitere Informationen zum Entwerfen von SharePoint\-Seiteninhalten mit dem Visual Web Designer in Visual Studio finden Sie in folgenden Themen:  
  
-   [Erstellen von Webparts für SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).  
  
-   [Erstellen von wiederverwendbaren Steuerelementen für Webparts oder Anwendungsseiten](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).  
  
## Siehe auch  
 [Exemplarische Vorgehensweise: Erstellen eines Workflows mit Zuordnungs- und Initiierungsformularen](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)   
 [Gewusst wie: Erstellen einer Anwendungsseite](../sharepoint/how-to-create-an-application-page.md)   
 [Erstellen von Anwendungsseiten für SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  