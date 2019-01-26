---
title: 'Exemplarische Vorgehensweise: Erstellen und Debuggen von SharePoint-Workflowlösung | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Workflow.WorkflowConditions
- VS.SharePointTools.Workflow.WorkflowList
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8b2affcb8339027f146a629b47db57154b173591
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54871389"
---
# <a name="walkthrough-create-and-debug-a-sharepoint-workflow-solution"></a>Exemplarische Vorgehensweise: Erstellen und Debuggen einer SharePoint-Workflow-Lösung
  Diese exemplarische Vorgehensweise veranschaulicht, wie Sie eine grundlegenden sequenziellen Workflowvorlage erstellen. Der Workflow überprüft eine Eigenschaft eine Bibliothek freigegebener Dokumente, um festzustellen, ob ein Dokument überprüft wurde. Wenn das Dokument überprüft wurde, wird der Workflow abgeschlossen.  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Erstellen einer SharePoint Liste Definition sequenziellen Workflow-Projekts in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
-   Erstellen von Workflowaktivitäten.  
  
-   Behandeln von Ereignissen für Workflow-Aktivität.  
  
> [!NOTE]  
>  Obwohl in dieser exemplarischen Vorgehensweise ein sequenzielles Workflowprojekt verwendet wird, ist der Prozess für ein Zustandsautomat-Workflowprojekt identisch.  
>   
>  Darüber hinaus kann Ihrem Computer unterschiedliche Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio Elemente der Benutzeroberfläche in den folgenden Anweisungen angezeigt. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   Unterstützte Editionen von Microsoft Windows und SharePoint.  
  
-   Visual Studio.  
  
## <a name="add-properties-to-the-sharepoint-shared-documents-library"></a>Eigenschaften der freigegebenen SharePoint-Dokumentbibliothek hinzufügen
 Verfolgen Sie den Überprüfungsstatus von Dokumenten in der **freigegebene Dokumente** -Bibliothek, erstellen wir drei neue Eigenschaften für freigegebene Dokumente auf der SharePoint-Website: `Status`, `Assignee`, und `Review Comments`. Wir definieren diese Eigenschaften in der **freigegebene Dokumente** Bibliothek.  
  
#### <a name="to-add-properties-to-the-sharepoint-shared-documents-library"></a>Eigenschaften hinzufügen, auf die freigegebene SharePoint-Dokumentbibliothek  
  
1.  Öffnen Sie eine SharePoint-Website, z. B. http://\<Systemname > / SitePages, in einem Webbrowser.  
  
2.  Wählen Sie auf der Schnellstartleiste **SharedDocuments**.  
  
3.  Wählen Sie **Bibliothek** auf die **Bibliothekstools** zuerst das Menüband, und wählen Sie dann die **Spalte erstellen** Menüband auf die Schaltfläche zum Erstellen einer neuen Spalteninhalts.  
  
4.  Den Namen der Spalte **Dokumentstatus**, legen Sie deren Typ auf **Auswahl (Menü zur Auswahl)**, geben Sie die folgenden drei Optionen aus, und wählen Sie dann die **OK** Schaltfläche:  
  
    -   **Überprüfung erforderlich**  
  
    -   **Vollständige Überprüfung**  
  
    -   **Änderungen angefordert**  
  
5.  Erstellen Sie zwei weitere Spalten aus, und nennen Sie diese **zugewiesene Person** und **Kommentare zum Codereview**. Legen Sie die zugewiesene Person Spaltentyp als einzelne Zeile des Texts und der Kommentare zum Codereview-Spaltentyp, als mehrere Textzeilen.  
  
## <a name="enable-documents-to-be-edited-without-requiring-a-check-out"></a>Aktivieren Sie die Dokumente bearbeitet werden kann, ohne dass ein Auschecken
 Es ist einfacher, die Workflowvorlage zu testen, wenn Sie die Dokumente bearbeiten können, ohne Auschecken. Im nächsten Schritt konfigurieren Sie die SharePoint-Website, um dies zu ermöglichen.  
  
#### <a name="to-enable-documents-to-be-edited-without-checking-them-out"></a>So aktivieren Sie die Dokumente Quellcodeverwaltungsclients ohne Auschecken bearbeitet werden  
  
1.  Wählen Sie auf der Schnellstartleiste der **freigegebene Dokumente** Link.  
  
2.  Auf der **Bibliothekstools** im Menüband der **Bibliothek** Registerkarte, und wählen Sie dann die **Bibliothekseinstellungen** anzuzeigenden Schaltfläche die **Dokumentbibliothekseinstellungen** Seite.  
  
3.  In der **Allgemeine Einstellungen** Abschnitt der **Versionsverwaltung Einstellungen** Link, um anzuzeigen die **Versionsverwaltung Einstellungen** Seite.  
  
4.  Überprüfen Sie, ob die Einstellung für **verlangen, dass Dokumente, ausgecheckt werden, bevor sie bearbeitet werden können** ist **keine**. Wenn sie nicht der Fall ist, ändern Sie ihn in **keine** und wählen Sie dann die **OK** Schaltfläche.  
  
5.  Schließen Sie den Browser.  
  
## <a name="create-a-sharepoint-sequential-workflow-project"></a>Erstellen Sie ein sequenzielles Workflowprojekt von SharePoint
 Ein sequenzieller Workflow ist eine Reihe von Schritten, die in der Reihenfolge ausgeführt wird, bis die letzte Aktivität abgeschlossen ist. In diesem Verfahren erstellen wir einen sequenziellen Workflow, der für unsere Liste Freigegebene Dokumente gelten. Workflow-Assistenten können Sie den Workflow entweder die Websitedefinition oder die Listendefinition zuordnen und können Sie bestimmen, wann der Workflow gestartet wird.  
  
#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>Erstellen Sie ein sequenzielles Workflowprojekt von SharePoint  
  
1.  Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Wählen Sie auf der Menüleiste **Datei** > **neu** > **Projekt** zum Anzeigen der **neues Projekt** Dialogfeld.  
  
3.  Erweitern Sie die **SharePoint** Knoten entweder **Visual C#-** oder **Visual Basic**, und wählen Sie dann die **2010** Knoten.  
  
4.  In der **Vorlagen** Bereich, wählen Sie die **SharePoint 2010-Projekt** Vorlage.  
  
5.  In der **Namen** geben **MySharePointWorkflow** und wählen Sie dann die **OK** Schaltfläche.  
  
     Die **SharePoint Customization Wizard** angezeigt wird.  
  
6.  In der **Geben Sie die Website und Sicherheitsebene für debugging** Seite die **als farmlösung bereitstellen** Optionsfeld aus, und wählen Sie dann die **Fertig stellen** Schaltfläche zum Akzeptieren der Trust-Ebene und Standard-Website.  
  
     In diesem Schritt wird die Vertrauensebene für die Lösung als Farm-Lösung, die einzig verfügbare Option für Workflowprojekte. Weitere Informationen finden Sie unter [Überlegungen zu sandkastenlösungen](../sharepoint/sandboxed-solution-considerations.md).  
  
7.  In **Projektmappen-Explorer**, wählen Sie den Projektknoten und anschließend auf der Menüleiste die Optionen **Projekt** > **neues Element hinzufügen**.  
  
8.  Entweder unter **Visual C#-** oder **Visual Basic**, erweitern Sie die **SharePoint** Knoten, und wählen Sie dann die **2010** Knoten.  
  
9. In der **Vorlagen** Bereich Wählen Sie die **sequenzieller Workflow (nur Farmlösung)** Vorlage, und wählen Sie dann die **hinzufügen** Schaltfläche.  
  
     Die **SharePoint Customization Wizard** angezeigt wird.  
  
10. In der **Geben Sie den Workflownamen für das Debuggen** Seite aus, übernehmen Sie den Standardnamen (**MySharePointWorkflow - Workflow1**). Beibehalten des Workflows Vorlage Typ Standardwerts, **Listenworkflow**, und wählen Sie dann die **Weiter** Schaltfläche.  
  
11. In der **möchten Sie Visual Studio, um den Workflow in einer Debugsitzung automatisch zuordnen?** Seite die **Weiter** Schaltfläche, um die Standardeinstellungen zu übernehmen.  
  
     Dieser Schritt wird der Workflow automatisch Bibliothek freigegebener Dokumente zugeordnet.  
  
12. In der **definieren die Bedingungen zum Starten des Workflows wird** Seite, lassen Sie die Standardoptionen ausgewählt, die der **wie soll den Workflow gestartet?** aus, und wählen Sie die **abgeschlossen** Schaltfläche.  
  
     Auf dieser Seite können Sie angeben, wenn der Workflow gestartet wird. Standardmäßig startet den Workflow entweder, wenn ein Benutzer er manuell in SharePoint oder die Erstellung eines Elements startet, das der Workflow zugeordnet ist.  
  
## <a name="create-workflow-activities"></a>Erstellen von Workflowaktivitäten
 Workflows enthalten eine oder mehrere *Aktivitäten* , die die auszuführende Aktionen darstellen. Verwenden Sie die Workflow-Designer, um Aktivitäten für einen Workflow anzuordnen. In diesem Verfahren fügen wir zwei Aktivitäten an den Workflow hinzu: HandleExternalEventActivity "und" OnWorkFlowItemChanged ". Diese Aktivitäten überwachen, den Überprüfungsstatus von Dokumenten in der **freigegebene Dokumente** Liste  
  
#### <a name="to-create-workflow-activities"></a>Zum Erstellen von Workflowaktivitäten  
  
1.  Der Workflow sollte im Workflow-Designer angezeigt werden. Wenn sie nicht der Fall ist, öffnen Sie dann entweder **Workflow1.cs** oder **Workflow1.vb** in **Projektmappen-Explorer**.  
  
2.  Wählen Sie im Designer die **OnWorkflowActivated1** Aktivität.  
  
3.  In der **Eigenschaften** Fenster eingeben **"onWorkflowActivated"** neben der **aufgerufen** -Eigenschaft, und wählen Sie dann die EINGABETASTE.  
  
     Der Code-Editor geöffnet, und eine Ereignishandlermethode, die mit dem Namen "onWorkflowActivated" wird die Codedatei "Workflow1" hinzugefügt.  
  
4.  Wechseln Sie zurück zum Workflow-Designer, öffnen Sie die Toolbox, und erweitern Sie dann die **Windows Workflow v3. 0** Knoten.  
  
5.  In der **Windows Workflow v3. 0** Knoten die **Toolbox**, führen Sie eine der folgenden Schritte:  
  
    1.  Öffnen Sie das Kontextmenü für die **während** -Aktivität, und wählen Sie dann **Kopie**. Öffnen Sie im Workflowdesigner das Kontextmenü für die Zeile unter der **onWorkflowActivated1** -Aktivität, und wählen Sie dann **einfügen**.  
  
    2.  Ziehen Sie die **während** Aktivität aus der **Toolbox** zum Workflow-Designer, und verbinden Sie die Aktivität mit der Zeile unter der **onWorkflowActivated1** Aktivität.  
  
6.  Wählen Sie die **WhileActivity1** Aktivität.  
  
7.  In der **Eigenschaften** legen **Bedingung** zu Codebedingung.  
  
8.  Erweitern Sie die **Bedingung** -Eigenschaft, geben Sie **IsWorkflowPending** neben das untergeordnete Element **Bedingung** -Eigenschaft, und wählen Sie dann die EINGABETASTE.  
  
     Der Code-Editor geöffnet, und eine Methode namens IsWorkflowPending wird die Codedatei "Workflow1" hinzugefügt.  
  
9. Wechseln Sie zurück zum Workflow-Designer, öffnen Sie die Toolbox, und erweitern Sie dann die **SharePoint-Workflow** Knoten.  
  
10. In der **SharePoint-Workflow** Knoten die **Toolbox**, führen Sie eine der folgenden Schritte:  
  
    -   Öffnen Sie das Kontextmenü für die **OnWorkflowItemChanged** -Aktivität, und wählen Sie dann **Kopie**. Öffnen Sie im Workflowdesigner das Kontextmenü für die Zeile innerhalb der **whileActivity1** -Aktivität, und wählen Sie dann **einfügen**.  
  
    -   Ziehen Sie die **OnWorkflowItemChanged** Aktivität aus der **Toolbox** zum Workflow-Designer, und verbinden Sie die Aktivität mit der Zeile innerhalb der **whileActivity1** Aktivität.  
  
11. Wählen Sie die **onWorkflowItemChanged1** Aktivität.  
  
12. In der **Eigenschaften** legen die Eigenschaften wie in der folgenden Tabelle gezeigt.  
  
    |Eigenschaft|Wert|  
    |--------------|-----------|  
    |**CorrelationToken**|**workflowToken**|  
    |**Wird aufgerufen**|**onWorkflowItemChanged**|  
  
## <a name="handle-activity-events"></a>Behandeln von Aktivitätsereignissen
 Überprüfen Sie schließlich den Status des Dokuments aus jeder Aktivität ein. Wenn das Dokument überprüft wurde, wird der Workflow abgeschlossen.  
  
#### <a name="to-handle-activity-events"></a>So behandeln Sie Aktivitätsereignisse  
  
1.  In *Workflow1.cs* oder *Workflow1.vb*, fügen Sie das folgende Feld am oberen Rand der `Workflow1` Klasse. Dieses Feld wird in einer Aktivität verwendet, um festzustellen, ob der Workflow abgeschlossen wurde.  
  
    ```vb  
    Dim workflowPending As Boolean = True  
    ```  
  
    ```csharp  
    Boolean workflowPending = true;  
    ```  
  
2.  Fügen Sie der `Workflow1` -Klasse die folgende Methode hinzu. Diese Methode überprüft den Wert des der `Document Status` Eigenschaft der Liste der Dokumente, um festzustellen, ob das Dokument überprüft wurde. Wenn die `Document Status` -Eigenschaftensatz auf `Review Complete`, und klicken Sie dann die `checkStatus` Methode wird die `workflowPending` Feld **"false"** um anzugeben, dass der Workflow kann jetzt abgeschlossen ist.  
  
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
  
3.  Fügen Sie den folgenden Code der `onWorkflowActivated` und `onWorkflowItemChanged` Methoden zum Aufrufen der `checkStatus` Methode. Wenn der Workflow gestartet wird, wird die `onWorkflowActivated` Methodenaufrufe der `checkStatus` Methode, um zu bestimmen, ob das Dokument bereits überprüft wurde. Wenn es nicht überprüft wurde, wird der Workflow fortgesetzt. Wenn das Dokument gespeichert wird, die `onWorkflowItemChanged` Methodenaufrufe der `checkStatus` Methode erneut aus, um zu bestimmen, ob das Dokument überprüft wurde. Während der `workflowPending` Feld nastaven NA hodnotu **"true"**, der Workflow wird weiterhin ausgeführt.  
  
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
  
4.  Fügen Sie den folgenden Code der `isWorkflowPending` Methode zum Überprüfen des Status von der `workflowPending` Eigenschaft. Jedes Mal, die das Dokument gespeichert, die **whileActivity1** Aktivität Ruft die `isWorkflowPending` Methode. Untersucht diese Methode die <xref:System.Workflow.Activities.ConditionalEventArgs.Result%2A> Eigenschaft der <xref:System.Workflow.Activities.ConditionalEventArgs> Objekt, um zu bestimmen, ob die **WhileActivity1** -Aktivität fortgesetzt oder beendet werden soll. Wenn die Eigenschaft, um festgelegt ist **"true"**, die Aktivität fortgesetzt wird. Klicken Sie andernfalls die Aktivität beendet wurde, und der Workflow abgeschlossen ist.  
  
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
  
## <a name="test-the-sharepoint-workflow-template"></a>Testen Sie die SharePoint-Workflowvorlage
 Wenn Sie den Debugger zu starten [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] stellt die Workflowvorlage zum SharePoint-Server bereit und ordnet Sie den Workflow mit dem die **freigegebene Dokumente** Liste. Um den Workflow zu testen, starten Sie eine Instanz des Workflows aus einem Dokument in der **freigegebene Dokumente** Liste.  
  
#### <a name="to-test-the-sharepoint-workflow-template"></a>So testen Sie die SharePoint-Workflowvorlage  
  
1.  In *Workflow1.cs* oder *Workflow1.vb*, legen Sie einen Haltepunkt neben der **"onWorkflowActivated"** Methode.  
  
2.  Wählen Sie die **F5** -Taste, um die Projektmappe erstellen und ausführen.  
  
     Die SharePoint-Website wird angezeigt.  
  
3.  Wählen Sie im Navigationsbereich in SharePoint die **freigegebene Dokumente** Link.  
  
4.  In der **freigegebene Dokumente** Seite der **Dokumente** auf einen link auf die **Bibliothekstools** Registerkarte, und wählen Sie dann die **Dokumentupload** Schaltfläche .  
  
5.  In der **Dokument hochladen** Dialogfeld wählen die **Durchsuchen** Schaltfläche eine Dokumentdatei aus, wählen Sie die **öffnen** Schaltfläche, und wählen Sie dann die **OK** Schaltfläche.  
  
     Dies lädt das ausgewählte Dokument in der **freigegebene Dokumente** aus und startet den Workflow.  
  
6.  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], stellen Sie sicher, dass der Debugger die Ausführung am Haltepunkt, neben anhält der `onWorkflowActivated` Methode.  
  
7.  Wählen Sie die **F5** Schlüssel, um die Ausführung fortzusetzen.  
  
8.  Ändern Sie die Einstellungen für das Dokument hier, aber lassen Sie sie auf die Standardwerte unverändert durch Auswählen der **speichern** Schaltfläche.  
  
     Wird die **freigegebene Dokumente** auf der Seite der standardmäßigen SharePoint-Website.  
  
9. In der **freigegebene Dokumente** Seite, überprüfen Sie, ob der Wert unterhalb der **MySharePointWorkflow - Workflow1** Spalte **In Bearbeitung**. Dies gibt an, dass der Workflow ausgeführt wird und das Dokument überprüfen erwartet wird.  
  
10. In der **freigegebene Dokumente** Seite des Dokuments aus, wählen Sie den Pfeil, der angezeigt wird, und wählen Sie dann die **Eigenschaften bearbeiten** Menüelement.  
  
11. Legen Sie **Dokumentstatus** zu **Review Complete**, und wählen Sie dann die **speichern** Schaltfläche.  
  
     Wird die **freigegebene Dokumente** auf der Seite der standardmäßigen SharePoint-Website.  
  
12. In der **freigegebene Dokumente** Seite, überprüfen Sie, ob der Wert unter der **Dokumentstatus** Spalte **Review Complete**. Aktualisieren der **freigegebene Dokumente** Seite, und überprüfen Sie, ob der Wert unterhalb der **MySharePointWorkflow - Workflow1** Spalte **abgeschlossen**. Dies bedeutet, dass Workflows abgeschlossen ist, und, die das Dokument überprüft wurde.  
  
## <a name="next-steps"></a>Nächste Schritte
 Erfahren Sie mehr über das Erstellen von Workflows in den folgenden Themen:  
  
-   Weitere Informationen zu SharePoint-Workflow-Aktivitäten finden Sie unter [Workflowaktivitäten für SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=178992).  
  
-   Weitere Informationen zu Windows Workflow Foundation-Aktivitäten finden Sie unter [System.Workflow.Activities Namespace](http://go.microsoft.com/fwlink/?LinkId=178993).  
  
## <a name="see-also"></a>Siehe auch
 [Erstellen von SharePoint-Workflow-Projektmappen](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [SharePoint-Projekte und Projektelementvorlagen](../sharepoint/sharepoint-project-and-project-item-templates.md)   
 [Erstellen und Debuggen von SharePoint-Lösungen](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
