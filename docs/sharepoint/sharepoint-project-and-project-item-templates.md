---
title: SharePoint-Projekt- und Projektelementvorlagen | Microsoft Docs
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
ms.openlocfilehash: 2878bd2092e000cf63c2b4fcb531a502a470203e
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649227"
---
# <a name="sharepoint-project-and-project-item-templates"></a>SharePoint-Projekt- und Projektelementvorlagen
  In den folgenden Abschnitten werden die in SharePoint verfügbaren Projekte und Projektelementvorlagen sowie deren Verwendung beschrieben.

## <a name="project-and-project-item-templates-overview"></a>Übersicht über Projekt- und Projektelementvorlagen
 Beim Erstellen eines neuen SharePoint-Projekts in Visual Studio wird dieses zusammen mit allen für den entsprechenden Projekttyp erforderlichen Projektelementen der Projektmappe hinzugefügt. Wenn Sie beispielsweise ein Silverlight-Webpartprojekt erstellen, wird von Visual Studio eine Projektmappe mit einem "Visuelles Webpart"-Projektelement und einem Silverlight-Anwendungsprojektelement erstellt, die auch alle für diese Projektelemente erforderlichen Dateien enthält. Projektelementvorlagen werden verwendet, um einem vorhandenen SharePoint-Projekt Projektelemente hinzuzufügen, z. B. Ereignisempfänger, Websitespalten oder Listen.

 Informationen zu SharePoint-Grundlagen finden Sie unter [SharePoint Foundation Building Blocks](/previous-versions/office/developer/sharepoint-2010/ee534971(v=office.14)). Fortgeschrittene Benutzer können angepasste Projekt- und Projektelementvorlagen erstellen. Weitere Informationen finden Sie unter [Erweitern des SharePoint-Projektsystems](../sharepoint/extending-the-sharepoint-project-system.md).

## <a name="project-templates"></a>Projektvorlagen
 Im Folgenden finden Sie eine Liste von SharePoint-Projektvorlagen. Um die SharePoint-Projektvorlagen in Visual Studio anzuzeigen, erweitern Sie im Dialogfeld **Neues Projekt** den **SharePoint-Knoten** unter **Visual C oder** Visual **Basic**, und wählen Sie dann **2010**aus.

### <a name="sharepoint-2010-project"></a>SharePoint 2010-Projekt
 Der Inhalt eines *SharePoint 2010-Projekts* ist in jeder SharePoint-Projektvorlage enthalten. Ein SharePoint 2010-Projekt enthält:

- Eine Projektdatei.

- Eine Projekteigenschaftenseite.

- Ein **Referenzordner,** der alle Assemblyverweise im Projekt auflistet.

- Ein **Features** Features-Ordner, der eine *.feature-Konfigurationsdatei* enthält, die zum Bereitstellen von Features auf SharePoint-Servern verwendet wird.

- Ein **Paketordner,** der eine *Package.package-Datei* enthält, die zum Bereitstellen der Lösung in SharePoint verwendet wird.

- Eine "key.snk"-Datei (Schlüssel mit starkem Namen), um die Assembly zwecks verbesserter Sicherheit mit einem starken Namen zu signieren.

### <a name="sharepoint-2010-silverlight-web-part"></a>SharePoint 2010 Silverlight-Webpart
 *Mit SharePoint 2010 Silverlight Web Part-Projekten* können Sie Webparts für SharePoint erstellen, die Silverlight-Anwendungen anzeigen. Beim Erstellen dieses Projekts können Sie angeben, ob eine neue Silverlight-Anwendung hinzugefügt oder auf eine vorhandene verwiesen werden soll. Weitere Informationen finden Sie unter [Erstellen von Webparts für SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) und [exemplarische Vorgehensweise: Erstellen eines Silverlight-Webparts, das OData für SharePoint anzeigt.](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)

### <a name="sharepoint-2010-visual-web-part"></a>Visuelles SharePoint 2010-Webpart
 Ein *SharePoint 2010 Visual Web Part-Projekt* enthält eine *Elements.xml-Definitionsdatei,* ein **Webpartelement** und ein **Benutzersteuerelementelement.** Sie können die Darstellung des visuellen Webparts durch Ziehen oder Kopieren der Steuerelemente von der Visual Studio-Toolbox auf die Oberfläche des Benutzersteuerelements entwerfen. Weitere Informationen finden Sie unter [Gewusst wie: Erstellen eines SharePoint-Webparts mithilfe eines Designers](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) und [eines Bausteins: Webparts](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

### <a name="import-sharepoint-2010-solution-package"></a>SharePoint 2010-Lösungspaket importieren
 *Mit SharePoint 2010-Lösungspaketprojekten* importieren, mit denen Sie eine vorhandene SharePoint 2010-Website, die in eine SharePoint-Projektmappe *(WSP*)-Datei exportiert wurde, ganz oder teilweise in Visual Studio importieren können. Nach dem Importieren in Visual Studio können Sie die zugehörigen Elemente anpassen und erneut bereitstellen. Weitere Informationen finden Sie unter [Importieren von Elementen von einer vorhandenen SharePoint-Website](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).

### <a name="import-reusable-sharepoint-2010-workflow"></a>Importieren des wiederverwendbaren SharePoint 2010-Workflows
 *Mit dem importieren sie wiederverwendbare SharePoint 2010 Workflowprojekte* können Sie einen wiederverwendbaren, deklarativen Workflow importieren, der in SharePoint Designer 2010 erstellt wurde, in Visual Studio. Der Workflow wird als *WSP-Datei* von der SharePoint-Website exportiert. Nach dem Importieren in Visual Studio können Sie den Workflow anpassen, Code hinzufügen und anschließend auf einer SharePoint-Website bereitstellen. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Importieren eines wiederverwendbaren SharePoint Designer-Workflows in Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md).

## <a name="project-item-templates"></a>Projektelementvorlagen
 Im Folgenden finden Sie eine Liste von SharePoint-Projektelementvorlagen. Durch Projektelementvorlagen werden der SharePoint-Lösung Dateien zur Unterstützung von SharePoint-Funktionalität hinzugefügt, z. B. Websitespalten, Listen und Inhaltstypen. Wenn Sie der Projektmappe beispielsweise eine Websitespalte hinzufügen, wird ein Websitespaltenprojekt hinzugefügt, das eine *Elements.xml-Definitionsdatei* enthält. Durch hinzufügen eines visuellen Webparts wird der Projektmappe ein visuelles Webpartprojekt hinzugefügt, das eine *Elements.xml-Datei,* ein Benutzersteuerelementelement und ein visuelles Webpartelement enthält.

 Um die SharePoint-Projektelementvorlagen anzuzeigen, öffnen Sie im **Projektmappen-Explorer**das Kontextmenü für ein SharePoint-Projekt, und wählen Sie dann **Hinzufügen**, **Neues Element**aus. Erweitern Sie den **SharePoint-Knoten** entweder unter **Visual C oder** Visual **Basic**, und wählen Sie dann **2010**aus.

### <a name="application-page-farm-solution-only"></a>Anwendungsseite (nur Farmlösung)
 Mit einem **Element "Nur Farmlösung" (Farm Solution)** können Sie eine [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] Webseite für eine SharePoint-Website entwerfen. Anwendungsseiten können nur in Farmlösungen verwendet werden. Dieses Projektelement kann nur Farmlösungen hinzugefügt werden. Weitere Informationen finden Sie unter [Gewusst wie: Erstellen einer Anwendungsseite](../sharepoint/how-to-create-an-application-page.md) und [Anwendung _layouts Seitentyp](/previous-versions/office/aa979604(v=office.14)).

### <a name="business-data-connectivity-model-farm-solution-only"></a>Business Data Connectivity-Modell (nur Farmlösung)
 Mit einem **Business Data Connectivity Model (Nur Farm Solution)** können Sie Geschäftsdaten in SharePoint integrieren. Geschäftsdaten können von Back-End-Serveranwendungen stammen, z. B. [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)], Siebel und Service Advertising Protocol (SAP). Business Data Connectivity-Modelle können nur in Farmlösungen verwendet werden. Dieses Projektelement kann nur Farmlösungen hinzugefügt werden. Weitere Informationen finden Sie unter [Gewusst wie: Erstellen eines BDC-Modells](../sharepoint/how-to-create-a-bdc-model.md), [Gewusst wie: Verwenden einer Ressourcendatei zum Angeben lokalisierter Namen, Eigenschaften und Berechtigungen](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)und [Neuerungen: Business Connectivity Services](/previous-versions/office/developer/sharepoint-2010/ee534979(v=office.14)).

### <a name="content-type"></a>Inhaltstyp
 *Mit Inhaltstypelementen* können Sie benutzerdefinierte Inhaltstypen basierend auf einem vorhandenen (Basis-)Inhaltstyp wie einem Dokument, einer Ankündigung oder einer Aufgabe erstellen. Von einem benutzerdefinierten Inhaltstyp werden neben denselben Attributen und Feldern wie vom grundlegenden Inhaltstyp auch alle definierten Websitespalten (Felder) bereitgestellt. Beispielsweise können Sie einen benutzerdefinierten Inhaltstyp "Kontakt" erstellen, der auf dem grundlegenden Inhaltstyp "Kontakt" aus SharePoint basiert. Sie können den Inhaltstyp anpassen, indem vorhandene Websitespalten ändern oder zusätzliche Websitespalten zu den bereits im grundlegenden Inhaltstyp enthaltenen hinzufügen.

> [!NOTE]
> Aufgrund einer SharePoint-Einschränkung können Sie keinen Farmprojektmappeninhaltstyp auf Grundlage eines Sandkastenlösungsinhaltstyps erstellen.

 Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer Websitespalte, eines Inhaltstyps und einer Liste für SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) und [Denbau: Inhaltstyp](/previous-versions/office/developer/sharepoint-2010/ee535063(v=office.14)).

### <a name="empty-element"></a>Leeres Element
 *Leere Elemente* werden am häufigsten verwendet, um SharePoint-Projektelemente zu definieren, denen eine Projekt- oder Projektelementvorlage in Visual Studio fehlt. Wenn Sie Ihrem Projekt ein leeres Element hinzufügen, wird ein Knoten mit dem\) Namen EmptyElement[x] (wobei [x] eine eindeutige Zahl ist, erstellt. EmptyElement[x] enthält eine einzelne Datei mit dem Namen *Elements.xml.* Verwenden [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] Sie Anweisungen, um die gewünschten Elemente in *Elements.xml*zu definieren.

### <a name="event-receiver"></a>Ereignisempfänger
 *Ereignisempfänger* behandeln Ereignisse für Elemente in der SharePoint-Website, z. B. wenn ein Element zu einer Liste hinzugefügt wird, wenn ein Webelement gelöscht wird oder wenn ein Workflow gestartet wird. Die Projektelementvorlage "Ereignisempfänger" ermöglicht die Behandlung folgender Elemente:

- Listet Ereignisse auf.

- Listenelementereignisse

- Listen-E-Mail-Ereignisse

- Webereignisse

- Listenworkflowereignisse

  Das Ereignisempfängerprojektelement erstellt einen **Event Receiver-Ordner** mit einer einzelnen Klassendatei, die Ereignishandler für alle Ereignisse enthält, die Sie beim Erstellen des Projekts im **SharePoint-Anpassungs-Assistenten**angegeben haben. Die Ereignisempfängerklasse kann Ereignisse verarbeiten, die auf der SharePoint-Website auftreten, wenn Elemente wie Dateien, Felder, Elemente, Listen, Anlagen, Webparts und Workflows hinzugefügt, aktualisiert, gelöscht oder entfernt werden. Weitere Informationen finden Sie unter [Gewusst wie: Erstellen eines Ereignisempfängers](../sharepoint/how-to-create-an-event-receiver.md) und [Bausteins: Ereignisbehandlung](/previous-versions/office/developer/sharepoint-2010/ee535057(v=office.14)).

### <a name="list"></a>List
 Bei einer Liste handelt es sich um eine Instanz einer wiederverwendbaren, grundlegenden SharePoint-Listendefinition, z. B. ein Kalender oder eine Aufgabenliste. Nach dem Hinzufügen einer Liste zu Ihrer Lösung können Sie mit dem Listen-Designer Websitespalten zur Liste hinzufügen und benutzerdefinierte Listenspalten erstellen. Dazu gehören Websitespalten aus Inhaltstypen. Sie können die *Ansicht* für die Liste angeben, die die Spalten bestimmt, die in der Liste angezeigt werden. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer Websitespalte, eines Inhaltstyps und einer Liste für SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) und [Baustein: Listen und Dokumentbibliotheken](/previous-versions/office/developer/sharepoint-2010/ee534985(v=office.14)).

### <a name="module"></a>Modul
 *Module* (nicht zu verwechseln mit [!include[vbprvb](../sharepoint/includes/vbprvb-md.md)] Modulen) enthalten alle Dateien, die Sie auf dem SharePoint-Server bereitstellen möchten, z. B. Bilder oder Notizen. Das Modulprojektelement enthält einen **Modulknoten.** Der Modulknoten enthält zwei Projektelementvorlagen: eine XML-Definitionsdatei, die als Manifest für das Modul fungiert, und eine *sample.txt-Datei,* eine Platzhalterdatei. Weitere Informationen finden Sie unter [Verwenden von Modulen zum Einschließen von Dateien in die Projektmappe](../sharepoint/using-modules-to-include-files-in-the-solution.md) und [Module](/previous-versions/office/developer/sharepoint-2010/ms453137(v=office.14)).

### <a name="sequential-workflow-farm-solution-only"></a>Sequenzieller Workflow (nur Farmlösung)
 Ein *sequenzieller Workflow* ist eine Reihe von Geschäftslogikschritten, die nacheinander ausgeführt werden, bis der letzte Schritt abgeschlossen ist. Sequenzielle Workflows werden verwendet, um Prozesse zu verwalten, die SharePoint-Elemente wie Listen und Dokumente einschließen. Sie können Workflows auf Websiteebene (global) oder auf Listenebene (lokal) erstellen, und Sie können auswählen, ob ein Workflow automatisch oder manuell startet. Dieses Projektelement kann nur in Farmlösungen verwendet werden. Dieses Projektelement kann nur Farmlösungen hinzugefügt werden. Weitere Informationen finden Sie unter [Erstellen von SharePoint-Workflowlösungen](../sharepoint/creating-sharepoint-workflow-solutions.md), [Workflows in SharePoint Server 2010](/previous-versions/office/developer/sharepoint-2010/ms549489(v=office.14))und [Neuerungen: Workflowverbesserungen](/previous-versions/office/developer/sharepoint-2010/ee537015(v=office.14)).

### <a name="silverlight-web-part"></a>Silverlight-Webpart
 *Mit Silverlight-Webpartprojektelementen* können Sie Webparts für SharePoint erstellen, die Silverlight-Anwendungen anzeigen. Wenn Sie dieses Projektelement in Ihre Lösung einfügen, können Sie entweder eine neue Silverlight-Anwendung hinzufügen oder zu einem späteren Zeitpunkt auf eine vorhandene verweisen. Weitere Informationen finden Sie unter [Erstellen von Webparts für SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) und [exemplarische Vorgehensweise: Erstellen eines Silverlight-Webparts, das OData für SharePoint anzeigt.](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)

### <a name="site-column"></a>Site-Spalte
 Eine *Websitespalte*, auch als *Feld*bezeichnet, ist eines der grundlegendsten Elemente, die Sie einem SharePoint-Projekt hinzufügen können. Eine Websitespalte stellt einen Datentyp dar, z. B. eine Telefonnummer, ein Textkommentar oder der Name der Stadt eines Kontakts in einer Kontaktliste. Weitere Informationen finden Sie unter [Erstellen von Websitespalten, Inhaltstypen und Listen für SharePoint](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md) und [Spalten](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14)).

### <a name="site-definition-farm-solution-only"></a>Sitedefinition (nur Farmlösung)
 *Websitedefinitionsprojektelemente* enthalten einen Websitedefinitionsordner, der die folgenden Dateien enthält:

- Eine ASPX-Standardseite, die als Standardwebseite für die Website verwendet wird.

- Eine *onet.xml-Datei,* die die Komponenten der Site definiert.

- Eine webtemp-XML-Datei, die die Websitedefinitionskonfigurationen angibt, die im Abschnitt **Vorlagenauswahl** auf der **Seite Neue SharePoint-Website** angezeigt werden.

  Nach dem Hinzufügen einer Websitedefinition fügen Sie Code und Dateien hinzu, um Funktionen bereitzustellen. Dieses Projektelement kann nur in Farmlösungen verwendet werden. Dieses Projektelement kann nur Farmlösungen hinzugefügt werden. Weitere Informationen finden Sie unter [Erstellen von Websitedefinitionen für SharePoint-](../sharepoint/creating-site-definitions-for-sharepoint.md) und [Websitedefinitionen und -Konfigurationen](/previous-versions/office/developer/sharepoint-2010/aa978512(v=office.14)).

### <a name="state-machine-workflow-farm-solution-only"></a>State Machine Workflow (nur Farmlösung)
 Ein *Zustandscomputerworkflow* ist eine Reihe von Geschäftslogikzuständen, Übergängen und Aktionen. Die Schritte in einem Zustandsautomatworkflow werden nicht nacheinander ausgeführt, sondern von Aktionen und Zuständen ausgelöst. Ebenso wie sequenzielle Workflows werden Zustandsautomatworkflows SharePoint-Elementen wie Listen und Dokumenten zugeordnet. Auch in diesem Fall können Sie Workflows auf Websiteebene (global) oder auf Listenebene (lokal) erstellen. Außerdem können Sie auswählen, ob ein Workflow automatisch oder manuell startet. Dieses Projektelement kann nur in Farmlösungen verwendet werden. Dieses Projektelement kann nur Farmlösungen hinzugefügt werden. Weitere Informationen finden Sie unter [Erstellen von SharePoint-Workflowlösungen](../sharepoint/creating-sharepoint-workflow-solutions.md), [Workflows in SharePoint Server 2010](/previous-versions/office/developer/sharepoint-2010/ms549489(v=office.14))und [Neuerungen: Workflowverbesserungen](/previous-versions/office/developer/sharepoint-2010/ee537015(v=office.14)).

### <a name="user-control-farm-solution-only"></a>Benutzersteuerung (nur Farmlösung)
 Ein *Benutzersteuerelement* ist ein benutzerdefiniertes, wiederverwendbares Steuerelement, dem Sie weitere ASP.NET Steuerelemente und SharePoint-Steuerelemente hinzufügen können. Das Benutzersteuerelement kann in SharePoint ausgeführten Anwendungsseiten und Webparts hinzugefügt werden. Dieses Projektelement kann nur in Farmlösungen verwendet werden. Dieses Projektelement kann nur Farmlösungen hinzugefügt werden. Weitere Informationen finden Sie unter [Erstellen wiederverwendbarer Steuerelemente für Webparts oder Anwendungsseiten](creating-reusable-controls-for-web-parts-or-application-pages.md).

### <a name="visual-web-part"></a>Visuelles Webpart
 Ein *visuelles Webpartprojektelement* enthält eine *Elements.xml-Definitionsdatei,* ein **Webpartelement** und ein **Benutzersteuerelementelement.** Sie können die Darstellung des visuellen Webparts durch Ziehen oder Kopieren der Steuerelemente von der Visual Studio-Toolbox auf die Oberfläche des Benutzersteuerelements entwerfen. Weitere Informationen finden Sie unter [Gewusst wie: Erstellen eines SharePoint-Webparts mithilfe eines Designers](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) und [eines Bausteins: Webparts](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

### <a name="web-part"></a>Webpart
 Ein *Webpart* ist ein serverseitiges Steuerelement, das innerhalb eines speziellen Seitentyps ausgeführt wird, der als Webpartseite bezeichnet wird. Dies sind die Bausteine von auf SharePoint-Websites angezeigten Seiten. Vom Webpartelement werden Dateien bereitgestellt, mit denen Sie ein Webpart für eine SharePoint-Website entwerfen können. Weitere Informationen finden Sie unter [Gewusst wie: Erstellen eines SharePoint-Webparts](../sharepoint/how-to-create-a-sharepoint-web-part.md) und [Bausteins: Webparts](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

## <a name="see-also"></a>Siehe auch
- [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)
- [SharePoint-Produkte und -Technologien](/previous-versions/office/developer/sharepoint-2010/dd776256(v=office.12))
