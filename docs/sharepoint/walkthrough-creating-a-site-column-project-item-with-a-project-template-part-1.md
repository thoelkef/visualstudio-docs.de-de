---
title: 'Exemplarische Vorgehensweise: Erstellen eines Projektelements Spalte mit einer Projektvorlage, Teil 1 | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint projects, creating custom templates
- SharePoint development in Visual Studio, defining new project item types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 202a9ac88310656c59fa507cbb8fe271b6f1d040
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49813209"
---
# <a name="walkthrough-create-a-site-column-project-item-with-a-project-template-part-1"></a>Exemplarische Vorgehensweise: Erstellen eines Projektelements Spalte mit einer Projektvorlage, Teil 1
  SharePoint-Projekte sind Container für SharePoint-Projektelemente. Sie können das SharePoint-Projektsystem in Visual Studio erweitern, indem Sie eigene SharePoint-Projektelementtypen erstellen und diese dann einer Projektvorlage zuordnen. In dieser exemplarischen Vorgehensweise definieren Sie einen Projektelementtyp zum Erstellen einer Websitespalte. Anschließend erstellen Sie eine Projektvorlage, mit der ein neues Projekt erstellt werden kann, das ein Projektelement einer Websitespalte enthält.  
  
 Diese exemplarische Vorgehensweise enthält die folgenden Aufgaben:  
  
- Erstellen einer Visual Studio-Erweiterung, die einen neuen Typ von SharePoint-Projektelement für eine Websitespalte definiert. Der Projektelementtyp enthält eine einfache benutzerdefinierte Eigenschaft, die in angezeigt wird. die **Eigenschaften** Fenster.  
  
- Erstellen einer [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]-Projektvorlage für das Projektelement.  
  
- Erstellen eines [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]-Erweiterungspakets (VSIX) zum Bereitstellen der Projektvorlage und der Erweiterungsassembly.  
  
- Debuggen und Testen des Projektelements  
  
  Dies ist eine eigenständige exemplarische Vorgehensweise. Nachdem Sie diese exemplarische Vorgehensweise abgeschlossen haben, können Sie das Projektelement erweitern, indem Sie der Projektvorlage einen Assistenten hinzufügen. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: erstellen ein Projektelements Spalte mit einer Projektvorlage, Teil 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
> [!NOTE]  
> Eine Reihe von Beispielworkflows, finden Sie unter [Beispiele für die SharePoint-Workflow](https://docs.microsoft.com/sharepoint/dev/general-development/sharepoint-workflow-samples).  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Zum Durchführen dieser exemplarischen Vorgehensweise werden auf dem Entwicklungscomputer die folgenden Komponenten benötigt:  
  
- Unterstützte Editionen von Microsoft Windows, SharePoint und [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
- Die [!include[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. Diese exemplarische Vorgehensweise verwendet die **VSIX-Projekt** Vorlage in das SDK zum Erstellen eines VSIX-Pakets zum Bereitstellen des Projektelements. Weitere Informationen finden Sie unter [Erweitern der SharePoint-Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
  Kenntnisse des folgenden Konzepts sind hilfreich, wenn auch für die Durchführung der exemplarischen Vorgehensweise nicht erforderlich:  
  
- Websitespalten in SharePoint Weitere Informationen finden Sie unter [Spalten](http://go.microsoft.com/fwlink/?LinkId=183547).  
  
- Projektvorlagen in Visual Studio. Weitere Informationen finden Sie unter [Erstellen von Projekt- und Elementvorlagen](/visualstudio/ide/creating-project-and-item-templates).  
  
## <a name="create-the-projects"></a>Erstellen Sie die Projekte
 Zum Abschließen dieser exemplarischen Vorgehensweise müssen Sie drei Projekte erstellen:  
  
- Ein VSIX-Projekt. In diesem Projekt wird das VSIX-Paket zum Bereitstellen des Projektelements für die Websitespalte sowie die Projektvorlage erstellt.  
  
- Ein Projektvorlagenprojekt. In diesem Projekt wird eine Projektvorlage zum Erstellen eines neuen SharePoint-Projekts mit dem Projektelement für die Websitespalte erstellt.  
  
- Ein Klassenbibliotheksprojekt. In diesem Projekt wird eine Visual Studio-Erweiterung implementiert, die das Verhalten des SharePoint-Projektelements definiert.  
  
  Beginnen Sie mit der exemplarischen Vorgehensweise, indem Sie beide Projekte erstellen.  
  
#### <a name="to-create-the-vsix-project"></a>So erstellen Sie das VSIX-Projekt  
  
1.  Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Klicken Sie in der Menüleiste auf **Datei** > **Neu** > **Projekt**.  
  
3.  Am oberen Rand der **neues Projekt** Dialogfeld Feld, stellen Sie sicher, dass **.NET Framework 4.5** wird in der Liste der Versionen von .NET Framework ausgewählt.  
  
4.  Erweitern Sie die **Visual Basic** oder **Visual C#-** Knoten, und wählen Sie dann die **Erweiterbarkeit** Knoten.  
  
    > [!NOTE]  
    >  Die **Erweiterbarkeit** Knoten ist nur verfügbar, wenn Sie Visual Studio SDK installieren. Weitere Informationen finden Sie weiter oben in diesem Thema im Abschnitt zu den erforderlichen Komponenten.  
  
5.  Wählen Sie in der Liste der Projektvorlagen das Projekt **VSIX-Projekt**.  
  
6.  In der **Namen** geben **SiteColumnProjectItem**, und wählen Sie dann die **OK** Schaltfläche.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Fügt der **SiteColumnProjectItem** Projekt **Projektmappen-Explorer**.  
  
#### <a name="to-create-the-project-template-project"></a>So erstellen Sie das Projektvorlagenprojekt  
  
1.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für den Projektmappenknoten, wählen **hinzufügen**, und wählen Sie dann **neues Projekt**.  
  
2.  Am oberen Rand der **neues Projekt** Dialogfeld Feld, stellen Sie sicher, dass **.NET Framework 4.5** wird in der Liste der Versionen von .NET Framework ausgewählt.  
  
3.  Erweitern Sie die **Visual C#-** oder **Visual Basic** Knoten, und wählen Sie dann die **Erweiterbarkeit** Knoten.  
  
4.  Wählen Sie in der Liste der Projektvorlagen, die **C#-Projektvorlage** oder **Visual Basic-Projektvorlage** Vorlage.  
  
5.  In der **Namen** geben **SiteColumnProjectTemplate**, und wählen Sie dann die **OK** Schaltfläche.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Fügt der **SiteColumnProjectTemplate** Projekt der Projektmappe.  
  
6.  Löschen Sie die Class1-Codedatei aus dem Projekt.  
  
7.  Wenn Sie ein Visual Basic-Projekt erstellt haben, löschen Sie auch die folgenden Dateien aus dem Projekt:  
  
    -   *MyApplication.Designer.vb*  
  
    -   MyApplication.myapp  
  
    -   *Resources.Designer.vb*  
  
    -   *"Resources.resx"*  
  
    -   *Settings.Designer.vb*  
  
    -   Settings.settings  
  
#### <a name="to-create-the-extension-project"></a>So erstellen Sie das Erweiterungsprojekt  
  
1.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für den Projektmappenknoten, wählen **hinzufügen**, und wählen Sie dann **neues Projekt**.  
  
2.  Am oberen Rand der **neues Projekt** Dialogfeld Feld, stellen Sie sicher, dass **.NET Framework 4.5** wird in der Liste der Versionen von .NET Framework ausgewählt.  
  
3.  Erweitern Sie die **Visual C#-** oder **Visual Basic** Knoten, wählen die **Windows** Knoten, und wählen Sie dann die **Klassenbibliothek** Vorlage.  
  
4.  In der **Namen** geben **ProjectItemTypeDefinition** und wählen Sie dann die **OK** Schaltfläche.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Fügt der **ProjectItemTypeDefinition** -Projekt zur Projektmappe und öffnet die Class1-Codedatei.  
  
5.  Löschen Sie die Class1-Codedatei aus dem Projekt.  
  
## <a name="configure-the-extension-project"></a>Konfigurieren Sie das Erweiterungsprojekt
 Fügen Sie Codedateien und Assemblyverweise hinzu, um das Erweiterungsprojekt zu konfigurieren.  
  
#### <a name="to-configure-the-project"></a>So konfigurieren Sie das Projekt  
  
1.  Fügen Sie in dem ProjectItemTypeDefinition-Projekt eine Codedatei mit dem Namen **SiteColumnProjectItemTypeProvider**.  
  
2.  Wählen Sie in der Menüleiste die Optionen **Projekt** > **Verweis hinzufügen** aus.  
  
3.  In der **Verweis-Manager - ProjectItemTypeDefinition** Dialogfeld erweitern Sie die **Assemblys** Knoten, wählen Sie die **Framework** Knoten, und wählen Sie dann die Kontrollkästchen "System.ComponentModel.Composition".  
  
4.  Wählen Sie die **Erweiterungen** Knoten, wählen Sie das Kontrollkästchen neben der Microsoft.VisualStudio.SharePoint-Assembly aus, und wählen Sie dann die **OK** Schaltfläche.  
  
## <a name="define-the-new-sharepoint-project-item-type"></a>Definieren Sie die neuen SharePoint-Projektelementtyp
 Erstellen Sie eine Klasse, die die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>-Schnittstelle implementiert, um das Verhalten des neuen Projektelementtyps zu definieren. Implementieren Sie diese Schnittstelle immer dann, wenn Sie einen neuen Projektelementtyp definieren möchten.  
  
#### <a name="to-define-the-new-sharepoint-project-item-type"></a>So definieren Sie den neuen SharePoint-Projektelementtyp  
  
1.  In der **SiteColumnProjectItemTypeProvider** Codedatei, ersetzen Sie den Standardcode durch den folgenden Code und speichern Sie die Datei.  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#1](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#1](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.vb#1)]  
  
## <a name="create-a-visual-studio-project-template"></a>Erstellen Sie eine Visual Studio-Projektvorlage
 Durch das Erstellen einer Projektvorlage ermöglichen Sie anderen Entwicklern das Erstellen von SharePoint-Projekten, die Websitespalten-Projektelemente enthalten. Eine SharePoint-Projektvorlage enthält Dateien, die für alle Projekte in Visual Studio, z. B. erforderlich sind *csproj* oder *vbproj* und *VSTEMPLATE* Dateien und Dateien, die sind spezifisch für SharePoint-Projekte. Weitere Informationen finden Sie unter [Erstellen von Vorlagen und Projektvorlagen für SharePoint-Projektelemente](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 Bei diesem Verfahren erstellen Sie ein leeres SharePoint-Projekt, um Dateien zu generieren, die spezifisch für SharePoint-Projekte sind. Sie fügen diese Dateien dem SiteColumnProjectTemplate-Projekt hinzu, damit sie in der Vorlage enthalten sind, die von diesem Projekt generiert wird. Sie auch konfigurieren, die Projektdatei "SiteColumnProjectTemplate", um anzugeben, in dem die Projektvorlage angezeigt wird der **neues Projekt** Dialogfeld.  
  
#### <a name="to-create-the-files-for-the-project-template"></a>So erstellen Sie die Dateien für die Projektvorlage  
  
1. Starten Sie eine zweite Instanz von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] mit Administratorrechten.  
  
2. Erstellen Sie ein SharePoint 2010-Projekt mit dem Namen **BaseSharePointProject**.  
  
   > [!IMPORTANT]  
   >  In der **SharePoint Customization Wizard**, wählen Sie nicht die **als farmlösung bereitstellen** Optionsfeld aus.  
  
3. Dem Projekt ein leeres Projektelement hinzugefügt werden soll, und nennen Sie das Element **"Field1"**.  
  
4. Speichern Sie das Projekt, und schließen Sie die zweite Instanz von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
5. In der Instanz von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , bei der Projektmappe SiteColumnProjectItem geöffnet, in dem **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **SiteColumnProjectTemplate** Projektknoten, wählen Sie  **Hinzufügen**, und wählen Sie dann **vorhandenes Element**.  
  
6. In der **vorhandenes Element hinzufügen** Dialogfeld, öffnen Sie die Liste der Dateierweiterungen, und wählen Sie dann **alle Dateien (\*.\*)** .  
  
7. Klicken Sie in das Verzeichnis, das das BaseSharePointProject-Projekt enthält, wählen Sie die key.snk-Datei, und wählen Sie dann die **hinzufügen** Schaltfläche.  
  
   > [!NOTE]  
   >  In dieser exemplarischen Vorgehensweise wird diese KEY.SNK-Datei von der Projektvorlage verwendet, die Sie erstellen, um die einzelnen Projekte zu signieren, die mit der Vorlage erstellt werden. Gewusst wie: Erweitern Sie in diesem Beispiel zum Erstellen einer neuen key.snk-Datei für die einzelnen finden Sie unter [Exemplarische Vorgehensweise: erstellen ein Projektelements Spalte mit einer Projektvorlage, Teil 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
8. Wiederholen Sie die Schritte 5-8, um die folgenden Dateien aus den angegebenen Unterordnern im Verzeichnis BaseSharePointProject hinzuzufügen:  
  
   - *\Field1\Elements.Xml*  
  
   - *\Field1\SharePointProjectItem.SPDATA*  
  
   - *\Features\Feature1\Feature1.Feature*  
  
   - *\Features\Feature1\Feature1.Template.Xml*  
  
   - *\Package\Package.Package*  
  
   - *\Package\Package.Template.Xml*  
  
     Fügen Sie die Dateien unmittelbar zum SiteColumnProjectTemplate-Projekt hinzu. Erstellen Sie die Unterordner „Field1“, „Feature“ oder „Package“ nicht erneut im Projekt. Weitere Informationen zu diesen Dateien finden Sie unter [Erstellen von Vorlagen und Projektvorlagen für SharePoint-Projektelemente](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
#### <a name="to-configure-how-developers-discover-the-project-template-in-the-new-project-dialog-box"></a>So konfigurieren Sie die Verwendung der Projektvorlage durch Entwickler im Dialogfeld "Neues Projekt"
  
1.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **SiteColumnProjectTemplate** Projektknoten, und wählen Sie dann **Projekt entladen**. Wenn Sie aufgefordert werden, alle Dateien zu speichern, wählen Sie die **Ja** Schaltfläche.  
  
2.  Öffnen Sie das Kontextmenü für die **SiteColumnProjectTemplate** Knoten erneut, und wählen Sie dann **SiteColumnProjectTemplate.csproj bearbeiten** oder **bearbeiten SiteColumnProjectTemplate.vbproj**.  
  
3.  Suchen Sie das folgende `VSTemplate`-Element in der Projektdatei.  
  
    ```xml  
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">  
    ```  
  
4.  Ersetzen Sie dieses Element durch das folgende XML.  
  
    ```xml  
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">  
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>  
    </VSTemplate>  
    ```  
  
     Das `OutputSubPath`-Element gibt weitere Ordner in dem Pfad an, unter dem die Projektvorlage beim Erstellen des Projekts erstellt wird. Hier angegebenen Ordnern wird sichergestellt, dass die Projektvorlage verfügbar sind, nur, wenn Kunden die **neues Projekt** Dialogfeld erweitern Sie die **SharePoint** Knoten, und wählen Sie dann die **2010**  Knoten.  
  
5.  Speichern und schließen Sie die Datei.  
  
6.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **SiteColumnProjectTemplate** Projekt, und wählen Sie dann **Projekt erneut laden**.  
  
## <a name="edit-the-project-template-files"></a>Bearbeiten der Projektvorlagendateien
 Bearbeiten Sie die folgenden Dateien im SiteColumnProjectTemplate-Projekt, um das Verhalten der Projektvorlage zu definieren:  
  
- *Datei "AssemblyInfo.cs"* oder *AssemblyInfo.vb*  
  
- *"Elements.xml"*  
  
- *SharePointProjectItem.spdata*  
  
- *"Feature1.Feature"*  
  
- *"Package.Package"*  
  
- *SiteColumnProjectTemplate.vstemplate*  
  
- *ProjectTemplate.csproj* oder *ProjectTemplate.vbproj*  
  
  In den folgenden Verfahren fügen Sie einigen Dateien ersetzbare Parameter hinzu. Ein ersetzbarer Parameter ist ein Token, das mit einem Dollarzeichen ($) beginnt und endet. Wenn ein Benutzer mit dieser Projektvorlage ein Projekt erstellt, werden diese Parameter im neuen Projekt von Visual Studio automatisch durch bestimmte Werte ersetzt. Weitere Informationen finden Sie unter [ersetzbare Parameter](../sharepoint/replaceable-parameters.md).  
  
#### <a name="to-edit-the-assemblyinfocs-or-assemblyinfovb-file"></a>So bearbeiten Sie die Datei AssemblyInfo.cs oder die Datei AssemblyInfo.vb
  
1.  Öffnen Sie im SiteColumnProjectTemplate-Projekt die *"AssemblyInfo.cs"* oder *AssemblyInfo.vb* Datei, und fügen Sie dann die folgende Anweisung oben in der sie:  
  
    ```vb  
    Imports System.Security  
    ```  
  
    ```csharp  
    using System.Security;  
    ```  
  
     Wenn die **Sandkastenlösung** eines SharePoint-Projekts-Eigenschaftensatz auf **"true"**, Visual Studio fügt die <xref:System.Security.AllowPartiallyTrustedCallersAttribute> der Codedatei "AssemblyInfo". Der Namespace <xref:System.Security> wird von der Codedatei AssemblyInfo in Projektvorlage allerdings nicht standardmäßig importiert. Sie müssen dies hinzufügen **mit** oder **Importe** Anweisung, um zu verhindern, dass Kompilierungsfehler.  
  
2.  Speichern und schließen Sie die Datei.  
  
#### <a name="to-edit-the-elementsxml-file"></a>So bearbeiten Sie die Datei Elements.xml
  
1.  Ersetzen Sie im SiteColumnProjectTemplate-Projekt den Inhalt der *"Elements.xml"* -Datei mit den folgenden XML-Code.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <Field ID="{$guid5$}"   
          Name="$safeprojectname$"   
          DisplayName="$projectname$"   
          Type="Text"   
          Group="Custom Columns">  
      </Field>  
    </Elements>  
    ```  
  
     Mit dem neuen XML wird ein `Field`-Element hinzugefügt, das den Namen der Websitespalte, den Basistyp sowie die Gruppe definiert, in der die Websitespalte im Katalog aufgelistet wird. Weitere Informationen zum Inhalt dieser Datei finden Sie unter [Feld-Definitionsschema](http://go.microsoft.com/fwlink/?LinkId=184290).  
  
2.  Speichern und schließen Sie die Datei.  
  
#### <a name="to-edit-the-sharepointprojectitemspdata-file"></a>So bearbeiten Sie die Datei SharePointProjectItem.spdata
  
1. Ersetzen Sie im SiteColumnProjectTemplate-Projekt den Inhalt der *SharePointProjectItem.spdata* -Datei mit den folgenden XML-Code.  
  
   ```xml  
   <?xml version="1.0" encoding="utf-8"?>  
   <ProjectItem Type="Contoso.SiteColumn" DefaultFile="Elements.xml"   
                xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">  
     <Files>  
       <ProjectItemFile Source="Elements.xml" Target="$safeprojectname$\" Type="ElementManifest" />  
     </Files>   
   </ProjectItem>  
   ```  
  
    Durch das neue XML werden folgende Änderungen an der Datei vorgenommen:  
  
   - Ändert das `Type`-Attribut des `ProjectItem`-Elements in dieselbe Zeichenfolge, die an <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> in der Projektdefinition übergeben wird (die `SiteColumnProjectItemTypeProvider`-Klasse, die Sie zuvor in dieser exemplarischen Vorgehensweise erstellt haben).  
  
   - Entfernt die Attribute `SupportedTrustLevels` und `SupportedDeploymentScopes` aus dem `ProjectItem`-Element. Diese Attributwerte werden nicht benötigt, da die Vertrauensebenen und Bereitstellungsbereiche in der `SiteColumnProjectItemTypeProvider`-Klasse im Projekt ProjectItemTypeDefinition angegeben werden.  
  
     Weitere Informationen über den Inhalt des *SPDATA* finden Sie unter [SharePoint-Projektelementschema](../sharepoint/sharepoint-project-item-schema-reference.md).  
  
2. Speichern und schließen Sie die Datei.  
  
#### <a name="to-edit-the-feature1feature-file"></a>So bearbeiten Sie die Datei „Feature1.feature“
  
1. Ersetzen Sie im SiteColumnProjectTemplate-Projekt den Inhalt der *"Feature1.Feature"* -Datei mit den folgenden XML-Code.  
  
   ```xml  
   <?xml version="1.0" encoding="utf-8"?>  
   <feature xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0" Id="$guid4$" featureId="$guid4$"   
            imageUrl="" solutionId="00000000-0000-0000-0000-000000000000" title="Site Column Feature1" version=""  
            deploymentPath="$SharePoint.Project.FileNameWithoutExtension$_$SharePoint.Feature.FileNameWithoutExtension$"  
            xmlns="http://schemas.microsoft.com/VisualStudio/2008/SharePointTools/FeatureModel">  
     <projectItems>  
       <projectItemReference itemId="$guid2$" />  
     </projectItems>  
   </feature>  
   ```  
  
    Durch das neue XML werden folgende Änderungen an der Datei vorgenommen:  
  
   - Ändert die Werte der Attribute `Id` und `featureId` des `feature`-Elements in `$guid4$`.  
  
   - Ändert die Werte des `itemId`-Attributs für das `projectItemReference`-Element in `$guid2$`.  
  
     Weitere Informationen zu *.feature* finden Sie unter [Erstellen von Vorlagen und Projektvorlagen für SharePoint-Projektelemente](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
2. Speichern und schließen Sie die Datei.  
  
#### <a name="to-edit-the-packagepackage-file"></a>So bearbeiten Sie die Datei Package.package
  
1. Ersetzen Sie im SiteColumnProjectTemplate-Projekt den Inhalt der *Package.package* -Datei mit den folgenden XML-Code.  
  
   ```xml  
   <?xml version="1.0" encoding="utf-8"?>  
   <package xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0"   
            Id="$guid3$" solutionId="$guid3$" resetWebServer="false" name="$safeprojectname$"   
            xmlns="http://schemas.microsoft.com/VisualStudio/2008/SharePointTools/PackageModel">  
     <features>  
       <featureReference itemId="$guid4$" />  
     </features>  
   </package>  
   ```  
  
    Durch das neue XML werden folgende Änderungen an der Datei vorgenommen:  
  
   - Ändert die Werte der Attribute `Id` und `solutionId` des `package`-Elements in `$guid3$`.  
  
   - Ändert die Werte des `itemId`-Attributs für das `featureReference`-Element in `$guid4$`.  
  
     Weitere Informationen zu *Package* finden Sie unter [Erstellen von Vorlagen und Projektvorlagen für SharePoint-Projektelemente](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
2. Speichern und schließen Sie die Datei.  
  
#### <a name="to-edit-the-sitecolumnprojecttemplatevstemplate-file"></a>So bearbeiten Sie die Datei SiteColumnProjectTemplate.VSTEMPLATE
  
1. Ersetzen Sie im SiteColumnProjectTemplate-Projekt die Inhalte der SiteColumnProjectTemplate.vstemplate-Datei durch einen der folgenden XML-Abschnitte.  
  
   -   Wenn Sie eine Visual C#-Projektvorlage erstellen, verwenden Sie das folgende XML:  
  
   ```xml  
   <?xml version="1.0" encoding="utf-8"?>  
   <VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Project">  
     <TemplateData>  
       <Name>Site Column</Name>  
       <Description>Creates a new site column in SharePoint</Description>  
       <FrameworkVersion>3.5</FrameworkVersion>  
       <ProjectType>CSharp</ProjectType>  
       <CreateNewFolder>true</CreateNewFolder>  
       <CreateInPlace>true</CreateInPlace>  
       <ProvideDefaultName>true</ProvideDefaultName>  
       <DefaultName>SiteColumn</DefaultName>  
       <LocationField>Enabled</LocationField>  
       <EnableLocationBrowseButton>true</EnableLocationBrowseButton>  
       <PromptForSaveOnCreation>true</PromptForSaveOnCreation>  
       <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
       <Icon>SiteColumnProjectTemplate.ico</Icon>  
       <SortOrder>1000</SortOrder>  
     </TemplateData>  
     <TemplateContent>  
       <Project TargetFileName="SharePointProject1.csproj" File="ProjectTemplate.csproj" ReplaceParameters="true">  
         <ProjectItem ReplaceParameters="true" TargetFileName="Properties\AssemblyInfo.cs">AssemblyInfo.cs</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.feature">Feature1.feature</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.Template.xml">Feature1.template.xml</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.package">Package.package</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.Template.xml">Package.Template.xml</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Field1\SharePointProjectItem.spdata">SharePointProjectItem.spdata</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Field1\Elements.xml" OpenInEditor="true">Elements.xml</ProjectItem>  
         <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>  
       </Project>  
     </TemplateContent>  
   </VSTemplate>  
   ```  
  
   -   Wenn Sie eine Visual Basic-Projektvorlage erstellen, verwenden Sie das folgende XML:  
  
   ```xml  
   <?xml version="1.0" encoding="utf-8"?>  
   <VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Project">  
     <TemplateData>  
       <Name>Site Column</Name>  
       <Description>Creates a new site column in SharePoint</Description>  
       <FrameworkVersion>3.5</FrameworkVersion>  
       <ProjectType>VisualBasic</ProjectType>  
       <CreateNewFolder>true</CreateNewFolder>  
       <CreateInPlace>true</CreateInPlace>  
       <ProvideDefaultName>true</ProvideDefaultName>  
       <DefaultName>SiteColumn</DefaultName>  
       <LocationField>Enabled</LocationField>  
       <EnableLocationBrowseButton>true</EnableLocationBrowseButton>  
       <PromptForSaveOnCreation>true</PromptForSaveOnCreation>  
       <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
       <Icon>SiteColumnProjectTemplate.ico</Icon>  
       <SortOrder>1000</SortOrder>  
     </TemplateData>  
     <TemplateContent>  
       <Project TargetFileName="SharePointProject1.vbproj" File="ProjectTemplate.vbproj" ReplaceParameters="true">  
         <ProjectItem ReplaceParameters="true" TargetFileName="My Project\AssemblyInfo.vb">AssemblyInfo.vb</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.feature">Feature1.feature</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.Template.xml">Feature1.template.xml</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.package">Package.package</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.Template.xml">Package.Template.xml</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Field1\SharePointProjectItem.spdata">SharePointProjectItem.spdata</ProjectItem>  
         <ProjectItem ReplaceParameters="true" TargetFileName="Field1\Elements.xml" OpenInEditor="true">Elements.xml</ProjectItem>  
         <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>  
       </Project>  
     </TemplateContent>  
   </VSTemplate>  
   ```  
  
    Durch das neue XML werden folgende Änderungen an der Datei vorgenommen:  
  
   - Legt die `Name` Elements mit dem Wert **Websitespalte**. (Dieser Name wird in der **neues Projekt** (Dialogfeld)).  
  
   - Fügt die `ProjectItem`-Elemente für alle Dateien hinzu, die in den einzelnen Projektinstanzen enthalten sind.  
  
   - Verwendet den Namespace "<http://schemas.microsoft.com/developer/vstemplate/2005>". Andere Projektdateien in dieser Lösung verwendet die "<http://schemas.microsoft.com/developer/msbuild/2003>" Namespace. Daher werden XML-Schema-Warnmeldungen generiert, die Sie aber bei dieser exemplarischen Vorgehensweise ignorieren können.  
  
     Weitere Informationen über den Inhalt des *VSTEMPLATE* finden Sie unter [Visual Studio Template Schema Reference](/visualstudio/extensibility/visual-studio-template-schema-reference).  
  
2. Speichern und schließen Sie die Datei.  
  
#### <a name="to-edit-the-projecttemplatecsproj-or-projecttemplatevbproj-file"></a>So bearbeiten Sie die Datei projecttemplate.csproj oder projecttemplate.vbproj
  
1.  Ersetzen Sie im SiteColumnProjectTemplate-Projekt den Inhalt der *ProjectTemplate.csproj* Datei oder *ProjectTemplate.vbproj* -Datei mit den folgenden Abschnitten des XML-Codes.  
  
    -   Wenn Sie eine Visual C#-Projektvorlage erstellen, verwenden Sie das folgende XML:  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <PropertyGroup>  
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
        <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>  
        <SchemaVersion>2.0</SchemaVersion>  
        <ProjectGuid>{$guid1$}</ProjectGuid>  
        <OutputType>Library</OutputType>  
        <AppDesignerFolder>Properties</AppDesignerFolder>  
        <RootNamespace>$safeprojectname$</RootNamespace>  
        <AssemblyName>$safeprojectname$</AssemblyName>  
        <TargetFrameworkVersion>v3.5</TargetFrameworkVersion>  
        <FileAlignment>512</FileAlignment>  
        <ProjectTypeGuids>{BB1F664B-9266-4fd6-B973-E1E44974B511};{14822709-B5A1-4724-98CA-57A101D1B079};{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}</ProjectTypeGuids>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">  
        <DebugSymbols>true</DebugSymbols>  
        <DebugType>full</DebugType>  
        <Optimize>false</Optimize>  
        <OutputPath>bin\Debug\</OutputPath>  
        <DefineConstants>DEBUG;TRACE</DefineConstants>  
        <ErrorReport>prompt</ErrorReport>  
        <WarningLevel>4</WarningLevel>  
        <UseVSHostingProcess>false</UseVSHostingProcess>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">  
        <DebugType>pdbonly</DebugType>  
        <Optimize>true</Optimize>  
        <OutputPath>bin\Release\</OutputPath>  
        <DefineConstants>TRACE</DefineConstants>  
        <ErrorReport>prompt</ErrorReport>  
        <WarningLevel>4</WarningLevel>  
      </PropertyGroup>  
      <PropertyGroup>  
        <SignAssembly>true</SignAssembly>  
        <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>  
      </PropertyGroup>  
      <ItemGroup>  
        <Reference Include="System" />  
        <Reference Include="System.Core" />  
        <Reference Include="System.Data" />  
        <Reference Include="System.Data.DataSetExtensions" />  
        <Reference Include="System.Web" />  
        <Reference Include="System.Xml" />  
        <Reference Include="System.Xml.Linq" />  
        <Reference Include="Microsoft.SharePoint" />  
        <Reference Include="Microsoft.SharePoint.Security" />  
      </ItemGroup>  
      <ItemGroup>  
        <Compile Include="Properties\AssemblyInfo.cs" />  
      </ItemGroup>  
      <ItemGroup>  
        <None Include="Field1\SharePointProjectItem.spdata">  
          <SharePointProjectItemId>{$guid2$}</SharePointProjectItemId>  
        </None>  
        <None Include="Field1\Elements.xml" />  
      </ItemGroup>  
      <ItemGroup>  
        <None Include="key.snk" />  
        <None Include="Package\Package.package">  
          <PackageId>{$guid3$}</PackageId>  
        </None>  
        <None Include="Package\Package.Template.xml">  
          <DependentUpon>Package.package</DependentUpon>  
        </None>  
        <None Include="Features\Feature1\Feature1.feature">  
          <FeatureId>{$guid4$}</FeatureId>  
        </None>  
        <None Include="Features\Feature1\Feature1.Template.xml">  
          <DependentUpon>Feature1.feature</DependentUpon>  
        </None>  
      </ItemGroup>  
      <Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />  
      <Import Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v10.0\SharePointTools\Microsoft.VisualStudio.SharePoint.targets" />  
    </Project>  
    ```  
  
    1.  Wenn Sie eine Visual Basic-Projektvorlage erstellen, verwenden Sie das folgende XML:  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <PropertyGroup>  
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
        <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>  
        <ProductVersion>  
        </ProductVersion>  
        <SchemaVersion>  
        </SchemaVersion>  
        <ProjectGuid>{$guid1$}</ProjectGuid>  
        <OutputType>Library</OutputType>  
        <RootNamespace>$safeprojectname$</RootNamespace>  
        <AssemblyName>$safeprojectname$</AssemblyName>  
        <TargetFrameworkVersion>v3.5</TargetFrameworkVersion>  
        <FileAlignment>512</FileAlignment>  
        <ProjectTypeGuids>{BB1F664B-9266-4fd6-B973-E1E44974B511};{D59BE175-2ED0-4C54-BE3D-CDAA9F3214C8};{F184B08F-C81C-45F6-A57F-5ABD9991F28F}</ProjectTypeGuids>  
        <OptionExplicit>On</OptionExplicit>  
        <OptionCompare>Binary</OptionCompare>  
        <OptionStrict>Off</OptionStrict>  
        <OptionInfer>On</OptionInfer>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">  
        <DebugSymbols>true</DebugSymbols>  
        <DebugType>full</DebugType>  
        <DefineDebug>true</DefineDebug>  
        <DefineTrace>true</DefineTrace>  
        <OutputPath>bin\Debug\</OutputPath>  
        <WarningLevel>4</WarningLevel>  
        <UseVSHostingProcess>false</UseVSHostingProcess>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">  
        <DebugType>pdbonly</DebugType>  
        <DefineDebug>false</DefineDebug>  
        <DefineTrace>true</DefineTrace>  
        <Optimize>true</Optimize>  
        <OutputPath>bin\Release\</OutputPath>  
        <UseVSHostingProcess>false</UseVSHostingProcess>  
      </PropertyGroup>  
      <PropertyGroup>  
        <SignAssembly>true</SignAssembly>  
        <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>  
      </PropertyGroup>  
      <ItemGroup>  
        <Reference Include="System" />  
        <Reference Include="System.Core" />  
        <Reference Include="System.Data" />  
        <Reference Include="System.Data.DataSetExtensions" />  
        <Reference Include="System.Xml" />  
        <Reference Include="System.Xml.Linq" />  
        <Reference Include="Microsoft.SharePoint" />  
        <Reference Include="Microsoft.SharePoint.Security" />  
      </ItemGroup>  
      <ItemGroup>  
        <Import Include="Microsoft.VisualBasic" />  
        <Import Include="System" />  
        <Import Include="System.Collections" />  
        <Import Include="System.Collections.Generic" />  
        <Import Include="System.Data" />  
        <Import Include="System.Diagnostics" />  
        <Import Include="System.Linq" />  
        <Import Include="System.Xml.Linq" />  
        <Import Include="Microsoft.SharePoint" />  
        <Import Include="Microsoft.SharePoint.Security" />  
      </ItemGroup>  
      <ItemGroup>  
        <Compile Include="My Project\AssemblyInfo.vb" />  
      </ItemGroup>  
      <ItemGroup>  
        <AppDesigner Include="My Project\" />  
      </ItemGroup>  
      <ItemGroup>  
        <None Include="Features\Feature1\Feature1.feature">  
          <FeatureId>{$guid4$}</FeatureId>  
        </None>  
        <None Include="Field1\SharePointProjectItem.spdata">  
          <SharePointProjectItemId>{$guid2$}</SharePointProjectItemId>  
        </None>  
        <None Include="key.snk" />  
        <None Include="Package\Package.package">  
          <PackageId>{$guid3$}</PackageId>  
        </None>  
        <None Include="Package\Package.Template.xml">  
          <DependentUpon>Package.package</DependentUpon>  
        </None>  
      </ItemGroup>  
      <ItemGroup>  
        <None Include="Features\Feature1\Feature1.Template.xml">  
          <DependentUpon>Feature1.feature</DependentUpon>  
        </None>  
        <None Include="Field1\Elements.xml" />  
      </ItemGroup>  
      <Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />  
      <Import Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v10.0\SharePointTools\Microsoft.VisualStudio.SharePoint.targets" />  
    </Project>  
    ```  
  
     Durch das neue XML werden folgende Änderungen an der Datei vorgenommen:  
  
    -   Verwendet das `TargetFrameworkVersion`-Element, um .NET Framework 3.5 und nicht .NET Framework 4.5 festzulegen.  
  
    -   Fügt die Elemente `SignAssembly` und `AssemblyOriginatorKeyFile` hinzu, um die Projektausgabe zu signieren.  
  
    -   Fügt die `Reference`-Elemente für Assemblyverweise hinzu, die von SharePoint-Projekten verwendet werden.  
  
    -   Fügt Elemente für alle Standarddateien im Projekt, z. B. *"Elements.xml"* und *SharePointProjectItem.spdata*.  
  
2.  Speichern und schließen Sie die Datei.  
  
## <a name="create-a-vsix-package-to-deploy-the-project-template"></a>Erstellen Sie ein VSIX-Paket zum Bereitstellen der Projektvorlage
 Verwenden Sie zum Bereitstellen der Erweiterungs VSIX-Projekt in der **SiteColumnProjectItem** Lösung ein VSIX-Paket zu erstellen. Konfigurieren Sie zuerst das VSIX-Paket, indem Sie die im VSIX-Projekt enthaltene Datei "source.extension.vsixmanifest" ändern. Erstellen Sie anschließend das VSIX-Paket, indem Sie die Lösung erstellen.  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>So erstellen und konfigurieren Sie das VSIX-Paket  
  
1.  In **Projektmappen-Explorer**in die **SiteColumnProjectItem** Projekt, öffnen Sie die Datei "Source.Extension.vsixmanifest" im manifest-Editor.  
  
     Die Datei "source.extension.vsixmanifest" bildet die Grundlage für die Datei "extension.vsixmanifest", die für alle VSIX-Pakete erforderlich ist. Weitere Informationen zu dieser Datei finden Sie unter [Referenz zum VSIX-Erweiterungsschema 1.0](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  In der **Produktname** geben **Websitespalte**.  
  
3.  In der **Autor** geben **Contoso**.  
  
4.  In der **Beschreibung** geben **ein SharePoint-Projekt zum Erstellen von Websitespalten**.  
  
5.  Wählen Sie die **Assets** Registerkarte, und wählen Sie dann die **neu** Schaltfläche.  
  
     Die **neue Anlage hinzufügen** Dialogfeld wird geöffnet.  
  
6.  In der **Typ** wählen **Microsoft.VisualStudio.ProjectTemplate**.  
  
    > [!NOTE]  
    >  Dieser Wert entspricht dem `ProjectTemplate`-Element in der Datei "extension.vsixmanifest". Durch dieses Element wird der Unterordner im VSIX-Paket identifiziert, der die Projektvorlage enthält. Weitere Informationen finden Sie unter ["ProjectTemplate"-Element (VSX-Schema)](http://msdn.microsoft.com/en-us/87add64c-9dcd-495f-8815-209dab182cb1).  
  
7.  In der **Quelle** wählen **ein Projekt in der aktuellen Projektmappe**.  
  
8.  In der **Projekt** aus, und wählen Sie **SiteColumnProjectTemplate**, und wählen Sie dann die **OK** Schaltfläche.  
  
9. Wählen Sie die **neu** erneut.  
  
     Die **neue Anlage hinzufügen** Dialogfeld wird geöffnet.  
  
10. In der **Typ** wählen **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Dieser Wert entspricht dem `MefComponent`-Element in der Datei "extension.vsixmanifest". Von diesem Element wird der Name einer Erweiterungsassembly im VSIX-Paket angegeben. Weitere Informationen finden Sie unter [MEFComponent-Element (VSX-Schema)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
11. In der **Quelle** wählen **ein Projekt in der aktuellen Projektmappe**.  
  
12. In der **Projekt** wählen **ProjectItemTypeDefinition**, und wählen Sie dann die **OK** Schaltfläche.  
  
13. Wählen Sie auf der Menüleiste **erstellen** > **Projektmappe**, und klicken Sie dann stellen Sie sicher, dass das Projekt ohne Fehler kompiliert wird.  
  
## <a name="test-the-project-template"></a>Die Projektvorlage für Tests
 Jetzt können Sie die Projektvorlage testen. Debuggen Sie die Projektmappe SiteColumnProjectItem zunächst in der experimentellen Instanz von Visual Studio. Testen Sie anschließend die **Websitespalte** -Projekt in der experimentellen Instanz von Visual Studio. Erstellen und führen Sie zum Schluss das SharePoint-Projekt aus, um sicherzustellen, dass die Websitespalte ordnungsgemäß funktioniert.  
  
#### <a name="to-start-debugging-the-solution"></a>So debuggen Sie die Projektmappe  
  
1.  Starten Sie Visual Studio erneut mit Administratoranmeldeinformationen, und öffnen Sie dann die Projektmappe "SiteColumnProjectItem".  
  
2.  
  
3.  Fügen Sie einen Haltepunkt in der SiteColumnProjectItemTypeProvider-Codedatei, um die erste Zeile des Codes in der `InitializeType` -Methode, und wählen Sie dann die **F5** Schlüssel mit dem Debuggen beginnen.  
  
     Die Erweiterung wird unter %UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\Websitespalte\1.0 installiert, und eine experimentelle Instanz von Visual Studio wird gestartet. Sie testen das Projektelement in dieser Instanz von Visual Studio.  
  
#### <a name="to-test-the-project-in-visual-studio"></a>So testen Sie das Projekt in Visual Studio  
  
1.  Wählen Sie in der experimentellen Instanz von Visual Studio auf der Menüleiste **Datei** > **neu** > **Projekt**.  
  
2.  Erweitern Sie die **Visual C#-** oder **Visual Basic** Knoten (je nach der die Projektvorlage unterstützten Sprache), erweitern Sie die **SharePoint** Knoten, und wählen Sie dann die **2010** Knoten.  
  
3.  Wählen Sie in der Liste der Projektvorlagen, die **Websitespalte** Vorlage.  
  
4.  In der **Namen** geben **SiteColumnTest** und wählen Sie dann die **OK** Schaltfläche.  
  
     In **Projektmappen-Explorer**, ein neues Projekt angezeigt wird, mit einem Projektelement mit dem Namen **"Field1"**.  
  
5.  Stellen Sie sicher, dass die codeausführung in der anderen Instanz von Visual Studio an dem Haltepunkt unterbrochen wird, die Sie zuvor im Festlegen der `InitializeType` -Methode, und wählen Sie dann die **F5** Schlüssel, um das Debuggen des Projekts fortzusetzen.  
  
6.  In **Projektmappen-Explorer**, wählen Sie die **"Field1"** Knoten, und wählen Sie dann die **F4** Schlüssel.  
  
     Die **Eigenschaften** Fenster wird geöffnet.  
  
7.  Überprüfen Sie in der Liste der Eigenschaften, ob die Eigenschaft **Beispieleigenschaft** angezeigt wird.  
  
#### <a name="to-test-the-site-column-in-sharepoint"></a>So testen Sie die Websitespalte in SharePoint  
  
1.  In **Projektmappen-Explorer**, wählen Sie die **SiteColumnTest** Knoten.  
  
2.  In der **Eigenschaften** Fenster in das Textfeld neben der **Website-URL** -Eigenschaft, geben Sie **http://localhost**.  
  
     Dadurch wird auf dem Entwicklungscomputer die lokale SharePoint-Website angegeben, die zum Debuggen verwendet werden soll.  
  
    > [!NOTE]  
    >  Die **Website-URL** Eigenschaft ist standardmäßig leer, da die Projektvorlage für Websitespalten enthalten keinen Assistenten zum Erfassen dieses Werts, wenn das Projekt erstellt wird. Weitere Informationen zum Hinzufügen eines Assistenten, die diesen Wert vom Entwickler abgefragt, und klicken Sie dann diese Eigenschaft im neuen Projekt konfiguriert, finden Sie unter [Exemplarische Vorgehensweise: erstellen ein Projektelements Spalte mit einer Projektvorlage, Teil 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
3.  Drücken Sie die Taste **F5**.  
  
     Die Websitespalte wird verpackt und bereitgestellt werden, auf die SharePoint-Website, die im angegebenen die **Website-URL** -Eigenschaft des Projekts. Im Webbrowser wird die Standardseite dieser Website geöffnet.  
  
    > [!NOTE]  
    >  Wenn die **Skriptdebugging deaktiviert** wählen Sie im angezeigten Dialogfeld die **Ja** Schaltfläche, um das Debuggen des Projekts fortzusetzen.  
  
4.  Auf der **Websiteaktionen** Menü wählen **Standorteinstellungen**.  
  
5.  Auf der **Standorteinstellungen** Seite die **Galerien** wählen die **Site Spalten** Link.  
  
6.  Überprüfen Sie in der Liste der Websitespalten, ob eine **benutzerdefinierte Spalten** Gruppe enthält eine Spalte mit dem Namen **SiteColumnTest**.  
  
7.  Schließen Sie den Webbrowser.  
  
## <a name="clean-up-the-development-computer"></a>Bereinigung auf dem Entwicklungscomputer
 Nachdem Sie die Tests des Projekts abgeschlossen haben, entfernen Sie die Projektvorlage aus der experimentellen Instanz von Visual Studio.  
  
#### <a name="to-clean-up-the-development-computer"></a>So bereinigen Sie den Entwicklungscomputer  
  
1.  Wählen Sie in der experimentellen Instanz von Visual Studio auf der Menüleiste **Tools** > **Erweiterungen und Updates**.  
  
     Das Dialogfeld **Erweiterungen und Updates** wird geöffnet.  
  
2.  Wählen Sie in der Liste der Erweiterungen, die **Websitespalte** -Erweiterung, und wählen Sie dann die **Deinstallieren** Schaltfläche.  
  
3.  Wählen Sie in das Dialogfeld, das angezeigt wird, die **Ja** , um zu bestätigen, dass Sie die Erweiterung deinstallieren möchten.  
  
4.  Wählen Sie die **schließen** Schaltfläche, um die Deinstallation abzuschließen.  
  
5.  Schließen Sie beide Instanzen von Visual Studio (die experimentelle Instanz und die Instanz von Visual Studio, in der die SiteColumnProjectItem-Projektmappe geöffnet ist).  
  
## <a name="next-steps"></a>Nächste Schritte
 Nachdem Sie diese exemplarische Vorgehensweise abgeschlossen haben, können Sie der Projektvorlage einen Assistenten hinzufügen. Beim Erstellen eines Websitespaltenprojekts wird der Benutzer vom Assistenten aufgefordert, die URL der Website anzugeben, die zum Debuggen verwendet werden soll. Darüber hinaus muss vom Benutzer angegeben werden, ob die neue Projektmappe als Sandkastenlösung bereitgestellt wird. Anschließend wird das Projekt vom Assistenten mit diesen Informationen konfiguriert. Der Assistent auch sammelt Informationen über die Spalte (z. B. der Basistyp und der Gruppe in der Spalte in der Spalte Websitekatalog aufgeführt) und fügt diese Informationen, um die *"Elements.xml"* -Datei in das neue Projekt. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: erstellen ein Projektelements Spalte mit einer Projektvorlage, Teil 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
## <a name="see-also"></a>Siehe auch
 [Exemplarische Vorgehensweise: Erstellen eines Projektelements Spalte mit einer Projektvorlage, Teil 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [Definieren von benutzerdefinierten SharePoint-Projektelementtypen](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Erstellen von Elementvorlagen und Projektvorlagen für SharePoint-Projektelemente](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Speichern von Daten in Erweiterungen des SharePoint-Projektsystem](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [Zuordnen von benutzerdefinierten Daten zu SharePoint-Tools-Erweiterungen](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
