---
title: SharePoint-Projekt und Projekt Elementvorlagen | Microsoft-Dokumentation
ms.date: 02/22/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.SPE.FirstWizardPage
- VS.SharePointTools.SPE.ListInstance
- VS.SharePointTools.SPE.ListDefinition
- VS.SharePointTools.SPE.ListDefFromContentType
- VS.SharePointTools.SPE.ContentType
- SPE.Wizard
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, project and project item templates
- SharePoint development in Visual Studio, templates
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3f2479d58dfb8e1e28a2de230c0838ef8c8f3768
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54872196"
---
# <a name="sharepoint-project-and-project-item-templates"></a>SharePoint-Projekte und Projektelementvorlagen
  In den folgenden Abschnitten werden die in SharePoint verfügbaren Projekte und Projektelementvorlagen sowie deren Verwendung beschrieben. 
  
## <a name="project-and-project-item-templates-overview"></a>Projekt- und Übersicht über Element-Projektvorlagen
 Wenn Sie ein neues SharePoint-Projekt in Visual Studio erstellen, wird ein SharePoint-Projekt der Projektmappe zusammen mit allen für den entsprechenden Projekttyp erforderlichen Projektelementen hinzugefügt. Wenn Sie beispielsweise ein Silverlight-Webpartprojekt erstellen, wird von Visual Studio eine Projektmappe mit einem "Visuelles Webpart"-Projektelement und einem Silverlight-Anwendungsprojektelement erstellt, die auch alle für diese Projektelemente erforderlichen Dateien enthält. Projektelementvorlagen werden verwendet, um einem vorhandenen SharePoint-Projekt Projektelemente hinzuzufügen, z. B. Ereignisempfänger, Websitespalten oder Listen.  
  
 Weitere Informationen zu den Grundlagen von SharePoint finden Sie unter [Bausteine von SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=179404). Fortgeschrittene Benutzer können angepasste Projekt- und Projektelementvorlagen erstellen. Weitere Informationen finden Sie unter [Erweitern der SharePoint-Projektsystem](../sharepoint/extending-the-sharepoint-project-system.md).  
  
## <a name="project-templates"></a>Projektvorlagen
 Im Folgenden finden Sie eine Liste von SharePoint-Projektvorlagen. So zeigen Sie in der SharePoint-Projektvorlagen in Visual Studio an der **neues Projekt** Dialogfeld erweitern Sie die **SharePoint** Knoten entweder **Visual C#**  oder  **Visual Basic**, und wählen Sie dann **2010**.  
  
### <a name="sharepoint-2010-project"></a>SharePoint 2010-Projekt
 Den Inhalt einer *SharePoint 2010-Projekt* in jeder SharePoint-Projektvorlage enthalten sind. Ein SharePoint 2010-Projekt enthält:  
  
-   Eine Projektdatei.  
  
-   Eine Projekteigenschaftenseite.  
  
-   Ein **Verweise** Ordner, in dem alle der Assemblyverweise im Projekt.  
  
-   Ein **Features** Ordner mit einem *.feature* Konfigurationsdatei verwendet, um Features auf SharePoint-Server bereitzustellen.  
  
-   Ein **Paket** Ordner mit einem *Package.package* -Datei verwendet, um die Lösung für SharePoint bereitstellen.  
  
-   Eine "key.snk"-Datei (Schlüssel mit starkem Namen), um die Assembly zwecks verbesserter Sicherheit mit einem starken Namen zu signieren.  
  
### <a name="sharepoint-2010-silverlight-web-part"></a>SharePoint 2010 Silverlight-Webparts
 *SharePoint 2010 Silverlight-Webpart* -Projekten können Sie zum Erstellen von Webparts für SharePoint, die Silverlight-Anwendungen angezeigt. Beim Erstellen dieses Projekts können Sie angeben, ob eine neue Silverlight-Anwendung hinzugefügt oder auf eine vorhandene verwiesen werden soll. Weitere Informationen finden Sie unter [Webparts für SharePoint erstellen](../sharepoint/creating-web-parts-for-sharepoint.md) und [Exemplarische Vorgehensweise: Erstellen ein Silverlight-Webparts, das OData für SharePoint anzeigt](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).  
  
### <a name="sharepoint-2010-visual-web-part"></a>Visuelles Webpart für SharePoint 2010
 Ein *visuelles für SharePoint 2010-Webpart* -Projekt enthält eine *"Elements.xml"* -Definitionsdatei, ein **Webpart** Element und ein **Benutzersteuerelement** Element . Sie können die Darstellung des visuellen Webparts durch Ziehen oder Kopieren der Steuerelemente in der Visual Studio-Toolbox auf die Oberfläche des Benutzersteuerelements entwerfen. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen Sie einen SharePoint-Webpart mithilfe eines Designers](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) und [Baustein: Webparts](http://go.microsoft.com/fwlink/?LinkId=179438).  
  
### <a name="import-sharepoint-2010-solution-package"></a>SharePoint 2010-Lösungspaket importieren
 *SharePoint 2010-Lösungspaket importieren* Projekte können Sie ganz oder teilweise einer vorhandenen SharePoint 2010-Website, die in einer SharePoint-Lösung exportiert zu importieren (*.wsp*)-Datei in Visual Studio. Nach dem Importieren in Visual Studio können Sie die zugehörigen Elemente anpassen und erneut bereitstellen. Weitere Informationen finden Sie unter [Importieren von Elementen aus einer vorhandenen SharePoint-Website](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).  
  
### <a name="import-reusable-sharepoint-2010-workflow"></a>Wiederverwendbaren SharePoint 2010-Workflow importieren
 *Wiederverwendbaren SharePoint 2010-Workflow importieren* Projekte können Sie einen wiederverwendbaren deklarativen Workflow in SharePoint Designer 2010 erstellt werden, in Visual Studio zu importieren. Der Workflow wird aus der SharePoint-Website als exportiert eine *.wsp* Datei. Nach dem Importieren in Visual Studio können Sie den Workflow anpassen, Code hinzufügen und anschließend auf einer SharePoint-Website bereitstellen. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Importieren ein wiederverwendbares Workflows aus SharePoint Designer in Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md).  
  
## <a name="project-item-templates"></a>Projektelementvorlagen
 Im Folgenden finden Sie eine Liste von SharePoint-Projektelementvorlagen. Durch Projektelementvorlagen werden der SharePoint-Lösung Dateien zur Unterstützung von SharePoint-Funktionalität hinzugefügt, z. B. Websitespalten, Listen und Inhaltstypen. Hinzufügen einer Websitespalte zur Projektmappe Fügt ein Websitespaltenprojekt, die enthält beispielsweise eine *"Elements.xml"* -Definitionsdatei. Durch das Hinzufügen eines visuellen Webparts Ihre Projektmappe, enthält einen visuellen Webpartprojekts hinzugefügt ein *"Elements.xml"* -Datei, einem Benutzersteuerelement und ein visual-WebPartElement.  
  
 So zeigen Sie in der SharePoint-Projektelementvorlagen an **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für ein SharePoint-Projekt, und wählen Sie dann **hinzufügen**, **neues Element**. Erweitern Sie die **SharePoint** Knoten entweder **Visual C#-** oder **Visual Basic**, und wählen Sie dann **2010**.  
  
### <a name="application-page-farm-solution-only"></a>Anwendungsseite (nur farmlösung)
 Ein **Anwendungsseite (nur Farmlösung)** Element ermöglicht Ihnen das Entwerfen einer [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] Webseite für eine SharePoint-Website. Anwendungsseiten können nur in Farmlösungen verwendet werden. Dieses Projektelement kann nur Farmlösungen hinzugefügt werden. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen einer Anwendungsseite](../sharepoint/how-to-create-an-application-page.md) und [Anwendungsseitentyp "_layouts"](http://go.microsoft.com/fwlink/?LinkId=179434).  
  
### <a name="business-data-connectivity-model-farm-solution-only"></a>Business Data Connectivity-Modell (nur farmlösung)
 Ein **Business Data Connectivity-Modell (nur Farmlösung)** Element können Sie zum Integrieren von Geschäftsdaten in SharePoint. Geschäftsdaten können von Back-End-Serveranwendungen stammen, z. B. [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)], Siebel und Service Advertising Protocol (SAP). Business Data Connectivity-Modelle können nur in Farmlösungen verwendet werden. Dieses Projektelement kann nur Farmlösungen hinzugefügt werden. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen eines BDC-Modells](../sharepoint/how-to-create-a-bdc-model.md), [Vorgehensweise: Verwenden Sie eine Ressourcendatei zum Angeben von lokalisierten Namen, Eigenschaften und Berechtigungen](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md), und [neuerungen: Business Connectivity Services](http://go.microsoft.com/fwlink/?LinkId=179411).  
  
### <a name="content-type"></a>Inhaltstyp
 *Inhaltstyp* Elemente können Sie benutzerdefinierte Inhaltstypen auf Grundlage eines vorhandenen (grundlegenden) Inhaltstyps wie z. B. ein Dokument, eine Ankündigung oder eine Aufgabe zu erstellen. Von einem benutzerdefinierten Inhaltstyp werden neben denselben Attributen und Feldern wie vom grundlegenden Inhaltstyp auch alle definierten Websitespalten (Felder) bereitgestellt. Beispielsweise können Sie einen benutzerdefinierten Inhaltstyp "Kontakt" erstellen, der auf dem grundlegenden Inhaltstyp "Kontakt" aus SharePoint basiert. Sie können den Inhaltstyp anpassen, indem vorhandene Websitespalten ändern oder zusätzliche Websitespalten zu den bereits im grundlegenden Inhaltstyp enthaltenen hinzufügen.  
  
> [!NOTE]  
>  Aufgrund einer SharePoint-Einschränkung können Sie keinen Farmprojektmappeninhaltstyp auf Grundlage eines Sandkastenlösungsinhaltstyps erstellen.  
  
 Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer Websitespalte, den Inhaltstyp und die Liste für SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) und [Baustein: Inhaltstyp](http://go.microsoft.com/fwlink/?LinkId=179413).  
  
### <a name="empty-element"></a>Leeres Element
 *Leere Elemente* werden meist verwendet, um SharePoint-Projektelemente zu definieren, die ein Projekt oder Element-Projektvorlage in Visual Studio hat. Wenn Sie dem Projekt ein leeres Element hinzufügen, wird ein Knoten mit dem Namen EmptyElement [x](where [x] is a unique number\) is created. EmptyElement [X] enthält eine einzelne Datei, d. h. benannte *"Elements.xml".* Verwendung [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] Anweisungen zum Definieren der gewünschten Elemente in *"Elements.xml"*.  
  
### <a name="event-receiver"></a>Ereignisempfänger
 *Ereignisempfänger* Behandeln von Ereignissen für Elemente in der SharePoint-Website, z. B. wenn ein Element einer Liste hinzugefügt wird, wird beim Löschen eines Webelements oder Starten eines Workflows. Die Projektelementvorlage "Ereignisempfänger" ermöglicht die Behandlung folgender Elemente:  
  
- Listenereignisse  
  
- Listenelementereignisse  
  
- Listen-E-Mail-Ereignisse  
  
- Webereignisse  
  
- Listenworkflowereignisse  
  
  Erstellt das Projekt ereignisempfängerelement ein **Ereignisempfänger** eine einzelne Klassendatei, die Ereignishandler für alle Ereignisse enthält, die Sie beim Erstellen des Projekts im angegebenen Ordner die **Anpassung von SharePoint Assistenten**. Die Ereignisempfängerklasse kann Ereignisse behandeln, die auf der SharePoint-Website auftreten, wenn Elemente wie z. B. Dateien, Felder, Elemente, Listen, Anlagen, Webparts und Workflows hinzugefügt, aktualisiert, gelöscht oder entfernt werden. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen eines Ereignisempfängers](../sharepoint/how-to-create-an-event-receiver.md) und [Baustein: Behandlung von Ereignissen](http://go.microsoft.com/fwlink/?LinkId=179416).  
  
### <a name="list"></a>Liste  
 Bei einer Liste handelt es sich um eine Instanz einer wiederverwendbaren, grundlegenden SharePoint-Listendefinition, z. B. ein Kalender oder eine Aufgabenliste. Nach dem Hinzufügen einer Liste zu Ihrer Lösung können Sie mit dem Listen-Designer Websitespalten zur Liste hinzufügen und benutzerdefinierte Listenspalten erstellen. Dazu gehören Websitespalten aus Inhaltstypen. Sie können angeben, die *Ansicht* Liste, welche der Spalten, die in der Liste angezeigt wird. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer Websitespalte, den Inhaltstyp und die Liste für SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) und [Baustein: Listen und Dokumentbibliotheken](http://go.microsoft.com/fwlink/?LinkId=179421).  
  
### <a name="module"></a>Modul  
 *Module* (nicht zu verwechseln mit [!include[vbprvb](../sharepoint/includes/vbprvb-md.md)] Module) enthält alle Dateien, die Sie zum SharePoint-Server, z. B. Bilder oder Notizen bereitstellen möchten. Das modulprojektelement weist einen **Modul** Knoten. Der Modulknoten enthält zwei Projektelementvorlagen: eine XML-Definitionsdatei, die als Manifest für das Modul fungiert, und ein *"Sample.txt"* Datei, eine Platzhalterdatei. Weitere Informationen finden Sie unter [verwenden Module zum Einschließen von Dateien in der Projektmappe](../sharepoint/using-modules-to-include-files-in-the-solution.md) und [Module](http://go.microsoft.com/fwlink/?LinkId=179425).  
  
### <a name="sequential-workflow-farm-solution-only"></a>Sequenzieller Workflow (nur farmlösung)
 Ein *sequenziellen Workflow* ist eine Reihe von Geschäftslogikschritten dar, die Reihenfolge, bis der letzte Schritt abgeschlossen ist. Sequenzielle Workflows werden verwendet, um Prozesse zu verwalten, die SharePoint-Elemente wie Listen und Dokumente einschließen. Sie können Workflows auf Websiteebene (global) oder auf Listenebene (lokal) erstellen, und Sie können auswählen, ob ein Workflow automatisch oder manuell startet. Dieses Projektelement kann nur in Farmlösungen verwendet werden. Dieses Projektelement kann nur Farmlösungen hinzugefügt werden. Weitere Informationen finden Sie unter [Erstellen von SharePoint-Workflow-Projektmappen](../sharepoint/creating-sharepoint-workflow-solutions.md), [Workflows in SharePoint Server 2010](http://go.microsoft.com/fwlink/?LinkId=260555), und [Neuigkeiten: Verbesserungen des Workflows](http://go.microsoft.com/fwlink/?LinkId=179418).  
  
### <a name="silverlight-web-part"></a>Silverlight-Webparts
 *Silverlight-Webpart* Projektelemente können Sie zum Erstellen von Webparts für SharePoint, die Silverlight-Anwendungen angezeigt. Wenn Sie dieses Projektelement in Ihre Lösung einfügen, können Sie entweder eine neue Silverlight-Anwendung hinzufügen oder zu einem späteren Zeitpunkt auf eine vorhandene verweisen. Weitere Informationen finden Sie unter [Webparts für SharePoint erstellen](../sharepoint/creating-web-parts-for-sharepoint.md) und [Exemplarische Vorgehensweise: Erstellen ein Silverlight-Webparts, das OData für SharePoint anzeigt](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).  
  
### <a name="site-column"></a>Websitespalte
 Ein *Websitespalte*, auch bekannt als eine *Feld*, ist eine der grundlegendsten Elemente können ein SharePoint-Projekt hinzugefügt. Eine Websitespalte stellt einen Datentyp dar, z. B. eine Telefonnummer, ein Textkommentar oder der Name der Stadt eines Kontakts in einer Kontaktliste. Weitere Informationen finden Sie unter [Erstellen von Websitespalten, Inhaltstypen und Listen für SharePoint](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md) und [Spalten](http://go.microsoft.com/fwlink/?LinkId=226840).  
  
### <a name="site-definition-farm-solution-only"></a>Sitedefinition (nur farmlösung)
 *Sitedefinition* -Projektelemente enthalten einen Websitedefinitionsordner, die die folgenden Dateien enthält:  
  
- Eine ASPX-Standardseite, die als Standardwebseite für die Website verwendet wird.  
  
- Ein *onet.xml* -Datei, die Komponenten der Website definiert.  
  
- Eine Webtemp-XML-Datei, die der Websitedefinitionskonfigurationen, die in angezeigt werden. die **Vorlagenauswahl** Teil der **neue SharePoint-Website** Seite.  
  
  Nach dem Hinzufügen einer Websitedefinition fügen Sie Code und Dateien hinzu, um Funktionen bereitzustellen. Dieses Projektelement kann nur in Farmlösungen verwendet werden. Dieses Projektelement kann nur Farmlösungen hinzugefügt werden. Weitere Informationen finden Sie unter [Erstellen von Websitedefinitionen für SharePoint](../sharepoint/creating-site-definitions-for-sharepoint.md) und [Websitedefinitionen und-Konfigurationen](http://go.microsoft.com/fwlink/?LinkId=260554).  
  
### <a name="state-machine-workflow-farm-solution-only"></a>Zustandsautomatworkflow (nur farmlösung)
 Ein *Zustandsautomatworkflow* ist ein Satz von Business Logic Zuständen, Übergängen und Aktionen. Die Schritte in einem Zustandsautomatworkflow werden nicht nacheinander ausgeführt, sondern von Aktionen und Zuständen ausgelöst. Ebenso wie sequenzielle Workflows werden Zustandsautomatworkflows SharePoint-Elementen wie Listen und Dokumenten zugeordnet. Auch in diesem Fall können Sie Workflows auf Websiteebene (global) oder auf Listenebene (lokal) erstellen. Außerdem können Sie auswählen, ob ein Workflow automatisch oder manuell startet. Dieses Projektelement kann nur in Farmlösungen verwendet werden. Dieses Projektelement kann nur Farmlösungen hinzugefügt werden. Weitere Informationen finden Sie unter [Erstellen von SharePoint-Workflow-Projektmappen](../sharepoint/creating-sharepoint-workflow-solutions.md), [Workflows in SharePoint Server 2010](http://go.microsoft.com/fwlink/?LinkId=260555), und [Neuigkeiten: Verbesserungen des Workflows](http://go.microsoft.com/fwlink/?LinkId=179418).  
  
### <a name="user-control-farm-solution-only"></a>Benutzersteuerelement (nur farmlösung)
 Ein *Benutzersteuerelement* ist ein benutzerdefiniertes, wiederverwendbares Steuerelement, die, die Sie anderen ASP.NET- und SharePoint-Steuerelemente hinzufügen können. Das Benutzersteuerelement kann in SharePoint ausgeführten Anwendungsseiten und Webparts hinzugefügt werden. Dieses Projektelement kann nur in Farmlösungen verwendet werden. Dieses Projektelement kann nur Farmlösungen hinzugefügt werden. Weitere Informationen finden Sie unter [Erstellen von Wiederverwendbaren Steuerelementen für Webparts oder Anwendungsseiten](http://go.microsoft.com/fwlink/?LinkId=226841).  
  
### <a name="visual-web-part"></a>Visuelles Webpart
 Ein *visuelles Webpart* -Projektelement enthält eine *"Elements.xml"* -Definitionsdatei, ein **Webpart** Element und ein **Benutzersteuerelement** Element. Sie können die Darstellung des visuellen Webparts durch Ziehen oder Kopieren der Steuerelemente in der Visual Studio-Toolbox auf die Oberfläche des Benutzersteuerelements entwerfen. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen Sie einen SharePoint-Webpart mithilfe eines Designers](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) und [Baustein: Webparts](http://go.microsoft.com/fwlink/?LinkId=179438).  
  
### <a name="web-part"></a>Webpart
 Ein *-Webpart* ist ein serverseitiges Steuerelement, das in eine besondere Art von Seite mit dem Namen einer Webpartseite ausgeführt wird. Dies sind die Bausteine von auf SharePoint-Websites angezeigten Seiten. Vom Webpartelement werden Dateien bereitgestellt, mit denen Sie ein Webpart für eine SharePoint-Website entwerfen können. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen eines SharePoint-Webparts](../sharepoint/how-to-create-a-sharepoint-web-part.md) und [Baustein: Webparts](http://go.microsoft.com/fwlink/?LinkId=179438).  
  
## <a name="see-also"></a>Siehe auch
 [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)   
 [SharePoint-Produkte und-Technologien](http://go.microsoft.com/fwlink/?LinkId=178818)  
