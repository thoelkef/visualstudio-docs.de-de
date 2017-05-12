---
title: "Creating Item Templates and Project Templates for SharePoint Project Items"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SharePoint project items, creating custom templates"
  - ".spdata files"
  - "projects [SharePoint development in Visual Studio], creating custom templates"
  - "SharePoint projects, creating custom templates"
  - "SharePoint development in Visual Studio, creating custom project and item templates"
  - "project items [SharePoint development in Visual Studio], creating custom templates"
ms.assetid: c95b5e35-76c4-4f0a-b645-0467ae683659
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# Creating Item Templates and Project Templates for SharePoint Project Items
  Wenn Sie einen benutzerdefinierten SharePoint\-Projektelementtyp definieren, können Sie ihn einer Elementvorlage oder einer Projektvorlage zuordnen, damit andere Entwickler das Projektelement in Visual Studio verwenden können.  Sie können auch einen Assistenten für die Vorlage erstellen.  
  
 So enthält Visual Studio beispielsweise keine Projektvorlage oder Elementvorlage für das Hinzufügen eines Felds zu einer SharePoint\-Website.  Sie können einen SharePoint\-Projektelementtyp definieren, der ein Feld darstellt, und anschließend eine Elementvorlage erstellen, mit der andere Entwickler das Feldelement einem SharePoint\-Projekt hinzufügen können.  Oder, können Sie eine Projektvorlage erstellen, damit Entwickler ein neues SharePoint\-Projekt erstellen können, das dem Feldelement. In beiden Fällen können Sie außerdem einen Assistenten bereitstellen, der angezeigt wird, wenn Entwickler Ihre Vorlage verwenden.  Mit dem Assistenten können Informationen von Entwicklern erfasst werden, um das neue Element oder Projekt zu konfigurieren.  
  
 Elementvorlagen und Projektvorlagen sind ZIP\-Dateien mit Dateien, die von Visual Studio verwendet werden, um ein Projektelement oder ein Projekt zu erstellen.  Weitere Informationen zu den Grundlagen von Elementvorlagen oder Projektvorlagen finden Sie unter [Erstellen von benutzerdefinierten Projekt- und Elementvorlagen in Visual Studio](../ide/creating-project-and-item-templates.md).  
  
##  <a name="creatingitemtemplates"></a> Erstellen von Elementvorlagen  
 Wenn Sie eine Elementvorlage für ein SharePoint\-Projektelement erstellen, sind einige Dateien immer erforderlich, während andere Dateien, die möglicherweise von bestimmten Projektelementtypen verwendet werden, optional sind.  Eine exemplarische Vorgehensweise, in der das Definieren eines SharePoint\-Projektelementtyps und das Erstellen einer Elementvorlage für den Elementtyp veranschaulicht werden, finden Sie unter [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).  
  
 In der folgenden Tabelle sind die erforderlichen Dateien zum Erstellen einer Elementvorlage für ein SharePoint\-Projektelement aufgeführt.  
  
|Erforderliche Datei|Description|  
|-------------------------|-----------------|  
|SPDATA\-Datei|Hierbei handelt es sich um eine XML\-Datei, mit der Inhalt und Standardverhalten des Projektelements angegeben werden.  Diese Datei muss in der Elementvorlage enthalten sein.  Weitere Informationen zum Inhalt von SPDATA\-Dateien finden Sie unter [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md).|  
|Eine VSTEMPLATE\-Datei.|Mit dieser Datei werden die Informationen für Visual Studio bereitgestellt, die erforderlich sind, um die Vorlage im Dialogfeld **Neues Element hinzufügen** anzuzeigen und ein Projektelement aus der Vorlage zu erstellen.  Diese Datei muss in der Elementvorlage enthalten sein.  Weitere Informationen finden Sie unter [NIB: Visual Studio Template Metadata Files](http://msdn.microsoft.com/de-de/129d59b5-7f9c-4daf-9832-eaedb3c4c961).|  
|Eine Visual Studio\-Erweiterungsassembly, von der die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>\-Schnittstelle implementiert wird.|Mit dieser Assembly wird das Verhalten der Laufzeit für das Projektelement definiert.  Diese Assembly muss sich im VSIX\-Paket mit der Elementvorlage befinden.  Weitere Informationen finden Sie unter [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md) und [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).|  
  
 In der folgenden Tabelle sind einige der gängigsten optionalen Dateien aufgelistet, die in der Elementvorlage enthalten sein können.  Einige Projektelementtypen erfordern möglicherweise andere Dateien, die hier nicht aufgeführt sind.  
  
|Optionale Datei|Description|  
|---------------------|-----------------|  
|Elements.xml|Eine Datei vom Typ *Feature\-Element*.  Mit dieser Datei werden Benutzeroberfläche und Verhalten der vom Projektelement erstellten Anpassung definiert.  Jeder Anpassungstyp \(beispielsweise Listeninstanzen, Inhaltstypen oder benutzerdefinierte Aktionen\) besitzt ein anderes Schema zum Definieren des Dateiinhalts.  Weitere Informationen finden Sie unter [Baustein: Funktionen](http://go.microsoft.com/fwlink/?LinkId=169183) sowie unter [Funktionsschemas](http://go.microsoft.com/fwlink/?LinkId=169192).|  
|Schema.xml|Die Schemadatei für Listendefinitionen.  Weitere Informationen finden Sie unter [Baustein: Listen und Dokumentbibliotheken](http://go.microsoft.com/fwlink/?LinkId=177792) sowie unter [Schema.xml](http://go.microsoft.com/fwlink/?LinkId=177793).|  
|WEBPART\-Datei|Eine Datei vom Typ *Webpartdefinition*.  Diese Datei enthält Eigenschafteneinstellungen für ein Webpart.  Weitere Informationen finden Sie unter [Baustein: Webparts](http://go.microsoft.com/fwlink/?LinkId=177791).|  
|.ascx|Eine ASP.NET\-UserControl\-Datei.  Mit dieser Datei wird die Benutzeroberfläche eines visuellen Webparts definiert.|  
|.aspx|Eine ASP.NET\-Datei.  Diese Datei enthält XML\-Markup zum Definieren einer Anwendungsseite.|  
|CS\- oder VB\-Dateien|Diese Codedateien dienen zum Definieren des Verhaltens von SharePoint\-Anpassungen mit einem Programmiermodell, auf das von Visual C\#\- oder Visual Basic\-Code aus zugegriffen werden kann \(beispielsweise Anwendungsseiten, Webparts oder Workflows\).|  
  
## Erstellen von Projektvorlagen  
 Wenn Sie eine SharePoint\-Projektvorlage erstellen, sind einige Dateien immer erforderlich, während andere optionale sind und nur von bestimmten Projekttypen verwendet werden.  Normalerweise enthalten SharePoint\-Projekte mindestens ein SharePoint\-Projektelement.  Dies ist jedoch nicht erforderlich.  Beispielsweise kann eine SharePoint\-Projektvorlage definiert werden, die ausschließlich zum Bereitstellen von SharePoint\-Lösungen verwendet werden soll, die in anderen Projekten erstellt wurden.  
  
 Eine exemplarische Vorgehensweise, in der das Definieren eines SharePoint\-Projektelementtyps und das Erstellen einer Projektvorlage für den Elementtyp veranschaulicht werden, finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines Projektelements "Websitespalte" mit einer Projektvorlage, Teil 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).  
  
 In der folgenden Tabelle sind die Dateien aufgelistet, die in einer SharePoint\-Projektvorlage enthalten sein müssen.  
  
|Erforderliche Datei|Description|  
|-------------------------|-----------------|  
|VSTEMPLATE\-Datei|Mit dieser Datei werden die Informationen für Visual Studio bereitgestellt, die erforderlich sind, um die Vorlage im Dialogfeld **Neues Projekt** anzuzeigen und ein Projekt aus der Vorlage zu erstellen.  Weitere Informationen finden Sie unter [NIB: Visual Studio Template Metadata Files](http://msdn.microsoft.com/de-de/129d59b5-7f9c-4daf-9832-eaedb3c4c961).|  
|CSPROJ\- oder VBPROJ\-Datei|Dies ist die Projektdatei.  Sie definiert den Inhalt und die Konfigurationseinstellungen des Projekts.|  
|Package.package|Mit dieser Datei wird das Bereitstellungspaket für das Projekt definiert.  Wenn Sie das Lösungspaket für das Projekt mithilfe des Paket\-Designers anpassen, werden in dieser Datei Daten zum Lösungspaket gespeichert.<br /><br /> Wenn Sie eine benutzerdefinierte SharePoint\-Projektvorlage erstellen, empfiehlt es sich, in die Datei "Package.package" lediglich den erforderlichen Mindestinhalt einzuschließen und das Lösungspaket mithilfe der APIs im <xref:Microsoft.VisualStudio.SharePoint.Packages>\-Namespace in einer der Projektvorlage zugeordneten Erweiterung zu konfigurieren.  Dadurch wird die Projektvorlage vor zukünftigen Änderungen an der Struktur der Datei "Package.package" geschützt.  Ein veranschaulichendes Beispiel für die Erstellung einer Datei vom Typ "Package.package" mit lediglich dem erforderlichen Mindestinhalt finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines Projektelements "Websitespalte" mit einer Projektvorlage, Teil 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).<br /><br /> Wenn Sie die Datei "Package.package" direkt ändern möchten, können Sie den Inhalt mithilfe des Schemas unter "%Programme \(x86\)%\\Microsoft Visual Studio 11.0\\Xml\\Schemas\\PackageModelSchema.xsd" überprüfen.|  
|Package.Template.xml|Von dieser Datei wird die Basis für die Lösungsmanifestdatei \("manifest.xml"\) für das SharePoint\-Lösungspaket \(WSP\-Datei\) bereitgestellt, das vom Projekt generiert wird.  Sie können dieser Datei Inhalt hinzufügen, wenn Sie ein Verhalten angeben möchten, das von den Benutzern des Projekttyps nicht geändert werden soll.  Weitere Informationen finden Sie unter [Baustein: Lösungen](http://go.microsoft.com/fwlink/?LinkId=169186) sowie unter [Lösungsschema](http://go.microsoft.com/fwlink/?LinkId=177794).<br /><br /> Wenn Sie ein Lösungspaket auf der Grundlage des Projekts erstellen, werden der Inhalt der Datei "Package.package" und der Inhalt der Datei "Package.Template.xml" in der Lösungsmanifestdatei zusammengeführt.  Weitere Informationen zum Erstellen von Lösungspaketen finden Sie unter [How to: Create a SharePoint Solution Package \(wsp\)](http://msdn.microsoft.com/de-de/b24be45c-e91d-49bb-afb0-7b265404214b).|  
  
 In der folgenden Tabelle sind die optionalen Dateien aufgeführt, die in der Projektvorlage enthalten sein können.  
  
|Optionale Datei|Description|  
|---------------------|-----------------|  
|SharePoint\-Projektelemente|Sie können eine oder mehrere SPDATA\-Dateien einschließen, mit denen SharePoint\-Projektelementtypen definiert werden.  Jede SPDATA\-Datei muss eine entsprechende <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>\-Implementierung in einer Erweiterungsassembly im VSIX\-Paket für die Projektvorlage aufweisen.  Weitere Informationen finden Sie unter [Erstellen von Elementvorlagen](#creatingitemtemplates).<br /><br /> Normalerweise enthalten SharePoint\-Projekte mindestens ein SharePoint\-Projektelement.  Dies ist jedoch nicht erforderlich.|  
|*Funktionsname*.feature|Mit dieser Datei wird eine SharePoint\-Funktion definiert, mit der mehrere Projektelemente für die Bereitstellung gruppiert werden.  Wenn Sie eine Funktion im Projekt mithilfe des Funktions\-Designers anpassen, werden in dieser Datei Daten zur Funktion gespeichert.  Wenn Sie die Projektelemente in andere Funktionen gruppieren möchten, können Sie mehrere FEATURE\-Dateien einschließen.<br /><br /> Wenn Sie eine benutzerdefinierte SharePoint\-Projektvorlage erstellen, empfiehlt es sich, in die einzelnen FEATURE\-Dateien lediglich den erforderlichen Mindestinhalt einzuschließen und Funktionen mithilfe der APIs im <xref:Microsoft.VisualStudio.SharePoint.Features>\-Namespace in einer der Projektvorlage zugeordneten Erweiterung zu konfigurieren.  Dadurch wird die Projektvorlage vor zukünftigen Änderungen an der Struktur der FEATURE\-Datei geschützt.  Ein veranschaulichendes Beispiel für die Erstellung einer FEATURE\-Datei mit lediglich dem erforderlichen Mindestinhalt finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines Projektelements "Websitespalte" mit einer Projektvorlage, Teil 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).<br /><br /> Wenn Sie eine FEATURE\-Datei direkt ändern möchten, können Sie den Inhalt mithilfe des Schemas unter "%Programme \(x86\)%\\Microsoft Visual Studio 11.0\\Xml\\Schemas\\FeatureModelSchema.xsd" überprüfen.|  
|*Funktionsname*.Template.xml|Von dieser Datei wird die Basis für die Funktionsmanifestdatei \("Feature.xml"\) der einzelnen Funktionen bereitgestellt, die vom Projekt generiert werden.  Sie können dieser Datei Inhalt hinzufügen, wenn Sie ein Verhalten angeben möchten, das von den Benutzern des Projekttyps nicht geändert werden soll.  Weitere Informationen finden Sie unter [Baustein: Funktionen](http://go.microsoft.com/fwlink/?LinkId=169183) sowie unter [Dateien vom Typ "Feature.xml"](http://go.microsoft.com/fwlink/?LinkId=177795).<br /><br /> Wenn Sie ein Lösungspaket auf der Grundlage des Projekts erstellen, wird der Inhalt der einzelnen Paare aus "*Funktionsname*.feature" und "*Funktionsname*.Template.xml" in einer Funktionsmanifestdatei zusammengeführt.  Weitere Informationen zum Erstellen von Lösungspaketen finden Sie unter [How to: Create a SharePoint Solution Package \(wsp\)](http://msdn.microsoft.com/de-de/b24be45c-e91d-49bb-afb0-7b265404214b).|  
  
## Erstellen von Assistenten für Elementvorlagen und Projektvorlagen  
 Nachdem Sie einen SharePoint\-Projektelementtyp definiert und diesen einem Element oder einer Projektvorlage zugeordnet haben, können Sie außerdem einen Assistenten erstellen.  Der Assistent wird angezeigt, wenn ein Entwickler das SharePoint\-Projektelement mithilfe der Elementvorlage einem Projekt hinzufügt oder wenn ein Entwickler mithilfe der Projektvorlage ein neues Projekt erstellt, das das SharePoint\-Projektelement enthält.  Mit dem Assistenten können Informationen von Entwicklern erfasst und neue SharePoint\-Projektelemente initialisiert werden.  
  
 Exemplarische Vorgehensweisen, in denen veranschaulicht wird, wie Assistenten für Elementvorlagen und Projektvorlagen erstellt werden, finden Sie unter [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md) und [Exemplarische Vorgehensweise: Erstellen eines Projektelements "Websitespalte" mit einer Projektvorlage, Teil 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
## Siehe auch  
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)   
 [Exemplarische Vorgehensweise: Erstellen eines Projektelements "Websitespalte" mit einer Projektvorlage, Teil 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [Exemplarische Vorgehensweise: Erstellen eines Projektelements "Websitespalte" mit einer Projektvorlage, Teil 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [Erstellen von benutzerdefinierten Projekt- und Elementvorlagen in Visual Studio](../ide/creating-project-and-item-templates.md)  
  
  