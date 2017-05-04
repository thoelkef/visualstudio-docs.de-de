---
title: "Entwickeln von SharePoint-L&#246;sungen | Microsoft Docs"
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
  - "VS.SharePointTools.Project.ProjectProperties"
  - "VS.SharePointTools.Project.ProjectItemProperties"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SharePoint-Entwicklung in Visual Studio (Übersicht)"
ms.assetid: 059bce0f-c301-4234-a0b4-9c14b7cdfa3e
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 34
---
# Entwickeln von SharePoint-L&#246;sungen
  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sind mehrere SharePoint-Projekttypvorlagen zum Erstellen von SharePoint-Websites und -Websiteelementen verfügbar. Eine Liste der verfügbaren Projekttypen, finden Sie unter [SharePoint-Projekte und Projektelementvorlagen](../sharepoint/sharepoint-project-and-project-item-templates.md). Im Folgenden finden Sie eine Beschreibung der Elemente und Eigenschaften eines SharePoint-Projekts.

 Informationen zu SharePoint 2013 und SharePoint hinzufügen\-ins finden Sie unter [SharePoint 2013](http://msdn.microsoft.com/library/jj162979.aspx) und [Erstellen SharePoint hinzufügen\-ins](http://msdn.microsoft.com/library/office/apps/jj163230%28v=office.15%29.aspx).

## <a name="elements-of-a-sharepoint-project"></a>Elemente eines SharePoint-Projekts
 Die Knoten unter einem SharePoint-Projekt werden als *SharePoint-Elemente*bezeichnet. SharePoint-Elemente können auch eine oder mehrere Unterdateien enthalten, die als *SharePoint-Elementdateien*bezeichnet werden, z. B. [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] -Konfigurationsdateien, ASPX-Formulare usw.

 Statt Projekte mithilfe von Projektvorlagen zu erstellen, die bereits mit Projektelementdateien aufgefüllt sind, können Sie die Vorlage **Leeres Projekt** verwenden, um ein leeres SharePoint-Projekt zu erstellen, und dann manuell Projektelemente hinzufügen. SharePoint-Projekte können optional auch eine oder mehrere Funktionsdateien enthalten \(zur Aktivierung in SharePoint\) und eine Paketdatei, in dem das Projekt verteilt.

### <a name="special-nodes"></a>Spezifische Knoten
 Jedes SharePoint-Projekt enthält zwei Knoten, die nicht umbenannt, gelöscht, ausgeschnitten, kopiert oder aus dem Projekt gezogen werden können. Diese Knoten lauten wie folgt:

-   Features

-   Package

 Beide Knoten werden in allen SharePoint-Projekten stets angezeigt, auch wenn keine Funktionen oder Pakete für das Projekt definiert werden.

#### <a name="features-node"></a>Knoten Funktionen
 Der Knoten **Funktionen** enthält eine oder mehrere SharePoint-Projektfunktionen. Eine Funktion ist ein Container mit Erweiterungen für SharePoint. Nachdem eine Funktion auf einem SharePoint-Server bereitgestellt wurde, kann sie in Websitedefinitionen eingeschlossen oder von SharePoint-Administratoren auf SharePoint-Websites einzeln aktiviert werden. Weitere Informationen finden Sie unter [Verwenden von Features](http://go.microsoft.com/fwlink/?LinkID=147704).

 Wenn Sie ein Element zu einem SharePoint-Projekt hinzufügen, z. B. einen Inhaltstyp oder eine Listeninstanz, wird dieses einer Funktion im Knoten **Funktionen** hinzugefügt. Der Gültigkeitsbereich des Elements bestimmt, ob es einer neuen oder einer vorhandene Funktion hinzugefügt wird. Wenn das neue Element denselben Gültigkeitsbereich wie eine vorhandene Funktion aufweist, wird es der betreffenden Funktion hinzugefügt. Andernfalls wird das Element einer neuen Funktion hinzugefügt.

 Um eine Funktion manuell hinzuzufügen, führen Sie im Kontextmenü des Funktionsknotens den Befehl **Funktion hinzufügen** aus. Sie können den Inhalt einer Funktion mit dem Funktions-Designer anzeigen oder ändern. Weitere Informationen finden Sie unter [Gewusst wie: Anpassen eines SharePoint-Features](../sharepoint/how-to-customize-a-sharepoint-feature.md).

 Wenn einem SharePoint-Projekt eine Funktion hinzugefügt wird, wird diese im **Projektmappen-Explorer** als Knoten mit dem Standardnamen Funktion*x*.feature angezeigt, wobei *x* eine eindeutige Zahl ist. Nachdem eine Funktion auf dem SharePoint-Server bereitgestellt wurde, kann sie von einem SharePoint-Administrator aktiviert und somit für SharePoint-Websitebenutzer verfügbar gemacht werden.

#### <a name="package-node"></a>Knoten Paket
 Der Knoten **Paket** enthält eine einzelne Datei, die als Verteilungsmechanismus für das SharePoint-Projekt fungiert. Diese Datei als eine *Lösung**Paket*, ist. CAB\-basiert, mit ein. WSP-Erweiterung. Ein Lösungspaket ist eine zur Bereitstellung geeignete, wiederverwendbare Datei, die einen Satz von Funktionen, Websitedefinitionen und Assemblys enthält, die für SharePoint-Websites gelten, und die Sie einzeln aktivieren oder deaktivieren können. Der Knoten **Paket** enthält darüber hinaus immer eine Datei mit dem Namen Package.wspdef, eine [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] -Definitionsdatei für das Paket. Sobald ein Paket auf dem Server bereitgestellt wurde, auf dem SharePoint ausgeführt wird, kann der SharePoint-Administrator es installieren und die zugehörigen Funktionen aktivieren.

 Sie können anzeigen oder ändern Sie den Inhalt des Pakets im Paket-Designer entweder durch doppelte\-durch Klicken auf den Knoten des Pakets oder öffnen Sie das Kontextmenü, und wählen Sie dann **Öffnen**. Weitere Informationen finden Sie unter [Erstellen von SharePoint-Lösungspaketen](../sharepoint/creating-sharepoint-solution-packages.md).

## <a name="sharepoint-project-and-project-item-properties"></a>Eigenschaften von SharePoint-Projekten und -Projektelementen
 Die Eigenschaften von SharePoint-Projekten werden wie bei anderen [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] -Projekten im Eigenschaftenfenster und auf der Eigenschaftenseite angezeigt. Welche Eigenschaften angezeigt werden, hängt vom ausgewählten Knoten ab.

 Wenn ein SharePoint-Projekt, Projektelement, oder Projektelementdateiknoten im **Projektmappen-Explorer**ausgewählt wird, werden die folgenden Eigenschaften im Eigenschaftenfenster oder auf der Eigenschaftenseite angezeigt:

### <a name="project-properties"></a>Projekteigenschaften

|Eigenschaftenname|Beschreibung|
|-------------------|-----------------|
|Aktive Bereitstellungskonfiguration|Gibt die Reihe von Schritten an, die während der Bereitstellung ausgeführt werden. Weitere Informationen finden Sie unter [How to: Edit a SharePoint Deployment Configuration](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).|
|Assemblybereitstellungsziel|Bestimmt den Speicherort von *SharePoint-Anwendungsassemblys* . Gültige Werte sind *GlobalAssemblyCache* \(Standard\), oder *WebApplication*.<br /><br /> Wenn die Eigenschaft *Sandboxed Solution* auf **true**festgelegt ist, wird diese Eigenschaft deaktiviert.|
|Automatische\-Nach Debuggen zurückziehen|Gibt an, ob die bereitgestellte Projektmappe in SharePoint automatisch zurückgezogen wird, nachdem Sie die Anwendung im Debugmodus in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]ausgeführt haben. Wenn diese Option ausgewählt ist, wird die Projektmappe zurückgezogen, wenn die IDE nach dem Debugging zurück zur Entwurfsansicht wechselt. Wenn die Option nicht ausgewählt ist, wird die Projektmappe nicht zurückgezogen. Weitere Informationen finden Sie unter [Deinstallieren und Zurückziehen einer Farmlösung](http://go.microsoft.com/fwlink/?LinkId=183819).|
|Konfigurationen bearbeiten|Gibt die Bereitstellungskonfiguration an, die für das Projekt verwendet werden soll. Weitere Informationen finden Sie unter [Gewusst wie: Bearbeiten einer SharePoint-Bereitstellungskonfiguration](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) und [bereitstellen, veröffentlichen und Aktualisieren von SharePoint-Lösungspaketen](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).|
|Silverlight-Debugging aktivieren \(anstelle von Skript-debugging\)|Wenn diese Option ausgewählt ist, wird der Silverlight-Debugger an den Debugprozess angefügt. Ist die Option nicht ausgewählt, wird der Skriptdebugger an den Debugprozess angefügt. Weitere Informationen finden Sie unter [Übersicht zum Debuggen mit Silverlight](http://go.microsoft.com/fwlink/?LinkId=179826).|
|Assembly in Paket einschließen|Gibt an, ob die Projektassembly zur Buildzeit verpackt wird.|
|Post\-Bereitstellung über die Befehlszeile|Gibt die Befehle an, die nach dem Bereitstellen der SharePoint-Lösung ausgeführt werden sollen. Diese Zeile unterstützt alle Batchbefehle sowie die Auflösung von MSBuild-Variablen. Weitere Informationen finden Sie unter [How to: Set SharePoint Deployment Commands](../sharepoint/how-to-set-sharepoint-deployment-commands.md).|
|Vor\-Bereitstellung über die Befehlszeile|Gibt die Befehle an, die vor dem Bereitstellen der SharePoint-Lösung ausgeführt werden sollen. Diese Zeile unterstützt alle Batchbefehle sowie die Auflösung von MSBuild-Variablen. Weitere Informationen finden Sie unter [How to: Set SharePoint Deployment Commands](../sharepoint/how-to-set-sharepoint-deployment-commands.md).|
|Projektdatei|Der Name der Datei, die Build- und Konfigurationsinformationen sowie andere Informationen zum Projekt enthält.|
|Projektordner|Der Speicherort der Projektdatei im System. \(Lesen\-nur.\)|
|Sandboxed Solution|Gibt an, ob das Projekt soll, als bereitgestellt werden ein *Sandbox-Lösung*, auch bekannt als ein *Benutzer\--Lösung erstellt*. Sandkastenlösungen sind nicht notwendigerweise vertrauenswürdig. Der Wert **true** bedeutet, dass das Projekt als Sandkastenlösung bereitgestellt wird. Der Wert **false** heißt, dass das Projekt als Farmlösung bereitgestellt wird. Weitere Informationen finden Sie unter [Sandboxed Solution Considerations](../sharepoint/sandboxed-solution-considerations.md) und [Differences Between Sandboxed and Farm Solutions](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).|
|Website-URL|Gibt die [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] der Zielwebsite für das Projekt an.|
|Startelement|Gibt das erste auszuführende Element im Projekt an.|

 Wenn Sie eine SharePoint-Elementdatei auswählen \(wie z. B. ein Workflow oder eine Funktion im Knoten Funktionen\), die folgenden Eigenschaften im Fenster Eigenschaften angezeigt:

### <a name="project-item-properties"></a>Eigenschaften von Projektelementen

|Eigenschaftenname|Beschreibung|
|-------------------|-----------------|
|Bereitstellungskonfliktlösung|Gibt die zu ergreifende Maßnahme beim Bereitstellen eines Projektelements an, dessen Eigenschaften mit denen eines bereits auf dem Server vorhandenen Elements identisch sind. Weitere Informationen finden Sie unter [Troubleshooting SharePoint Packaging and Deployment](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).|
|Featureeigenschaften|Gibt einen Satz von Werten \(gespeichert als Schlüssel\/-Wert-Paare\) die beim Bereitstellen für SharePoint in eine Funktion eingeschlossen wird. Nach dem Bereitstellen der Funktion können Sie im Code auf die Eigenschaftswerte zugreifen. Weitere Informationen finden Sie unter [Providing Packaging and Deployment Information in Project Items](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|
|Funktionsempfänger|Stellt Code bereit, der ausgeführt wird, wenn für die Funktion, in der ein Projektelement enthalten ist, bestimmte Ereignisse auftreten. Weitere Informationen finden Sie unter [Providing Packaging and Deployment Information in Project Items](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|
|Ordnername|Der Name des SharePoint-Projektelementordners.|
|Projektausgabeverweise|Gibt eine Abhängigkeit (z. B. eine Assembly) an, die zum Ausführen des Projektelements benötigt wird. Weitere Informationen finden Sie unter [Providing Packaging and Deployment Information in Project Items](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|
|Einträge für sicheres Steuerelement|Gibt Steuerelemente an, die sicher sind und von nicht vertrauenswürdigen Benutzern bearbeitet werden können. Weitere Informationen finden Sie unter [Providing Packaging and Deployment Information in Project Items](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|

### <a name="project-item-file-properties"></a>Eigenschaften von Projektelementdateien

|Eigenschaftenname|Beschreibung|
|-------------------|-----------------|
|Buildvorgang|Gibt die Beziehung der Datei zu den Build- und Bereitstellungsvorgängen an. Weitere Informationen finden Sie unter [Dateieigenschaften](http://msdn.microsoft.com/library/0c6xyb66(v=vs.100).aspx).|
|In Ausgabeverzeichnis kopieren|Gibt an, ob die Quelldatei\(s\) in das Ausgabeverzeichnis kopiert werden. Kann einer der folgenden Werte sein:<br /><br /> -   *Nicht kopieren*<br />-   *Immer kopieren*<br />-   *Kopieren, wenn neuer*<br /><br /> Weitere Informationen finden Sie unter [Dateieigenschaften](http://msdn.microsoft.com/library/0c6xyb66(v=vs.100).aspx).|
|Benutzerdefiniertes Tool|Gibt ggf. den Namen eines Tools an, das die Datei zur Entwurfszeit umwandelt und die Ausgabe der Umwandlung in einer anderen Datei platziert. Angenommen, ein Dataset \(.[!INCLUDE[TLA2#tla_xsd](../sharepoint/includes/tla2sharptla-xsd-md.md)]\) Datei hat ein benutzerdefiniertes Standardtool. Weitere Informationen finden Sie unter [Dateieigenschaften](http://msdn.microsoft.com/library/0c6xyb66(v=vs.100).aspx).|
|Namespace des benutzerdefinierten Tools|Der Namespace, in den die Ausgabe des benutzerdefinierten Tools kopiert wird. Weitere Informationen finden Sie unter [Dateieigenschaften](http://msdn.microsoft.com/library/0c6xyb66(v=vs.100).aspx).|
|Bereitstellungsspeicherort|Der vollständig\-Pfad der Datei auf dem SharePoint-Server. Dieser Pfad besteht aus den untergeordneten Bereitstellungsstamm- und Bereitstellungspfad\-Eigenschaften.|
|Bereitstellungspfad|Der relative Pfad der Datei auf dem SharePoint-Serverdatei, z. B. Workflow1\\. Der vollständig\-Pfad für die Datei wird erstellt, durch die Verkettung der *Bereitstellungspfad* Wert an das Ende der *Deployment Root* Wert.<br /><br /> Auswählen eines Werts von *RootFile* für die *Bereitstellungstyp* -Eigenschaft ändert die *Deployment Root* -Eigenschaft in {SharePointRoot}\\, was zu einer vollständig\-gekennzeichnete Pfad der {SharePointRoot}\\Workflow1\\. Weitere Informationen finden Sie unter [Verpacken und Bereitstellen von SharePoint Solutions](../sharepoint/packaging-and-deploying-sharepoint-solutions.md).|
|Deployment Root|Zeichenfolge. Der Stammordner, in dem die Datei auf dem SharePoint-Server bereitgestellt wird. Z. B. {SharePointRoot}\\Vorlage\\Funktionen\\{FeatureName}\\.<br /><br /> Der Wert der *Deployment Root* -Eigenschaft wird vom Wert der *Deployment Type* -Einstellung bestimmt.|
|Deployment Type|Der Bereitstellungstyp der Datei, der den zugehörigen *Deployment Root* -Wert bestimmt. Kann einer der folgenden Werte sein:<br /><br /> NoDeployment: \<kein Wert\><br /><br /> ElementManifest: {SharePointRoot}\\Vorlage\\Funktionen\\{FeatureName}\\<br /><br /> ElementFile: {SharePointRoot}\\Vorlage\\Funktionen\\{FeatureName}\\<br /><br /> TemplateFile: {SharePointRoot}\\Vorlage\\<br /><br /> RootFile: {SharePointRoot}\\<br /><br /> GlobalResource: {SharePointRoot}\\Ressourcen\\<br /><br /> ClassResource: {ClassResourcePath}\\<br /><br /> Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.SharePoint.DeploymentType>.|
|Dateiname|Der Name der Datei oder des Ordners für die Elementdatei.|
|Vollständiger Pfad|Der Speicherort der Datei für das Element. \(Lesen\-nur.\)|

## <a name="related-topics"></a>Verwandte Themen

|Titel|Beschreibung|
|-----------|-----------------|
|[SharePoint-Projekte und Projektelementvorlagen](../sharepoint/sharepoint-project-and-project-item-templates.md)|Beschreibt die in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]verfügbaren Vorlagen für SharePoint-Projekte und Projektelemente.|
|[Gewusst wie: Hinzufügen von Elementen zu einem SharePoint-Projekt](../sharepoint/how-to-add-items-to-a-sharepoint-project.md)|Beschreibt, wie einem [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] -SharePoint-Projekt neue oder vorhandene Elemente hinzugefügt werden.|
|[Exemplarische Vorgehensweise: Erstellen einer Websitespalte, den Inhaltstyp und die Liste für SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)|Führt Sie schrittweise\-durch\-Schritt in einem Feld, Inhaltstyp, Listendefinition und Listeninstanz erstellen.|
|[Gewusst wie: Erstellen eines Ereignisempfängers](../sharepoint/how-to-create-an-event-receiver.md)|Beschreibt das Hinzufügen ein Ereignisempfängers für das Projekt erstellt haben, [Exemplarische Vorgehensweise: Erstellen einer Websitespalte, den Inhaltstyp und die Liste für SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md).|
|[Erstellen von SharePoint-Workflow-Projektmappen](../sharepoint/creating-sharepoint-workflow-solutions.md)|Beschreibt, wie Workflowprojekte erstellt werden, die Workflowzuordnungsformulare und Workflowinitiierungsformulare einschließen.|
|[Erstellen von Seiten für SharePoint](../sharepoint/creating-pages-for-sharepoint.md)|Beschreibt, wie Sie Seiten (beispielsweise Anwendungsseiten, Websiteseiten, Gestaltungsvorlagen und Seitenlayouts) für SharePoint erstellen können.|
|[Erstellen von Webparts für SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)|Beschreibt, wie Sie Steuerelemente hinzufügen, mit denen Benutzer Inhalt, Darstellung und Verhalten der Seiten einer SharePoint-Website direkt im Browser ändern können.|
|[Erstellen von Wiederverwendbaren Steuerelementen für Webparts oder Anwendungsseiten](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|Beschreibt, wie Benutzersteuerelemente erstellt werden, die von Anwendungsseiten und Webparts genutzt werden können, die in SharePoint ausgeführt werden.|
|[Integrieren von Geschäftsdaten in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)|Beschreibt, wie Sie Daten von Webdiensten integrieren und wieder\-serveranwendungen in eine SharePoint-Anwendung zu beenden.|
|[Erstellen von Websitedefinitionen für SharePoint](../sharepoint/creating-site-definitions-for-sharepoint.md)|Beschreibt, wie Websitedefinitionen erstellt werden: Vorlagen, die zum Erstellen von SharePoint-Websites verwendet werden.|
|[Importieren von Elementen aus einer vorhandenen SharePoint-Website](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)|Beschreibt, wie Elemente wie Inhaltstypen und Module von einer vorhandenen SharePoint-Website in ein [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] -SharePoint-Projekt importiert werden.|
|[Verwenden von Modulen zum Einfügen von Dateien in der Projektmappe](../sharepoint/using-modules-to-include-files-in-the-solution.md)|Beschreibt, wie Module verwendet werden, um Dateien aus dem [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] -Projekt auf der SharePoint-Website bereitzustellen.|
|[Durchsuchen von SharePoint-Verbindungen mit dem Server-Explorer](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)|Beschreibt, wie lokale SharePoint-Websites mit Server-Explorer durchsucht werden.|
|[Bereitstellen von Pack- und Bereitstellungsinformationen in Projektelementen](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)|Beschreibt, wie Projektelementeigenschaften verwendet werden, um Verpackungs- und Bereitstellungsinformationen für Projekte bereitzustellen, z. B. Einträge für sichere Steuerelemente, Projektausgabeverweise und Funktionseigenschaften.|
|[Gewusst wie: Hinzufügen und entfernen zugeordneter Ordner](../sharepoint/how-to-add-and-remove-mapped-folders.md)|Beschreibt, wie dem Projekt zugeordnete Ordner hinzugefügt werden können, um den Zugriff auf SharePoint-Ressourcen zu erleichtern.|
|[Überlegungen zu Sandkastenlösungen](../sharepoint/sandboxed-solution-considerations.md)|Beschreibt die mit Sandkastenlösungen zusammenhängenden Probleme.|
|[Sicherheit für SharePoint-Lösungen](../sharepoint/security-for-sharepoint-solutions.md)|Erläutert Sicherheitsaspekte bei der Entwicklung von SharePoint-Lösungen in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].|
|[URL-Auswahldialogfeld &#40; SharePoint-Entwicklung in Visual Studio &#41;](../sharepoint/url-picker-dialog-box-sharepoint-development-in-visual-studio.md)|Beschreibt ein Dialogfeld, mit dem Sie Pfadverweise auf Ressourcen im Projekt oder auf dem lokalen SharePoint-Server hinzufügen können.|

## <a name="see-also"></a>Siehe auch
 [Erste Schritte &#40; SharePoint-Entwicklung in Visual Studio &#41;](../sharepoint/getting-started-sharepoint-development-in-visual-studio.md) 
 [Durchsuchen von SharePoint-Verbindungen mit dem Server-Explorer](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md) 
 [Erstellen und Debuggen von SharePoint-Lösungen](../sharepoint/building-and-debugging-sharepoint-solutions.md) 
 [Verpacken und Bereitstellen von SharePoint Solutions](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)

  