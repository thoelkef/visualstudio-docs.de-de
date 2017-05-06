---
title: "Vorlagen f&#252;r SharePoint-Projekte und Projektelemente"
ms.custom: ""
ms.date: "02/22/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.SPE.FirstWizardPage"
  - "VS.SharePointTools.SPE.ListInstance"
  - "VS.SharePointTools.SPE.ListDefinition"
  - "VS.SharePointTools.SPE.ListDefFromContentType"
  - "VS.SharePointTools.SPE.ContentType"
  - "SPE.Wizard"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SharePoint-Entwicklung in Visual Studio, Vorlagen für Projekte und Projektelemente"
  - "SharePoint-Entwicklung in Visual Studio, Vorlagen"
ms.assetid: 54a7576f-d3f9-475d-8ed7-b675ad21cb53
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 40
---
# Vorlagen f&#252;r SharePoint-Projekte und Projektelemente
  In den folgenden Abschnitten werden die in SharePoint verfügbaren Projekte und Projektelementvorlagen sowie deren Verwendung beschrieben.  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
##  <a name="project_items_templates_overview"></a> Übersicht über Vorlagen für SharePoint\-Projekte und Projektelemente  
 Beim Erstellen eines neuen SharePoint\-Projekts in Visual Studio wird dieses zusammen mit allen für den entsprechenden Projekttyp erforderlichen Projektelementen der Projektmappe hinzugefügt.  Wenn Sie beispielsweise ein Silverlight\-Webpartprojekt erstellen, wird von Visual Studio eine Projektmappe mit einem "Visuelles Webpart"\-Projektelement und einem Silverlight\-Anwendungsprojektelement erstellt, die auch alle für diese Projektelemente erforderlichen Dateien enthält.  Projektelementvorlagen werden verwendet, um einem vorhandenen SharePoint\-Projekt Projektelemente hinzuzufügen, z. B. Ereignisempfänger, Websitespalten oder Listen.  
  
 Grundlegende Informationen zu SharePoint finden Sie unter [Bausteine von SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=179404).  Fortgeschrittene Benutzer können angepasste Projekt\- und Projektelementvorlagen erstellen.  Weitere Informationen finden Sie unter [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md).  
  
##  <a name="project_templates"></a> Projektvorlagen  
 Im Folgenden finden Sie eine Liste von SharePoint\-Projektvorlagen.  Zum Anzeigen der SharePoint\-Projektvorlagen in Visual Studio erweitern Sie im Dialogfeld **Neues Projekt** unter entweder **Visual C\#** oder **Visual Basic** den **SharePoint**\-Knoten und wählen dann **2010** aus.  
  
### SharePoint 2010\-Projekt  
 Jede SharePoint\-Projektvorlage weist den Inhalt eines *SharePoint 2010\-Projekts* auf.  Ein SharePoint 2010\-Projekt enthält:  
  
-   Eine Projektdatei.  
  
-   Eine Projekteigenschaftenseite.  
  
-   Einen Ordner **Verweise**, in dem alle Assemblyverweise des Projekts aufgeführt werden.  
  
-   Einen Ordner **Funktionen** mit einer FEATURE\-Konfigurationsdatei zum Bereitstellen von Funktionen auf dem SharePoint\-Server.  
  
-   Ein Ordner **Paket** mit einer "Package.package"\-Datei zum Bereitstellen der Lösung auf SharePoint.  
  
-   Eine "key.snk"\-Datei \(Schlüssel mit starkem Namen\), um die Assembly zwecks verbesserter Sicherheit mit einem starken Namen zu signieren.  
  
### SharePoint 2010 Silverlight\-Webpart  
 Mithilfe des *SharePoint 2010 Silverlight\-Webpartprojekts* können Sie Webparts für SharePoint erstellen, von denen Silverlight\-Anwendungen angezeigt werden.  Beim Erstellen dieses Projekts können Sie angeben, ob eine neue Silverlight\-Anwendung hinzugefügt oder auf eine vorhandene verwiesen werden soll.  Weitere Informationen finden Sie unter [Erstellen von Webparts für SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) und [Exemplarische Vorgehensweise: Erstellen eines Silverlight-Webparts, das OData für SharePoint anzeigt](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).  
  
### Visuelles SharePoint 2010\-Webpart  
 Ein *Visuelles SharePoint 2010\-Webpart*\-Projekt enthält eine "Elements.xml"\-Definitionsdatei, ein **Webpart**\-Element und ein **Benutzersteuerelement**.  Sie können die Darstellung des visuellen Webparts durch Ziehen oder Kopieren der Steuerelemente von der Visual Studio\-Toolbox auf die Oberfläche des Benutzersteuerelements entwerfen.  Weitere Informationen finden Sie unter [Gewusst wie: Erstellen eines SharePoint-Webparts mithilfe eines Designers](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) und [Baustein: Webparts](http://go.microsoft.com/fwlink/?LinkId=179438).  
  
### SharePoint 2010\-Lösungspaket importieren  
 Mit dem *SharePoint 2010\-Lösungspaket importieren*\-Projekt können Sie eine vorhandene SharePoint 2010\-Website, die in eine SharePoint\-Lösungsdatei \(WSP\-Datei\) exportiert wurde, vollständig oder teilweise in Visual Studio importieren.  Nach dem Importieren in Visual Studio können Sie die zugehörigen Elemente anpassen und erneut bereitstellen.  Weitere Informationen finden Sie unter [Importieren von Elementen aus einer vorhandenen SharePoint-Website](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).  
  
### Wiederverwendbaren SharePoint 2010\-Workflow importieren  
 Mit *Wiederverwendbaren SharePoint\-2010 Workflow importieren*\-Projekten können Sie einen mit SharePoint Designer 2010 erstellten, wiederverwendbaren deklarativen Workflow in Visual Studio importieren.  Der Workflow wird als WSP\-Datei von der SharePoint\-Website exportiert.  Nach dem Importieren in Visual Studio können Sie den Workflow anpassen, Code hinzufügen und anschließend auf einer SharePoint\-Website bereitstellen.  Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Importieren eines wiederverwendbaren Workflows aus SharePoint-Designer in Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md).  
  
##  <a name="project_item_templates"></a> Projektelementvorlagen  
 Im Folgenden finden Sie eine Liste von SharePoint\-Projektelementvorlagen.  Durch Projektelementvorlagen werden der SharePoint\-Lösung Dateien zur Unterstützung von SharePoint\-Funktionalität hinzugefügt, z. B. Websitespalten, Listen und Inhaltstypen.  Beispielsweise wird durch das Hinzufügen einer Websitespalte zur Lösung ein Websitespaltenprojekt mit einer "Elements.xml"\-Definitionsdatei hinzugefügt.  Durch das Hinzufügen eines visuellen Webparts wird der Projektmappe ein visuelles Webpartprojekt mit einer "Elements.xml"\-Datei, einem Benutzersteuerelement und einem visuellem Webpartelement hinzugefügt.  
  
 Öffnen Sie zum Anzeigen der SharePoint\-Projektelementvorlagen im **Projektmappen\-Explorer** das Kontextmenü eines SharePoint\-Projekts, und wählen Sie dann **Hinzufügen** und **Neues Element** aus.  Erweitern Sie unter **Visual C\#** oder **Visual Basic** den **SharePoint**\-Knoten, und wählen Sie dann **2010** aus.  
  
### Anwendungsseite \(nur Farmlösung\)  
 Mit einem **Anwendungsseite \(nur Farmlösung\)**\-Element können Sie eine [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]\-Webseite für eine SharePoint\-Website entwerfen.  Anwendungsseiten können nur in Farmlösungen verwendet werden.  Dieses Projektelement kann nur Farmlösungen hinzugefügt werden.  Weitere Informationen finden Sie unter [Gewusst wie: Erstellen einer Anwendungsseite](../sharepoint/how-to-create-an-application-page.md) und [Anwendungsseitentyp "\_layouts"](http://go.microsoft.com/fwlink/?LinkId=179434).  
  
### Business Data Connectivity\-Modell \(nur Farmlösung\)  
 Mit einem **Business Data Connectivity\-Modell \(nur Farmlösung\)**\-Element können Sie Geschäftsdaten in SharePoint integrieren.  Geschäftsdaten können von Back\-End\-Serveranwendungen stammen, z. B. [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)], Siebel und Service Advertising Protocol \(SAP\).  Business Data Connectivity\-Modelle können nur in Farmlösungen verwendet werden.  Dieses Projektelement kann nur Farmlösungen hinzugefügt werden.  Weitere Informationen finden Sie [Gewusst wie: Erstellen eines BDC-Modells](../sharepoint/how-to-create-a-bdc-model.md), [Gewusst wie: Angeben von lokalisierten Namen, Eigenschaften und Berechtigungen mithilfe einer Ressourcendatei](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md) und [Neuigkeiten: Business Connectivity Services](http://go.microsoft.com/fwlink/?LinkId=179411).  
  
### Inhaltstyp  
 Mit *Inhaltstyp*\-Elementen können Sie benutzerdefinierte Inhaltstypen auf Grundlage eines vorhandenen \(grundlegenden\) Inhaltstyps erstellen, z. B. ein Dokument, eine Ankündigung oder eine Aufgabe.  Von einem benutzerdefinierten Inhaltstyp werden neben denselben Attributen und Feldern wie vom grundlegenden Inhaltstyp auch alle definierten Websitespalten \(Felder\) bereitgestellt.  Beispielsweise können Sie einen benutzerdefinierten Inhaltstyp "Kontakt" erstellen, der auf dem grundlegenden Inhaltstyp "Kontakt" aus SharePoint basiert.  Sie können den Inhaltstyp anpassen, indem vorhandene Websitespalten ändern oder zusätzliche Websitespalten zu den bereits im grundlegenden Inhaltstyp enthaltenen hinzufügen.  
  
> [!NOTE]  
>  Aufgrund einer SharePoint\-Einschränkung können Sie keinen Farmprojektmappeninhaltstyp auf Grundlage eines Sandkastenlösungsinhaltstyps erstellen.  
  
 Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer Websitespalte, eines Inhaltstyps und einer Liste für SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) und [Baustein: Inhaltstyp](http://go.microsoft.com/fwlink/?LinkId=179413).  
  
### Leeres Element  
 *Leere Elemente* werden häufig zum Definieren von SharePoint\-Projektelementen verwendet, für die in Visual Studio ein Projekt oder eine Projektvorlage fehlt.  Wenn Sie Ihrem Projekt ein leeres Element hinzufügen, wird ein Knoten mit dem Namen "EmptyElement\[x\]" \(wobei \[x\] eine eindeutige Zahl ist\) erstellt.  "EmptyElement\[x\]" enthält eine einzelne Datei mit dem Namen "Elements.xml".  Mithilfe von [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]\-Anweisungen können Sie die gewünschten Elemente in "Elements.xml" definieren.  
  
### Ereignisempfänger  
 *Ereignisempfänger* behandeln Ereignisse für Elemente auf der SharePoint\-Website, z. B. das Hinzufügen eines Elements zu einer Liste, das Löschen eines Webelements oder das Starten eines Workflows.  Die Projektelementvorlage "Ereignisempfänger" ermöglicht die Behandlung folgender Elemente:  
  
-   Listenereignisse  
  
-   Listenelementereignisse  
  
-   Listen\-E\-Mail\-Ereignisse  
  
-   Webereignisse  
  
-   Listenworkflowereignisse  
  
 Vom Projektelement "Ereignisempfänger" wird der Ordner **Ereignisempfänger** erstellt, der eine einzelne Klassendatei mit Ereignishandlern für alle Ereignisse enthält, die Sie im **Assistent zum Anpassen von SharePoint** beim Erstellen des Projekts angegeben haben.  Mit der event receiver\-Klasse können Ereignisse behandelt werden, die auf der SharePoint\-Website auftreten, wenn Elemente wie Dateien, Felder, Elemente, Listen, Anlagen, Webparts und Workflows hinzugefügt, aktualisiert, gelöscht oder entfernt werden.  Weitere Informationen finden Sie unter [Gewusst wie: Erstellen eines Ereignisempfängers](../sharepoint/how-to-create-an-event-receiver.md) und [Baustein: Ereignisbehandlung](http://go.microsoft.com/fwlink/?LinkId=179416).  
  
### List  
 Bei einer Liste handelt es sich um eine Instanz einer wiederverwendbaren, grundlegenden SharePoint\-Listendefinition, z. B. ein Kalender oder eine Aufgabenliste.  Nach dem Hinzufügen einer Liste zu Ihrer Lösung können Sie mit dem Listen\-Designer Websitespalten zur Liste hinzufügen und benutzerdefinierte Listenspalten erstellen.  Dazu gehören Websitespalten aus Inhaltstypen.  Durch Angabe der *Ansicht* für die Liste wird festgelegt, welche der Spalten in der Liste angezeigt werden.  Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer Websitespalte, eines Inhaltstyps und einer Liste für SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) und [Baustein: Listen und Dokumentbibliotheken](http://go.microsoft.com/fwlink/?LinkId=179421).  
  
### Modul  
 *Module* \(nicht zu verwechseln mit [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]\-Modulen enthalten alle Dateien, die Sie auf dem SharePoint\-Server bereitstellen möchten, z. B. Bilder oder Notizen.  Das Modulprojektelement weist einen **Modul**\-Knoten auf.  Der Modulknoten enthält zwei Projektelementvorlagen: eine XML\-Definitionsdatei, die als Manifest für das Modul fungiert, und die Platzhalterdatei "sample.txt".  Weitere Informationen finden Sie unter [Verwenden von Modulen zum Einfügen von Dateien in die Projektmappe](../sharepoint/using-modules-to-include-files-in-the-solution.md) und [Module](http://go.microsoft.com/fwlink/?LinkId=179425).  
  
### Sequenzieller Workflow \(nur Farmlösung\)  
 Ein *sequenzieller Workflow* stellt eine Reihe von Geschäftslogikschritten dar, die nacheinander bis zum letzten Schritt ausgeführt werden.  Sequenzielle Workflows werden verwendet, um Prozesse zu verwalten, die SharePoint\-Elemente wie Listen und Dokumente einschließen.  Sie können Workflows auf Websiteebene \(global\) oder auf Listenebene \(lokal\) erstellen, und Sie können auswählen, ob ein Workflow automatisch oder manuell startet.  Dieses Projektelement kann nur in Farmlösungen verwendet werden.  Dieses Projektelement kann nur Farmlösungen hinzugefügt werden.  Weitere Informationen finden Sie unter [Erstellen von SharePoint-Workflow-Projektmappen](../sharepoint/creating-sharepoint-workflow-solutions.md), [Workflows in SharePoint Server 2010](http://go.microsoft.com/fwlink/?LinkId=260555) und [Neuigkeiten: Verbesserungen bei Workflows](http://go.microsoft.com/fwlink/?LinkId=179418).  
  
### Silverlight\-Webpart  
 Mit Projektelementen für *Silverlight\-Webparts* können Sie Webparts für SharePoint erstellen, in denen Silverlight\-Anwendungen angezeigt werden.  Wenn Sie dieses Projektelement in Ihre Lösung einfügen, können Sie entweder eine neue Silverlight\-Anwendung hinzufügen oder zu einem späteren Zeitpunkt auf eine vorhandene verweisen.  Weitere Informationen finden Sie unter [Erstellen von Webparts für SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) und [Exemplarische Vorgehensweise: Erstellen eines Silverlight-Webparts, das OData für SharePoint anzeigt](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).  
  
### Websitespalte  
 Bei einer *Websitespalte*, auch als *Feld* bezeichnet, handelt es sich um eines der grundlegendsten Elemente, die einem SharePoint\-Projekt hinzugefügt werden können.  Eine Websitespalte stellt einen Datentyp dar, z. B. eine Telefonnummer, ein Textkommentar oder der Name der Stadt eines Kontakts in einer Kontaktliste.  Weitere Informationen finden Sie unter [Erstellen von Websitespalten, Inhaltstypen und Listen für SharePoint](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md) und [Spalten](http://go.microsoft.com/fwlink/?LinkId=226840).  
  
### Sitedefinition \(nur Farmlösung\)  
 Projektelemente für *Sitedefinitionen* enthalten einen Websitedefinitionsordner mit folgenden Dateien:  
  
-   Eine ASPX\-Standardseite, die als Standardwebseite für die Website verwendet wird.  
  
-   Die Datei "onet.xml", in der die Komponenten der Website definiert werden.  
  
-   Die Datei "webtemp.xml" zur Angabe der Websitedefinitionskonfigurationen, die auf der Seite **Neue SharePoint\-Website** im Abschnitt **Vorlagenauswahl** angezeigt werden.  
  
 Nach dem Hinzufügen einer Websitedefinition fügen Sie Code und Dateien hinzu, um Funktionen bereitzustellen.  Dieses Projektelement kann nur in Farmlösungen verwendet werden.  Dieses Projektelement kann nur Farmlösungen hinzugefügt werden.  Weitere Informationen finden Sie unter [Erstellen von Websitedefinitionen für SharePoint](../sharepoint/creating-site-definitions-for-sharepoint.md) und [Websitedefinitionen und \-konfigurationen](http://go.microsoft.com/fwlink/?LinkId=260554).  
  
### Zustandsautomatworkflow \(nur Farmlösung\)  
 Ein *Zustandsautomatworkflow* stellt einen Satz von Zuständen, Übergängen und Aktionen für Geschäftslogik dar.  Die Schritte in einem Zustandsautomatworkflow werden nicht nacheinander ausgeführt, sondern von Aktionen und Zuständen ausgelöst.  Ebenso wie sequenzielle Workflows werden Zustandsautomatworkflows SharePoint\-Elementen wie Listen und Dokumenten zugeordnet.  Auch in diesem Fall können Sie Workflows auf Websiteebene \(global\) oder auf Listenebene \(lokal\) erstellen.  Außerdem können Sie auswählen, ob ein Workflow automatisch oder manuell startet.  Dieses Projektelement kann nur in Farmlösungen verwendet werden.  Dieses Projektelement kann nur Farmlösungen hinzugefügt werden.  Weitere Informationen finden Sie unter [Erstellen von SharePoint-Workflow-Projektmappen](../sharepoint/creating-sharepoint-workflow-solutions.md), [Workflows in SharePoint Server 2010](http://go.microsoft.com/fwlink/?LinkId=260555) und [Neuigkeiten: Verbesserungen bei Workflows](http://go.microsoft.com/fwlink/?LinkId=179418).  
  
### Benutzersteuerelement \(nur Farmlösung\)  
 Bei einem *Benutzersteuerelement* handelt es sich um ein benutzerdefiniertes, wiederverwendbares Steuerelement, das Sie anderen ASP.NET\- und SharePoint\-Steuerelementen hinzufügen können.  Das Benutzersteuerelement kann in SharePoint ausgeführten Anwendungsseiten und Webparts hinzugefügt werden.  Dieses Projektelement kann nur in Farmlösungen verwendet werden.  Dieses Projektelement kann nur Farmlösungen hinzugefügt werden.  Weitere Informationen finden Sie unter [Creating Reusable Controls for Web Parts or Application Pages](http://go.microsoft.com/fwlink/?LinkId=226841).  
  
### Visuelles Webpart  
 Ein Projektelement für ein *Visuelles Webpart* enthält die "Elements.xml"\-Definitionsdatei, ein **Webpart**\-Element und ein **Benutzersteuerelement**.  Sie können die Darstellung des visuellen Webparts durch Ziehen oder Kopieren der Steuerelemente von der Visual Studio\-Toolbox auf die Oberfläche des Benutzersteuerelements entwerfen.  Weitere Informationen finden Sie unter [Gewusst wie: Erstellen eines SharePoint-Webparts mithilfe eines Designers](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) und [Baustein: Webparts](http://go.microsoft.com/fwlink/?LinkId=179438).  
  
### Webpart  
 Bei einem *Webpart* handelt es sich um ein serverseitiges Steuerelement, das innerhalb eines als Webpartseite bezeichneten besonderen Seitentyps ausgeführt wird.  Dies sind die Bausteine von auf SharePoint\-Websites angezeigten Seiten.  Vom Webpartelement werden Dateien bereitgestellt, mit denen Sie ein Webpart für eine SharePoint\-Website entwerfen können.  Weitere Informationen finden Sie unter [Gewusst wie: Erstellen eines SharePoint-Webparts](../sharepoint/how-to-create-a-sharepoint-web-part.md) und [Baustein: Webparts](http://go.microsoft.com/fwlink/?LinkId=179438).  
  
## Siehe auch  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)   
 [SharePoint\-Produkte und \-Technologien](http://go.microsoft.com/fwlink/?LinkId=178818)  
  
  