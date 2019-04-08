---
title: Erstellen von Item und Projektvorlagen für SharePoint-Projektelemente | Microsoft-Dokumentation
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a7bc365df9ef84b5ef8e501bcbbfd48865bb865e
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2019
ms.locfileid: "57868034"
---
# <a name="create-item-templates-and-project-templates-for-sharepoint-project-items"></a>Erstellen von Elementvorlagen und Projektvorlagen für SharePoint-Projektelemente
  Wenn Sie einen benutzerdefinierten SharePoint-Projektelementtyp definieren, können Sie es mit einer Elementvorlage oder einer Projektvorlage zuordnen. Diese Zuordnung ermöglicht anderen Entwicklern das Projektelement in Visual Studio verwenden. Sie können auch einen Assistenten für die Vorlage erstellen.

 Visual Studio umfasst z. B. keine Projektvorlage oder Elementvorlage für das Hinzufügen eines Felds zu einer SharePoint-Website. Sie können definieren ein SharePoint-Projektelementtyps, das ein Feld darstellt und erstellen dann eine Item-Vorlage, mit denen andere Entwickler das Field-Element zu einer SharePoint-Projekt hinzufügen. Oder Sie können eine Projektvorlage aus, damit Entwickler ein neues SharePoint-Projekt erstellen können, die das Field-Element erstellen. In beiden Fällen können Sie auch einen Assistenten angeben, der angezeigt wird, wenn der Entwickler Ihre Vorlage zu verwenden. Mit diesem Assistenten können Sie Informationen von Entwicklern so konfigurieren Sie das neue Element oder Projekt sammeln.

 Elementvorlagen und Projektvorlagen sind *ZIP* Dateien, die Dateien, die von Visual Studio verwendet werden enthalten, um ein Projektelement oder das Projekt zu erstellen. Weitere Informationen zu den Grundlagen von Elementvorlagen und Projektvorlagen finden Sie unter [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md).

## <a name="create-item-templates"></a>Erstellen von Elementvorlagen
 Wenn Sie eine Elementvorlage für eine SharePoint-Projektelement erstellen, gibt es einige Dateien, die immer erforderlich sind, und optionale Dateien, die von bestimmten Typen von Projektelementen verwendet werden können. Eine exemplarische Vorgehensweise, die zeigt, wie Sie einen SharePoint-Projektelementtyp definieren und das Erstellen einer Elementvorlage für finden Sie unter [Exemplarische Vorgehensweise: Erstellen Sie benutzerdefinierte Aktionsprojektelement, mit einer Elementvorlage, Teil 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).

 Die folgende Tabelle enthält die erforderlichen Dateien zum Erstellen einer Elementvorlage für ein SharePoint-Projektelement.

|Erforderliche Datei|Beschreibung|
|-------------------|-----------------|
|Ein *SPDATA* Datei|Diese XML-Datei gibt an, den Inhalt und das Standardverhalten des Projektelements. Diese Datei muss in der Elementvorlage enthalten sein. Weitere Informationen über den Inhalt des *SPDATA* finden Sie unter [SharePoint-Projektelementschema](../sharepoint/sharepoint-project-item-schema-reference.md).|
|Ein *VSTEMPLATE* Datei.|Diese Datei werden die erforderlichen Informationen zum Anzeigen der Vorlage in Visual Studio bietet die **neues Element hinzufügen** Dialogfeld und ein Projektelement aus der Vorlage zu erstellen. Diese Datei muss in der Elementvorlage enthalten sein. Weitere Informationen finden Sie unter [Visual Studio-Vorlagen-Metadatendateien](/previous-versions/visualstudio/visual-studio-2010/xsxc3ete\(v\=vs.100\)).|
|Eine Visual Studio-Erweiterungsassembly, implementiert die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> Schnittstelle.|Diese Assembly definiert, das Laufzeitverhalten des Projektelements. Diese Assembly muss im VSIX-Paket mit der Elementvorlage enthalten sein. Weitere Informationen finden Sie unter [definieren Sie benutzerdefinierte SharePoint-Projektelementtypen](../sharepoint/defining-custom-sharepoint-project-item-types.md) und [Bereitstellen von Erweiterungen für SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).|

 Die folgende Tabelle enthält einige der am häufigsten verwendeten optionalen Dateien, die in der Elementvorlage aufgenommen werden können. Einige Typen von Projektelementen möglicherweise andere Dateien, die hier nicht aufgeführt.


| Optionale Datei | Beschreibung |
|----------------------| - |
| *Elements.xml* | Ein *"Feature"-Element* Datei. Diese Datei definiert die Benutzeroberfläche und das Verhalten der Anpassung des Projektelements erstellt. Jede Anpassung, z. B. Listeninstanzen, Inhaltstypen und benutzerdefinierte Aktionen verfügt über ein anderes Schema, das den Inhalt dieser Datei definiert. Weitere Informationen finden Sie unter [Baustein: Features](http://go.microsoft.com/fwlink/?LinkId=169183) und [Feature Schemas](http://go.microsoft.com/fwlink/?LinkId=169192). |
| *Schema.xml* | Die Schemadatei für Listendefinitionen. Weitere Informationen finden Sie unter [Baustein: Listen und Dokumentbibliotheken](http://go.microsoft.com/fwlink/?LinkId=177792) und ["Schema.xml"](http://go.microsoft.com/fwlink/?LinkId=177793). |
| *.webpart* | Ein *Webpartdefinition* Datei. Diese Datei enthält die Einstellungen der Eigenschaft für ein Webpart. Weitere Informationen finden Sie unter [Baustein: Webparts](http://go.microsoft.com/fwlink/?LinkId=177791). |
| *.ascx* | Eine ASP.NET UserControl-Datei. Diese Datei definiert die Benutzeroberfläche des ein visuelles Webpart an. |
| *.aspx* | Eine Datei der ASP.NET-Seite. Diese Datei enthält die XML-Markup, das eine Seite "Anwendung" definiert. |
| *cs* oder *vb* Dateien | Dieser Codedateien definieren das Verhalten des SharePoint-Anpassungen, die ein Programmiermodell, das die von Visual C# oder Visual Basic-Code, z. B. Anwendungsseiten, Webparts und Workflows zugegriffen werden kann. |

## <a name="create-project-templates"></a>Erstellen von Projektvorlagen
 Wenn Sie eine SharePoint-Projektvorlage erstellen, gibt es einige Dateien, die immer erforderlichen und optionalen Dateien sind, die von bestimmten Typen von Projekten verwendet werden kann. SharePoint-Projekte enthalten in der Regel mindestens eine SharePoint-Projektelement. Dies ist jedoch nicht erforderlich. Sie können z. B. eine SharePoint-Projektvorlage definieren, die nur für die Bereitstellung von SharePoint-Lösungen, die in anderen Projekten erstellt verwendet werden soll.

 Eine exemplarische Vorgehensweise, die zeigt, wie Sie einen SharePoint-Projektelementtyp definieren und das Erstellen einer Projektvorlage für finden Sie unter [Exemplarische Vorgehensweise: Erstellen ein Projektelements Spalte mit einer Projektvorlage, Teil 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).

 Die folgende Tabelle enthält die Dateien, die in einer SharePoint-Projektvorlage enthalten sein müssen.

|Erforderliche Datei|Beschreibung|
|-------------------|-----------------|
|Ein *VSTEMPLATE* Datei|Diese Datei werden die erforderlichen Informationen zum Anzeigen der Vorlage in Visual Studio bietet die **neues Projekt** Dialogfeld und zum Erstellen eines Projekts aus der Vorlage. Weitere Informationen finden Sie unter [Visual Studio-Vorlagen-Metadatendateien](/previous-versions/visualstudio/visual-studio-2010/xsxc3ete\(v\=vs.100\)).|
|Ein *csproj* oder *vbproj* Datei|Dies ist der Projektdatei. Er definiert den Inhalt und die Konfigurationseinstellungen des Projekts.|
|*Package.package*|Diese Datei definiert Bereitstellungspakets für das Projekt. Wenn Sie die Paket-Designer verwenden, das Lösungspaket für Ihr Projekt anpassen, speichert Visual Studio Daten über das Lösungspaket in dieser Datei.<br /><br /> Wenn Sie eine benutzerdefinierte SharePoint-Projektvorlage erstellen, empfohlen, dass Sie nur den minimalen erforderlichen Inhalt in die *Package.package* -Datei, und konfigurieren das Projektmappenpaket mithilfe der APIs in der <xref:Microsoft.VisualStudio.SharePoint.Packages> Der Namespace in eine Erweiterung, die mit der Projektvorlage zugeordnet ist. Wenn Sie dies tun, Ihre Projektvorlage ist geschützt, über zukünftige Änderungen an der Struktur des der *Package.package* Datei. Ein Beispiel für die Vorgehensweise: Erstellen einer *Package.package* Inhalt der Datei mit nur einem Minimum erforderlich sind, finden Sie unter [Exemplarische Vorgehensweise: Erstellen ein Projektelements Spalte mit einer Projektvorlage, Teil 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).<br /><br /> Wenn Sie ändern möchten, die *"Package.Package"* Datei direkt, Sie können den Inhalt überprüfen, indem Sie mit dem Schema auf *%Programme (x86)%\Microsoft Visual Studio 11.0\Xml\Schemas\PackageModelSchema.xsd* .|
|*Package.Template.xml*|Diese Datei bildet die Grundlage für die Manifestdatei der Lösung (*"Manifest.xml"*) für die SharePoint-Lösungspaket (*.wsp*), die aus dem Projekt generiert wird. Sie können die Inhalte dieser Datei hinzufügen, sollten Sie ein Verhalten angeben, die nicht von Benutzern der Art Ihres Projekts geändert werden soll. Weitere Informationen finden Sie unter [Baustein: Lösungen](http://go.microsoft.com/fwlink/?LinkId=169186) und [Lösung Schema](http://go.microsoft.com/fwlink/?LinkId=177794).<br /><br /> Wenn Sie ein Lösungspaket aus dem Projekt erstellen, führt Visual Studio den Inhalt des der *Package.package* und *Package.Template.xml* -Dateien in der Lösung der Manifestdatei. Weitere Informationen zum Erstellen von Lösungspaketen finden Sie unter [Vorgehensweise: Erstellen eines SharePoint-Lösungspakets mithilfe von MSBuild-Aufgaben](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).|

 Die folgende Tabelle enthält die optionalen Dateien, die in der Projektvorlage aufgenommen werden können.

|Optionale Datei|Beschreibung|
|-------------------|-----------------|
|SharePoint-Projektelemente|Sie können eine oder mehrere SPDATA-Dateien einschließen, die SharePoint-Projektelementtypen definieren. Jede *SPDATA* Datei muss ein entsprechendes haben <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> Implementierung in einer Erweiterungsassembly, die im VSIX-Paket mit der Projektvorlage enthalten ist. Weitere Informationen finden Sie unter [Erstellen von Elementvorlagen](#createitemtemplates).<br /><br /> SharePoint-Projekte enthalten in der Regel mindestens eine SharePoint-Projektelement. Dies ist jedoch nicht erforderlich.|
|*\<featureName>.feature*|Diese Datei definiert eine SharePoint-Funktion, die verwendet wird, um mehrere Projektelemente für die Bereitstellung zu gruppieren. Wenn Sie die Funktions-Designer verwenden, um ein Feature in Ihrem Projekt anzupassen, speichert Visual Studio Daten über das Feature in dieser Datei. Wenn Sie die Projektelemente in andere Funktionen gruppieren möchten, können Sie mehrere einschließen *.feature* Dateien.<br /><br /> Wenn Sie eine benutzerdefinierte SharePoint-Projektvorlage erstellen, es wird empfohlen, dass Sie nur den mindestens erforderlichen Inhalt in den einzelnen einschließen *.feature* -Datei, und Sie Features konfigurieren, werden mithilfe der APIs in der <xref:Microsoft.VisualStudio.SharePoint.Features> -Namespace in eine Erweiterung, die mit der Projektvorlage zugeordnet ist. Wenn Sie dies tun, Ihre Projektvorlage ist geschützt, über zukünftige Änderungen an der Struktur des der *.feature* Datei. Ein Beispiel für die Vorgehensweise: Erstellen einer *.feature* Inhalt der Datei mit nur einem Minimum erforderlich sind, finden Sie unter [Exemplarische Vorgehensweise: Erstellen ein Projektelements Spalte mit einer Projektvorlage, Teil 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).<br /><br /> Wenn Sie ändern möchten, eine *.feature* Datei direkt, Sie können den Inhalt überprüfen, indem Sie mit dem Schema auf *%Programme (x86)%\Microsoft Visual Studio 11.0\Xml\Schemas\FeatureModelSchema.xsd*.|
|*\<featureName>.Template.xml*|Diese Datei bildet die Grundlage für die Manifestdatei des Features (*"Feature.xml"*) für jede Funktion, die aus dem Projekt generiert wird. Sie können die Inhalte dieser Datei hinzufügen, sollten Sie ein Verhalten angeben, die nicht von Benutzern der Art Ihres Projekts geändert werden soll. Weitere Informationen finden Sie unter [Baustein: Features](http://go.microsoft.com/fwlink/?LinkId=169183) und ["Feature.xml"](http://go.microsoft.com/fwlink/?LinkId=177795) Dateien.<br /><br /> Wenn Sie ein Lösungspaket aus dem Projekt erstellen, führt Visual Studio den Inhalt der einzelnen  *\<FeatureName > .feature* Datei und  *\<FeatureName >. Template.XML* -Dateien in ein Feature der Manifestdatei. Weitere Informationen zum Erstellen von Lösungspaketen finden Sie unter [Vorgehensweise: Erstellen eines SharePoint-Lösungspakets mithilfe von MSBuild-Aufgaben](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).|

## <a name="create-wizards-for-item-templates-and-project-templates"></a>Erstellen von Elementvorlagen und Projektvorlagen-Assistenten
 Nachdem Sie einen SharePoint-Projektelementtyp definieren und ein Element oder einer Projektvorlage zuordnen, können Sie auch einen Assistenten erstellen. Der Assistent zeigt an, wenn ein Entwickler die Item-Vorlage verwendet, um SharePoint-Projektelements zu einem Projekt hinzuzufügen, oder wenn ein Entwickler die Projektvorlage verwendet, um ein neues Projekt zu erstellen, das die SharePoint-Projektelement enthält. Der Assistent kann zum Sammeln von Informationen von Entwicklern und initialisieren das neue SharePoint-Projektelement verwendet werden.

 Exemplarische Vorgehensweisen, die veranschaulichen, wie Sie den Assistenten für Elementvorlagen und Projektvorlagen erstellen, finden Sie unter [Exemplarische Vorgehensweise: Erstellen ein Projektelements benutzerdefinierte Aktion mit einer Elementvorlage, Teil 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md) und [Exemplarische Vorgehensweise: Erstellen ein Projektelements Spalte mit einer Projektvorlage, Teil 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).

## <a name="see-also"></a>Siehe auch

- [Definieren von benutzerdefinierten SharePoint-Projektelementtypen](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Exemplarische Vorgehensweise: Erstellen eines Projektelements benutzerdefinierte Aktion mit einer Elementvorlage, Teil 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [Exemplarische Vorgehensweise: Erstellen eines Projektelements benutzerdefinierte Aktion mit einer Elementvorlage, Teil 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)
- [Exemplarische Vorgehensweise: Erstellen eines Projektelements Spalte mit einer Projektvorlage, Teil 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [Exemplarische Vorgehensweise: Erstellen eines Projektelements Spalte mit einer Projektvorlage, Teil 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)
- [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)
