---
title: Erstellen von SharePoint-Workflow Lösungen | Microsoft-Dokumentation
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f4139760995d655dbeb4e1c76d164f21949a9b50
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984547"
---
# <a name="create-sharepoint-workflow-solutions"></a>Erstellen von SharePoint-Workflow Lösungen

[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] stellt Tools bereit, die Sie beim Erstellen von benutzerdefinierten Workflows unterstützen, die den Lebenszyklus von Dokumenten und Listenelementen in einer SharePoint-Website verwalten. Zu den bereitgestellten Elementen gehören ein Designer, ein Satz von Aktivitäts Steuerelementen und die erforderlichen Assemblyverweise. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] umfasst auch den Assistenten zum Anpassen von **SharePoint**, um die Erstellung und Konfiguration der Workflows zu unterstützen.

Weitere Informationen zu SharePoint finden Sie unter [Microsoft SharePoint-Produkte und-Technologien](/sharepoint/dev/).

## <a name="workflows-in-sharepoint"></a>Workflows in SharePoint
 Wenn Sie einem SharePoint-Bibliothek oder einer SharePoint-Liste einen Workflow hinzufügen, erzwingen Sie einen Geschäftsprozess für alle Elemente in der Bibliothek oder Liste. Ein Workflow beschreibt die Aktionen, die das System oder die Benutzer für jedes Element ausführen müssen, z. b. das Senden des zu bearbeitenden und dann zu überprüfenden Elements. Diese Aktionen werden als *Aktivitäten*bezeichnet und sind die Bausteine des Workflows.

 Sie können SharePoint-Workflows in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] erstellen und auf einer SharePoint-Website bereitstellen. Nachdem ein Workflow in SharePoint bereitgestellt wurde, ordnen Sie ihn einer Bibliothek oder einer Liste zu. Sie kann dann automatisch, von einem Prozess oder manuell von einem Benutzer gestartet werden. Weitere Informationen zum Workflow Vorgang finden Sie unter [entwickeln von SharePoint-Workflows mithilfe von Visual Studio](/sharepoint/dev/general-development/develop-sharepoint-workflows-using-visual-studio).

## <a name="create-custom-sharepoint-workflows"></a>Erstellen von benutzerdefinierten SharePoint-Workflows
 In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]stehen zwei SharePoint-Workflow Projekte zur Verfügung: **sequenzieller Workflow** und **Status Computer Workflow**.

 Ein *sequenzieller Workflow* stellt eine Reihe von Schritten dar. Die Schritte werden nacheinander ausgeführt, bis die letzte Aktivität abgeschlossen ist. Sequenzielle Workflows sind in ihrer Ausführung immer genau sequenziell. Da Sie externe Ereignisse empfangen können und parallele logische Flows einschließen, kann die genaue Ausführungsreihenfolge variieren. Die folgende Abbildung zeigt ein Beispiel für einen sequenziellen Workflow.

 ![Sequenzieller Workflow](../sharepoint/media/sp-sequential.png "Sequenzieller Workflow")

 Ein *Zustands Automaten Workflow* stellt einen Satz von Zuständen, Übergängen und Aktionen dar. Die Schritte in einem Zustands Automaten Workflow werden asynchron ausgeführt. Dies bedeutet, dass Sie nicht notwendigerweise nacheinander ausgeführt werden, sondern stattdessen durch Aktionen und Zustände ausgelöst werden. Ein Status wird als Startstatus zugewiesen, und auf der Grundlage eines Ereignisses wird ein Übergang in einen anderen Zustand vorgenommen. Der Zustands Automat kann einen Endzustand aufweisen, der das Ende des Workflows bestimmt. Das folgende Diagramm zeigt ein Beispiel für einen Status Computer Workflow.

 ![Zustands Automat-Workflow](../sharepoint/media/sp-state.png "Zustandsautomat-Workflow")

 Weitere Informationen zu Workflow Typen finden Sie unter [Workflow Typen](/previous-versions/office/developer/sharepoint-2010/ms468447(v=office.14)).

### <a name="use-the-wizard"></a>Verwenden des Assistenten
 Wenn Sie in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]ein SharePoint-Workflow Projekt erstellen, geben Sie die Einstellungen zunächst im Assistenten zum Anpassen von **SharePoint**an. Der Assistent verwendet diese Einstellungen zum Erstellen eines Projekts in **Projektmappen-Explorer**. Dieses Projekt enthält eine Codedatei, mehrere Dateien, die zum Bereitstellen des Workflows verwendet werden, sowie Verweise auf Assemblys, die zum Erstellen eines benutzerdefinierten SharePoint-Workflows erforderlich sind.

 Nachdem Sie den Workflow erstellt haben, können Sie seine Eigenschaften im Eigenschaftenfenster ändern. Obwohl die meisten Workflow Eigenschaften direkt in der Eigenschaftenfenster geändert werden können, müssen Sie auf eine Schaltfläche mit den Auslassungs Punkten (![ASP.NET Mobile Designer Ellipse](../sharepoint/media/mwellipsis.gif "Auslassungszeichen im ASP.NET Mobile-Designer")) klicken, um ihre Werte zu ändern. Mit dieser Schaltfläche wird der Assistent zum Anpassen von **SharePoint**neu gestartet. Nachdem Sie die Eigenschafts Wertänderungen vorgenommen haben, klicken Sie auf die Schaltfläche **Fertig** stellen, um Sie abzuschließen.

> [!NOTE]
> Die **Workflowtyp** -Eigenschaft ist schreibgeschützt und kann nicht geändert werden. Wenn Sie den Workflowtyp ändern möchten, müssen Sie einen weiteren Workflow erstellen.

## <a name="design-a-sharepoint-workflow"></a>Entwerfen eines SharePoint-Workflows
 Nachdem Sie alle Schritte im Geschäftsprozess definiert haben, verwenden Sie den [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Workflow-Designer, um den SharePoint-Workflow zu entwerfen. Um den Designer zu öffnen, doppelklicken Sie auf Workflow1.cs oder Workflow1. vb in **Projektmappen-Explorer**, oder öffnen Sie das Kontextmenü für eine dieser Dateien, und wählen Sie dann **Öffnen**aus.

### <a name="activities"></a>Aktivitäten
 Zum Entwerfen eines Workflows fügen Sie Aktivitäten aus der **Toolbox** einem *Workflow Zeitplan* im Designer hinzu. Ein Workflow Zeitplan enthält die Abfolge der Aktivitäten in der Reihenfolge, in der Sie ausgeführt werden sollen.

 Es gibt zwei Arten von Aktivitäten:

- *Einfache Aktivitäten* führen eine einzelne Arbeitseinheit aus, z. b. "Verzögerung für einen Tag" oder "Webdienst starten".

- Zusammen *gesetzte Aktivitäten* enthalten andere Aktivitäten. Beispielsweise kann eine bedingte Aktivität zwei Verzweigungen enthalten.

  Beide Arten von Aktivitäten sind in der **Toolbox**verfügbar.

  Aktivitäten können über Eigenschaften, Methoden und Ereignisse verfügen. Verwenden Sie das **Eigenschaften** Fenster, um die Eigenschaften einer Aktivität festzulegen.

  Sie können auch eine benutzerdefinierte Aktivität erstellen. Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Erstellen einer benutzerdefinierten Site Workflow Aktivität](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md).

  Aktivitäten werden auf den folgenden Registerkarten der **Toolbox**organisiert:

- **SharePoint-Workflow**

- **Windows Workflow v 3.0**

- **Windows Workflow v 3.5**

  Nicht alle Kern Workflow Aktivitäten werden von SharePoint unterstützt. Weitere Informationen finden Sie unter [Workflow Activities for Windows SharePoint Services Overview](/previous-versions/office/developer/sharepoint-2010/ms446847(v=office.14)).

#### <a name="sharepoint-workflow-activities"></a>SharePoint-Workflow Aktivitäten
 Die Registerkarten des **SharePoint-Workflows** enthalten spezialisierte Aktivitäten für die Verwendung in [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]. Diese Aktivitäten vereinfachen und vereinfachen die Entwicklung von Lebenszyklus Workflows für Dokumente. Weitere Informationen zu den auf der Registerkarte **SharePoint-Workflow** aufgeführten Aktivitäten finden Sie unter [Workflow Activities for Windows SharePoint Services Overview](/previous-versions/office/developer/sharepoint-2010/ms446847(v=office.14)).

#### <a name="windows-workflow-activities"></a>Windows Workflow-Aktivitäten
 Die Registerkarten **Windows Workflow** enthalten Aktivitäten, die vom [!INCLUDE[TLA#tla_workflow](../sharepoint/includes/tlasharptla-workflow-md.md)]bereitgestellt werden. Sie können diese Aktivitäten verwenden, um Workflow Zeitpläne für jede Art von Windows-Workflow Anwendung zu erstellen.

 Weitere Informationen zu den Aktivitäten, die auf der Registerkarte **Windows-Workflows** aufgelistet sind, finden Sie unter [Windows Workflow Foundation Aktivitäten](/previous-versions/dotnet/netframework-3.5/ms733615(v=vs.90)). Weitere Informationen zum Windows Workflow Foundation finden Sie unter [Windows Workflow Foundation Übersicht](/previous-versions/dotnet/netframework-3.5/ms734631(v=vs.90)).

### <a name="work-with-activities-in-the-designer"></a>Arbeiten mit Aktivitäten im Designer
 Der Workflow Zeitplan kann eine Kombination aus Windows Workflow-Aktivitäten und SharePoint-Workflow Aktivitäten enthalten.

 Der Designer zeigt visuelle Hinweise an, die Ihnen helfen, Aktivitäten ordnungsgemäß zu positionieren und zu konfigurieren. Beim ziehen oder Kopieren einer Aktivität auf den Workflow Zeitplan zeigt der Designer grüne Pluszeichen (+)-Symbole an, die Ihnen gültige Positionen für diese Aktivität im Workflow zeigen. Sie können eine Aktivität nicht an einem Speicherort positionieren, an dem Sie nicht gültig ist. Beispielsweise können Sie eine Send-Aktivität nicht als erste Aktivität in einer lausch Aktivitäts Verzweigung positionieren. Weitere Informationen finden Sie im [SharePoint Designer Developer Center](https://developer.microsoft.com/office/docs).

## <a name="collect-information-during-the-workflow"></a>Sammeln von Informationen während des Workflows
 Möglicherweise möchten Sie Informationen von Benutzern zu vordefinierten Zeitpunkten im Workflow sammeln. Informationen können mithilfe von Formularen oder Element Eigenschaften gesammelt werden.

### <a name="forms"></a>Formulare
 Formulare sind ähnliche Dialogfelder, die Fragen enthalten und Benutzern Möglichkeiten bieten, Antworten zu erhalten.

 Es gibt vier Arten von Formularen, die in einem Workflow verwendet werden können:

- Zuordnung

- Initiierung

- Änderung

- Aufgabe

  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] enthält Element Vorlagen für Zuordnungs-und Initiierungs Formulare. Ein Beispiel für ein Zuordnungs *Formular* besteht darin, dass der Administrator, der den Workflow installiert, die Parameter eingeben kann, die mit dem Workflow in Beziehung stehen, z. b. ein Ausgabenlimit für einen Ausgaben Workflow. Ein Beispiel für ein *Initiierungs Formular* ist eine, mit der der Benutzer eines Ausgaben Workflows den Betrag eingeben kann, den Sie im Workflow aufgewendet haben. Weitere Informationen zu diesen Formular Typen finden Sie unter [SharePoint-Projekt-und Projekt Element Vorlagen](../sharepoint/sharepoint-project-and-project-item-templates.md).

### <a name="item-properties"></a>Element Eigenschaften
 Sie können auch Informationen von Benutzern erfassen, indem Sie die Eigenschaften eines Elements in der SharePoint-Bibliothek oder-Liste verwenden. Die Haupt Codedatei (Workflow1.cs oder Workflow1. vb) deklariert eine Instanz der Klasse Microsoft. SharePoint. Workflow. SPWorkflowActivationProperties. workflowProperties mit dem Namen `workflowProperties`. Verwenden Sie das `workflowProperties`-Objekt, um auf die Eigenschaften der Bibliothek oder Liste im Code zuzugreifen. Ein Beispiel finden Sie unter Exemplarische Vorgehensweise [: Erstellen und Debuggen einer SharePoint-Workflow](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md)-Projekt Mappe.

## <a name="debug-a-sharepoint-workflow-template"></a>Debuggen einer SharePoint-Workflow Vorlage
 Sie können ein SharePoint-Workflow Projekt genauso Debuggen, wie Sie andere [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] webbasierte Projekte Debuggen. Wenn Sie den [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Debugger starten, verwendet [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] die Einstellungen, die Sie im Assistenten zum Anpassen von **SharePoint** angeben, um die entsprechende SharePoint-Website zu öffnen und die Workflow Vorlage der entsprechenden Bibliothek automatisch zuzuordnen. List. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fügt auch den [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Debugger an den [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]-Prozess mit dem Namen *w3wp. exe*an.

 Um den Workflow zu testen, müssen Sie ihn manuell starten. Weitere Informationen finden Sie im Abschnitt "Debuggen von Workflows" in [Debuggen von SharePoint-Lösungen](../sharepoint/debugging-sharepoint-solutions.md). Weitere Informationen zum Debuggen von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Webanwendungen finden Sie unter [Debug-Webanwendungen und Skript](../debugger/how-to-enable-debugging-for-aspnet-applications.md).

## <a name="deploy-a-sharepoint-workflow-template"></a>Bereitstellen einer SharePoint-Workflow Vorlage
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint-Workflow Projekte werden genau wie andere [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint-Projekte bereitgestellt. Weitere Informationen finden Sie unter [packen und Bereitstellen von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md).

## <a name="import-globally-reusable-workflows"></a>Importieren Global wiederverwendbarer Workflows
 Mit SharePoint Designer können Sie nicht nur Site spezifische, wiederverwendbare Workflows erstellen, sondern auch *Global wiederverwendbare Workflows*erstellen, bei denen es sich um Workflows handelt, die von jeder SharePoint-Website verwendet werden können. Das Projekt "wiederverwendbares Workflow importieren" in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] importiert derzeit keine Global wiederverwendbaren Workflows. Sie können jedoch entweder SharePoint Designer verwenden, um einen Global wiederverwendbaren Workflow in einen wiederverwendbaren Workflow zu konvertieren, oder den Workflow als nicht konvertierten deklarativen Workflow importieren. Weitere Informationen finden Sie unter [Importieren von Elementen aus einer vorhandenen SharePoint-Website](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).

## <a name="related-topics"></a>Verwandte Themen

|Titel|Beschreibung|
|-----------|-----------------|
|[Exemplarische Vorgehensweise: Erstellen und Debuggen einer SharePoint-Workflow Lösung](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md)|Führt Sie Schritt für Schritt durch das Erstellen und Debuggen eines einfachen [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Workflows.|
|[Exemplarische Vorgehensweise: Erstellen eines Workflows mit Zuordnungs-und Initiierungs Formularen](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)|Führt Sie Schritt für Schritt durch das Erstellen eines voll funktionsfähigen [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Workflows, der mit Zuordnungs-und Initiierungs Formularen vollständig ausgeführt wird.|
|[Exemplarische Vorgehensweise: Hinzufügen einer Anwendungsseite zu einem Workflow](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)|Baut auf dem Thema Exemplarische Vorgehensweise [: Erstellen eines Workflows mit Zuordnungs-und Initiierungs Formularen](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md) durch Hinzufügen einer zusätzlichen *aspx* -Anwendungsseite auf, mit der die in den Workflow eingegebenen Daten berichtet werden.|
|[Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Site Workflow-Aktivität](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md)|Veranschaulicht, wie zwei Hauptaufgaben ausgeführt werden: Erstellen eines Workflows auf Website Ebene und Erstellen einer benutzerdefinierten Workflow Aktivität.|
|[Exemplarische Vorgehensweise: Importieren eines wiederverwendbaren Workflows in SharePoint Designer in Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)|Veranschaulicht, wie wiederverwendbare deklarative Workflows importiert werden, die in SharePoint Designer 2010 erstellt wurden, in ein [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint-Projekt.|

## <a name="see-also"></a>Siehe auch

- [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)
- [Erstellen und Debuggen von SharePoint-Lösungen](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Erstellen von Anwendungs Seiten für SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)