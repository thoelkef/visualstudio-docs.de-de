---
title: "Exemplarische Vorgehensweise: Erstellen und Debuggen einer SharePoint-Workflow-Projektmappe | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.Workflow.WorkflowConditions"
  - "VS.SharePointTools.Workflow.WorkflowList"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SharePoint-Entwicklung in Visual Studio, Workflows"
  - "Workflows [SharePoint-Entwicklung in Visual Studio]"
ms.assetid: 81756490-ab5a-4fa4-96c6-eed2cfbf8374
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# Exemplarische Vorgehensweise: Erstellen und Debuggen einer SharePoint-Workflow-Projektmappe
  In dieser exemplarischen Vorgehensweise wird gezeigt, wie eine grundlegende sequenzielle Workflowvorlage erstellt wird.  Der Workflow überprüft eine Eigenschaft einer freigegebenen Dokumentbibliothek, um zu bestimmen, ob ein Dokument überprüft wurde.  Nach dem Prüfen des Dokuments wird der Workflow fertig gestellt.  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Erstellen eines sequenziellen Workflowprojekts vom Typ SharePoint\-Listendefinition in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
-   Erstellen von Workflowaktivitäten.  
  
-   Behandeln von Workflowaktivitätsereignissen.  
  
> [!NOTE]  
>  Obwohl in dieser exemplarischen Vorgehensweise ein sequenzielles Workflowprojekt verwendet wird, ist der Prozess für ein Projekt vom Typ Zustandsautomatworkflow identisch.  
>   
>  Auf Ihrem Computer werden möglicherweise auch andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten.  Die Elemente werden durch die verwendete Edition von Visual Studio und die gewählten Einstellungen bestimmt.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   Unterstützte Editionen von Microsoft Windows und SharePoint.  Weitere Informationen finden Sie unter [Anforderungen für die Entwicklung von SharePoint-Lösungen](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
## Hinzufügen von Eigenschaften zur freigegebenen SharePoint\-Dokumentbibliothek  
 Um den Prüfstatus von Dokumenten in der Bibliothek **Freigegebene Dokumente** nachzuverfolgen, werden drei neue Eigenschaften für freigegebene Dokumente auf der SharePoint\-Website erstellt: `Status`, `Assignee` und `Review Comments`.  Diese Eigenschaften werden in der Bibliothek **Freigegebene Dokumente** definiert.  
  
#### So fügen Sie der freigegebenen SharePoint\-Dokumentbibliothek Eigenschaften hinzu  
  
1.  Öffnen Sie eine SharePoint\-Website, z http:\/\/system\-\<Name\>\/SitePages\/Home.aspx, in einem Webbrowser.  
  
2.  Klicken Sie auf der Schnellstartleiste wählen Sie **DokumenteFreigegeben** aus.  
  
3.  Wählen Sie auf dem Menüband **BibliothekstoolsBibliothek** aus und dann die Schaltfläche **Erstellen einer neuen Website** auf dem Menüband, um eine neue Spalte zu erstellen.  
  
4.  Geben Sie für die Spalte den Namen "Document Status" ein, legen Sie den Typ auf **Auswahl \(Menü\)** fest, geben Sie die folgenden drei Optionen an, und wählen Sie dann die Schaltfläche **OK** aus:  
  
    -   **Review Needed**  
  
    -   **Review Complete**  
  
    -   **Changes Requested**  
  
5.  Erstellen Sie zwei zusätzliche Spalten, und nennen Sie diese Assignee und Review Comments.  Legen Sie den Spaltentyp Assignee als einzelne Textzeile und den Spaltentyp Review Comments als aus mehreren Zeilen bestehenden Text fest.  
  
## Bearbeiten von Dokumenten ohne Auschecken  
 Es ist einfacher, die Workflowvorlage zu testen, wenn die Dokumente ohne Auschecken bearbeitet werden können.  Im nächsten Verfahren konfigurieren Sie die SharePoint\-Website, um dies zu ermöglichen.  
  
#### So können Dokumente ohne Auschecken bearbeitet werden  
  
1.  Klicken Sie auf der Schnellstartleiste auf den Link **Freigegebene Dokumente** aus.  
  
2.  Klicken Sie im Menüband **Bibliothekstools** wählen Sie die Registerkarte **Bibliothek** aus, und wählen Sie die Schaltfläche **Bibliothekeinstellungen**, um die Seite **Einstellungen Dokumentbibliothek** anzuzeigen.  
  
3.  Im Abschnitt **Allgemeine Einstellungen** wählen Sie den Link **Versionierungseinstellungen**, um die Seite **Versionierungseinstellungen** anzuzeigen.  
  
4.  Vergewissern Sie sich, dass **Auschecken von Dokumenten erfordern, bevor sie bearbeitet werden können** auf **Nein** festgelegt ist.  Wenn nicht, ändern Sie diese in **Nein** und die Schaltfläche anschließend **OK** aus.  
  
5.  Schließen Sie den Browser.  
  
## Erstellen eines sequenziellen Workflowprojekts für SharePoint.  
 Ein sequenzieller Workflow ist ein Satz von Schritten, die der Reihe nach ausgeführt werden, bis die letzte Aktivität fertig gestellt wurde.  In diesem Verfahren wird ein sequenzieller Workflow erstellt, der für die Liste Freigegebene Dokumente gilt.  Mit dem Workflow\-Assistenten können Sie den Workflow entweder der Websitedefinition oder der Listendefinition zuordnen und bestimmen, wann der Workflow starten soll.  
  
#### So erstellen Sie ein sequenzielles Workflowprojekt für SharePoint:  
  
1.  Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Klicken Sie auf der Menüleiste **Neu**, **Projekt**, **Datei**, um das Dialogfeld **Neues Projekt** anzuzeigen.  
  
3.  Erweitern Sie den Knoten **SharePoint** entweder unter **Visual C\#** oder **Visual Basic**, und wählen Sie den Knoten **2010** aus.  
  
4.  Im Bereich **Vorlagen** wählen Sie die Vorlage **SharePoint 2010\-Projekt** aus.  
  
5.  Im Feld **Name** geben Sie MySharePointWorkflow ein und wählen Sie dann die Schaltfläche **OK** aus.  
  
     Der **Assistent zum Anpassen von SharePoint** wird angezeigt.  
  
6.  Auf der Seite **Site und Sicherheitsebene für Debugging angeben** wählen Sie das Optionsfeld **Als Farmlösung bereitstellen** aus, und wählen Sie die Schaltfläche **Fertig stellen**, um die Vertrauensebenen\- und Standardsite zu übernehmen.  
  
     In diesem Schritt wird die Vertrauensebene für die Lösung als Farmlösung festgelegt, wobei es sich um die einzige verfügbare Option für Workflowprojekte handelt.  Weitere Informationen finden Sie unter [Überlegungen zu Sandkastenlösungen](../sharepoint/sandboxed-solution-considerations.md).  
  
7.  Wählen Sie im **Projektmappen\-Explorer** den Projektknoten, und klicken Sie auf der Menüleiste, **Projekt** auswählen, **Neues Element hinzufügen** aus.  
  
8.  Entweder unter **Visual C\#** oder den Knoten **Visual BasicSharePoint**, und wählen Sie den Knoten **2010** aus.  
  
9. Im Bereich **Vorlagen** wählen Sie die Vorlage **Sequenzieller Workflow \(nur Farmlösung\)** aus, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.  
  
     Der **Assistent zum Anpassen von SharePoint** wird angezeigt.  
  
10. Akzeptieren Sie auf der Seite **Workflownamen für das Debugging angeben** den Standardnamen \(**MySharePointWorkflow \- Workflow1**\).  Übernehmen Sie den Standardwert für den Workflowvorlagentyp, **Listenworkflow**, und wählen Sie die Schaltfläche **Weiter** aus.  
  
11. Auf der Seite **Soll Visual Studio den Workflow in einer Debugsitzung automatisch zuordnen?** wählen Sie die Schaltfläche **Weiter**, um die Standardeinstellungen zu übernehmen.  
  
     In diesem Schritt wird der Workflow automatisch der Bibliothek freigegebener Dokumente zugeordnet.  
  
12. Auf der Seite **Bedingungen zum Starten des Workflows angeben** lassen Sie die Standardoptionen ausgewählt im Abschnitt **Wie soll der Workflow gestartet werden?** und wählen Sie die Schaltfläche **Fertig stellen** aus.  
  
     Auf dieser Seite können Sie angeben, wann der Workflow gestartet wird.  Standardmäßig wird der Workflow gestartet, wenn ein Benutzer den Workflow in SharePoint manuell startet oder wenn ein Element erstellt wird, das dem Workflow zugeordnet ist.  
  
## Erstellen von Workflowaktivitäten  
 Workflows enthalten eine oder mehrere *Aktivitäten*, die auszuführende Aktionen darstellen.  Ordnen Sie mit dem Workflow\-Designer Aktivitäten für einen Workflow an.  In diesem Verfahren werden dem Workflow zwei Aktivitäten hinzugefügt: HandleExternalEventActivity und OnWorkFlowItemChanged.  Diese Aktivitäten überwachen den Prüfstatus von Dokumenten in der Liste **Freigegebene Dokumente**.  
  
#### So erstellen Sie Workflowaktivitäten  
  
1.  Der Workflow sollte im Workflow\-Designer angezeigt werden.  Andernfalls ist, öffnen Sie **Workflow1.cs** oder **Workflow1.vb** in **Projektmappen\-Explorer**.  
  
2.  Wählen Sie im Designer die Aktivität **OnWorkflowActivated1** aus.  
  
3.  Im Fenster **Eigenschaften**  onWorkflowActivated geben Sie neben der Eigenschaft **Invoked** ein, und wählen Sie dann die EINGABETASTE aus.  
  
     Der Code\-Editor wird geöffnet, und eine Ereignishandlermethode mit der Bezeichnung onWorkflowActivated wird der Workflow1\-Codedatei hinzugefügt.  
  
4.  Wechseln Sie wieder zum Workflow\-Designer, öffnen Sie die Toolbox, und erweitern Sie dann den Knoten **Windows Workflow v3.0**.  
  
5.  Im Knoten **Windows Workflow v3.0Werkzeugkasten**, führen Sie einen der folgenden Schritte aus:  
  
    1.  Öffnen Sie das Kontextmenü für **While** die Aktivität, und wählen Sie dann **Kopieren** aus.  im Workflow\-Designer öffnen Sie das Kontextmenü für die Zeile unter der Aktivität **onWorkflowActivated1**, und wählen Sie dann **Einfügen** aus.  
  
    2.  Ziehen Sie die Aktivität **While** von **Werkzeugkasten** zum Workflow\-Designer, und schließen Sie die Aktivität an die Zeile unter der Aktivität **onWorkflowActivated1** angezeigt.  
  
6.  Wählen Sie die Aktivität **WhileActivity1** aus.  
  
7.  Im Fenster **EigenschaftenBedingung** festgelegt, auf Code.  
  
8.  Erweitern Sie die Eigenschaft **Bedingung**, den isWorkflowPending neben der untergeordneten Eigenschaft **Bedingung** ein, und wählen Sie dann die EINGABETASTE aus.  
  
     Der Code\-Editor wird geöffnet, und eine Methode mit dem Namen isWorkflowPending wird der Workflow1\-Codedatei hinzugefügt.  
  
9. Wechseln Sie wieder zum Workflow\-Designer, öffnen Sie die Toolbox, und erweitern Sie dann den Knoten **SharePoint Workflow**.  
  
10. Im Knoten **SharePoint WorkflowWerkzeugkasten**, führen Sie einen der folgenden Schritte aus:  
  
    -   Öffnen Sie das Kontextmenü für **OnWorkflowItemChanged** die Aktivität, und wählen Sie dann **Kopieren** aus.  im Workflow\-Designer öffnen Sie das Kontextmenü für die Zeile innerhalb der Aktivität **whileActivity1**, und wählen Sie dann **Einfügen** aus.  
  
    -   Ziehen Sie die Aktivität **OnWorkflowItemChanged** von **Werkzeugkasten** zum Workflow\-Designer, und schließen Sie die Aktivität an der Zeile innerhalb der Aktivität **whileActivity1** angezeigt.  
  
11. Wählen Sie die Aktivität **onWorkflowItemChanged1** aus.  
  
12. Legen Sie im Fenster **Eigenschaften** die Eigenschaften entsprechend der Anzeige in der folgenden Tabelle fest.  
  
    |Eigenschaft|Wert|  
    |-----------------|----------|  
    |**CorrelationToken**|**workflowToken**|  
    |**Invoked**|**onWorkflowItemChanged**|  
  
## Behandeln von Aktivitätsereignissen  
 Überprüfen Sie abschließend den Status des Dokuments jeder Aktivität.  Wenn das Dokument geprüft wurde, ist der Workflow fertig gestellt.  
  
#### So behandeln Sie Aktivitätsereignisse:  
  
1.  Fügen Sie in Workflow1.cs oder Workflow1.vb das folgende Feld am Anfang der `Workflow1`\-Klasse hinzu.  Dieses Feld wird in einer Aktivität verwendet, um zu bestimmen, ob der Workflow abgeschlossen wurde.  
  
    ```vb  
    Dim workflowPending As Boolean = True  
    ```  
  
    ```csharp  
    Boolean workflowPending = true;  
    ```  
  
2.  Fügen Sie der `Workflow1`\-Klasse die folgende Methode hinzu.  Mit dieser Methode wird der Wert der Eigenschaft `Document Status` der Dokumentliste überprüft, um zu bestimmen, ob das Dokument überprüft wurde.  Wurde die Eigenschaft `Document Status` auf `Review Complete` festgelegt, wird das `workflowPending`\-Feld mit der `checkStatus`\-Methode auf **false** festgelegt, um anzugeben, dass der Workflow beendet werden kann.  
  
    ```vb  
    Private Sub checkStatus()  
        If CStr(workflowProperties.Item("Document Status")) = "Review Complete" Then  
            workflowPending = False  
        End If  
    End Sub   
    ```  
  
    ```csharp  
    private void checkStatus()  
    {  
        if ((string)workflowProperties.Item["Document Status"] == "Review Complete")  
        workflowPending = false;  
    }  
    ```  
  
3.  Fügen Sie den folgenden Code der `onWorkflowActivated`\-Methode und der `onWorkflowItemChanged`\-Methode hinzu, um die `checkStatus`\-Methode aufzurufen.  Beim Start des Workflows wird mit der `onWorkflowActivated`\-Methode die `checkStatus`\-Methode aufgerufen, um zu bestimmen, ob das Dokument bereits überprüft wurde.  Wurde der Workflow noch nicht überprüft, wird der Workflow fortgesetzt.  Beim Speichern des Dokuments wird mit der `onWorkflowItemChanged`\-Methode erneut die `checkStatus`\-Methode aufgerufen, um zu bestimmen, ob das Dokument überprüft wurde.  Während das `workflowPending`\-Feld auf **true** festgelegt ist, wird die Ausführung des Workflows fortgesetzt.  
  
    ```vb  
    Private Sub onWorkflowActivated(ByVal sender As System.Object, ByVal e As System.Workflow.Activities.ExternalDataEventArgs)  
        checkStatus()  
    End Sub  
  
    Private Sub onWorkflowItemChanged(ByVal sender As System.Object, ByVal e As System.Workflow.Activities.ExternalDataEventArgs)  
        checkStatus()  
    End Sub  
    ```  
  
    ```csharp  
    private void onWorkflowActivated(object sender, ExternalDataEventArgs e)  
    {  
        // Check the status.  
        checkStatus();  
    }  
  
    private void onWorkflowItemChanged(object sender, ExternalDataEventArgs e)  
    {  
        // Check the status.  
        checkStatus();  
    }  
    ```  
  
4.  Fügen Sie der `isWorkflowPending`\-Methode den folgenden Code hinzu, um den Status der `workflowPending`\-Eigenschaft zu überprüfen.  Bei jedem Speichern des Dokuments wird mit der **whileActivity1**\-Aktivität die `isWorkflowPending`\-Methode aufgerufen.  Mit dieser Methode wird die <xref:System.Workflow.Activities.ConditionalEventArgs.Result%2A>\-Eigenschaft des <xref:System.Workflow.Activities.ConditionalEventArgs>\-Objekts überprüft, um zu bestimmen, ob die **WhileActivity1**\-Aktivität fortgesetzt oder beendet werden soll.  Wurde die Eigenschaft auf **true** festgelegt, wird die Aktivität fortgesetzt.  Andernfalls werden die Aktivität und der Workflow beendet.  
  
    ```vb  
    Private Sub isWorkflowPending(ByVal sender As System.Object, ByVal e As System.Workflow.Activities.ConditionalEventArgs)  
        e.Result = workflowPending  
    End Sub  
    ```  
  
    ```csharp  
    private void isWorkflowPending(object sender, ConditionalEventArgs e)  
    {  
        e.Result = workflowPending;  
    }  
    ```  
  
5.  Speichern Sie das Projekt.  
  
## Testen der SharePoint\-Workflowvorlage  
 Beim Starten des Debuggers stellt [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] die Workflowvorlage für den SharePoint\-Server bereit und ordnet den Workflow der Liste **Freigegebene Dokumente** zu.  Starten Sie zum Testen des Workflows eine Instanz des Workflows von einem Dokument in der Liste **Freigegebene Dokumente**.  
  
#### So testen Sie die SharePoint\-Workflowvorlage:  
  
1.  Legen Sie in Workflow1.cs oder Workflow1.vb neben der **onWorkflowActivated**\-Methode einen Haltepunkt fest.  
  
2.  Drücken Sie die F5\-TASTE, um die Projektmappe zu erstellen und auszuführen.  
  
     Die SharePoint\-Website wird angezeigt.  
  
3.  im Navigationsbereich in SharePoint, wählen Sie den Link **Freigegebene Dokumente** aus.  
  
4.  Auf der Seite **Freigegebene Dokumente** Wählen Sie den Link **Dokumente** auf der Registerkarte **Bibliothekstools**, und wählen Sie dann die Schaltfläche **Dokument hochladen** aus.  
  
5.  Im Dialogfeld **Dokument hochladen** wählen Sie die Schaltfläche **Durchsuchen** aus, wählen Sie eine Dokumentdatei aus, wählen Sie die Schaltfläche **Öffnen**, und wählen Sie dann die Schaltfläche **OK** aus.  
  
     Hierdurch wird das ausgewählte Dokument in die Liste **Freigegebene Dokumente** hochgeladen, und der Workflow wird gestartet.  
  
6.  Überprüfen Sie in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], ob der Debugger am Haltepunkt neben der `onWorkflowActivated`\-Methode beendet wird.  
  
7.  Drücken Sie die F5\-TASTE, um die Ausführung fortzusetzen.  
  
8.  Sie können die Einstellungen für das Dokument hier ändern, aber zunächst die Standardwerte, indem Sie die Schaltfläche **Speichern** auswählen.  
  
     Hiermit kehren Sie zur Seite **Freigegebene Dokumente** der standardmäßigen SharePoint\-Website zurück.  
  
9. Auf der Seite **Freigegebene Dokumente**  überprüfen Sie, ob der Wert unter der Spalte **MySharePointWorkflow – Workflow1** auf **In Bearbeitung** festgelegt wird.  Dadurch wird angegeben, dass sich der Workflow in Bearbeitung befindet und dass die Überprüfung des Dokuments ansteht.  
  
10. Auf der Seite **Freigegebene Dokumente** Wählen Sie das Dokument, den Pfeil, der angezeigt wird, und wählen Sie dann das Menüelement **Eigenschaften bearbeiten** aus.  
  
11. **Dokumentstatus** festgelegt zu **Überprüfen abgeschlossen** und wählen Sie dann die Schaltfläche **Speichern** aus.  
  
     Hiermit kehren Sie zur Seite **Freigegebene Dokumente** der standardmäßigen SharePoint\-Website zurück.  
  
12. Auf der Seite **Freigegebene Dokumente**  überprüfen Sie, ob der Wert unter der Spalte **Dokumentstatus** auf **Überprüfen abgeschlossen** festgelegt wird.  Aktualisieren Sie die Seite **Freigegebene Dokumente** und überprüfen Sie, ob der Wert unter der Spalte **MySharePointWorkflow – Workflow1** auf **Abgeschlossen** festgelegt wird.  Dadurch wird angegeben, dass der Workflow beendet ist und dass das Dokument überprüft wurde.  
  
## Nächste Schritte  
 Weitere Informationen zum Erstellen von Workflowvorlagen finden Sie in diesen Themen:  
  
-   Weitere Informationen zu SharePoint\-Workflowaktivitäten, Sie finden [Workflow\-Aktivitäten für SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=178992).  
  
-   Weitere Informationen zu Windows Workflow Foundation\-Aktivitäten zu erfahren, finden Sie unter [System.Workflow.Activities\-Namespace](http://go.microsoft.com/fwlink/?LinkId=178993).  
  
## Siehe auch  
 [Erstellen von SharePoint-Workflow-Projektmappen](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [Vorlagen für SharePoint-Projekte und Projektelemente](../sharepoint/sharepoint-project-and-project-item-templates.md)   
 [Erstellen und Debuggen von SharePoint-Lösungen](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
  