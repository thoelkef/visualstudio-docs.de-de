---
title: SharePoint-Projekte und Projekt Elementvorlagen | Microsoft Docs
ms.custom: 
ms.date: 02/22/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
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
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, project and project item templates
- SharePoint development in Visual Studio, templates
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 3890d7678fdc50a867e254edbbb7503acbebcd76
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="sharepoint-project-and-project-item-templates"></a>Vorlagen für SharePoint-Projekte und Projektelemente
  In den folgenden Abschnitten werden die in SharePoint verfügbaren Projekte und Projektelementvorlagen sowie deren Verwendung beschrieben. 
  
##  <a name="project-and-project-item-templates-overview"></a>Übersicht über Vorlagen für SharePoint-Projekte und Projektelemente  
 Beim Erstellen eines neuen SharePoint-Projekts in Visual Studio wird ein SharePoint-Projekt der Projektmappe zusammen mit allen von der entsprechenden Projekttyp erforderlichen Projektelementen hinzugefügt. Wenn Sie beispielsweise ein Silverlight-Webpartprojekt erstellen, wird von Visual Studio eine Projektmappe mit einem "Visuelles Webpart"-Projektelement und einem Silverlight-Anwendungsprojektelement erstellt, die auch alle für diese Projektelemente erforderlichen Dateien enthält. Projektelementvorlagen werden verwendet, um einem vorhandenen SharePoint-Projekt Projektelemente hinzuzufügen, z. B. Ereignisempfänger, Websitespalten oder Listen.  
  
 Informationen zu SharePoint-Grundlagen finden Sie unter [SharePoint Foundation-Bausteine](http://go.microsoft.com/fwlink/?LinkId=179404). Fortgeschrittene Benutzer können angepasste Projekt- und Projektelementvorlagen erstellen. Weitere Informationen finden Sie unter [Erweitern des SharePoint-Projektsystems](../sharepoint/extending-the-sharepoint-project-system.md).  
  
##  <a name="project-templates"></a>Projektvorlagen  
 Im Folgenden finden Sie eine Liste von SharePoint-Projektvorlagen. So zeigen Sie die SharePoint-Projektvorlagen in Visual Studio im an die **neues Projekt** Dialogfeld erweitern Sie die **SharePoint** Knoten unter einem **Visual C#-** oder  **Visual Basic**, und wählen Sie dann **2010**.  
  
### <a name="sharepoint-2010-project"></a>SharePoint 2010-Projekt  
 Den Inhalt einer *SharePoint 2010-Projekt* in jeder SharePoint-Projektvorlage enthalten sind. Ein SharePoint 2010-Projekt enthält:  
  
-   Eine Projektdatei.  
  
-   Eine Projekteigenschaftenseite.  
  
-   Ein **Verweise** Ordner, in dem alle Assemblyverweise im Projekt.  
  
-   Ein **Funktionen** Ordner mit einer Feature-Konfigurationsdatei zum Bereitstellen von Funktionen auf SharePoint-Server verwendet.  
  
-   Ein **Paket** Ordner mit einer "Package.Package"-Datei zum Bereitstellen der Lösung auf SharePoint.  
  
-   Eine "key.snk"-Datei (Schlüssel mit starkem Namen), um die Assembly zwecks verbesserter Sicherheit mit einem starken Namen zu signieren.  
  
### <a name="sharepoint-2010-silverlight-web-part"></a>SharePoint 2010 Silverlight-Webpart  
 *SharePoint 2010 Silverlight-Webpart* Projekte ermöglichen es Ihnen das Erstellen von Webparts für SharePoint, die Silverlight-Anwendungen angezeigt. Beim Erstellen dieses Projekts können Sie angeben, ob eine neue Silverlight-Anwendung hinzugefügt oder auf eine vorhandene verwiesen werden soll. Weitere Informationen finden Sie unter [Erstellen von Webparts für SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) und [Exemplarische Vorgehensweise: Erstellen einer Silverlight-Webpart, zeigt OData für SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).  
  
### <a name="sharepoint-2010-visual-web-part"></a>Visuelles SharePoint 2010-Webpart  
 Ein *visuelles für SharePoint 2010-Webpart* -Projekt enthält eine Datei "Elements.xml"-Definitionsdatei, ein **Webpart** Element, und ein **Benutzersteuerelement** Element. Sie können die Darstellung des visuellen Webparts durch Ziehen oder Kopieren der Steuerelemente in der Visual Studio-Toolbox auf die Oberfläche des Benutzersteuerelements entwerfen. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen einer SharePoint-Webpart mithilfe eines Designers](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) und [Baustein: Webparts](http://go.microsoft.com/fwlink/?LinkId=179438).  
  
### <a name="import-sharepoint-2010-solution-package"></a>SharePoint 2010-Lösungspaket importieren  
 *SharePoint 2010-Lösungspaket importieren* Projekte können Sie alle oder einen Teil einer vorhandenen SharePoint 2010-Website in einer SharePoint-Lösungsdatei (WSP)-Datei exportiert werden, in Visual Studio zu importieren. Nach dem Importieren in Visual Studio können Sie die zugehörigen Elemente anpassen und erneut bereitstellen. Weitere Informationen finden Sie unter [Importieren von Elementen aus einer vorhandenen SharePoint-Website](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).  
  
### <a name="import-reusable-sharepoint-2010-workflow"></a>Wiederverwendbaren SharePoint 2010-Workflow importieren  
 *Wiederverwendbaren SharePoint 2010-Workflow importieren* Projekte können Sie einen wiederverwendbaren deklarativen Workflow in SharePoint Designer 2010 erstellt werden, in Visual Studio zu importieren. Der Workflow wird als WSP-Datei von der SharePoint-Website exportiert. Nach dem Importieren in Visual Studio können Sie den Workflow anpassen, Code hinzufügen und anschließend auf einer SharePoint-Website bereitstellen. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Importieren eines Wiederverwendbaren Workflows von SharePoint-Designer in Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md).  
  
##  <a name="project-item-templates"></a>Projektelementvorlagen  
 Im Folgenden finden Sie eine Liste von SharePoint-Projektelementvorlagen. Durch Projektelementvorlagen werden der SharePoint-Lösung Dateien zur Unterstützung von SharePoint-Funktionalität hinzugefügt, z. B. Websitespalten, Listen und Inhaltstypen. Beispielsweise wird durch das Hinzufügen einer Websitespalte zur Lösung ein Websitespaltenprojekt mit einer "Elements.xml"-Definitionsdatei hinzugefügt. Durch das Hinzufügen eines visuellen Webparts wird der Projektmappe ein visuelles Webpartprojekt mit einer "Elements.xml"-Datei, einem Benutzersteuerelement und einem visuellem Webpartelement hinzugefügt.  
  
 So zeigen Sie in der SharePoint-Projektelementvorlagen an **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für ein SharePoint-Projekt, und wählen Sie dann **hinzufügen**, **neues Element**. Erweitern Sie die **SharePoint** Knoten unter einem **Visual C#-** oder **Visual Basic**, und wählen Sie dann **2010**.  
  
### <a name="application-page-farm-solution-only"></a>Anwendungsseite (nur Farmlösung)  
 Ein **Anwendungsseite (nur Farmlösung)** Element ermöglicht Ihnen das Entwerfen einer [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] Webseite auf einer SharePoint-Website. Anwendungsseiten können nur in Farmlösungen verwendet werden. Dieses Projektelement kann nur Farmlösungen hinzugefügt werden. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen einer Anwendungsseite](../sharepoint/how-to-create-an-application-page.md) und [Anwendung _layouts Seitentyp](http://go.microsoft.com/fwlink/?LinkId=179434).  
  
### <a name="business-data-connectivity-model-farm-solution-only"></a>Business Data Connectivity-Modell (nur Farmlösung)  
 Ein **Business Data Connectivity-Modell (nur Farmlösung)** Element können Sie Geschäftsdaten in SharePoint integrieren. Geschäftsdaten können von Back-End-Serveranwendungen stammen, z. B. [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)], Siebel und Service Advertising Protocol (SAP). Business Data Connectivity-Modelle können nur in Farmlösungen verwendet werden. Dieses Projektelement kann nur Farmlösungen hinzugefügt werden. Weitere Informationen finden Sie unter [wie: Erstellen Sie ein BDC-Modell](../sharepoint/how-to-create-a-bdc-model.md), [wie: Verwenden Sie eine Ressourcendatei lokalisierte Namen geben, Eigenschaften und Berechtigungen](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md), und [neues: Business-Konnektivität Services](http://go.microsoft.com/fwlink/?LinkId=179411).  
  
### <a name="content-type"></a>Inhaltstyp  
 *Inhaltstyp* -Elementen können Sie benutzerdefinierte Inhaltstypen auf Grundlage eines vorhandenen (grundlegenden) Inhaltstyps z. B. ein Dokument, eine Ankündigung oder eine Aufgabe zu erstellen. Von einem benutzerdefinierten Inhaltstyp werden neben denselben Attributen und Feldern wie vom grundlegenden Inhaltstyp auch alle definierten Websitespalten (Felder) bereitgestellt. Beispielsweise können Sie einen benutzerdefinierten Inhaltstyp "Kontakt" erstellen, der auf dem grundlegenden Inhaltstyp "Kontakt" aus SharePoint basiert. Sie können den Inhaltstyp anpassen, indem vorhandene Websitespalten ändern oder zusätzliche Websitespalten zu den bereits im grundlegenden Inhaltstyp enthaltenen hinzufügen.  
  
> [!NOTE]  
>  Aufgrund einer SharePoint-Einschränkung können Sie keinen Farmprojektmappeninhaltstyp auf Grundlage eines Sandkastenlösungsinhaltstyps erstellen.  
  
 Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer Websitespalte, den Inhaltstyp und die Liste für SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) und [Baustein: Inhaltstyp](http://go.microsoft.com/fwlink/?LinkId=179413).  
  
### <a name="empty-element"></a>Leeres Element  
 *Leere Elemente* werden am häufigsten verwendet werden, um die SharePoint-Projektelemente zu definieren, die ein Projekt oder Element-Projektvorlage in Visual Studio hat. Wenn Sie dem Projekt ein leeres Element hinzufügen, wird ein Knoten mit dem Namen EmptyElement [x](where [x] is a unique number\) is created. EmptyElement [X] enthält eine einzelne Datei mit dem Namen "Elements.xml". Mithilfe von [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]-Anweisungen können Sie die gewünschten Elemente in "Elements.xml" definieren.  
  
### <a name="event-receiver"></a>Ereignisempfänger  
 *Ereignisempfänger* behandeln Ereignisse für Elemente in der SharePoint-Website, z. B. wenn eine Liste ein Element hinzugefügt wird, wenn ein Webelement gelöscht wird oder beim Starten eines Workflows. Die Projektelementvorlage "Ereignisempfänger" ermöglicht die Behandlung folgender Elemente:  
  
-   Listenereignisse  
  
-   Listenelementereignisse  
  
-   Listen-E-Mail-Ereignisse  
  
-   Webereignisse  
  
-   Listenworkflowereignisse  
  
 Das Ereignis Empfänger Projektelement erstellt ein **Ereignisempfänger** mit einer einzelnen Klassendatei, die Ereignishandler für alle Ereignisse enthält, die Sie beim Erstellen des Projekts im angegebenen Ordner die **SharePoint-Anpassung Assistent**. Die Ereignisempfängerklasse kann Ereignisse behandeln, die auf der SharePoint-Website auftreten, wenn Elemente wie Dateien, Felder, Elemente, Listen, Anlagen, Webparts und Workflows hinzugefügt, aktualisiert, gelöscht oder entfernt werden. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen eines Ereignisempfängers](../sharepoint/how-to-create-an-event-receiver.md) und [Baustein: Ereignisbehandlung](http://go.microsoft.com/fwlink/?LinkId=179416).  
  
### <a name="list"></a>Liste  
 Bei einer Liste handelt es sich um eine Instanz einer wiederverwendbaren, grundlegenden SharePoint-Listendefinition, z. B. ein Kalender oder eine Aufgabenliste. Nach dem Hinzufügen einer Liste zu Ihrer Lösung können Sie mit dem Listen-Designer Websitespalten zur Liste hinzufügen und benutzerdefinierte Listenspalten erstellen. Dazu gehören Websitespalten aus Inhaltstypen. Sie können angeben, die *Ansicht* Liste, welche der Spalten, die in der Liste angezeigt werden. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer Websitespalte, den Inhaltstyp und die Liste für SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) und [Baustein: Listen und Dokumentbibliotheken](http://go.microsoft.com/fwlink/?LinkId=179421).  
  
### <a name="module"></a>Modul  
 *Module* (nicht zu verwechseln mit [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] Module) enthalten alle Dateien, die Sie auf dem SharePoint-Server, z. B. Bilder oder Notizen bereitstellen möchten. Das modulprojektelement weist einen **Modul** Knoten. Der Modulknoten enthält zwei Projektelementvorlagen: eine XML-Definitionsdatei, die als Manifest für das Modul fungiert, und die Platzhalterdatei "sample.txt". Weitere Informationen finden Sie unter [mithilfe von Modulen zum Einschließen von Dateien in der Projektmappe](../sharepoint/using-modules-to-include-files-in-the-solution.md) und [Module](http://go.microsoft.com/fwlink/?LinkId=179425).  
  
### <a name="sequential-workflow-farm-solution-only"></a>Sequenzieller Workflow (nur Farmlösung)  
 Ein *sequenzieller Workflow* ist eine Reihe von Geschäftslogikschritten dar, die Reihenfolge, bis der letzte Schritt abgeschlossen ist. Sequenzielle Workflows werden verwendet, um Prozesse zu verwalten, die SharePoint-Elemente wie Listen und Dokumente einschließen. Sie können Workflows auf Websiteebene (global) oder auf Listenebene (lokal) erstellen, und Sie können auswählen, ob ein Workflow automatisch oder manuell startet. Dieses Projektelement kann nur in Farmlösungen verwendet werden. Dieses Projektelement kann nur Farmlösungen hinzugefügt werden. Weitere Informationen finden Sie unter [SharePoint-Workflow-Projektmappen erstellen](../sharepoint/creating-sharepoint-workflow-solutions.md), [Workflows in SharePoint Server 2010](http://go.microsoft.com/fwlink/?LinkId=260555), und [neues: Workflow Verbesserungen](http://go.microsoft.com/fwlink/?LinkId=179418).  
  
### <a name="silverlight-web-part"></a>Silverlight-Webpart  
 *Silverlight-Webpart* Projektelemente ermöglichen Ihnen das Erstellen von Webparts für SharePoint, die Silverlight-Anwendungen angezeigt. Wenn Sie dieses Projektelement in Ihre Lösung einfügen, können Sie entweder eine neue Silverlight-Anwendung hinzufügen oder zu einem späteren Zeitpunkt auf eine vorhandene verweisen. Weitere Informationen finden Sie unter [Erstellen von Webparts für SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) und [Exemplarische Vorgehensweise: Erstellen einer Silverlight-Webpart, zeigt OData für SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).  
  
### <a name="site-column"></a>Websitespalte  
 Ein *Websitespalte*, auch bekannt als ein *Feld*, ist eine der grundlegendsten Elemente, die Sie zu einem SharePoint-Projekt hinzufügen können. Eine Websitespalte stellt einen Datentyp dar, z. B. eine Telefonnummer, ein Textkommentar oder der Name der Stadt eines Kontakts in einer Kontaktliste. Weitere Informationen finden Sie unter [Erstellen von Websitespalten, Inhaltstypen und Listen für SharePoint](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md) und [Spalten](http://go.microsoft.com/fwlink/?LinkId=226840).  
  
### <a name="site-definition-farm-solution-only"></a>Sitedefinition (nur Farmlösung)  
 *Websitedefinition* -Projektelemente enthalten einen Ordner der Website-Definition, die folgenden Dateien enthält:  
  
-   Eine ASPX-Standardseite, die als Standardwebseite für die Website verwendet wird.  
  
-   Die Datei "onet.xml", in der die Komponenten der Website definiert werden.  
  
-   Eine Webtemp-XML-Datei, die der Websitedefinitionskonfigurationen, die in angezeigt werden die **Vorlagenauswahl** Teil der **neue SharePoint-Website** Seite.  
  
 Nach dem Hinzufügen einer Websitedefinition fügen Sie Code und Dateien hinzu, um Funktionen bereitzustellen. Dieses Projektelement kann nur in Farmlösungen verwendet werden. Dieses Projektelement kann nur Farmlösungen hinzugefügt werden. Weitere Informationen finden Sie unter [Erstellen von Websitedefinitionen für SharePoint](../sharepoint/creating-site-definitions-for-sharepoint.md) und [Websitedefinitionen und Konfigurationen](http://go.microsoft.com/fwlink/?LinkId=260554).  
  
### <a name="state-machine-workflow-farm-solution-only"></a>Zustandsautomatworkflow (nur Farmlösung)  
 Ein *zustandsautomatenworkflow* ist ein Satz von Business Logic Zuständen, Übergängen und Aktionen. Die Schritte in einem Zustandsautomatworkflow werden nicht nacheinander ausgeführt, sondern von Aktionen und Zuständen ausgelöst. Ebenso wie sequenzielle Workflows werden Zustandsautomatworkflows SharePoint-Elementen wie Listen und Dokumenten zugeordnet. Auch in diesem Fall können Sie Workflows auf Websiteebene (global) oder auf Listenebene (lokal) erstellen. Außerdem können Sie auswählen, ob ein Workflow automatisch oder manuell startet. Dieses Projektelement kann nur in Farmlösungen verwendet werden. Dieses Projektelement kann nur Farmlösungen hinzugefügt werden. Weitere Informationen finden Sie unter [SharePoint-Workflow-Projektmappen erstellen](../sharepoint/creating-sharepoint-workflow-solutions.md), [Workflows in SharePoint Server 2010](http://go.microsoft.com/fwlink/?LinkId=260555), und [neues: Workflow Verbesserungen](http://go.microsoft.com/fwlink/?LinkId=179418).  
  
### <a name="user-control-farm-solution-only"></a>Benutzersteuerelement (nur Farmlösung)  
 Ein *Benutzersteuerelement* ein benutzerdefiniertes, wiederverwendbares Steuerelement, das Sie anderen ASP.NET- und SharePoint-Steuerelemente hinzufügen können. Das Benutzersteuerelement kann in SharePoint ausgeführten Anwendungsseiten und Webparts hinzugefügt werden. Dieses Projektelement kann nur in Farmlösungen verwendet werden. Dieses Projektelement kann nur Farmlösungen hinzugefügt werden. Weitere Informationen finden Sie unter [Erstellen von Wiederverwendbaren Steuerelementen für Webparts oder Anwendungsseiten](http://go.microsoft.com/fwlink/?LinkId=226841).  
  
### <a name="visual-web-part"></a>Visuelles Webpart  
 Ein *visuelles Webpart* Projektelement enthält eine "Elements.xml"-Definitionsdatei, ein **Webpart** Element, und ein **Benutzersteuerelement** Element. Sie können die Darstellung des visuellen Webparts durch Ziehen oder Kopieren der Steuerelemente in der Visual Studio-Toolbox auf die Oberfläche des Benutzersteuerelements entwerfen. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen einer SharePoint-Webpart mithilfe eines Designers](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) und [Baustein: Webparts](http://go.microsoft.com/fwlink/?LinkId=179438).  
  
### <a name="web-part"></a>Webpart  
 Ein *Webpart* ist ein serverseitiges Steuerelement, das in ein besonderer Typ einer Webpartseite bezeichneten ausgeführt wird. Dies sind die Bausteine von auf SharePoint-Websites angezeigten Seiten. Vom Webpartelement werden Dateien bereitgestellt, mit denen Sie ein Webpart für eine SharePoint-Website entwerfen können. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen eines SharePoint-Webparts](../sharepoint/how-to-create-a-sharepoint-web-part.md) und [Baustein: Webparts](http://go.microsoft.com/fwlink/?LinkId=179438).  
  
## <a name="see-also"></a>Siehe auch  
 [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)   
 [SharePoint-Produkte und Technologien](http://go.microsoft.com/fwlink/?LinkId=178818)  
  
  
