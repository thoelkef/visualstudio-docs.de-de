---
title: Erstellen und Projektvorlagen für SharePoint-Projektelemente | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, creating custom templates
- .spdata files
- projects [SharePoint development in Visual Studio], creating custom templates
- SharePoint projects, creating custom templates
- SharePoint development in Visual Studio, creating custom project and item templates
- project items [SharePoint development in Visual Studio], creating custom templates
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 94f93d58933ad0aba6cde985dc260fe3341aa5d2
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/01/2018
ms.locfileid: "34691962"
---
# <a name="creating-item-templates-and-project-templates-for-sharepoint-project-items"></a>Erstellen von Elementvorlagen und Projektvorlagen für SharePoint-Projektelemente
  Wenn Sie einen benutzerdefinierten SharePoint-Projektelementtyp definieren, können Sie eine Elementvorlage oder einer Projektvorlage zuordnen, damit andere Entwickler das Projektelement in Visual Studio verwenden können. Sie können auch einen Assistenten für die Vorlage erstellen.  
  
 Visual Studio umfasst z. B. keine Projektvorlage oder Elementvorlage für eine SharePoint-Website ein Feld hinzugefügt. Sie können definieren einen SharePoint-Projektelementtyp, der ein Feld darstellt und erstellen Sie eine Elementvorlage, die andere Entwickler verwenden können, um das Feldelement zu einem SharePoint-Projekt hinzuzufügen. Oder Sie können eine Projektvorlage erstellen, damit Entwickler ein neues SharePoint-Projekt erstellen können, das das Feldelement enthält. In beiden Fällen können Sie auch einen Assistenten bereitstellen, der angezeigt wird, wenn Entwickler Ihre Vorlage verwenden. Mit diesem Assistenten kann Entwickler so konfigurieren Sie das neue Element oder ein Projekt Informationen sammeln.  
  
 Elementvorlagen und Projektvorlagen sind ZIP-Dateien, die Dateien enthalten, die zum Erstellen eines Projektelements oder ein Projekt von Visual Studio verwendet werden. Weitere Informationen zu den Grundlagen von Elementvorlagen und Projektvorlagen finden Sie unter [Erstellen von Projekt- und Elementvorlagen](/visualstudio/ide/creating-project-and-item-templates).  
  
## <a name="create-item-templates"></a>Erstellen von Elementvorlagen
 Wenn Sie eine Elementvorlage für eine SharePoint-Projektelement erstellen, gibt es einige Dateien, die immer erforderlich sind, und optionale Dateien, die von bestimmten Typen von Projektelementen verwendet werden können. Eine exemplarische Vorgehensweise, die veranschaulicht, wie einen SharePoint-Projektelementtyp definieren und erstellen eine Elementvorlage für finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer Custom Action Project Item mit einer Elementvorlage, Teil 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).  
  
 Die folgende Tabelle enthält die erforderlichen Dateien, um eine Elementvorlage für eine SharePoint-Projektelements zu erstellen.  
  
|Erforderliche Datei|Beschreibung|  
|-------------------|-----------------|  
|SPDATA-Datei|Dies ist eine XML-Datei, die den Inhalt und das Standardverhalten des Projektelements angibt. Diese Datei muss in der Elementvorlage enthalten sein. Weitere Informationen zum Inhalt von SPDATA-Dateien finden Sie unter [SharePoint-Projektelementschema](../sharepoint/sharepoint-project-item-schema-reference.md).|  
|Eine VSTEMPLATE-Datei.|Diese Datei erforderlichen Informationen zum Anzeigen der Vorlage in Visual Studio bietet die **neues Element hinzufügen** Dialogfeld und ein Projektelement aus der Vorlage zu erstellen. Diese Datei muss in der Elementvorlage enthalten sein. Weitere Informationen finden Sie unter [Visual Studio-Vorlage Metadatendateien](http://msdn.microsoft.com/en-us/129d59b5-7f9c-4daf-9832-eaedb3c4c961).|  
|Eine Assembly der Visual Studio-Erweiterung, die implementiert die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> Schnittstelle.|Diese Assembly wird das Laufzeitverhalten des Projektelements definiert. Diese Assembly muss im VSIX-Paket mit der Elementvorlage enthalten sein. Weitere Informationen finden Sie unter [Definieren von benutzerdefinierten SharePoint Projektelementtypen](../sharepoint/defining-custom-sharepoint-project-item-types.md) und [Bereitstellen von Erweiterungen für SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).|  
  
 Die folgende Tabelle enthält einige der am häufigsten verwendeten optionale Dateien, die in der Elementvorlage aufgenommen werden können. Einige Typen von Projektelementen möglicherweise andere Dateien, die hier nicht aufgeführt.  
  
|Optionale Datei|Beschreibung|  
|-------------------|-----------------|  
|Elements.xml|Ein *Funktionselement* Datei. Diese Datei definiert die Benutzeroberfläche und das Verhalten der Anpassung durch das Projektelement erstellt. Jeder Anpassung, z. B. Listeninstanzen, Inhaltstypen oder benutzerdefinierte Aktionen hat ein anderes Schema, das den Inhalt dieser Datei definiert. Weitere Informationen finden Sie unter [Baustein: Funktionen](http://go.microsoft.com/fwlink/?LinkId=169183) und [Feature Schemas](http://go.microsoft.com/fwlink/?LinkId=169192).|  
|Datei "Schema.xml"|Die Schemadatei für Listendefinitionen. Weitere Informationen finden Sie unter [Baustein: Listen und Dokumentbibliotheken](http://go.microsoft.com/fwlink/?LinkId=177792) und ["Schema.xml"](http://go.microsoft.com/fwlink/?LinkId=177793).|  
|Webpart|Ein *Webpart Definition* Datei. Diese Datei enthält die eigenschafteneinstellungen für ein Webpart. Weitere Informationen finden Sie unter [Baustein: Webparts](http://go.microsoft.com/fwlink/?LinkId=177791).|  
|.ascx|Ein ASP.NET-Benutzersteuerelement-Datei. Diese Datei definiert die Benutzeroberfläche des ein visuelles Webpart an.|  
|aspx|Eine Auslagerungsdatei für ASP.NET. Diese Datei enthält XML-Markup, das einer Seite "Anwendung" definiert.|  
|cs- oder VB-Dateien|Diese Dateien definieren das Verhalten des SharePoint-Anpassungen, die ein Programmiermodell aufweisen, die von Visual c# oder Visual Basic-Code, wie Anwendungsseiten, Webparts und Workflows zugegriffen werden kann.|  
  
## <a name="create-project-templates"></a>Erstellen von Projektvorlagen
 Wenn Sie eine SharePoint-Projektvorlage erstellen, sind einige Dateien, die immer erforderlichen und optionalen Dateien sind, die von bestimmten Typen von Projekten verwendet werden kann. SharePoint-Projekte enthalten in der Regel über mindestens ein SharePoint-Projektelement. Allerdings ist dies nicht erforderlich. Beispielsweise können Sie eine SharePoint-Projektvorlage definieren, die nur zur Bereitstellung von SharePoint-Lösungen, die in anderen Projekten erstellt verwendet werden sollen.  
  
 Eine exemplarische Vorgehensweise, die veranschaulicht, wie einen SharePoint-Projektelementtyp definieren und das Erstellen einer Projektvorlage für finden Sie unter [Exemplarische Vorgehensweise: Erstellen von Projektelement einer Websitespalte mit einer Projektvorlage, Teil 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).  
  
 Die folgende Tabelle enthält die Dateien, die in einer SharePoint-Projektvorlage enthalten sein müssen.  
  
|Erforderliche Datei|Beschreibung|  
|-------------------|-----------------|  
|Eine VSTEMPLATE-Datei|Diese Datei erforderlichen Informationen zum Anzeigen der Vorlage in Visual Studio bietet die **neues Projekt** (Dialogfeld) und ein Projekt aus der Vorlage zu erstellen. Weitere Informationen finden Sie unter [Visual Studio-Vorlage Metadatendateien](http://msdn.microsoft.com/en-us/129d59b5-7f9c-4daf-9832-eaedb3c4c961).|  
|Eine Csproj oder VBPROJ-Datei|Dies ist die Projektdatei. Er definiert den Inhalt und die Konfigurationseinstellungen des Projekts.|  
|Package.package|Diese Datei definiert, das Bereitstellungspaket für das Projekt. Wenn Sie die Paket-Designer verwenden, um das Lösungspaket für Ihr Projekt anzupassen, speichert Visual Studio Daten über das Lösungspaket in dieser Datei.<br /><br /> Wenn Sie eine benutzerdefinierte SharePoint-Projektvorlage erstellen, es wird empfohlen, dass Sie nur den Inhalt der Datei "Package.Package" erforderliche einschließen und des Lösungspakets konfigurieren, über die APIs in der <xref:Microsoft.VisualStudio.SharePoint.Packages> -Namespace in eine Erweiterung dar die Projektvorlage zugeordnet ist. Wenn Sie dies tun, ist die Projektvorlage aus zukünftigen Änderungen auf die Struktur der Datei "Package.Package" geschützt. Ein Beispiel für die Erstellung einer "Package.Package"-Datei mit nur den erforderlichen Inhalt veranschaulicht, finden Sie unter [Exemplarische Vorgehensweise: Erstellen von Projektelement einer Websitespalte mit einer Projektvorlage, Teil 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).<br /><br /> Wenn Sie die Datei "Package.Package" direkt ändern möchten, können Sie den Inhalt überprüfen, unter Verwendung des Schemas auf %Programme (x86)%\Microsoft Visual Studio 11.0\Xml\Schemas\PackageModelSchema.xsd.|  
|Package.Template.xml|Diese Datei bildet die Grundlage für die Lösung-Manifestdatei ("Manifest.xml") für die SharePoint-Lösungspaket (.wsp), das aus dem Projekt generiert wird. Wenn einige Verhaltensweisen, die nicht von Benutzern des Project-Typs geändert werden sollen, angeben möchten, können Sie Inhalt an dieser Datei hinzufügen. Weitere Informationen finden Sie unter [Baustein: Lösungen](http://go.microsoft.com/fwlink/?LinkId=169186) und [Lösung Schema](http://go.microsoft.com/fwlink/?LinkId=177794).<br /><br /> Bei der Erstellung eines Lösungspakets aus dem Projekt Visual Studio führt den Inhalt der Package.package zusammen, und die Package.Template.xml-Dateien in der Projektmappe Manifestdatei. Weitere Informationen zum Erstellen von Lösungspaketen finden Sie unter [Vorgehensweise: Erstellen eines SharePoint-Lösungspakets (Wsp)](http://msdn.microsoft.com/en-us/b24be45c-e91d-49bb-afb0-7b265404214b).|  
  
 Die folgende Tabelle enthält die optionalen Dateien, die in der Projektvorlage aufgenommen werden können.  
  
|Optionale Datei|Beschreibung|  
|-------------------|-----------------|  
|SharePoint-Projektelemente|Sie können eine oder mehrere SPDATA-Dateien einschließen, die SharePoint-Projektelementtypen zu definieren. Jede SPDATA-Datei muss kein entsprechendes vorhanden <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> Implementierung in einer Erweiterungsassembly, die im VSIX-Paket mit der Projektvorlage enthalten ist. Weitere Informationen finden Sie unter [Erstellen von Elementvorlagen](#creatingitemtemplates).<br /><br /> SharePoint-Projekte enthalten in der Regel über mindestens ein SharePoint-Projektelement. Allerdings ist dies nicht erforderlich.|  
|*FeatureName*Ereignisempfängers|Diese Datei definiert eine SharePoint-Funktion, die verwendet wird, um mehrere Projektelemente für die Bereitstellung zu gruppieren. Wenn Sie dem Funktions-Designer verwenden, um eine Funktion in Ihrem Projekt anzupassen, speichert Visual Studio Daten über die Funktion in dieser Datei. Wenn Sie die Projektelemente in andere Funktionen gruppieren möchten, können Sie mehrere Feature-Dateien einschließen.<br /><br /> Wenn Sie eine benutzerdefinierte SharePoint-Projektvorlage erstellen, es wird empfohlen, dass Sie nur den mindestens erforderlichen Inhalt in jeder Datei des Ereignisempfängers einschließen und der Features, zu konfigurieren, mithilfe der APIs in der <xref:Microsoft.VisualStudio.SharePoint.Features> -Namespace in eine Erweiterung, die mit zugeordnetem der Projektvorlage. Wenn Sie dies tun, ist die Projektvorlage aus zukünftigen Änderungen an der Struktur der Datei des Ereignisempfängers geschützt. Ein Beispiel, das veranschaulicht, wie eine Datei des Ereignisempfängers mit nur den erforderlichen Inhalt erstellen, finden Sie unter [Exemplarische Vorgehensweise: Erstellen von Projektelement einer Websitespalte mit einer Projektvorlage, Teil 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).<br /><br /> Wenn Sie eine Datei des Ereignisempfängers direkt ändern möchten, können Sie den Inhalt überprüfen, unter Verwendung des Schemas auf %Programme (x86)%\Microsoft Visual Studio 11.0\Xml\Schemas\FeatureModelSchema.xsd.|  
|*FeatureName*. Template.Xml|Diese Datei bildet die Grundlage für die Feature-Manifestdatei (Feature.xml) für jede Funktion, die aus dem Projekt generiert wird. Wenn einige Verhaltensweisen, die nicht von Benutzern des Project-Typs geändert werden sollen, angeben möchten, können Sie Inhalt an dieser Datei hinzufügen. Weitere Informationen finden Sie unter [Baustein: Funktionen](http://go.microsoft.com/fwlink/?LinkId=169183) und [Feature.xml](http://go.microsoft.com/fwlink/?LinkId=177795) Dateien.<br /><br /> Wenn Sie ein Lösungspaket aus dem Projekt erstellen, führt Visual Studio den Inhalt jedes Paars aus *FeatureName*Feature-Datei und *FeatureName*. Template.XML-Dateien in einer Funktion-Manifestdatei. Weitere Informationen zum Erstellen von Lösungspaketen finden Sie unter [Vorgehensweise: Erstellen eines SharePoint-Lösungspakets (Wsp)](http://msdn.microsoft.com/en-us/b24be45c-e91d-49bb-afb0-7b265404214b).|  
  
## <a name="create-wizards-for-item-templates-and-project-templates"></a>Assistenten für Elementvorlagen und Projektvorlagen erstellen
 Nachdem Sie einen SharePoint-Projektelementtyp definieren und ein Element oder einer Projektvorlage zuordnen, können Sie auch einen Assistenten erstellen. Der Assistent wird angezeigt, wenn ein Entwickler die Elementvorlage verwendet, um die SharePoint-Projektelement einem Projekt hinzufügen, oder wenn ein Entwickler die Projektvorlage verwendet, um ein neues Projekt erstellen, das die SharePoint-Projektelement enthält. Der Assistent kann zum Sammeln von Informationen von Entwicklern und die neue SharePoint-Projektelement initialisiert werden, verwendet werden.  
  
 Exemplarische Vorgehensweisen, die zum Erstellen der Assistenten für Elementvorlagen und Projektvorlagen zu veranschaulichen, finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer Custom Action Project Item mit einer Elementvorlage, Teil 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md) und [Exemplarische Vorgehensweise: Erstellen einer Website Projektelement mit einer Projektvorlage, Teil 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
## <a name="see-also"></a>Siehe auch
 [Definieren von benutzerdefinierten SharePoint-Projektelementtypen](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Exemplarische Vorgehensweise: Erstellen eines Projektelements für die benutzerdefinierte Aktion mit einer Elementvorlage, Teil 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Exemplarische Vorgehensweise: Erstellen eines Projektelements benutzerdefinierte Aktion mit einer Elementvorlage, Teil 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)   
 [Exemplarische Vorgehensweise: Erstellen ein Projekts Websitespalte mit einer Projektvorlage, Teil 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [Exemplarische Vorgehensweise: Erstellen ein Projekts Websitespalte mit einer Projektvorlage, Teil 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [Erstellen von Projekt- und Elementvorlagen](/visualstudio/ide/creating-project-and-item-templates)  
  
 