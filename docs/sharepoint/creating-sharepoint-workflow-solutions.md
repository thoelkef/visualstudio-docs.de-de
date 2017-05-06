---
title: "Erstellen von SharePoint-Workflow-Projektmappen"
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
  - "VSTO.NewSharePointWorkflowWizard.Page3"
  - "VS.SharePointTools.Workflow.WorkflowName"
  - "VSTO.NewSharePointWorkflowWizard.Page2"
  - "VSTO.NewSharePointWorkflowWizard.Page1"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SharePoint-Entwicklung in Visual Studio, Workflows"
  - "Workflows [SharePoint-Entwicklung in Visual Studio]"
ms.assetid: fe79b99a-cb7c-4a14-8d9f-bce0c0805ba0
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Erstellen von SharePoint-Workflow-Projektmappen
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] beinhaltet Tools zum Erstellen von benutzerdefinierten Workflows, die zum Verwalten des Lebenszyklus von Dokumenten und zum Auflisten von Elementen auf einer SharePoint\-Website dienen.  Die bereitgestellten Elemente umfassen einen Designer, einen Satz von Aktivität steuert und die erforderlichen Assemblyverweise.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] enthält auch den **Assistenten zum Anpassen von SharePoint**, der Sie beim Erstellen und Konfigurieren der Workflows unterstützt.  
  
 Die Liste der erforderlichen Komponenten zum Erstellen von SharePoint\-Projekten in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] finden Sie unter [Anforderungen für die Entwicklung von SharePoint-Lösungen](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  Weitere Informationen zu SharePoint, Sie finden.[Microsoft SharePoint\-Produkt und\-Technologien](http://go.microsoft.com/fwlink/?LinkId=178470)  
  
## Workflows in SharePoint  
 Beim Hinzufügen eines Workflows zu einer SharePoint\-Bibliothek oder \-Liste erzwingen Sie einen Geschäftsprozess für alle Elemente in der Bibliothek oder der Liste.  Ein Workflow beschreibt die Aktionen, die vom System oder den Benutzern für jedes Element ausgeführt werden müssen. Dazu zählt beispielsweise das Senden eines Elements zur Bearbeitung und anschließenden Prüfung.  Diese Aktionen \(so genannte *Aktivitäten*\) sind die Bausteine des Workflows.  
  
 Sie können SharePoint\-Workflows in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] erstellen und auf einer SharePoint\-Website bereitstellen.  Nachdem ein Workflow in SharePoint bereitgestellt wurde, ordnen Sie ihn einer Bibliothek oder einer Liste zu.  Dann kann der Workflow automatisch, durch einen Prozess oder manuell durch einen Benutzer gestartet werden.  Weitere Informationen über Workflowvorgang, Sie finden [Mithilfe der Workflows, z von Prozessen zu verwalten](http://go.microsoft.com/fwlink/?LinkId=79757).  
  
## Erstellen von benutzerdefinierten SharePoint\-Workflows  
 Zwei SharePoint\-Workflowprojekte stehen in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] zur Verfügung: **Sequenzieller Workflow** und **Zustandsautomatworkflow**.  
  
 Ein *sequenzieller Workflow* stellt eine Reihe von Schritten dar.  Die Schritte werden nacheinander ausgeführt, bis die letzte Aktivität abgeschlossen wurde.  Sequenzielle Workflows sind in ihrer Ausführung immer streng sequenziell.  Da sie externe Ereignisse empfangen können und parallele Logikflüsse einschließen, kann die genaue Reihenfolge der Ausführung möglicherweise variieren.  Die folgende Darstellung zeigt ein Beispiel eines sequenziellen Workflows.  
  
 ![Sequenzieller Workflow](../sharepoint/media/sp-sequential.png "Sequenzieller Workflow")  
  
 Ein *Zustandsautomatworkflow* stellt einen Satz von Zuständen, Übergängen und Aktionen dar.  Die Schritte in einem Zustandsautomatworkflow werden asynchron ausgeführt.  Dies bedeutet, dass sie nicht notwendigerweise nacheinander ausgeführt, sondern von Aktionen und Zuständen ausgelöst werden.  Ein Zustand wird als Startzustand zugewiesen. Anschließend kann auf Grundlage eines Ereignisses ein Wechsel in einen anderen Zustand vollzogen werden.  Der Zustandsautomat kann einen abschließenden Zustand aufweisen, der das Ende des Workflows bestimmt.  Im folgenden Diagramm finden Sie ein Beispiel eines Zustandsautomatworkflows.  
  
 ![Zustandsautomatworkflow](../sharepoint/media/sp-state.png "Zustandsautomatworkflow")  
  
 Weitere Informationen zu Workflowtypen, Sie finden [Workflow\-Typen](http://go.microsoft.com/fwlink/?LinkId=178995).  
  
### Verwenden des Assistenten  
 Wenn Sie in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ein SharePoint\-Workflowprojekt erstellen, geben Sie zunächst die Einstellungen im **Assistenten zum Anpassen von SharePoint** an.  Der Assistent verwendet diese Einstellungen, um ein Projekt im **Projektmappen\-Explorer** zu erstellen.  Dieses Projekt beinhaltet eine Codedatei, mehrere Dateien, die zum Bereitstellen des Workflows verwendet werden, sowie Verweise auf Assemblys, die zum Erstellen eines benutzerdefinierten SharePoint\-Workflows vorhanden sein müssen.  
  
 Nachdem Sie den Workflow erstellt haben, können Sie die zugehörigen Eigenschaften im Eigenschaftenfenster ändern.  Obwohl die meisten Workfloweigenschaften direkt im Eigenschaftenfenster geändert werden können, müssen Sie bei einigen auf eine Schaltfläche mit Auslassungspunkten \(![Auslassungszeichen im ASP.NET Mobile-Designer](../sharepoint/media/mwellipsis.png "Auslassungszeichen im ASP.NET Mobile-Designer")\) klicken, um die Werte zu ändern.  Über diese Schaltfläche wird der **Assistent zum Anpassen von SharePoint** neu gestartet.  Nachdem Sie die Änderungen an den Eigenschaftswerten vorgenommen haben, wählen Sie die Schaltfläche **Fertig stellen**, um sie auszuführen.  
  
> [!NOTE]  
>  Die Eigenschaft **Workflowtyp** ist schreibgeschützt und kann nicht geändert werden.  Wenn Sie den Workflowtyp ändern möchten, müssen Sie einen anderen Workflow erstellen.  
  
## Entwerfen eines SharePoint\-Workflows  
 Nachdem Sie alle Schritte im Geschäftsprozess definiert haben, entwerfen Sie den SharePoint\-Workflow mithilfe des [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-Workflow\-Designers.  Um den Designer zu öffnen, doppelklicken Sie im **Projektmappen\-Explorer** auf Workflow1.cs oder Workflow1.vb, oder öffnen Sie das Kontextmenü für jede dieser Dateien und wählen Sie dann **Öffnen** aus.  
  
### Aktivitäten  
 Wenn Sie einen Workflow entwerfen möchten, fügen Sie einem *Workflowzeitplan* für den Designer Aktivitäten aus der **Toolbox** hinzu.  Ein Workflowzeitplan beinhaltet die Abfolge der Aktivitäten in der Reihenfolge, in der sie ausgeführt werden sollten.  
  
 Man unterscheidet zwei Arten von Aktivitäten:  
  
-   *Einfache Aktivitäten* dienen zum Ausführen einer einzelnen Arbeitseinheit, wie beispielsweise "Verzögerung für einen Tag" oder "Webdienst starten".  
  
-   *Zusammengesetzte Aktivitäten* beinhalten andere Aktivitäten; beispielsweise beinhaltet eine Bedingungsaktivität möglicherweise zwei Verzweigungen.  
  
 Beide Aktivitätstypen sind in der **Toolbox** verfügbar.  
  
 Aktivitäten können über Eigenschaften, Methoden und Ereignisse verfügen.  Legen Sie im Fenster **Eigenschaften** die Eigenschaften einer Aktivität fest.  
  
 Sie können auch eine benutzerdefinierte Aktivität erstellen.  Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Websiteworkflowaktivität](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md).  
  
 Aktivitäten sind auf den folgenden Registerkarten in der **Toolbox** organisiert:  
  
-   **SharePoint\-Workflow**  
  
-   **Windows Workflow v3.0**  
  
-   **Windows Workflow v3.5**  
  
 Nicht alle Kernworkflowaktivitäten werden von SharePoint unterstützt.  Weitere Informationen finden Sie unter [Workflow\-Aktivitäten für Windows SharePoint Services\-Übersicht](http://go.microsoft.com/fwlink/?LinkID=156094).  
  
#### SharePoint\-Workflowaktivitäten  
 Die Registerkarten **SharePoint\-Workflow** enthalten spezielle Aktivitäten zur Verwendung in [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)].  Diese Aktivitäten vereinfachen und optimieren die Entwicklung von Dokumentlebenszyklus\-Workflows.  Weitere Informationen zu den Aktivitäten, die auf der Registerkarte **SharePoint Workflow** aufgeführt werden, finden Sie unter [Workflow\-Aktivitäten für Windows SharePoint Services\-Übersicht](http://go.microsoft.com/fwlink/?LinkID=156094).  
  
#### Windows Workflow\-Aktivitäten  
 Die Registerkarten **Windows Workflow** enthalten Aktivitäten, die vom [!INCLUDE[TLA#tla_workflow](../sharepoint/includes/tlasharptla-workflow-md.md)] bereitgestellt werden.  Mit diesen Aktivitäten können Workflowzeitpläne für jede Art von Windows Workflow\-Anwendungen erstellt werden.  
  
 Weitere Informationen zu den Aktivitäten, die auf der Registerkarte **Windows Workflows** aufgeführt werden, finden Sie unter [Windows Workflow Foundation\-Aktivitäten](http://go.microsoft.com/fwlink/?LinkID=156096).  Weitere Informationen zur Windows Workflow Foundation, Sie finden [Windows Workflow Foundations\-Übersicht](http://go.microsoft.com/fwlink/?LinkID=128632).  
  
### Arbeiten mit Aktivitäten im Designer  
 Der Workflowzeitplan kann eine Kombination aus Windows Workflow\-Aktivitäten und SharePoint\-Workflowaktivitäten beinhalten.  
  
 Der Designer zeigt visuelle Hinweise an und unterstützt den Benutzer dadurch beim ordnungsgemäßen Positionieren und Konfigurieren von Aktivitäten.  Wird eine Aktivität in den Workflowzeitplan gezogen oder kopieren, zeigt der Designer grüne Pluszeichensymbole \(\+\) an, die gültige Positionen für diese Aktivität im Workflow zeigen.  Eine Aktivität darf nicht an einer Stelle positioniert werden, an der sie nicht gültig ist.  Beispielsweise kann eine Sendeaktivität nicht als erste Aktivität in einer Listen\-Aktivitätsverzweigung angeordnet werden.  Weitere Informationen finden Sie unter [SharePoint Designer\-Developer Center](http://go.microsoft.com/fwlink/?LinkId=178476).  
  
## Sammeln von Informationen während des Workflows  
 Unter Umständen möchten Sie Informationen von Benutzern zu vordefinierten Zeitpunkten im Workflow sammeln.  Sie können Informationen mithilfe von Formularen oder Elementeigenschaften sammeln.  
  
### Formulare  
 Formulare sind mit Dialogfeldern vergleichbar, die Fragen beinhalten und Möglichkeiten zur Angabe von Antworten bieten.  
  
 Es gibt vier Arten von Formularen, die in einem Workflow verwendet werden können:  
  
-   Zuordnung  
  
-   Initiierung  
  
-   Änderung  
  
-   Aufgabe  
  
 Hierfür schließt [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Elementvorlagen für Zuordnungs\- und Initiierungsformulare ein.  Ein Beispiel für ein *Zuordnungsformular* ist ein Formular, über das der Administrator, der den Workflow installiert, Parameter eingeben kann, die sich auf den Workflow beziehen, z. B. eine Ausgabengrenze für einen Kostenworkflow.  Ein Beispiel für ein Initiierungsformular ist ein, das der Benutzer eines Kostenworkflows der Menge eingeben kann, die in den ausgegebenen Betrag im Workflow.  Weitere Informationen zu diesen Formulartypen, finden Sie unter [Vorlagen für SharePoint-Projekte und Projektelemente](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
### Elementeigenschaften  
 Sie können auch Informationen von Benutzern sammeln, indem Sie die Eigenschaften eines Elements in der SharePoint\-Bibliothek oder \-Liste verwenden.  In der Hauptcodedatei \(Workflow1.cs oder Workflow1.vb\) wird eine Instanz der Microsoft.SharePoint.Workflow.SPWorkflowActivationProperties.WorkflowProperties\-Klasse mit der Bezeichnung `workflowProperties` deklariert.  Greifen Sie mithilfe des `workflowProperties`\-Objekts auf die Eigenschaften der Bibliothek oder Liste im Code zu.  Ein Beispiel finden Sie unter [Exemplarische Vorgehensweise: Erstellen und Debuggen einer SharePoint-Workflow-Projektmappe](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md).  
  
## Debuggen einer SharePoint\-Workflowvorlage  
 Das Debuggen eines SharePoint\-Workflowprojekts funktioniert ebenso wie bei anderen webbasierten [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-Projekten.  Beim Start des [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-Debuggers verwendet [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] die Einstellungen, die Sie im **Assistenten zum Anpassen von SharePoint** angeben, um die entsprechende SharePoint\-Website zu öffnen und die Workflowvorlage automatisch der entsprechenden Bibliothek oder Liste zuzuordnen.  Außerdem fügt [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] den [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-Debugger an den [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]\-Prozess "w3wp.exe" an.  
  
 Für einen Test des Workflows muss dieser manuell gestartet werden.  Weitere Informationen finden Sie im Abschnitt "Debuggen von Workflows" unter [Debuggen von SharePoint-Lösungen](../sharepoint/debugging-sharepoint-solutions.md).  Weitere Informationen zum Debuggen von Webanwendungen in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] finden Sie unter [Debuggen von Webanwendungen und Skripts](../debugger/debugging-web-applications-and-script.md).  
  
## Bereitstellen einer SharePoint\-Workflowvorlage  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-SharePoint\-Workflowprojekte werden wie andere [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-SharePoint\-Projekte bereitgestellt.  Weitere Informationen finden Sie unter [Verpacken und Bereitstellen von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md).  
  
## Importieren von global wiederverwendbaren Workflows  
 Zusätzlich zum Erstellen von websitespezifischen wiederverwendbaren Workflows können Sie mit SharePoint Designer *global wiederverwendbare Workflows* erstellen, die von jeder SharePoint\-Website verwendet werden können.  Das Projekt Wiederverwendbaren Workflow importieren in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] importiert derzeit keine global wiederverwendbaren Workflows.  Sie können einen global wiederverwendbaren Workflow jedoch mit SharePoint Designer in einen wiederverwendbaren Workflow konvertieren oder den Workflow ohne Konvertierung als deklarativen Workflow importieren.  Weitere Informationen finden Sie unter [Importieren von Elementen aus einer vorhandenen SharePoint-Website](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).  
  
## Verwandte Themen  
  
|Titel|**Beschreibung**|  
|-----------|----------------------|  
|[Exemplarische Vorgehensweise: Erstellen und Debuggen einer SharePoint-Workflow-Projektmappe](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md)|Enthält eine schrittweise Einführung in das Erstellen und Debuggen eines einfachen [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-Workflows.|  
|[Exemplarische Vorgehensweise: Erstellen eines Workflows mit Zuordnungs- und Initiierungsformularen](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)|Enthält eine schrittweise Einführung in das Erstellen eines [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-Workflows mit größerem Funktionsumfang, einschließlich von Zuordnungs\- und Initiierungsformularen.|  
|[Exemplarische Vorgehensweise: Hinzufügen einer Anwendungsseite zu einem Workflow](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)|Beruht auf dem Thema [Exemplarische Vorgehensweise: Erstellen eines Workflows mit Zuordnungs- und Initiierungsformularen](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md) und erläutert das Hinzufügen einer zusätzlichen ASPX\-Anwendungsseite, die in den Workflow eingegebene Daten meldet.|  
|[Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Websiteworkflowaktivität](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md)|Veranschaulicht, wie zwei Hauptaufgaben ausgeführt werden: Erstellen eines Workflows auf Websiteebene und Erstellen einer benutzerdefinierten Workflowaktivität.|  
|[Exemplarische Vorgehensweise: Importieren eines wiederverwendbaren Workflows aus SharePoint-Designer in Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)|Veranschaulicht, wie im SharePoint\-Designer 2010 erstellte wiederverwendbare, deklarative Workflows in ein [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-SharePoint Projekt importiert werden.|  
  
## Siehe auch  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)   
 [Erstellen und Debuggen von SharePoint-Lösungen](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [Erstellen von Anwendungsseiten für SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)  
  
  