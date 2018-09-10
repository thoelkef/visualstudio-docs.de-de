---
title: Erstellen von SharePoint-Workflow-Projektmappen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VSTO.NewSharePointWorkflowWizard.Page3
- VS.SharePointTools.Workflow.WorkflowName
- VSTO.NewSharePointWorkflowWizard.Page2
- VSTO.NewSharePointWorkflowWizard.Page1
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: dd67173078a81c5fc250ca993474a60057076d70
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "42634721"
---
# <a name="create-sharepoint-workflow-solutions"></a>Erstellen von SharePoint-Workflow-Projektmappen

[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] bietet Tools, mit denen Sie benutzerdefinierte Workflows zu erstellen, die den Lebenszyklus der Dokumente und Listenelemente in einer SharePoint-Website zu verwalten. Die bereitgestellten Elemente umfassen einen Designer, einen Satz von Aktivitätssteuerelementen und die erforderlichen Assemblyverweise. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] enthält auch die **SharePoint Customization Wizard**, um das Erstellen und Konfigurieren von Workflows.

Weitere Informationen zu SharePoint, finden Sie unter [Microsoft SharePoint-Produkten und-Technologien](http://go.microsoft.com/fwlink/?LinkId=178470).

## <a name="workflows-in-sharepoint"></a>Workflows in SharePoint
 Wenn Sie einen Workflow auf einer SharePoint-Bibliothek oder Liste hinzufügen, erzwingen Sie einen Geschäftsprozess für alle Elemente in der Bibliothek oder Liste aus. Ein Workflow beschreibt die Aktionen, die das System oder Benutzer, auf die einzelnen Elemente ausführen müssen, z. B. das Element, das bearbeitet werden, und klicken Sie dann überprüft senden. Diese Aktionen, die genannte *Aktivitäten*, sind die Bausteine des Workflows.

 Sie können angeben, Erstellen von SharePoint Workflows in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] und auf einer SharePoint-Website bereitzustellen. Nachdem ein Workflow in SharePoint bereitgestellt wird, ordnen Sie es mit einer Bibliothek oder Liste. Es kann dann automatisch von einem Prozess oder manuell von einem Benutzer gestartet werden. Weitere Informationen zu Workflowvorgang, finden Sie unter [Entwickeln von SharePoint-Workflows, die mithilfe von Visual Studio](https://docs.microsoft.com/sharepoint/dev/general-development/develop-sharepoint-workflows-using-visual-studio).

## <a name="create-custom-sharepoint-workflows"></a>Erstellen Sie benutzerdefinierte SharePoint-workflows
 Zwei SharePoint-Workflow-Projekte stehen Ihnen im [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]: **sequenziellen Workflow** und **Zustandsautomatworkflow**.

 Ein *sequenziellen Workflow* stellt eine Reihe von Schritten dar. Die Schritte werden nacheinander ausgeführt, bis die letzte Aktivität abgeschlossen ist. Sequenzielle Workflows sind immer streng sequenziell ausgeführt. Da sie externe Ereignisse empfangen und parallele logische Abläufe enthalten können, variieren die genaue Reihenfolge der Ausführung. Die folgende Abbildung zeigt ein Beispiel für einen sequenziellen Workflow.

 ![Sequenzieller Workflow](../sharepoint/media/sp-sequential.png "sequenziellen Workflows")

 Ein *Zustandsautomatworkflow* stellt einen Satz von Zuständen, Übergängen und Aktionen. Die Schritte in einem Statuscomputer-Workflow asynchron ausgeführt. Dies bedeutet, dass sie nach dem anderen nicht unbedingt ausgeführt werden, aber stattdessen von Aktionen und Zuständen ausgelöst werden. Ein Zustand wird als Startstatus zugewiesen, und klicken Sie dann auf der Grundlage von Ereignissen Übergang in einen anderen Zustand. Das Zustandsautomat kann es sich um einen Endzustand verfügen, der bestimmt, das Ende des Workflows. Das folgende Diagramm zeigt ein Beispiel für einen Statuscomputerworkflow.

 ![Status der Zustandsautomatworkflows](../sharepoint/media/sp-state.png "Zustand der Zustandsautomatworkflows")

 Weitere Informationen zu Workflowtypen, finden Sie unter [Workflowtypen](http://go.microsoft.com/fwlink/?LinkId=178995).

### <a name="use-the-wizard"></a>Verwenden Sie den Assistenten
 Beim Erstellen einer SharePoint-Workflowprojekt in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], geben Sie zunächst die Einstellungen in der **SharePoint Customization Wizard**. Der Assistent verwendet diese Einstellungen zum Erstellen eines Projekts in **Projektmappen-Explorer**. Dieses Projekt enthält eine Codedatei, mehrere Dateien, die verwendet werden, um den Workflow, bereitstellen und Verweise auf Assemblys, die zum Erstellen eines benutzerdefinierten SharePoint-Workflows erforderlich sind.

 Nachdem Sie den Workflow erstellt haben, können Sie seine Eigenschaften im Eigenschaftenfenster ändern. Obwohl die meisten Workfloweigenschaften direkt im Eigenschaftenfenster geändert werden können, einige erfordern Sie eine Schaltfläche klicken (![ASP.NET Mobile-Designer Ellipse](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile-Designer Ellipse")), Ändern Sie deren Werte an. Diese Schaltfläche, Neustart der **SharePoint Customization Wizard**. Nach dem vornehmen der Eigenschaft-Wert ändert, wählen Sie die **Fertig stellen** Schaltfläche, um sie abzuschließen.

> [!NOTE]
>  Die **Workflowtyp** -Eigenschaft ist schreibgeschützt und kann nicht geändert werden. Wenn Sie den Workflow ändern möchten, müssen Sie einen anderen Workflow erstellen.

## <a name="design-a-sharepoint-workflow"></a>Entwerfen eines SharePoint-Workflows
 Nachdem Sie alle Schritte in den Geschäftsprozess definieren, verwenden Sie die [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Workflow-Designer zum Entwerfen des SharePoint-Workflows. Um den Designer zu öffnen, doppelklicken Sie auf Workflow1.cs klicken oder Workflow1.vb in **Projektmappen-Explorer**, oder öffnen Sie das Kontextmenü für eine dieser Dateien, und wählen Sie dann **öffnen**.

### <a name="activities"></a>Aktivitäten
 Fügen Sie um einen Workflow zu entwerfen, Aktivitäten, die von der **Toolbox** zu einem *Workflowzeitplan* im Designer. Ein Workflowzeitplan enthält die Abfolge von Aktivitäten in der Reihenfolge, in der sie ausgeführt werden soll.

 Es gibt zwei Arten von Aktivitäten:

-   *Einfache Aktivitäten* führen Sie eine einzelne Arbeitseinheit, z. B. "1 Tag verzögern" oder "Webdienst starten".

-   *Zusammengesetzte Aktivitäten* andere Aktivitäten enthalten, die eine bedingte Aktivität kann beispielsweise zwei Verzweigungen enthalten.

 Beide Arten von Aktivitäten finden Sie in der **Toolbox**.

 Aktivitäten können Eigenschaften, Methoden und Ereignisse haben. Verwenden der **Eigenschaften** Fenster zum Festlegen der Eigenschaften einer Aktivität.

 Sie können auch eine benutzerdefinierte Aktivität erstellen. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: erstellen eine benutzerdefinierten Websiteworkflowaktivität](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md).

 Aktivitäten sind in den folgenden Registerkarten organisiert die **Toolbox**:

-   **SharePoint-Workflow**

-   **Windows Workflow v3. 0**

-   **Windows Workflow v3. 5**

 Nicht alle Core-Workflow-Aktivitäten werden von SharePoint unterstützt. Weitere Informationen finden Sie unter [Workflow Aktivitäten für Windows SharePoint Services Overview](http://go.microsoft.com/fwlink/?LinkID=156094).

#### <a name="sharepoint-workflow-activities"></a>SharePoint-Workflow-Aktivitäten
 Die **SharePoint-Workflow** Registerkarten enthalten spezielle Aktivitäten für die Verwendung in [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]. Diese Aktivitäten vereinfachen und optimieren die Entwicklung von Workflows des Lebenszyklus. Weitere Informationen zu den aufgeführten Aktivitäten der **SharePoint-Workflow** finden Sie unter [Workflow Aktivitäten für Windows SharePoint Services Overview](http://go.microsoft.com/fwlink/?LinkID=156094).

#### <a name="windows-workflow-activities"></a>Windows Workflow-Aktivitäten
 Die **Windows Workflow** Registerkarten enthalten, die vom bereitgestellten Aktivitäten der [!INCLUDE[TLA#tla_workflow](../sharepoint/includes/tlasharptla-workflow-md.md)]. Sie können diese Aktivitäten verwenden, um Workflow-Zeitpläne für jede Art von Windows Workflow-Anwendung zu erstellen.

 Weitere Informationen zu den aufgeführten Aktivitäten der **Windows Workflows** finden Sie unter [Windows Workflow Foundation-Aktivitäten](http://go.microsoft.com/fwlink/?LinkID=156096). Weitere Informationen zu der Windows Workflow Foundation, finden Sie unter [Übersicht über die Windows Workflow Foundation](http://go.microsoft.com/fwlink/?LinkID=128632).

### <a name="work-with-activities-in-the-designer"></a>Arbeiten Sie mit Aktivitäten im designer
 Der Workflowzeitplan kann eine Kombination von Windows Workflow-Aktivitäten und SharePoint-Workflow-Aktivitäten enthalten.

 Der Designer zeigt visuelle Hinweise zum Positionieren und Aktivitäten ordnungsgemäß zu konfigurieren. Wenn Sie ziehen oder kopieren Sie eine Aktivität in den Workflowzeitplan, zeigt der Designer grünes Pluszeichen (+)-Symbole, die Sie gültige Positionen für diese Aktivität im Workflow anzuzeigen. Sie können keine Aktivität an einem Ort positionieren, wo sie ungültig wäre. Sie können keine z. B. eine Send-Aktivität als erste Aktivität in einer Verzweigung der warten-Aktivität positionieren. Weitere Informationen finden Sie unter [Entwicklercenter für SharePoint Designer](http://go.microsoft.com/fwlink/?LinkId=178476).

## <a name="collect-information-during-the-workflow"></a>Sammeln von Informationen während des Workflows
 Möglicherweise möchten Sie Informationen von Benutzern sammeln vordefinierten Zeitpunkten während des Workflows. Sie können Informationen sammeln, indem Sie mithilfe von Formularen oder Eigenschaften des Elements.

### <a name="forms"></a>Formulare
 Formen sind z. B. Dialogfelder, die Fragen enthalten, und bieten Möglichkeiten für Benutzer, um Antworten zu geben.

 Es gibt vier Arten von Formularen, die in einem Workflow verwendet werden können:

-   Zuordnung

-   Initiierung

-   Änderung

-   Aufgabe

 Von diesen [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Elementvorlagen für Zuordnungs-und Initiierungsformularen enthält. Ein Beispiel für eine *Zuordnungsformular* ist eine, die den Administrator installiert den Workflow können Geben Sie Parameter, die für den Workflow, z. B. ein Ausgabenlimit für einen Expense-Workflow beziehen. Ein Beispiel für eine *Initiierungsformular* ist ein, der dem der Benutzer einen Expense-Workflow geben in den Workflow der Betrag, der sie ausgegeben. Weitere Informationen zu diesen Arten von Formularen, finden Sie unter [SharePoint-Projekt und Projekt Elementvorlagen](../sharepoint/sharepoint-project-and-project-item-templates.md).

### <a name="item-properties"></a>Elementeigenschaften
 Sie können Informationen auch mithilfe der Eigenschaften eines Elements in der SharePoint-Bibliothek oder Liste von Benutzern sammeln. Die Hauptcodedatei (Workflow1.cs oder Workflow1.vb) deklariert eine Instanz der Microsoft.SharePoint.Workflow.SPWorkflowActivationProperties.WorkflowProperties-Klasse, die mit dem Namen `workflowProperties`. Verwenden der `workflowProperties` Objekt, das die Eigenschaften der Bibliothek oder Liste im Code zugreifen. Ein Beispiel finden Sie unter [Exemplarische Vorgehensweise: Erstellen und Debuggen eine SharePoint-workflowlösung](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md).

## <a name="debug-a-sharepoint-workflow-template"></a>Debuggen einer SharePoint-Workflowvorlage
 Sie können Debuggen einer SharePoint-Workflowprojekt identisch wie bei anderen [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] webbasierten Projekte. Beim Starten der [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] -Debugger, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] verwendet die Einstellungen, die Sie, in angeben der **SharePoint Customization Wizard** öffnen Sie die entsprechenden SharePoint-Website und automatisch zuordnen der Workflowvorlage der entsprechende Bibliothek oder Liste. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Außerdem fügt die [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] debugger an den [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] Prozess mit dem Namen *w3wp.exe*.

 Um den Workflow zu testen, müssen Sie sie manuell starten. Weitere Informationen finden Sie im Abschnitt "Debuggen von Workflows" in [SharePoint-Lösungen Debuggen](../sharepoint/debugging-sharepoint-solutions.md). Weitere Informationen zu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Web zu Anwendungsdebuggen, finden Sie unter [Debuggen von Webanwendungen und Skripts](../debugger/debugging-web-applications-and-script.md).

## <a name="deploy-a-sharepoint-workflow-template"></a>Bereitstellen einer SharePoint-Workflowvorlage
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Bereitstellen von SharePoint-Workflow-Projekte wie andere [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint-Projekte. Weitere Informationen finden Sie unter [Pakets und Bereitstellen von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md).

## <a name="import-globally-reusable-workflows"></a>Global wiederverwendbare Workflows importieren
 Zusätzlich zur Erstellung standortspezifischen wiederverwendbaren Workflows, SharePoint Designer ermöglicht Ihnen die Erstellung *Global wiederverwendbare Workflows*, welche sind Workflows, die von jedem SharePoint-Website verwendet werden können. Das Projekt "Wiederverwendbaren Workflow importieren" in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] derzeit nicht global wiederverwendbare Workflows importieren. Allerdings können entweder mit SharePoint Designer können Sie um global wiederverwendbaren Workflow in einer wiederverwendbaren Workflow zu konvertieren oder importieren den Workflow als eine nicht konvertierte deklarativen Workflows. Weitere Informationen finden Sie unter [Importieren von Elementen aus einer vorhandenen SharePoint-Website](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).

## <a name="related-topics"></a>Verwandte Themen

|Titel|Beschreibung|
|-----------|-----------------|
|[Exemplarische Vorgehensweise: Erstellen und Debuggen einer SharePoint-Workflow-Lösung](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md)|Führt Sie schrittweise durch das Erstellen und Debuggen eines einfachen [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Workflow.|
|[Exemplarische Vorgehensweise: Erstellen eines Workflows mit Zuordnungs-und Initiierungsformularen](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)|Führt Sie Schritt für Schritt erstellen Sie eine voll funktionsfähige [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Workflows mit Zuordnungs-und Initiierungsformularen nicht abgeschlossen.|
|[Exemplarische Vorgehensweise: Hinzufügen einer Anwendungsseite zu einem workflow](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)|Zu diesem Thema erstellt [Exemplarische Vorgehensweise: Erstellen eines Workflows mit Zuordnungs-und Initiierungsformularen](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md) durch Hinzufügen einer zusätzlichen *aspx* Seite "Anwendung", die in den Workflow eingegebene Daten meldet.|
|[Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Websiteworkflowaktivität](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md)|Veranschaulicht, wie zwei wesentliche Aufgaben zu erledigen: Erstellen eines Workflows auf, und erstellen Sie eine benutzerdefinierte Workflowaktivität.|
|[Exemplarische Vorgehensweise: Importieren eines wiederverwendbaren Workflows aus SharePoint Designer in Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)|Veranschaulicht das Importieren von wiederverwendbaren deklarativen Workflows, die in SharePoint Designer 2010 in erstellt eine [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint-Projekt.|

## <a name="see-also"></a>Siehe auch

- [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)
- [Erstellen und Debuggen von SharePoint-Lösungen](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Erstellen von Anwendungsseiten für SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)