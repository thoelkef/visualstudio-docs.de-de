---
title: 'Exemplarische Vorgehensweise: Erstellen und Debuggen einer SharePoint-Workflow-Projektmappe | Microsoft Docs'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.Workflow.WorkflowConditions
- VS.SharePointTools.Workflow.WorkflowList
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
ms.assetid: 81756490-ab5a-4fa4-96c6-eed2cfbf8374
caps.latest.revision: "28"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d64c0767cce43d5b157fca82cc3e1e210a2f8c58
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-creating-and-debugging-a-sharepoint-workflow-solution"></a>Exemplarische Vorgehensweise: Erstellen und Debuggen einer SharePoint-Workflow-Projektmappe
  Diese exemplarische Vorgehensweise veranschaulicht das Erstellen einer grundlegenden sequenziellen Workflowvorlage. Der Workflow überprüft eine Eigenschaft einer freigegebenen Dokumentbibliothek zu bestimmen, ob ein Dokument überprüft wurde. Wenn das Dokument überprüft wurde, wird der Workflow abgeschlossen.  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Erstellen einer SharePoint-Liste Definition sequenzieller Workflowprojekts in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
-   Erstellen von Workflowaktivitäten.  
  
-   Behandlung von Ereignissen für Workflow-Aktivität.  
  
> [!NOTE]  
>  Obwohl in dieser exemplarischen Vorgehensweise ein sequenzielles Workflowprojekt verwendet wird, ist der Prozess für einen Zustandsautomat-Workflowprojekt identisch.  
>   
>  Darüber hinaus möglicherweise Ihren Computer andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio Elemente der Benutzeroberfläche in den folgenden Anweisungen angezeigt. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   Unterstützte Editionen von Microsoft Windows und SharePoint. Weitere Informationen finden Sie unter [Anforderungen für die Entwicklung von SharePoint-Lösungen](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
## <a name="adding-properties-to-the-sharepoint-shared-documents-library"></a>Hinzufügen von Eigenschaften in der SharePoint freigegebene Bibliothek "Dokumente"  
 Zum Nachverfolgen von Dokumenten in des Überprüfungsstatus der **freigegebene Dokumente** Bibliothek wir drei neue Eigenschaften für freigegebene Dokumente auf SharePoint-Website erstellen: `Status`, `Assignee`, und `Review Comments`. Definieren wir diese Eigenschaften in der **Shared Documents** Bibliothek.  
  
#### <a name="to-add-properties-to-the-sharepoint-shared-documents-library"></a>Hinzufügen von Eigenschaften zu freigegebenen SharePoint-Dokumentbibliothek  
  
1.  Öffnen Sie eine SharePoint-Website, z. B. http://\<Systemname > / SitePages, in einem Webbrowser.  
  
2.  Wählen Sie in der Schnellstartleiste **SharedDocuments**.  
  
3.  Wählen Sie **Bibliothek** auf die **Bibliothekstools** des Menübands, und wählen Sie dann die **Spalte erstellen** Schaltfläche auf dem Menüband eine neue Spalte erstellen.  
  
4.  Den Namen der Spalte **Dokumentstatus**, legen Sie deren Typ auf **Auswahl (Menü)**, geben Sie die folgenden drei Optionen aus, und wählen Sie dann die **OK** Schaltfläche:  
  
    -   **Überprüfung erforderlich**  
  
    -   **Vollständige Überprüfung**  
  
    -   **Änderungen, die angefordert**  
  
5.  Erstellen Sie zwei weitere Spalten, und nennen Sie diese **Beauftragter** und **Überprüfungskommentare**. Legen Sie den Spaltentyp Beauftragter als eine einzelne Textzeile und den Spaltentyp Überprüfungskommentare als mehrere Textzeilen an.  
  
## <a name="enabling-documents-to-be-edited-without-requiring-a-check-out"></a>Aktivieren Dokumente bearbeitet werden, ohne eine Auschecken  
 Es ist einfacher, die Workflowvorlage zu testen, wenn Sie die Dokumente bearbeiten können, ohne sie auszuchecken. Im nächsten Verfahren konfigurieren Sie die SharePoint-Website, um dies zu ermöglichen.  
  
#### <a name="to-enable-documents-to-be-edited-without-checking-them-out"></a>So aktivieren Sie die Dokumente Quellcodeverwaltungsclients ohne Auschecken bearbeitet werden  
  
1.  Wählen Sie in der Schnellstartleiste der **Shared Documents** Link.  
  
2.  Auf der **Bibliothekstools** Menüband der **Bibliothek** Registerkarte, und wählen Sie dann die **Bibliothekseinstellungen** Schaltfläche zum Anzeigen der **Dokumentbibliothekseinstellungen** Seite.  
  
3.  In der **Allgemeine Einstellungen** Abschnitt der **Versionierungseinstellungen** Link, um anzuzeigen die **Versionierungseinstellungen** Seite.  
  
4.  Überprüfen Sie, ob die Einstellung für **ausgecheckt werden, bevor sie bearbeitet werden, können von Dokumenten erfordern** ist **keine**. Wenn sie nicht der Fall ist, ändern Sie ihn in **keine** und wählen Sie dann die **OK** Schaltfläche.  
  
5.  Schließen Sie den Browser.  
  
## <a name="creating-a-sharepoint-sequential-workflow-project"></a>Erstellen ein sequenzielles Workflowprojekt von SharePoint  
 Ein sequenzieller Workflow ist eine Reihe von Schritten, die in der Reihenfolge ausgeführt wird, bis die letzte Aktivität abgeschlossen ist. In diesem Verfahren erstellen Sie einen sequenziellen Workflow, der für unsere Liste Freigegebene Dokumente gelten. Workflow-Assistenten können Sie den Workflow mit Standortdefinition oder die Listendefinition zuordnen und können Sie bestimmen, wann der Workflow gestartet wird.  
  
#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>So erstellen ein sequenzielles Workflowprojekt von SharePoint  
  
1.  Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Wählen Sie in der Menüleiste **Datei**, **neu**, **Projekt** zum Anzeigen der **neues Projekt** (Dialogfeld).  
  
3.  Erweitern Sie die **SharePoint** Knoten unter einem **Visual C#-** oder **Visual Basic**, und wählen Sie dann die **2010** Knoten.  
  
4.  In der **Vorlagen** Bereich, wählen Sie die **SharePoint 2010-Projekt** Vorlage.  
  
5.  In der **Namen** geben **MySharePointWorkflow** und wählen Sie dann die **OK** Schaltfläche.  
  
     Die **Assistent zum Anpassen von SharePoint** angezeigt wird.  
  
6.  In der **Geben Sie die Website und die Sicherheit für das Debuggen** Seite der **als farmlösung bereitstellen** Optionsfeld aus, und wählen Sie dann die **Fertig stellen** Schaltfläche zum Akzeptieren der Vertrauensstellung Ebene und Standard-Website.  
  
     In diesem Schritt wird die Vertrauensebene für die Projektmappe als farmlösung, die einzig verfügbare Option für Workflowprojekte. Weitere Informationen finden Sie unter [Überlegungen zu Sandkastenlösungen](../sharepoint/sandboxed-solution-considerations.md).  
  
7.  In **Projektmappen-Explorer**, wählen Sie den Projektknoten, und wählen Sie dann auf der Menüleiste **Projekt**, **neues Element hinzufügen**.  
  
8.  Unter einem **Visual C#-** oder **Visual Basic**, erweitern Sie die **SharePoint** Knoten, und wählen Sie dann die **2010** Knoten.  
  
9. In der **Vorlagen** Bereich, wählen Sie die **sequenzieller Workflow (nur Farmlösung)** Vorlage, und wählen Sie dann die **hinzufügen** Schaltfläche.  
  
     Die **Assistent zum Anpassen von SharePoint** angezeigt wird.  
  
10. In der **Geben Sie den Workflownamen für das Debuggen** Seite, übernehmen Sie den Standardnamen (**MySharePointWorkflow - Workflow1**). Beibehalten des Workflow-Vorlage Typ Standardwerts, **Listenworkflow**, und wählen Sie dann die **Weiter** Schaltfläche.  
  
11. In der **möchten Sie Visual Studio, um den Workflow in einer Debugsitzung automatisch zuordnen?** Seite, und wählen Sie die **Weiter** Schaltfläche, um die Standardeinstellungen zu übernehmen.  
  
     Dieser Schritt ordnet den Workflow automatisch der Bibliothek Dokumente freigegeben.  
  
12. In der **definieren die Bedingungen zum wie der Workflow gestartet wird** Seite, lassen Sie die Standardoptionen ausgewählt, die der **wie soll den Workflow gestartet?** Abschnitt, und wählen Sie die **Beenden** Schaltfläche.  
  
     Auf dieser Seite können Sie angeben, wenn der Workflow gestartet wird. Standardmäßig startet den Workflow, entweder, wenn ein Benutzer er manuell in SharePoint oder der Erstellung eines Elements startet, das der Workflow zugeordnet ist.  
  
## <a name="creating-workflow-activities"></a>Erstellen von Workflowaktivitäten  
 Workflows enthalten eine oder mehrere *Aktivitäten* , die Aktionen darstellen. Verwenden Sie die Workflow-Designer, um Aktivitäten für einen Workflow anzuordnen. In diesem Verfahren fügen wir zwei Aktivitäten des Workflows: HandleExternalEventActivity und OnWorkFlowItemChanged. Diese Aktivitäten überwachen den Überprüfungsstatus von Dokumenten in der **Shared Documents** Liste  
  
#### <a name="to-create-workflow-activities"></a>Zum Erstellen von Workflowaktivitäten  
  
1.  Der Workflow sollte im Workflow-Designer angezeigt werden. Wenn sie nicht der Fall ist, öffnen Sie dann entweder **Workflow1.cs** oder **Workflow1.vb** in **Projektmappen-Explorer**.  
  
2.  Wählen Sie im Designer die **OnWorkflowActivated1** Aktivität.  
  
3.  In der **Eigenschaften** Fenster, geben Sie **OnWorkflowActivated** neben der **aufgerufen** -Eigenschaft, und wählen Sie dann die EINGABETASTE.  
  
     Code-Editor wird geöffnet, und eine Ereignishandlermethode mit der Bezeichnung OnWorkflowActivated wird der Workflow1-Codedatei hinzugefügt.  
  
4.  Wechseln Sie zurück zum Workflow-Designer, öffnen Sie die Toolbox, und erweitern Sie dann die **Windows Workflow v3. 0** Knoten.  
  
5.  In der **Windows Workflow v3. 0** Knoten der **Toolbox**, führen Sie einen der folgenden Schritte aus:  
  
    1.  Öffnen Sie das Kontextmenü für die **während** Aktivität, und wählen Sie dann **Kopie**. Öffnen Sie im Workflow-Designer das Kontextmenü für die Zeile unter der **onWorkflowActivated1** Aktivität, und wählen Sie dann **einfügen**.  
  
    2.  Ziehen Sie die **während** Aktivität aus der **Toolbox** dem Workflow-Designer, und verbinden Sie die Aktivität mit der Zeile unter der **onWorkflowActivated1** Aktivität.  
  
6.  Wählen Sie die **WhileActivity1** Aktivität.  
  
7.  In der **Eigenschaften** legen **Bedingung** Code Bedingung.  
  
8.  Erweitern Sie die **Bedingung** -Eigenschaft, geben Sie **IsWorkflowPending** neben der untergeordneten **Bedingung** -Eigenschaft, und wählen Sie dann die EINGABETASTE.  
  
     Code-Editor wird geöffnet, und eine Methode mit dem Namen IsWorkflowPending wird der Workflow1-Codedatei hinzugefügt.  
  
9. Wechseln Sie zurück zum Workflow-Designer, öffnen Sie die Toolbox, und erweitern Sie dann die **SharePoint-Workflow** Knoten.  
  
10. In der **SharePoint-Workflow** Knoten der **Toolbox**, führen Sie einen der folgenden Schritte aus:  
  
    -   Öffnen Sie das Kontextmenü für die **OnWorkflowItemChanged** Aktivität, und wählen Sie dann **Kopie**. Öffnen Sie im Workflow-Designer das Kontextmenü für die Zeile innerhalb der **whileActivity1** Aktivität, und wählen Sie dann **einfügen**.  
  
    -   Ziehen Sie die **OnWorkflowItemChanged** Aktivität aus der **Toolbox** dem Workflow-Designer, und verbinden Sie die Aktivität mit der Zeile in der **whileActivity1** Aktivität.  
  
11. Wählen Sie die **onWorkflowItemChanged1** Aktivität.  
  
12. In der **Eigenschaften** Fenster, legen Sie die Eigenschaften wie in der folgenden Tabelle gezeigt.  
  
    |Eigenschaft|Wert|  
    |--------------|-----------|  
    |**CorrelationToken**|**workflowToken**|  
    |**Wird aufgerufen**|**onWorkflowItemChanged**|  
  
## <a name="handling-activity-events"></a>Behandlung von Aktivitätsereignissen  
 Überprüfen Sie schließlich den Status des Dokuments aus jeder Aktivität ein. Wenn das Dokument überprüft wurde, wird der Workflow beendet.  
  
#### <a name="to-handle-activity-events"></a>So behandeln Sie Aktivitätsereignisse  
  
1.  Fügen Sie in Workflow1.cs oder Workflow1.vb das folgende Feld ein, an den Anfang der `Workflow1` Klasse. Dieses Feld wird in einer Aktivität verwendet, um zu bestimmen, ob der Workflow abgeschlossen ist.  
  
    ```vb  
    Dim workflowPending As Boolean = True  
    ```  
  
    ```csharp  
    Boolean workflowPending = true;  
    ```  
  
2.  Fügen Sie der `Workflow1`-Klasse die folgende Methode hinzu. Diese Methode überprüft den Wert, der die `Document Status` Eigenschaft der Liste der Dokumente, um zu bestimmen, ob das Dokument überprüft wurde. Wenn die `Document Status` -Eigenschaftensatz auf `Review Complete`, die `checkStatus` Methode legt die `workflowPending` Feld **"false"** um anzugeben, dass der Workflow beendet ist.  
  
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
  
3.  Fügen Sie folgenden Code, der `onWorkflowActivated` und `onWorkflowItemChanged` Methoden aufrufen, die `checkStatus` Methode. Wenn der Workflow gestartet wird, wird die `onWorkflowActivated` Methodenaufrufe der `checkStatus` Methode, um zu bestimmen, ob das Dokument bereits überprüft wurde. Wenn es nicht überprüft wurde, wird der Workflow fortgesetzt. Wenn das Dokument gespeichert wird, die `onWorkflowItemChanged` Methodenaufrufe der `checkStatus` Methode erneut aus, um zu bestimmen, ob das Dokument überprüft wurde. Während der `workflowPending` Feld **"true"**, der Workflow wird weiterhin ausgeführt.  
  
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
  
4.  Fügen Sie folgenden Code, der `isWorkflowPending` Methode zum Überprüfen des Status von der `workflowPending` Eigenschaft. Jedes Mal, die das Dokument gespeichert wird, die **whileActivity1** Aktivität Ruft die `isWorkflowPending` Methode. Überprüft diese Methode die <xref:System.Workflow.Activities.ConditionalEventArgs.Result%2A> Eigenschaft von der <xref:System.Workflow.Activities.ConditionalEventArgs> Objekt, um zu bestimmen, ob die **WhileActivity1** Aktivität fortgesetzt oder beendet werden soll. Wenn die Eigenschaft, um festgelegt wird **"true"**, die Aktivität fortgesetzt wird. Andernfalls wird die Aktivität abgeschlossen wurde, und der Workflow abgeschlossen ist.  
  
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
  
## <a name="testing-the-sharepoint-workflow-template"></a>Testen der SharePoint-Workflow-Vorlage  
 Wenn Sie den Debugger starten [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] die Workflowvorlage auf dem SharePoint-Server bereitgestellt und ordnet den Workflow mit der **Shared Documents** Liste. Starten Sie zum Testen des Workflows eine Instanz des Workflows aus einem Dokument in der **Shared Documents** Liste.  
  
#### <a name="to-test-the-sharepoint-workflow-template"></a>So testen Sie die SharePoint-Workflow-Vorlage  
  
1.  In Workflow1.cs oder Workflow1.vb, legen Sie einen Haltepunkt neben der **OnWorkflowActivated** Methode.  
  
2.  Wählen Sie die F5-Taste zum Erstellen und führen Sie die Projektmappe aus.  
  
     Die SharePoint-Website wird angezeigt.  
  
3.  Wählen Sie im Navigationsbereich in SharePoint die **Shared Documents** Link.  
  
4.  In der **Shared Documents** Seite, und wählen Sie die **Dokumente** link die **Bibliothekstools** Registerkarte, und wählen Sie dann die **Dokument hochladen** Schaltfläche .  
  
5.  In der **Dokument hochladen** Dialogfeld Wählen Sie die **Durchsuchen** Schaltfläche, wählen Sie eine Dokumentdatei, wählen Sie die **öffnen** aus, und klicken Sie dann die **OK** Schaltfläche.  
  
     Dies hochlädt, dass das ausgewählte Dokument in die **Shared Documents** aus und startet den Workflow.  
  
6.  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], stellen Sie sicher, dass der Debugger am Haltepunkt, neben anhält dem `onWorkflowActivated` Methode.  
  
7.  Drücken Sie die Taste F5, um die Ausführung fortzusetzen.  
  
8.  Die Einstellungen für das Dokument hier ändern, aber lassen sie auf den Standardwerten jetzt durch Auswählen der **speichern** Schaltfläche.  
  
     Dies gibt Ihnen die **Shared Documents** auf der Seite der standardmäßigen SharePoint-Website.  
  
9. In der **Shared Documents** Seite, überprüfen Sie, ob der Wert unterhalb der **MySharePointWorkflow - Workflow1** Spalte **In Bearbeitung**. Dies gibt an, dass der Workflow ausgeführt wird und dass das Dokument überprüfen erwartet wird.  
  
10. In der **Shared Documents** Seite, wählen Sie das Dokument, wählen Sie den Pfeil, der angezeigt wird, und wählen Sie dann die **Eigenschaften bearbeiten** Menüelement.  
  
11. Legen Sie **Dokumentstatus** auf **vollständige Überprüfung**, und wählen Sie dann die **speichern** Schaltfläche.  
  
     Dies gibt Ihnen die **Shared Documents** auf der Seite der standardmäßigen SharePoint-Website.  
  
12. In der **Shared Documents** Seite, überprüfen Sie, ob der Wert unterhalb der **Dokumentstatus** Spalte **vollständige Überprüfung**. Aktualisieren der **Shared Documents** Seite, und überprüfen Sie, ob der Wert unterhalb der **MySharePointWorkflow - Workflow1** Spalte **abgeschlossen**. Dies bedeutet, dass Workflows abgeschlossen ist und, die das Dokument überprüft wurde.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Erfahren Sie mehr über das Erstellen von Workflow-Vorlagen in den folgenden Themen:  
  
-   Weitere Informationen zu SharePoint-Workflow-Aktivitäten finden Sie unter [Workflowaktivitäten für SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=178992).  
  
-   Weitere Informationen zu Windows Workflow Foundation-Aktivitäten finden Sie unter [System.Workflow.Activities Namespace](http://go.microsoft.com/fwlink/?LinkId=178993).  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von SharePoint-Workflow-Projektmappen](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [SharePoint-Projekte und Projektelementvorlagen](../sharepoint/sharepoint-project-and-project-item-templates.md)   
 [Erstellen und Debuggen von SharePoint-Projektmappen](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
  