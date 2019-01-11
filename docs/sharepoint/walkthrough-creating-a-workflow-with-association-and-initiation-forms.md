---
title: 'Exemplarische Vorgehensweise: Erstellen eines Workflows mit Zuordnungs- und Initiierungsformularen | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
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
ms.openlocfilehash: c9878da7c1384dec8d0c8aa863b0eff4252e9efe
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53824735"
---
# <a name="walkthrough-create-a-workflow-with-association-and-initiation-forms"></a>Exemplarische Vorgehensweise: Erstellen eines Workflows mit Zuordnungs-und Initiierungsformularen
  In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie Sie einen grundlegenden sequenziellen Workflow erstellen, der die Verwendung von Zuordnungs-und Initiierungsformularen beinhaltet. Hierbei handelt es sich um ASPX-Formulare, mit denen Parameter für die zu einem Workflow hinzugefügt werden, wenn es zuerst von der SharePoint-Administrator (Zuordnungsformular) zugeordnet ist und der Workflow gestartet wird, durch den Benutzer (des Initiierungsformulars).  
  
 In dieser exemplarischen Vorgehensweise wird beschrieben, ein Szenario, in denen ein Benutzer möchte einen Genehmigungsworkflow für spesenabrechnungen erstellen, der folgenden Anforderungen erfüllt, werden:  
  
- Wenn der Workflow einer Liste zugeordnet ist, wird der Administrator ein Zuordnungsformular angezeigt, in dem sie eine Beschränkung der Gesamtbetrag in Dollar für Ausgabenberichte eingeben.  
  
- Mitarbeiter ihre spesenabrechnungen in der Liste Freigegebene Dokumente hochladen, starten Sie den Workflow und geben Sie dann die Kosten der Workflowinitiierungsformular insgesamt.  
  
- Wenn ein Mitarbeiter Ausgabenbericht insgesamt des Administrators vordefinierte Grenze überschreitet, wird eine Aufgabe für den Vorgesetzten des Mitarbeiters genehmigen die Spesenabrechnung erstellt. Jedoch ist ein Mitarbeiter Expense Report insgesamt kleiner als oder gleich dem Expense-Limit, eine Nachricht automatisch genehmigt, die Workflowverlaufsliste geschrieben wird.  
  
  In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
- Erstellen einer SharePoint Liste Definition sequenziellen Workflow-Projekts in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
- Erstellen einen Workflowzeitplan.  
  
- Behandeln von Ereignissen für Workflow-Aktivität.  
  
- Erstellen Workflows Zuordnungs-und Initiierungsformularen.  
  
- Zuordnen des Workflows.  
  
- Wird den Workflow manuell gestartet.  
  
> [!NOTE]  
>  Obwohl in dieser exemplarischen Vorgehensweise ein sequenzielles Workflowprojekt verwendet wird, ist der Prozess für der Zustandsautomatworkflows identisch.  
>   
>  Darüber hinaus kann auf Ihrem Computer angezeigt, andere Namen oder Speicherorte für die [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Elemente der Benutzeroberfläche in den folgenden Anweisungen. Die [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] -Version und die Einstellungen, die Sie verwenden, bestimmen diese Elemente. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   Unterstützte Editionen von [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] und SharePoint.  
  
-   Visual Studio.  
  
## <a name="create-a-sharepoint-sequential-workflow-project"></a>Erstellen Sie ein sequenzielles Workflowprojekt von SharePoint
 Erstellen Sie zunächst ein sequenzielles Workflowprojekt in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Ein sequenzieller Workflow ist eine Reihe von Schritten, die in der Reihenfolge ausgeführt wird, bis die letzte Aktivität abgeschlossen ist. In diesem Verfahren erstellen Sie einen sequenziellen Workflow, der für die Liste "Freigegebene Dokumente" in SharePoint gilt. Dem Workflow-Assistenten können Sie die Website oder die Listendefinition zuordnen des Workflows und ermöglicht Ihnen das bestimmen, wann der Workflow gestartet wird.  
  
#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>Erstellen Sie ein sequenzielles Workflowprojekt von SharePoint  
  
1.  Wählen Sie auf der Menüleiste **Datei** > **neu** > **Projekt** zum Anzeigen der **neues Projekt** Dialogfeld.  
  
2.  Erweitern Sie die **SharePoint** Knoten entweder **Visual C#-** oder **Visual Basic**, und wählen Sie dann die **2010** Knoten.  
  
3.  In der **Vorlagen** Bereich, wählen Sie die **SharePoint 2010-Projekt** Projektvorlage.  
  
4.  In der **Namen** geben **ExpenseReport** und wählen Sie dann die **OK** Schaltfläche.  
  
     Die **SharePoint Customization Wizard** angezeigt wird.  
  
5.  In der **Geben Sie die Website und Sicherheitsebene für debugging** Seite die **als farmlösung bereitstellen** Optionsfeld aus, und wählen Sie dann die **Fertig stellen** Schaltfläche zum Akzeptieren der Trust-Ebene und Standard-Website.  
  
     In diesem Schritt wird auch die Vertrauensebene für die Lösung als Farm-Lösung, die die einzige verfügbare Option für Workflowprojekte ist.  
  
6.  Wählen Sie im **Projektmappen-Explorer**den Projektknoten aus.  
  
7.  Wählen Sie in der Menüleiste **Projekt** > **Neues Element hinzufügen** aus.  
  
8.  Entweder unter **Visual C#-** oder **Visual Basic**, erweitern Sie die **SharePoint** Knoten, und wählen Sie dann die **2010** Knoten.  
  
9. In der **Vorlagen** Bereich wählen **sequenzieller Workflow (nur Farmlösung)** Vorlage, und wählen Sie dann die **hinzufügen** Schaltfläche.  
  
     Die **SharePoint Customization Wizard** angezeigt wird.  
  
10. In der **Geben Sie den Workflownamen für das Debuggen** Seite aus, übernehmen Sie den Standardnamen (**ExpenseReport - Workflow1**). Beibehalten des Standardwerts Workflow Vorlage Typ (**Listenworkflow)**. Klicken Sie auf **Weiter**.  
  
11. In der **möchten Sie Visual Studio, um den Workflow in einer Debugsitzung automatisch zuordnen?** Seite, deaktivieren Sie das Kontrollkästchen, die automatisch Ihrer Workflowvorlage zuordnet, wenn diese Option aktiviert ist.  
  
     Dadurch können Sie manuell auf den Workflow in der Liste Freigegebene Dokumente später zuordnen Zuordnungsformular angezeigt.  
  
12. Wählen Sie die **Fertig stellen** Schaltfläche.  
  
## <a name="add-an-association-form-to-the-workflow"></a>Fügen Sie ein Zuordnungsformular an den Workflow hinzu.
 Als Nächstes erstellen Sie ein. Aspx-Zuordnung-Formular, das angezeigt wird, wenn der SharePoint-Administrator zunächst den Workflow ein Dokument für den ausgabenbeispielbericht zuordnet.  
  
#### <a name="to-add-an-association-form-to-the-workflow"></a>Der Workflow ein Zuordnungsformular hinzu  
  
1.  Wählen Sie die **Workflow1** Knoten **Projektmappen-Explorer**.  
  
2.  Wählen Sie auf der Menüleiste **Projekt** > **neues Element hinzufügen** zum Anzeigen der **neues Element hinzufügen** Dialogfeld.  
  
3.  Erweitern Sie in der Strukturansicht des Dialogfelds, entweder **Visual C#-** oder **Visual Basic** (abhängig von der Projektsprache), erweitern Sie die **SharePoint** Knoten, und wählen Sie dann die **2010** Knoten.  
  
4.  Wählen Sie in der Liste der Vorlagen, die **Workflowzuordnungsformular** Vorlage.  
  
5.  In der **Namen** Text geben **ExpenseReportAssocForm.aspx**.  
  
6.  Wählen Sie die **hinzufügen** , um das Formular zum Projekt hinzuzufügen.  
  
## <a name="designing-and-coding-the-association-form"></a>Entwerfen und Programmieren von Zuordnungsformular
 In diesem Verfahren führen Sie die Funktionalität auf das Zuordnungsformular durch Hinzufügen von Steuerelementen und Code darauf.  
  
#### <a name="to-design-and-code-the-association-form"></a>Entwerfen und Programmieren Zuordnungsformular  
  
1.  Suchen Sie in der Form der Zuordnung (ExpenseReportAssocForm.aspx), die `asp:Content` Element mit `ID="Main"`.  
  
2.  Fügen Sie direkt nach der ersten Zeile im Content-Element, den folgenden Code zum Erstellen einer Bezeichnung und der Textbox, der für die Ausgaben genehmigungsgrenzwert auffordert (*AutoApproveLimit*):  
  
    ```aspx-csharp  
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />  
  
    <asp:TextBox ID="AutoApproveLimit" runat="server" />  
    <br /><br />  
    ```  
  
3.  Erweitern Sie die **ExpenseReportAssocForm.aspx** Datei **Projektmappen-Explorer** seinen abhängigen Dateien angezeigt.  
  
    > [!NOTE]  
    >  Wenn Ihr Projekt in [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)], müssen Sie auswählen, die **alle Dateien anzeigen** Schaltfläche, um diesen Schritt auszuführen.  
  
4.  Öffnen Sie das Kontextmenü für die ExpenseReportAssocForm.aspx-Datei, und wählen **Ansichtscode**.  
  
5.  Ersetzen Sie die `GetAssociationData` -Methode mit:  
  
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
  
## <a name="add-an-initiation-form-to-the-workflow"></a>Fügen Sie ein Initiierungsformular an den Workflow hinzu.
 Erstellen Sie als Nächstes des Initiierungsformulars, die angezeigt wird, wenn Benutzer den Workflow für die spesenabrechnungen ausgeführt.  
  
#### <a name="to-create-an-initiation-form"></a>Erstellen Sie ein Initiierungsformular  
  
1.  Wählen Sie die **Workflow1** Knoten **Projektmappen-Explorer**.  
  
2.  Wählen Sie auf der Menüleiste **Projekt** > **neues Element hinzufügen** Anzeigen der **neues Element hinzufügen** Dialogfeld.  
  
3.  Erweitern Sie in der Strukturansicht des Dialogfelds, entweder **Visual C#-** oder **Visual Basic** (abhängig von der Projektsprache), erweitern Sie die **SharePoint** Knoten, und wählen Sie dann die **2010** Knoten.  
  
4.  Wählen Sie in der Liste der Vorlagen, die **Workflowinitiierungsformular** Vorlage.  
  
5.  In der **Namen** Text geben **ExpenseReportInitForm.aspx**.  
  
6.  Wählen Sie die **hinzufügen** , um das Formular zum Projekt hinzuzufügen.  
  
## <a name="designing-and-coding-the-initiation-form"></a>Entwerfen und Programmieren des Initiierungsformulars
 Führen Sie als Nächstes Funktionen des Initiierungsformulars durch Hinzufügen von Steuerelementen und Code darauf.  
  
#### <a name="to-code-the-initiation-form"></a>Code des Initiierungsformulars  
  
1.  Suchen Sie im des Initiierungsformulars (ExpenseReportInitForm.aspx), die `asp:Content` -Element mit `ID="Main"`.  
  
2.  Direkt nach der ersten Zeile in diesem Inhaltselement, fügen Sie folgenden Code zum Erstellen einer Bezeichnung und ein Textfeld, das die Ausgaben genehmigungsgrenzwert anzeigt (*AutoApproveLimit*), die in das Zuordnungsformular und eine andere Bezeichnung eingegeben wurde und Textfeld für den gesamten Aufwand aufgefordert (*ExpenseTotal*):  
  
    ```aspx-csharp  
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />  
  
    <asp:TextBox ID="AutoApproveLimit" ReadOnly="true" runat="server" />  
    <br /><br />  
    <asp:Label ID="lblExpenseTotal" Text="Expense Total:" runat="server" />  
  
    <asp:TextBox ID="ExpenseTotal" runat="server" />  
    <br /><br />  
    ```  
  
3.  Erweitern Sie die **ExpenseReportInitForm.aspx** Datei **Projektmappen-Explorer** seinen abhängigen Dateien angezeigt.  
  
4.  Öffnen Sie das Kontextmenü für die ExpenseReportInitForm.aspx-Datei, und wählen **Ansichtscode**.  
  
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
  
## <a name="cutomize-the-workflow"></a>Anpassen des Workflows
 Als Nächstes den Workflow anpassen. Später ordnen Sie zwei Formen an den Workflow.  
  
#### <a name="to-customize-the-workflow"></a>Um den Workflow anpassen  
  
1.  Zeigen Sie den Workflow im Workflow-Designer, öffnen Sie Workflow1 in das Projekt.  
  
2.  In der **Toolbox**, erweitern Sie die **Windows Workflow v3. 0** Knoten, und suchen Sie die **IfElse** Aktivität.  
  
3.  Fügen Sie diese Aktivität an den Workflow, indem Sie eine der folgenden Schritte ausführen:  
  
    -   Öffnen Sie das Kontextmenü für die **IfElse** -Aktivität, wählen Sie **Kopie**, öffnen Sie das Kontextmenü für die Zeile unter der **onWorkflowActivated1** Aktivität im Workflow-Designer und wählen Sie dann **einfügen**.  
  
    -   Ziehen Sie die **IfElse** Aktivität aus der **Toolbox**, und verbinden Sie es mit der Zeile unter der **onWorkflowActiviated1** Aktivität im Workflow-Designer.  
  
4.  Erweitern Sie in der Toolbox die **SharePoint-Workflow** Knoten, und suchen Sie die **CreateTask** Aktivität.  
  
5.  Fügen Sie diese Aktivität an den Workflow, indem Sie eine der folgenden Schritte ausführen:  
  
    -   Öffnen Sie das Kontextmenü für die **CreateTask** -Aktivität, wählen Sie **Kopie**, öffnen Sie das Kontextmenü für einen der beiden **Aktivitäten hier ablegen** Bereichen in  **IfElseActivity1-Aktivität ziehen** im Workflow-Designer, und wählen Sie dann **einfügen**.  
  
    -   Ziehen Sie die **CreateTask** Aktivität aus der **Toolbox** auf einem der beiden **Aktivitäten hier ablegen** Bereichen in **IfElseActivity1-Aktivität ziehen**.  
  
6.  In der **Eigenschaften** Fenster, geben Sie den Eigenschaftswert einer *TaskToken* für die **"CorrelationToken"** Eigenschaft.  
  
7.  Erweitern Sie die **"CorrelationToken"** Eigenschaft, indem Sie das Pluszeichen auswählen (![TreeView-plus](../sharepoint/media/plus.gif "TreeView-plus")) daneben.  
  
8.  Wählen Sie auf den Dropdown-Pfeil der **OwnerActivityName** sub-Eigenschaft, und legen Sie die *Workflow1* Wert.  
  
9. Wählen Sie die **"TaskID"** -Eigenschaft, und klicken Sie dann auf die Auslassungspunkte (![ASP.NET Mobile-Designer Ellipse](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile-Designer Ellipse")) Schaltfläche zum Anzeigen der **Eigenschaft binden** Dialogfeld.  
  
10. Wählen Sie die **Binden an einen neuen Member** Registerkarte die **Feld erstellen** Optionsfeld aus, und wählen Sie dann die **OK** Schaltfläche.  
  
11. Wählen Sie die **"taskproperties"** -Eigenschaft, und klicken Sie dann auf die Auslassungspunkte (![ASP.NET Mobile-Designer Ellipse](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile-Designer Ellipse")) Schaltfläche, um die anzeigen **Eigenschaft binden** Dialogfeld.  
  
12. Wählen Sie die **Binden an einen neuen Member** Registerkarte die **Feld erstellen** Optionsfeld aus, und wählen Sie dann die **OK** Schaltfläche.  
  
13. In der **Toolbox**, erweitern Sie die **SharePoint-Workflow** Knoten, und suchen Sie nach der **LogToHistoryListActivity** Aktivität.  
  
14. Fügen Sie diese Aktivität an den Workflow, indem Sie eine der folgenden Schritte ausführen:  
  
    -   Öffnen Sie das Kontextmenü für die **LogToHistoryListActivity** Aktivität auswählen **Kopie**, öffnen Sie das Kontextmenü für die anderen **Aktivitäten hier ablegen** Bereich im **IfElseActivity1-Aktivität ziehen** im Workflow-Designer, und wählen Sie dann **einfügen**.  
  
    -   Ziehen Sie die **LogToHistoryListActivity** Aktivität aus der **Toolbox**, und legen Sie es auf die andere **Aktivitäten hier ablegen** Bereich im **IfElseActivity1-Aktivität ziehen** .  
  
## <a name="add-code-to-the-workflow"></a>Fügen Sie Code für den Workflow hinzu.
 Als Nächstes fügen Sie Code zum Workflow, um es mit Funktionen auszustatten.  
  
#### <a name="to-add-code-to-the-workflow"></a>Hinzufügen von Code für den workflow  
  
1.  Öffnen Sie das Kontextmenü für die **createTask1** Aktivität im Workflow-Designer, und wählen Sie dann **Ansichtscode**.  
  
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
    >  Ersetzen Sie im Code, `somedomain\\someuser` mit einer Domäne und den Namen, die für die eine Aufgabe, z. B. erstellt werden "`Office\\JoeSch`". Zu Testzwecken ist es am einfachsten, das Konto zu verwenden, die für die Entwicklung verwendet werden.  
  
3.  Unterhalb der `MethodInvoking` -Methode, fügen Sie im folgenden Beispiel hinzu:  
  
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
  
5.  In der **Eigenschaften** Fenster Wählen Sie den Dropdown-Pfeil, der die **Bedingung** -Eigenschaft, und legen die *Codebedingung* Wert.  
  
6.  Erweitern Sie die **Bedingung** Eigenschaft, indem Sie das Pluszeichen auswählen (![TreeView-plus](../sharepoint/media/plus.gif "TreeView-plus")) angezeigt wird, und legen Sie dessen Wert auf *CheckApprovalNeeded* .  
  
7.  Im Workflow-Designer, öffnen Sie das Kontextmenü für die **logToHistoryListActivity1** -Aktivität, und wählen Sie dann **Handler generieren** generieren Sie eine leere Methode für die `MethodInvoking` Ereignis.  
  
8.  Ersetzen Sie die `MethodInvoking` Code durch Folgendes:  
  
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
  
9. Wählen Sie die **F5** -Taste, um das Programm zu debuggen.  
  
     Dies wird die Anwendung kompiliert, gepackt, bereitgestellt, die Funktionen werden aktiviert, wiederverwendet wird die [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] Anwendungspool, und klicken Sie dann gestartet, die der Browser an der Position angegeben wird, in der **Website-Url** Eigenschaft.  
  
## <a name="associating-the-workflow-to-the-documents-list"></a>Zuordnen des Workflows zur Dokumentliste
 Zeigen Sie dann die Workflowzuordnungsformular durch Zuordnen des Workflows mit der **SharedDocuments** Liste auf der SharePoint-Website.  
  
#### <a name="to-associate-the-workflow"></a>Den Workflow zuordnen  
  
1.  Wählen Sie die **freigegebene Dokumente** Link auf der Schnellstartleiste.  
  
2.  Wählen Sie die **Bibliothek** auf einen link auf die **Bibliothekstools** Registerkarte, und wählen Sie dann die **Bibliothekseinstellungen** Schaltfläche des Menübands.  
  
3.  In der **Berechtigungen und Verwaltung** Abschnitt der **Workfloweinstellungen** verknüpfen, und wählen Sie dann die **fügen Sie einen Workflow** auf einen link auf die **Workflows** Seite.  
  
4.  Wählen Sie in der oberen Liste auf der Einstellungsseite für den Workflow der **ExpenseReport - Workflow1** Vorlage.  
  
5.  Geben Sie im nächsten Feld **ExpenseReportWorkflow** und wählen Sie dann die **Weiter** Schaltfläche.  
  
     Dadurch wird den Workflow mit dem verknüpft die **freigegebene Dokumente** aus und zeigt die Workflowzuordnungsformular.  
  
6.  In der **automatisch Genehmigungsgrenzwert** Text geben **1200** und wählen Sie dann die **Workflow zuordnen** Schaltfläche.  
  
## <a name="start-the-workflow"></a>Starten Sie den workflow
 Als Nächstes ordnen Sie den Workflow zu einem der Dokumente in der **freigegebene Dokumente** Liste, um das Workflowinitiierungsformular anzuzeigen.  
  
#### <a name="to-start-the-workflow"></a>Zum Starten des Workflows  
  
1.  Wählen Sie auf der SharePoint-Seite, die **Startseite** Schaltfläche.  
  
2.  Wählen Sie die **freigegebene Dokumente** Link auf der Schnellstartleiste zum Anzeigen der **freigegebene Dokumente** Liste.  
  
3.  Wählen Sie die **Dokumente** auf einen link auf die **Bibliothekstools** Registerkarte am oberen Rand der Seite, und wählen Sie dann die **Dokument hochladen** Menüband auf die Schaltfläche zum Hochladen eines neuen Dokuments in der **Freigegebene Dokumente** Liste.  
  
4.  In der **Dokument hochladen** Dialogfeld wählen die **Durchsuchen** Schaltfläche eine Dokumentdatei aus, wählen Sie die **öffnen** Schaltfläche, und wählen Sie dann die **OK** Schaltfläche.  
  
     Ändern Sie die Einstellungen für das Dokument in das Dialogfeld zu öffnen, aber behalten sie die Standardwerte durch Auswählen der **speichern** Schaltfläche.  
  
5.  Wählen Sie das hochgeladene Dokument aus, wählen Sie den Dropdown-Pfeil, der angezeigt wird, und wählen Sie dann die **Workflows** Element.  
  
6.  Wählen Sie das Image neben ExpenseReportWorkflow.  
  
     Dadurch werden die Workflowinitiierungsformular angezeigt. (Beachten Sie, die der Wert, in angezeigt der **Genehmigungsgrenzwert automatisch** Feld ist schreibgeschützt, da er in der Zuordnung Form eingegeben wurde.)  
  
7.  In der **Expense Total** Text geben **1600**, und wählen Sie dann die **Workflow starten** Schaltfläche.  
  
     Dies zeigt die **freigegebene Dokumente** erneut auflisten. Eine neue Spalte namens **ExpenseReportWorkflow** mit dem Wert **abgeschlossen** auf das Element, das der Workflow nur gestartet wurde.  
  
8.  Wählen Sie den Dropdown-Pfeil neben dem hochgeladenen Dokument, und wählen Sie dann die **Workflows** Element, um die Statusseite für den Workflow anzuzeigen. Wählen Sie die **abgeschlossen** Wert **Workflows abgeschlossen**. Der Task wird aufgeführt, unter dem **Aufgaben** Abschnitt.  
  
9. Wählen Sie den Titel der Aufgabe, um die Aufgabendetails anzuzeigen.  
  
10. Wechseln Sie zurück zu den **SharedDocuments** aus, und starten Sie den Workflow mithilfe des gleichen Dokuments oder einem anderen Konto neu.  
  
11. Geben Sie eine Menge in der Einleitung-Seite, die kleiner oder gleich der Menge auf der Seite "Zuordnung" eingegeben wird (**1200**).  
  
     In diesem Fall wird ein Eintrag in der Verlaufsliste anstelle eines Task erstellt. Der Eintrag wird im der **Workflowverlauf** der Workflow-Status-Seite. Beachten Sie die Nachricht in die **Ergebnis** Spalte des Verlaufsereignisses. Sie enthält die in eingegebenen Text die `logToHistoryListActivity1.MethodInvoking` -Ereignis, das die Menge enthält, das automatisch genehmigt wurde.  
  
## <a name="next-steps"></a>Nächste Schritte
 Erfahren Sie mehr über das Erstellen von Workflows in den folgenden Themen:  
  
-   Weitere Informationen zu SharePoint-Workflows finden Sie unter [Workflows in Windows SharePoint Services](http://go.microsoft.com/fwlink/?LinkID=166275).  
  
## <a name="see-also"></a>Siehe auch
 [Erstellen von SharePoint-Workflow-Projektmappen](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [Exemplarische Vorgehensweise: Hinzufügen einer Anwendungsseite zu einem workflow](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)  
