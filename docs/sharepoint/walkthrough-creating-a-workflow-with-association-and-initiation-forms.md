---
title: "Exemplarische Vorgehensweise: Erstellen eines Workflows mit Zuordnungs- und Initiierungsformularen"
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
  - "Zuordnungsformulare [SharePoint-Entwicklung in Visual Studio]"
  - "Initiierungsformulare [SharePoint-Entwicklung in Visual Studio]"
  - "SharePoint-Entwicklung in Visual Studio, Workflowzuordnungsformulare"
  - "SharePoint-Entwicklung in Visual Studio, Workflowinitiierungsformulare"
  - "SharePoint-Entwicklung in Visual Studio, Workflows"
  - "Workflows [SharePoint-Entwicklung in Visual Studio]"
ms.assetid: c8666d8c-b173-4245-8014-9c1cd6acb071
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# Exemplarische Vorgehensweise: Erstellen eines Workflows mit Zuordnungs- und Initiierungsformularen
  In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie ein grundlegender sequenzieller Workflow erstellt wird, der die Verwendung von Zuordnungs\- und Initiierungsformularen integriert.  Dabei handelt es sich um ASPX\-Formulare, die das Hinzufügen von Parametern zu einem Workflow ermöglichen, wenn dieser erstmals vom SharePoint\-Administrator zugeordnet wird \(das Zuordnungsformular\) und wenn der Workflow vom Benutzer gestartet wird \(das Initiierungsformular\).  
  
 In dieser exemplarischen Vorgehensweise wird ein Szenario beschrieben, in dem ein Benutzer einen Genehmigungsworkflow für Spesenabrechnungen mit den folgenden Anforderungen erstellen möchte:  
  
-   Wenn der Workflow einer Liste zugeordnet wird, wird der Administrator über ein Zuordnungsformular aufgefordert, einen Höchstbetrag in Dollar für Spesenabrechnungen einzugeben.  
  
-   Die Mitarbeiter laden ihre Spesenabrechnungen in der Liste Freigegebene Dokumente hoch, starten den Workflow und geben dann den Gesamtbetrag im Workflowinitiierungsformular ein.  
  
-   Wenn der Gesamtbetrag der Spesenabrechnung eines Mitarbeiters die vordefinierte Höchstgrenze des Administrators überschreitet, wird eine Aufgabe erstellt, damit der Vorgesetzte des Mitarbeiters die Spesenabrechnung genehmigen kann.  Falls der Gesamtbetrag der Spesenabrechnung eines Mitarbeiters jedoch kleiner oder gleich der Höchstgrenze für Spesen ist, wird eine automatisch genehmigte Meldung in die Verlaufsliste des Workflows geschrieben.  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Erstellen eines sequenziellen Workflowprojekts vom Typ SharePoint\-Listendefinition in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
-   Erstellen eines Workflowzeitplans.  
  
-   Behandeln von Workflowaktivitätsereignissen.  
  
-   Erstellen von Zuordnungs\- und Initiierungsformularen für Workflows.  
  
-   Zuordnen des Workflows.  
  
-   Manuelles Starten des Workflows.  
  
> [!NOTE]  
>  Obwohl in dieser exemplarischen Vorgehensweise ein sequenzielles Workflowprojekt verwendet wird, ist der Vorgang für Zustandsautomatworkflows identisch.  
>   
>  Außerdem werden auf Ihrem Computer möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] angezeigt als die in den folgenden Anweisungen aufgeführten.  Die Elemente werden durch die verwendete Ausgabe von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] und die gewählten Einstellungen bestimmt.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   Unterstützte Editionen von [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] und SharePoint.  Weitere Informationen finden Sie unter [Anforderungen für die Entwicklung von SharePoint-Lösungen](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
## Erstellen eines sequenziellen Workflowprojekts für SharePoint.  
 Erstellen Sie zunächst in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ein sequenzielles Workflowprojekt.  Ein sequenzieller Workflow ist ein Abfolge von Schritten, die der Reihe nach ausgeführt werden, bis die letzte Aktivität fertig gestellt wurde.  In diesem Verfahren erstellen Sie einen sequenziellen Workflow, der für die Liste Freigegebene Dokumente in SharePoint gilt.  Mit dem Workflow\-Assistenten können Sie den Workflow entweder der Websitedefinition oder der Listendefinition zuordnen und bestimmen, wann der Workflow starten soll.  
  
#### So erstellen Sie ein sequenzielles Workflowprojekt für SharePoint:  
  
1.  Klicken Sie auf der Menüleiste **Neu**, **Projekt**, **Datei**, um das Dialogfeld **Neues Projekt** anzuzeigen.  
  
2.  Erweitern Sie den Knoten **SharePoint** entweder unter **Visual C\#** oder **Visual Basic**, und wählen Sie den Knoten **2010** aus.  
  
3.  Im Bereich **Vorlagen** wählen Sie die Projektvorlage **SharePoint 2010\-Projekt** aus.  
  
4.  Im Feld **Name** geben Sie ExpenseReport ein und wählen Sie dann die Schaltfläche **OK** aus.  
  
     Der **Assistent zum Anpassen von SharePoint** wird angezeigt.  
  
5.  Auf der Seite **Site und Sicherheitsebene für Debugging angeben** wählen Sie das Optionsfeld **Als Farmlösung bereitstellen** aus, und wählen Sie die Schaltfläche **Fertig stellen**, um die Vertrauensebenen\- und Standardsite zu übernehmen.  
  
     In diesem Schritt wird auch die Vertrauensebene für die Lösung als Farmlösung festgelegt, wobei es sich um die einzige verfügbare Option für Workflowprojekte handelt.  
  
6.  Wählen Sie im **Projektmappen\-Explorer** den Projektknoten aus.  
  
7.  Wählen Sie in der Menüleiste **Projekt**,  **Neues Element hinzufügen** aus.  
  
8.  Entweder unter **Visual C\#** oder den Knoten **Visual BasicSharePoint**, und wählen Sie den Knoten **2010** aus.  
  
9. Im Bereich **Vorlagen** wählen Sie **Sequenzieller Workflow \(nur Farmlösung\)** Vorlage aus und wählen Sie dann die Schaltfläche **Hinzufügen** aus.  
  
     Der **Assistent zum Anpassen von SharePoint** wird angezeigt.  
  
10. Akzeptieren Sie auf der Seite **Workflownamen für das Debugging angeben** den Standardnamen \(**ExpenseReport \- Workflow1**\).  Übernehmen Sie den Standardwert für den Workflowvorlagentyp \(**Listenworkflow**\).  Wählen Sie die Schaltfläche **Weiter** aus.  
  
11. Deaktivieren Sie auf der Seite **Soll Visual Studio den Workflow in einer Debugsitzung automatisch zuordnen?** das Kontrollkästchen für die automatische Zuordnung der Workflowvorlage, sofern dieses aktiviert ist.  
  
     Dieser Schritt ermöglicht es Ihnen, den Workflow später manuell der Liste Freigegebene Dokumente zuzuordnen, in der das Zuordnungsformular angezeigt wird.  
  
12. Wählen Sie die Schaltfläche **Fertig stellen** aus.  
  
## Hinzufügen eines Zuordnungsformulars zum Workflow  
 Erstellen Sie dann ein ASPX\-Zuordnungsformular, das angezeigt wird, wenn der SharePoint\-Administrator den Workflow erstmals einem Spesenabrechnungsdokument zuordnet.  
  
#### So fügen Sie dem Workflow ein Zuordnungsformular hinzu  
  
1.  Wählen Sie den Knoten **Workflow1** im **Projektmappen\-Explorer** aus.  
  
2.  Wählen Sie in der Menüleiste **Neues Element hinzufügen**, **Projekt**, um das Dialogfeld **Neues Element hinzufügen** anzuzeigen.  
  
3.  Erweitern Sie in der Strukturansicht **Visual C\#** oder **Visual Basic** \(abhängig von der Projektsprache\), erweitern Sie den Knoten **SharePoint**, und wählen Sie den Knoten **2010** aus.  
  
4.  In der Liste der Vorlagen, wählen Sie die Vorlage **Workflowzuordnungsformular** aus.  
  
5.  Im Textfeld **Name** geben Sie "ExpenseReportAssocForm.aspx" ein.  
  
6.  Wählen Sie die Schaltfläche **Hinzufügen**, um dem Projekt das Formular hinzuzufügen.  
  
## Entwerfen des Zuordnungsformulars und Schreiben von Code für das Zuordnungsformular  
 In diesem Verfahren fügen Sie dem Zuordnungsformular Funktionen hinzu, indem Sie Steuerelemente und Code hinzufügen.  
  
#### So entwerfen Sie das Zuordnungsformular und schreiben Code für das Zuordnungsformular  
  
1.  Suchen Sie im Zuordnungsformular \(ExpenseReportAssocForm.aspx\) nach dem `asp:Content`\-Element mit `ID="Main"`.  
  
2.  Fügen Sie direkt nach der ersten Zeile in diesem Inhaltselement den folgenden Code hinzu, um eine Bezeichnung und ein Textfeld zu erstellen, das zur Eingabe der zu genehmigenden Spesenhöchstgrenze auffordert \(*AutoApproveLimit*\):  
  
    ```  
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />  
  
    <asp:TextBox ID="AutoApproveLimit" runat="server" />  
    <br /><br />  
    ```  
  
3.  Erweitern Sie im **Projektmappen\-Explorer** die Datei **ExpenseReportAssocForm.aspx**, um deren abhängigen Dateien anzuzeigen.  
  
    > [!NOTE]  
    >  Wenn das Projekt in [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] ist, müssen Sie die Schaltfläche **Alle Dateien anzeigen** auswählen, um diesen Schritt auszuführen.  
  
4.  Öffnen Sie das Kontextmenü für die Datei ExpenseReportAssocForm.aspx und wählen Sie **Code anzeigen** aus.  
  
5.  Ersetzen Sie die `GetAssociationData`\-Methode durch Folgendes:  
  
    ```vb  
    Private Function GetAssociationData() As String  
        ' TODO: Return a string that contains the association data that   
        ' will be passed to the workflow. Typically, this is in XML   
        ' format.  
        Return Me.AutoApproveLimit.Text  
    End Function  
    ```  
  
    ```csharp  
    private string GetAssociationData()  
    {  
        // TODO: Return a string that contains the association data that   
        // will be passed to the workflow. Typically, this is in XML   
        // format.  
        return this.AutoApproveLimit.Text;  
    }  
    ```  
  
## Hinzufügen eines Initiierungsformulars zum Workflow  
 Erstellen Sie jetzt das Initiierungsformular, das angezeigt wird, wenn Benutzer den Workflow für ihre Spesenabrechnungen ausführen.  
  
#### So erstellen Sie ein Initiierungsformular  
  
1.  Wählen Sie den Knoten **Workflow1** im **Projektmappen\-Explorer** aus.  
  
2.  Wählen Sie in der Menüleiste **Neues Element hinzufügen**, Anzeige das Dialogfeld **Neues Element hinzufügenProjekt** aus.  
  
3.  Erweitern Sie in der Strukturansicht **Visual C\#** oder **Visual Basic**  \(abhängig von der Projektsprache\), erweitern Sie den Knoten **SharePoint**, und wählen Sie den Knoten **2010** aus.  
  
4.  In der Liste der Vorlagen, wählen Sie die Vorlage **Workflowinitiierungsformular** aus.  
  
5.  Im Textfeld **Name** geben Sie "ExpenseReportInitForm.aspx" ein.  
  
6.  Wählen Sie die Schaltfläche **Hinzufügen**, um dem Projekt das Formular hinzuzufügen.  
  
## Entwerfen des Initiierungsformulars und Schreiben von Code für das Initiierungsformular  
 Fügen Sie dem Initiierungsformular dann Funktionen hinzu, indem Sie Steuerelemente und Code hinzufügen.  
  
#### So schreiben Sie Code für das Initiierungsformular  
  
1.  im Initiierungsformular \(ExpenseReportInitForm.aspx\), suchen Sie das `asp:Content`\-Element, das `ID="Main"` enthält.  
  
2.  Fügen Sie direkt nach der ersten Zeile in diesem Inhaltselement den folgenden Code hinzu, um eine Bezeichnung und ein Textfeld zu erstellen, das die zu genehmigende Spesenhöchstgrenze anzeigt \(*AutoApproveLimit*\), die im Zuordnungsformular eingegeben wurde, sowie um eine weitere Bezeichnung und ein weiteres Textfeld zu erstellen, das zur Eingabe der zu genehmigenden Spesenhöchstgrenze auffordert \(*ExpenseTotal*\):  
  
    ```  
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />  
  
    <asp:TextBox ID="AutoApproveLimit" ReadOnly="true" runat="server" />  
    <br /><br />  
    <asp:Label ID="lblExpenseTotal" Text="Expense Total:" runat="server" />  
  
    <asp:TextBox ID="ExpenseTotal" runat="server" />  
    <br /><br />  
    ```  
  
3.  Erweitern Sie im **Projektmappen\-Explorer** die Datei **ExpenseReportInitForm.aspx**, um deren abhängigen Dateien anzuzeigen.  
  
4.  Öffnen Sie das Kontextmenü für die Datei ExpenseReportInitForm.aspx und wählen Sie **Code anzeigen** aus.  
  
5.  Ersetzen Sie die `Page_Load`\-Methode durch das folgende Beispiel:  
  
    ```vb  
    Protected Sub Page_Load(ByVal sender As Object, ByVal e As   
      EventArgs) Handles Me.Load  
        InitializeParams()  
        Me.AutoApproveLimit.Text = workflowList.WorkflowAssociations(New   
          Guid(associationGuid)).AssociationData  
        ' Optionally, add code here to pre-populate your form fields.  
    End Sub  
    ```  
  
    ```csharp  
    protected void Page_Load(object sender, EventArgs e)  
    {  
        InitializeParams();  
        this.AutoApproveLimit.Text =   
          workflowList.WorkflowAssociations[new   
          Guid(associationGuid)].AssociationData;  
    }  
    ```  
  
6.  Ersetzen Sie die `GetInitiationData`\-Methode durch das folgende Beispiel:  
  
    ```vb  
    ' This method is called when the user clicks the button to start the workflow.  
    Private Function GetInitiationData() As String  
        Return Me.ExpenseTotal.Text  
        ' TODO: Return a string that contains the initiation data that   
        ' will be passed to the workflow. Typically, this is in XML   
        ' format.  
        Return String.Empty  
    End Function  
    ```  
  
    ```csharp  
    // This method is called when the user clicks the button to start the workflow.          
    private string GetInitiationData()  
    {  
        // TODO: Return a string that contains the initiation data that   
        // will be passed to the workflow. Typically, this is in XML   
        // format.  
        return this.ExpenseTotal.Text;  
    }  
    ```  
  
## Anpassen des Workflows  
 Passen Sie danach den Workflow an.  Später ordnen Sie dem Workflow zwei Formulare zu.  
  
#### So passen Sie den Workflow an  
  
1.  Zeigen Sie den Workflow im Workflow\-Designer an, indem Sie Workflow1 im Projekt öffnen.  
  
2.  Erweitern Sie in **Werkzeugkasten** den Knoten **Windows Workflow v3.0** und suchen Sie die Aktivität **IfElse**.  
  
3.  Fügen Sie dem Workflow diese Aktivität hinzu, indem Sie einen der folgenden Schritte ausführen:  
  
    -   Öffnen Sie das Kontextmenü für die Aktivität **IfElse**, wählen Sie **Kopieren** aus, öffnen Sie das Kontextmenü für die Zeile unter der Aktivität **onWorkflowActivated1** im Workflow\-Designer, und wählen Sie dann **Einfügen** aus.  
  
    -   Ziehen Sie die Aktivität **IfElse** von **Werkzeugkasten**, und schließen Sie sie an die Zeile unter der Aktivität **onWorkflowActivated1** im Workflow\-Designer an.  
  
4.  Erweitern Sie in der Toolbox den Knoten **SharePoint\-Workflow**, und suchen Sie die **CreateTask**\-Aktivität.  
  
5.  Fügen Sie dem Workflow diese Aktivität hinzu, indem Sie einen der folgenden Schritte ausführen:  
  
    -   Öffnen Sie das Kontextmenü für die Aktivität **CreateTask**, wählen Sie **Kopieren** aus, öffnen Sie das Kontextmenü für einen der beiden Bereiche **Aktivitäten hier ablegen** innerhalb IfElseActivity1 im Workflow\-Designer, und wählen Sie dann **Einfügen** aus.  
  
    -   Ziehen Sie die Aktivität **CreateTask** aus der **Werkzeugkasten** auf einen der beiden Bereiche **Aktivitäten hier ablegen** innerhalb IfElseActivity1.  
  
6.  Geben Sie im Fenster **Eigenschaften** den Eigenschaftswert *taskToken* für die **CorrelationToken**\-Eigenschaft ein.  
  
7.  Erweitern Sie die Eigenschaft **CorrelationToken**, indem Sie das Pluszeichen \(![TreeView-Plus](~/docs/sharepoint/media/plus.gif "TreeView-Plus")\) daneben aus.  
  
8.  Wählen Sie den Dropdownpfeil der **OwnerActivityName** Subventionseigenschaft, und legen Sie den *Workflow1*\-Wert fest.  
  
9. Wählen Sie die **TaskId**\-Eigenschaft aus, und wählen Sie die Schaltfläche mit den Auslassungszeichen \(![Auslassungszeichen im ASP.NET Mobile-Designer](~/docs/sharepoint/media/mwellipsis.gif "Auslassungszeichen im ASP.NET Mobile-Designer")\), um das Dialogfeld **Eigenschaft binden** anzuzeigen.  
  
10. Wählen Sie die Registerkarte **An neues Mitglied binden** aus, wählen Sie das Optionsfeld **Feld erstellen**, und wählen Sie dann die Schaltfläche **OK** aus.  
  
11. Wählen Sie die **TaskProperties**\-Eigenschaft aus, und wählen Sie die Schaltfläche mit den Auslassungszeichen \(![Auslassungszeichen im ASP.NET Mobile-Designer](~/docs/sharepoint/media/mwellipsis.gif "Auslassungszeichen im ASP.NET Mobile-Designer")\), um das Dialogfeld **Eigenschaft binden** anzuzeigen.  
  
12. Wählen Sie die Registerkarte **An neues Mitglied binden** aus, wählen Sie das Optionsfeld **Feld erstellen**, und wählen Sie dann die Schaltfläche **OK** aus.  
  
13. Erweitern Sie in **Werkzeugkasten** den Knoten **SharePoint Workflow** und suchen Sie die Aktivität **LogToHistoryListActivity**.  
  
14. Fügen Sie dem Workflow diese Aktivität hinzu, indem Sie einen der folgenden Schritte ausführen:  
  
    -   Öffnen Sie das Kontextmenü für die Aktivität **LogToHistoryListActivity**, wählen Sie **Kopieren** aus, öffnen Sie das Kontextmenü für den anderen Bereich **Aktivitäten hier ablegen** innerhalb IfElseActivity1 im Workflow\-Designer, und wählen Sie dann **Einfügen** aus.  
  
    -   Ziehen Sie die Aktivität **LogToHistoryListActivity** von **Werkzeugkasten**, und legen Sie sie auf den anderen Bereich **Aktivitäten hier ablegen** innerhalb IfElseActivity1 ab.  
  
## Hinzufügen von Code zum Workflow  
 Fügen Sie dem Workflow nun Code hinzu, um Funktionen hinzuzufügen.  
  
#### So fügen Sie dem Workflow Code hinzu  
  
1.  Öffnen Sie das Kontextmenü für **createTask1** die Aktivität im Workflow\-Designer, und wählen Sie dann **Code anzeigen** aus.  
  
2.  Fügen Sie die folgende Methode hinzu:  
  
    ```vb  
    Private Sub createTask1_MethodInvoking(ByVal sender As   
      System.Object, ByVal e As System.EventArgs)  
        createTask1_TaskId1 = Guid.NewGuid  
        createTask1_TaskProperties1.AssignedTo = "somedomain\\someuser"  
        createTask1_TaskProperties1.Description = "Please approve the   
          expense report"  
        createTask1_TaskProperties1.Title = "Expense Report Approval   
          Needed"  
    End Sub   
    ```  
  
    ```csharp  
    private void createTask1_MethodInvoking(object sender, EventArgs e)  
    {  
        createTask1_TaskId1 = Guid.NewGuid();  
        createTask1_TaskProperties1.AssignedTo = "somedomain\\someuser";  
        createTask1_TaskProperties1.Description = "Please approve the   
          expense report";  
        createTask1_TaskProperties1.Title = "Expense Report Approval   
          Needed";  
    }   
    ```  
  
    > [!NOTE]  
    >  Ersetzen Sie im Code `somedomain\\someuser` durch eine Domäne und einen Benutzernamen, für die eine Aufgabe erstellt wird, z. B. "`Office\\JoeSch`".  Zu Testzwecken ist es am einfachsten, das Konto zu verwenden, das Sie zur Entwicklung verwenden.  
  
3.  Fügen Sie unter der `MethodInvoking`\-Methode das folgende Beispiel hinzu:  
  
    ```vb  
    Private Sub checkApprovalNeeded(ByVal sender As Object, ByVal e As   
      ConditionalEventArgs)  
        Dim approval As Boolean = False  
        If (Convert.ToInt32(workflowProperties.InitiationData) >   
          Convert.ToInt32(workflowProperties.AssociationData)) Then  
            approval = True  
        End If  
        e.Result = approval  
    End Sub   
    ```  
  
    ```csharp  
    private void checkApprovalNeeded(object sender, ConditionalEventArgs   
      e)  
    {  
        bool approval = false;  
        if (Convert.ToInt32(workflowProperties.InitiationData) >   
          Convert.ToInt32(workflowProperties.AssociationData))  
        {  
            approval = true;  
        }  
        e.Result = approval;  
    }   
    ```  
  
4.  im Workflow\-Designer auf die Aktivität **ifElseBranchActivity1** aus.  
  
5.  Im Fenster **Eigenschaften** wählen Sie den Dropdownpfeil der Eigenschaft **Bedingung** aus, und legen Sie den *Code Condition*\-Wert fest.  
  
6.  Erweitern Sie die Eigenschaft **Bedingung**, indem Sie das Pluszeichen \(![TreeView-Plus](~/docs/sharepoint/media/plus.gif "TreeView-Plus")\) daneben aus, und legen Sie den Wert dann auf *checkApprovalNeeded* fest.  
  
7.  im Workflow\-Designer öffnen Sie das Kontextmenü für **logToHistoryListActivity1** die Aktivität, und wählen Sie dann **Handler generieren**, um eine leere Methode für das `MethodInvoking`\-Ereignis zu generieren.  
  
8.  Ersetzen Sie den `MethodInvoking`\-Code durch Folgendes:  
  
    ```vb  
    Private Sub logToHistoryListActivity1_MethodInvoking(ByVal sender As   
      System.Object, ByVal e As System.EventArgs)  
        Me.logToHistoryListActivity1.HistoryOutcome = ("Expense was auto   
          approved for " + workflowProperties.InitiationData)  
    End Sub   
    ```  
  
    ```csharp  
    private void logToHistoryListActivity1_MethodInvoking(object sender,   
      EventArgs e)  
    {  
        this.logToHistoryListActivity1.HistoryOutcome = "Expense was   
          auto approved for " + workflowProperties.InitiationData;  
    }   
    ```  
  
9. Drücken Sie die F5\-TASTE, um das Programm zu debuggen.  
  
     Hiermit wird Folgendes ausgeführt: Die Anwendung wird kompiliert, verpackt und bereitgestellt, die Funktionen werden aktiviert, der [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)]\-Anwendungspool wird wiederverwendet, und dann wird der Browser mit dem in der Eigenschaft **Website\-URL** angegebenen Ort gestartet.  
  
## Zuordnen des Workflows zur Liste Dokumente  
 Zeigen Sie dann das Workflowzuordnungsformular an, indem Sie den Workflow der Liste **FreigegebeneDokumente** auf der SharePoint\-Website zuordnen.  
  
#### So ordnen Sie den Workflow zu  
  
1.  Wählen Sie den Link **Freigegebene Dokumente** auf der Schnellstartleiste aus.  
  
2.  Wählen Sie den Link **Bibliothek** auf der Registerkarte **Bibliothekstools** und wählen Sie dann die **Bibliothekeinstellungen** \-Schaltfläche Menüband aus.  
  
3.  Im Abschnitt **Berechtigungen und Verwaltung** Wählen Sie den Link **Workfloweinstellungen** aus und anschließend den Link **Workflow hinzufügen** auf der Seite **Workflows** aus.  
  
4.  Wählen Sie in der obersten Liste in den Workfloweinstellungen blättern Sie, wählen Sie die Vorlage **ExpenseReport \- Workflow1** aus.  
  
5.  Geben Sie im nächsten Feld geben Sie ExpenseReportWorkflow ein und wählen Sie dann die Schaltfläche **Weiter** aus.  
  
     Hierdurch wird der Workflow der Liste **Freigegebene Dokumente** zugeordnet, und das Workflowzuordnungsformular wird angezeigt.  
  
6.  Im Textfeld **Automatische Genehmigungsgrenze** geben Sie 1200 ein und wählen Sie dann die Schaltfläche **Workflow zuordnen** aus.  
  
## Starten des Workflows  
 Ordnen Sie den Workflow danach einem der Dokumenten in der Liste **Freigegebene Dokumente** zu, um das Workflowinitiierungsformular anzuzeigen.  
  
#### So starten Sie den Workflow  
  
1.  Klicken Sie auf der SharePoint\-Seite auf die Schaltfläche **Startseite** aus.  
  
2.  Wählen Sie den Link **Freigegebene Dokumente** auf der Schnellstartleiste, um die Liste **Freigegebene Dokumente** anzuzeigen.  
  
3.  Wählen Sie den Link **Dokumente** auf der Registerkarte **Bibliothekstools** oben auf der Seite aus, und wählen Sie die Schaltfläche **Dokument hochladen** auf dem Menüband, um ein neues Dokument in die Liste **Freigegebene Dokumente** hochzuladen.  
  
4.  Im Dialogfeld **Dokument hochladen** wählen Sie die Schaltfläche **Durchsuchen** aus, wählen Sie eine Dokumentdatei aus, wählen Sie die Schaltfläche **Öffnen**, und wählen Sie dann die Schaltfläche **OK** aus.  
  
     Sie können die Einstellungen für das Dokument in diesem Dialogfeld ändern, aber lassen sie an die Standardwerte, indem Sie die Schaltfläche **Speichern** auswählen.  
  
5.  Wählen Sie das hochgeladene Dokument aus, wählen Sie den Dropdownpfeil, der angezeigt wird, und wählen Sie das Element **Workflows** aus.  
  
6.  Wählen Sie das Bild neben ExpenseReportWorkflow aus.  
  
     Hierdurch wird das Workflowinitiierungsformular angezeigt. \(Beachten Sie, dass der im Feld **Auto Approval Limit** angezeigte Wert schreibgeschützt ist, da er im Zuordnungsformular eingegeben wurde.\)  
  
7.  Im Textfeld **Gesamtausgaben** geben Sie 1600 ein und wählen Sie dann die Schaltfläche **Workflow starten** aus.  
  
     Hiermit wird erneut die Liste **Freigegebene Dokumente** angezeigt.  Eine neue Spalte namens **ExpenseReportWorkflow** mit dem Wert **Abgeschlossen** wird dem Element hinzugefügt, das der Workflow gerade gestartet hat.  
  
8.  Wählen Sie den Dropdownpfeil neben dem hochgeladenen Dokument aus und wählen Sie dann das Element **Workflows**, um die Workflowstatusseite anzuzeigen.  Wählen Sie den Wert unter **AbgeschlossenAbgeschlossener Workflow** aus.  Die Aufgabe wird im Abschnitt **Aufgaben** aufgeführt.  
  
9. Wählen Sie den Titel der Aufgabe, um die Aufgabendetails anzuzeigen aus.  
  
10. Wechseln Sie wieder zur Liste **FreigegebeneDokumente**, und starten Sie den Workflow mit demselben oder einem anderen Dokument erneut.  
  
11. Geben Sie auf der Initiierungsseite einen Betrag an, der kleiner oder gleich der Menge ist, die auf der Zuordnungsseite eingegebenen Betrag \(1200\) ist.  
  
     In diesem Fall wird statt einer Aufgabe ein Eintrag in der Verlaufsliste erstellt.  Der Eintrag wird im Abschnitt **Workflowverlauf** der Workflowstatusseite angezeigt.  Beachten Sie die Meldung in der Spalte **Ergebnis** des Verlaufsereignisses.  Sie enthält den Text, der im `logToHistoryListActivity1.MethodInvoking`\-Ereignis eingegeben wurde und der den automatisch genehmigten Betrag einschließt.  
  
## Nächste Schritte  
 Weitere Informationen zum Erstellen von Workflowvorlagen finden Sie in diesen Themen:  
  
-   Weitere Informationen zu SharePoint\-Workflows, Sie finden [Workflows in Windows SharePoint Services](http://go.microsoft.com/fwlink/?LinkID=166275).  
  
## Siehe auch  
 [Erstellen von SharePoint-Workflow-Projektmappen](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [Exemplarische Vorgehensweise: Hinzufügen einer Anwendungsseite zu einem Workflow](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)  
  
  