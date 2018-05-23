---
title: 'Exemplarische Vorgehensweise: Erstellen eines Workflows mit Zuordnungs- und Initiierungsformularen | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- SharePoint development in Visual Studio, workflow association forms
- workflows [SharePoint development in Visual Studio]
- association forms [SharePoint development in Visual Studio]
- initiation forms [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, workflow initiation forms
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0c232d541e985944fe64d9eb40da7e344b32c0cc
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2018
---
# <a name="walkthrough-creating-a-workflow-with-association-and-initiation-forms"></a>Exemplarische Vorgehensweise: Erstellen eines Workflows mit Zuordnungs- und Initiierungsformularen
  Diese exemplarische Vorgehensweise veranschaulicht die Erstellung ein grundlegenden sequenziellen Workflows, das die Verwendung von Zuordnungs-und Initiierungsformularen integriert. Hierbei handelt es sich um ASPX-Formulare, die Parameter eines Workflows hinzugefügt werden, wenn es zuerst vom SharePoint-Administrator (Form Zuordnung) zugewiesen ist und der Workflow gestartet wird, vom Benutzer (Initiierung Form) aktivieren.  
  
 In dieser exemplarischen Vorgehensweise wird beschrieben, ein Szenario, bei denen ein Benutzer möchte einen Genehmigungsworkflow für Ausgabenberichte erstellen, der folgenden Anforderungen erfüllt:  
  
-   Wenn der Workflow einer Liste zugeordnet ist, wird der Administrator mit einem Zuordnungsformular aufgefordert, in dem sie ein Limit Dollar für Ausgabenberichte eingeben.  
  
-   Mitarbeiter ihre Ausgabenberichte in der Liste Freigegebene Dokumente hochladen, starten Sie den Workflow und geben Sie dann die Ausgabe im Workflow Initiierungsformular insgesamt.  
  
-   Wenn ein Mitarbeiter Ausgabenbericht insgesamt des Administrators vordefinierte Grenze überschreitet, wird eine Aufgabe für die Mitarbeiter-Manager So genehmigen Sie die Ausgabenbericht erstellt. Arbeitnehmers Bericht Gesamtausgaben kleiner als oder gleich dem Limit von Ausgaben ist, ist jedoch eine automatisch genehmigte Nachricht an den Workflow-Verlaufsliste geschrieben.  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Erstellen einer SharePoint-Liste Definition sequenzieller Workflowprojekts in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
-   Erstellen einen Workflowzeitplan.  
  
-   Behandlung von Ereignissen für Workflow-Aktivität.  
  
-   Erstellen Workflows Zuordnungs-und Initiierungsformularen.  
  
-   Zuordnen des Workflows.  
  
-   Wird den Workflow manuell gestartet.  
  
> [!NOTE]  
>  Obwohl in dieser exemplarischen Vorgehensweise ein sequenzielles Workflowprojekt verwendet wird, ist der Prozess für Zustandsautomatworkflows identisch.  
>   
>  Ihr Computer kann außerdem angezeigt, andere Namen oder Speicherorte für die Benutzeroberflächenelemente von der [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Elemente der Benutzeroberfläche in den folgenden Anweisungen. Die [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] -Version und die Einstellungen, mit denen Sie bestimmen diese Elemente. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   Unterstützte Editionen von [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] und SharePoint. Weitere Informationen finden Sie unter [Anforderungen für die Entwicklung von SharePoint-Lösungen](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
## <a name="creating-a-sharepoint-sequential-workflow-project"></a>Erstellen ein sequenzielles Workflowprojekt von SharePoint  
 Erstellen Sie zunächst ein sequenzielles Workflowprojekt in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Ein sequenzieller Workflow ist eine Reihe von Schritten, die in der Reihenfolge ausgeführt wird, bis die letzte Aktivität abgeschlossen ist. In diesem Verfahren erstellen Sie einen sequenziellen Workflow, der für die Liste Freigegebene Dokumente in SharePoint gilt. Die Workflow-Assistenten können Sie den Workflow mit der Website oder die Listendefinition zuordnen und können Sie bestimmen, wann der Workflow gestartet wird.  
  
#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>So erstellen ein sequenzielles Workflowprojekt von SharePoint  
  
1.  Wählen Sie in der Menüleiste **Datei**, **neu**, **Projekt** zum Anzeigen der **neues Projekt** (Dialogfeld).  
  
2.  Erweitern Sie die **SharePoint** Knoten unter einem **Visual C#-** oder **Visual Basic**, und wählen Sie dann die **2010** Knoten.  
  
3.  In der **Vorlagen** Bereich, wählen Sie die **SharePoint 2010-Projekt** -Projektvorlage.  
  
4.  In der **Namen** geben **ExpenseReport** und wählen Sie dann die **OK** Schaltfläche.  
  
     Die **Assistent zum Anpassen von SharePoint** angezeigt wird.  
  
5.  In der **Geben Sie die Website und die Sicherheit für das Debuggen** Seite der **als farmlösung bereitstellen** Optionsfeld aus, und wählen Sie dann die **Fertig stellen** Schaltfläche zum Akzeptieren der Vertrauensstellung Ebene und Standard-Website.  
  
     Dieser Schritt legt außerdem die Vertrauensebene für die Projektmappe als farmlösung, also die einzig verfügbare Option für Workflowprojekte.  
  
6.  Wählen Sie im **Projektmappen-Explorer**den Projektknoten aus.  
  
7.  Wählen Sie in der Menüleiste **Projekt**, **neues Element hinzufügen**.  
  
8.  Unter einem **Visual C#-** oder **Visual Basic**, erweitern Sie die **SharePoint** Knoten, und wählen Sie dann die **2010** Knoten.  
  
9. In der **Vorlagen** Bereich auswählen **sequenzieller Workflow (nur Farmlösung)** Vorlage, und wählen Sie dann die **hinzufügen** Schaltfläche.  
  
     Die **Assistent zum Anpassen von SharePoint** angezeigt wird.  
  
10. In der **Geben Sie den Workflownamen für das Debuggen** Seite, übernehmen Sie den Standardnamen (**ExpenseReport - Workflow1**). Beibehalten des Standardwerts Workflow Vorlage Typ (**Listenworkflow)**. Klicken Sie auf **Weiter**.  
  
11. In der **möchten Sie Visual Studio, um den Workflow in einer Debugsitzung automatisch zuordnen?** Seite, deaktivieren Sie das Kontrollkästchen, die automatisch Ihrer Workflowvorlage zuordnet, wenn diese Option aktiviert ist.  
  
     Dadurch können Sie manuell den Workflow in der Liste Freigegebene Dokumente später Zuordnen der Zuordnung Form angezeigt.  
  
12. Wählen Sie die **Fertig stellen** Schaltfläche.  
  
## <a name="adding-an-association-form-to-the-workflow"></a>Hinzufügen einer Zuordnungsformulars zum Workflow  
 Als Nächstes erstellen Sie ein. Aspx-Zuordnung-Formular, das angezeigt wird, wenn der SharePoint-Administrator zunächst den Workflow ein Dokument für den ausgabenbeispielbericht zuordnet.  
  
#### <a name="to-add-an-association-form-to-the-workflow"></a>Der Workflow eine Zuordnungsformular hinzu  
  
1.  Wählen Sie die **Workflow1** Knoten **Projektmappen-Explorer**.  
  
2.  Wählen Sie in der Menüleiste **Projekt**, **neues Element hinzufügen** zum Anzeigen der **neues Element hinzufügen** (Dialogfeld).  
  
3.  Erweitern Sie in der Strukturansicht des Dialogfelds entweder **Visual C#-** oder **Visual Basic** (abhängig von der Projektsprache), erweitern Sie die **SharePoint** Knoten, und wählen Sie dann die **2010** Knoten.  
  
4.  Wählen Sie in der Liste der Vorlagen, die **Workflow Zuordnungsformular** Vorlage.  
  
5.  In der **Namen** Text geben **ExpenseReportAssocForm.aspx**.  
  
6.  Wählen Sie die **hinzufügen** Schaltfläche, um das Formular zum Projekt hinzuzufügen.  
  
## <a name="designing-and-coding-the-association-form"></a>Entwurf und die Codierung des Formulars Zuordnung  
 In diesem Verfahren machen Sie die Funktionalität in das Zuordnungsformular von Steuerelementen und Code hinzugefügt.  
  
#### <a name="to-design-and-code-the-association-form"></a>Entwurf und Code der Zuordnungsformular  
  
1.  Suchen Sie in der Form der Zuordnung (ExpenseReportAssocForm.aspx), die `asp:Content` Element mit `ID="Main"`.  
  
2.  Fügen Sie direkt nach der ersten Zeile in diesem Inhaltselement den folgenden Code zum Erstellen, eine Bezeichnung und ein Textfeld, das für die Ausgaben genehmigungsgrenzwert auffordert (*AutoApproveLimit*):  
  
    ```aspx-csharp  
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />  
  
    <asp:TextBox ID="AutoApproveLimit" runat="server" />  
    <br /><br />  
    ```  
  
3.  Erweitern Sie die **ExpenseReportAssocForm.aspx** Datei **Projektmappen-Explorer** seinen abhängigen Dateien angezeigt.  
  
    > [!NOTE]  
    >  Wenn Ihr Projekt in [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)], müssen Sie auswählen, die **alle Dateien anzeigen** Schaltfläche, um diesen Schritt auszuführen.  
  
4.  Öffnen Sie das Kontextmenü für die Datei ExpenseReportAssocForm.aspx, und wählen Sie **Code anzeigen**.  
  
5.  Ersetzen Sie die `GetAssociationData` Methode mit:  
  
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
  
## <a name="adding-an-initiation-form-to-the-workflow"></a>Ein Formular für die Initiierung von hinzufügen dem Workflow  
 Als Nächstes erstellen Sie die Initiierung von-Formular, das angezeigt wird, wenn der Benutzer des Workflows für ihre Ausgabenberichte ausgeführt.  
  
#### <a name="to-create-an-initiation-form"></a>So erstellen Sie ein Initiierungsformular  
  
1.  Wählen Sie die **Workflow1** Knoten **Projektmappen-Explorer**.  
  
2.  Wählen Sie in der Menüleiste **Projekt**, **neues Element hinzufügen** Anzeigen der **neues Element hinzufügen** (Dialogfeld).  
  
3.  Erweitern Sie in der Strukturansicht des Dialogfelds entweder **Visual C#-** oder **Visual Basic** (abhängig von der Projektsprache), erweitern Sie die **SharePoint** Knoten, und wählen Sie dann die **2010** Knoten.  
  
4.  Wählen Sie in der Liste der Vorlagen, die **Workflow Initiierungsformular** Vorlage.  
  
5.  In der **Namen** Text geben **ExpenseReportInitForm.aspx**.  
  
6.  Wählen Sie die **hinzufügen** Schaltfläche, um das Formular zum Projekt hinzuzufügen.  
  
## <a name="designing-and-coding-the-initiation-form"></a>Entwerfen und Programmieren das Formular für die Initiierung von  
 Als Nächstes führen Sie Funktionalität in das Initiierungsformular von Steuerelementen und Code hinzugefügt ein.  
  
#### <a name="to-code-the-initiation-form"></a>Um das Formular für die Initiierung von code  
  
1.  Suchen Sie in der Form (ExpenseReportInitForm.aspx) für die Initiierung der `asp:Content` Element, das enthält `ID="Main"`.  
  
2.  Direkt nach der ersten Zeile in diesem Inhaltselement, fügen Sie folgenden Code zum Erstellen einer Bezeichnung und ein Textfeld, das die Ausgaben genehmigungsgrenzwert anzeigt (*AutoApproveLimit*), die im Zuordnungsformular und eine andere Bezeichnung eingegeben wurde und Textfeld für die Gesamtausgaben aufgefordert (*ExpenseTotal*):  
  
    ```aspx-csharp  
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />  
  
    <asp:TextBox ID="AutoApproveLimit" ReadOnly="true" runat="server" />  
    <br /><br />  
    <asp:Label ID="lblExpenseTotal" Text="Expense Total:" runat="server" />  
  
    <asp:TextBox ID="ExpenseTotal" runat="server" />  
    <br /><br />  
    ```  
  
3.  Erweitern Sie die **ExpenseReportInitForm.aspx** Datei **Projektmappen-Explorer** seinen abhängigen Dateien angezeigt.  
  
4.  Öffnen Sie das Kontextmenü für die Datei ExpenseReportInitForm.aspx, und wählen Sie **Code anzeigen**.  
  
5.  Ersetzen Sie die `Page_Load` Methode mit dem folgenden Beispiel:  
  
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
  
6.  Ersetzen Sie die `GetInitiationData` Methode mit dem folgenden Beispiel:  
  
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
  
## <a name="customizing-the-workflow"></a>Anpassen des Workflows  
 Als Nächstes den Workflow anpassen. Später ordnen Sie zwei Formen an den Workflow.  
  
#### <a name="to-customize-the-workflow"></a>Anpassen des Workflows  
  
1.  Zeigen Sie den Workflow im Workflow-Designer Workflow1 in das Projekt zu öffnen.  
  
2.  In der **Toolbox**, erweitern Sie die **Windows Workflow v3. 0** Knoten, und suchen Sie die **IfElse** Aktivität.  
  
3.  Fügen Sie diese Aktivität an den Workflow, indem Sie eine der folgenden Schritte ausführen:  
  
    -   Öffnen Sie das Kontextmenü für die **IfElse** Aktivität, wählen Sie **Kopie**, öffnen Sie das Kontextmenü für die Zeile unter der **onWorkflowActivated1** Aktivität im Workflow-Designer und wählen Sie dann **einfügen**.  
  
    -   Ziehen Sie die **IfElse** Aktivität aus der **Toolbox**, und verbinden Sie ihn mit der Zeile unter der **onWorkflowActiviated1** Aktivität im Workflow-Designer.  
  
4.  Erweitern Sie in der Toolbox die **SharePoint-Workflow** Knoten, und suchen Sie die **CreateTask** Aktivität.  
  
5.  Fügen Sie diese Aktivität an den Workflow, indem Sie eine der folgenden Schritte ausführen:  
  
    -   Öffnen Sie das Kontextmenü für die **CreateTask** Aktivität, wählen Sie **Kopie**, öffnen Sie das Kontextmenü für einen der beiden **Aktivitäten hier ablegen** Bereichen in  **IfElseActivity1-Aktivität ziehen** im Workflow-Designer, und wählen Sie dann **einfügen**.  
  
    -   Ziehen Sie die **CreateTask** Aktivität aus der **Toolbox** auf einem der beiden **Aktivitäten hier ablegen** Bereichen in **IfElseActivity1-Aktivität ziehen**.  
  
6.  In der **Eigenschaften** Fenster, geben Sie den Eigenschaftswert einer *TaskToken* für die **CorrelationToken** Eigenschaft.  
  
7.  Erweitern Sie die **CorrelationToken** Eigenschaft durch das Pluszeichen auswählen (![TreeView-plus](../sharepoint/media/plus.gif "TreeView-plus")) daneben.  
  
8.  Wählen Sie auf den Dropdown Pfeil der **OwnerActivityName** sub-Eigenschaft, und legen Sie die *Workflow1* Wert.  
  
9. Wählen Sie die **TaskId** -Eigenschaft, und klicken Sie dann auf die Auslassungspunkte (![Ellipse, die ASP.NET Mobile-Designer](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile-Designer Ellipse")) Schaltfläche zum Anzeigen der **Eigenschaft binden** (Dialogfeld).  
  
10. Wählen Sie die **Binden an einen neuen Member** Registerkarte, und wählen Sie die **Feld erstellen** Optionsfeld aus, und wählen Sie dann die **OK** Schaltfläche.  
  
11. Wählen Sie die **TaskProperties** -Eigenschaft, und klicken Sie dann auf die Auslassungspunkte (![ASP.NET Mobile-Designer Ellipse](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile-Designer Ellipse")) Schaltfläche, um die anzuzeigen **Eigenschaft binden** (Dialogfeld).  
  
12. Wählen Sie die **Binden an einen neuen Member** Registerkarte, und wählen Sie die **Feld erstellen** Optionsfeld aus, und wählen Sie dann die **OK** Schaltfläche.  
  
13. In der **Toolbox**, erweitern Sie die **SharePoint-Workflow** Knoten, und suchen Sie die **LogToHistoryListActivity** Aktivität.  
  
14. Fügen Sie diese Aktivität an den Workflow, indem Sie eine der folgenden Schritte ausführen:  
  
    -   Öffnen Sie das Kontextmenü für die **LogToHistoryListActivity** Aktivität, wählen Sie **Kopie**, öffnen Sie das Kontextmenü für die anderen **Aktivitäten hier ablegen** Bereich im **IfElseActivity1-Aktivität ziehen** im Workflow-Designer, und wählen Sie dann **einfügen**.  
  
    -   Ziehen Sie die **LogToHistoryListActivity** Aktivität aus der **Toolbox**, und legen ihn auf die andere **Aktivitäten hier ablegen** Bereich im **IfElseActivity1-Aktivität ziehen** .  
  
## <a name="adding-code-to-the-workflow"></a>Hinzufügen von Code für den Workflow  
 Als Nächstes fügen Sie Code für den Workflow, um Funktionen hinzuzufügen.  
  
#### <a name="to-add-code-to-the-workflow"></a>So fügen Sie Code für den Workflow hinzu  
  
1.  Öffnen Sie das Kontextmenü für die **createTask1** Aktivität im Workflow-Designer, und wählen Sie dann **Code anzeigen**.  
  
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
    >  Ersetzen Sie im Code, `somedomain\\someuser` mit einer Domäne und den Namen für die eine Aufgabe, z. B. erstellt werden "`Office\\JoeSch`". Für Testzwecke ist es am einfachsten, das Konto verwenden, die von dem Ihnen entwickelten.  
  
3.  Unterhalb der `MethodInvoking` -Methode, fügen Sie das folgende Beispiel:  
  
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
  
4.  Wählen Sie im Workflow-Designer die **ifElseBranchActivity1** Aktivität.  
  
5.  In der **Eigenschaften** Fenster, wählen Sie den Dropdown-Pfeil der der **Bedingung** -Eigenschaft, und legen Sie anschließend die *Code Bedingung* Wert.  
  
6.  Erweitern Sie die **Bedingung** Eigenschaft durch das Pluszeichen auswählen (![TreeView-plus](../sharepoint/media/plus.gif "TreeView-plus")) daneben aus, und legen Sie dessen Wert auf *CheckApprovalNeeded* .  
  
7.  Öffnen Sie im Workflow-Designer das Kontextmenü für die **logToHistoryListActivity1** Aktivität, und wählen Sie dann **Handler generiert** eine leere Methode zum Generieren der `MethodInvoking` Ereignis.  
  
8.  Ersetzen Sie die `MethodInvoking` durch den folgenden Code:  
  
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
  
9. Wählen Sie die Taste F5, um das Programm zu debuggen.  
  
     Dadurch wird die Anwendung kompiliert, wird, stellt sie bereit, dessen Funktionen aktiviert, wiederverwendet wird die [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] Anwendungspool, und klicken Sie dann beginnt mit der Browser an der Position angegeben, in der **Website-Url** Eigenschaft.  
  
## <a name="associating-the-workflow-to-the-documents-list"></a>Zuordnen des Workflows zur Dokumentliste  
 Zeigen Sie das Workflow-Zuordnung-Formular als Nächstes durch das Zuordnen von Workflows mit der **SharedDocuments** Liste auf der SharePoint-Website.  
  
#### <a name="to-associate-the-workflow"></a>Der Workflow zuordnen  
  
1.  Wählen Sie die **Shared Documents** Link auf der Schnellstartleiste.  
  
2.  Wählen Sie die **Bibliothek** link die **Bibliothekstools** Registerkarte, und wählen Sie dann die **Bibliothekseinstellungen** Schaltfläche des Menübands.  
  
3.  In der **Berechtigungen und Verwaltung** Abschnitt der **Workfloweinstellungen** verknüpfen, und wählen Sie dann die **Hinzufügen eines Workflows** link die **Workflows** Seite.  
  
4.  Wählen Sie in der oberen Liste auf der Einstellungsseite des Workflows für die **ExpenseReport - Workflow1** Vorlage.  
  
5.  Geben Sie in das nächste Feld **ExpenseReportWorkflow** und wählen Sie dann die **Weiter** Schaltfläche.  
  
     Dies ordnet den Workflow mit der **Shared Documents** aus und zeigt das Formular der Workflow-Zuordnung.  
  
6.  In der **Auto Genehmigungsgrenzwert** Text geben **1200** und wählen Sie dann die **Workflow zuordnen** Schaltfläche.  
  
## <a name="starting-the-workflow"></a>Starten des Workflows  
 Als Nächstes ordnen Sie den Workflow zu einem der Dokumente in der **Shared Documents** Liste aus, um das Workflow-Initiierung von Formular anzuzeigen.  
  
#### <a name="to-start-the-workflow"></a>Zum Starten des Workflows  
  
1.  Wählen Sie in der SharePoint-Seite der **Home** Schaltfläche.  
  
2.  Wählen Sie die **Shared Documents** Link auf der Schnellstartleiste zum Anzeigen der **Shared Documents** Liste.  
  
3.  Wählen Sie die **Dokumente** link die **Bibliothekstools** Registerkarte am oberen Rand der Seite ", und wählen Sie dann die **Dokument hochladen** Menüband auf die Schaltfläche zum Hochladen eines neuen Dokuments in der **Shared Documents** Liste.  
  
4.  In der **Dokument hochladen** Dialogfeld Wählen Sie die **Durchsuchen** Schaltfläche, wählen Sie eine Dokumentdatei, wählen Sie die **öffnen** aus, und klicken Sie dann die **OK** Schaltfläche.  
  
     Ändern Sie die Einstellungen für das Dokument in das Dialogfeld zu öffnen, aber lassen Sie sie auf den Standardwerten durch Auswählen der **speichern** Schaltfläche.  
  
5.  Wählen Sie das hochgeladene Dokument, wählen Sie den Dropdown-Pfeil, der angezeigt wird, und wählen Sie dann die **Workflows** Element.  
  
6.  Wählen Sie das Bild neben ExpenseReportWorkflow.  
  
     Dadurch werden das Workflow-Initiierung von Formular angezeigt. (Hinweis, der der Wert, in angezeigt der **automatisch Genehmigungsgrenzwert** Feld ist schreibgeschützt, da er in der Zuordnung Form eingegeben wurde.)  
  
7.  In der **Expense Total** Text geben **1600**, und wählen Sie dann die **Workflow starten** Schaltfläche.  
  
     Dadurch wird die **Shared Documents** erneut. Eine neue Spalte namens **ExpenseReportWorkflow** mit dem Wert **abgeschlossen** hinzugefügt wird, auf das Element, das der Workflow gerade gestartet.  
  
8.  Wählen Sie den Dropdownpfeil neben dem hochgeladenen Dokument, und wählen Sie dann die **Workflows** Element, um die Seite "Workflow-Status" anzuzeigen. Wählen Sie die **abgeschlossen** unter Wert **Workflows abgeschlossen**. Der Task wird aufgeführt, unter der **Aufgaben** Abschnitt.  
  
9. Wählen Sie den Titel des Tasks um Vorgang Details dafür anzuzeigen.  
  
10. Wechseln Sie zurück zu den **SharedDocuments** aus, und starten Sie den Workflow, der mithilfe des gleichen Dokuments oder einer anderen.  
  
11. Geben Sie eine Menge in der Einleitung-Seite, die kleiner oder gleich der Menge auf der Seite "Zuordnung" eingegeben wird (**1200**).  
  
     In diesem Fall wird ein Eintrag in der Verlaufsliste statt einer Aufgabe erstellt. Der Eintrag wird der **Workflowverlauf** Teil der Seite "Workflow-Status". Beachten Sie die Nachricht in die **Ergebnis** Spalte des Verlaufsereignisses. Es enthält den im eingegebenen Text die `logToHistoryListActivity1.MethodInvoking` Ereignis, das die Menge umfasst die automatisch genehmigt wurde.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Erfahren Sie mehr über das Erstellen von Workflow-Vorlagen in den folgenden Themen:  
  
-   Weitere Informationen zu SharePoint-Workflows finden Sie unter [Workflows in Windows SharePoint Services](http://go.microsoft.com/fwlink/?LinkID=166275).  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von SharePoint-Workflow-Projektmappen](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [Exemplarische Vorgehensweise: Hinzufügen einer Anwendungsseite zu einem Workflow](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)  
  
  