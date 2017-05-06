---
title: "Exemplarische Vorgehensweise: Erstellen eines Projektelements &quot;Websitespalte&quot; mit einer Projektvorlage, Teil&#160;1"
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
  - "SharePoint-Projektelemente, Definieren eigener Typen"
  - "Projektelemente [SharePoint-Entwicklung in Visual Studio], Definieren eigener Typen"
  - "SharePoint-Projekte, Erstellen von benutzerdefinierten Vorlagen"
  - "SharePoint-Entwicklung in Visual Studio, Definieren neuer Projektelementtypen"
ms.assetid: b53d48d7-cbf2-45c2-9537-06a6819be397
caps.latest.revision: 60
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 59
---
# Exemplarische Vorgehensweise: Erstellen eines Projektelements &quot;Websitespalte&quot; mit einer Projektvorlage, Teil&#160;1
  SharePoint\-Projekte sind Container für SharePoint\-Projektelemente.  Sie können das SharePoint\-Projektsystem in Visual Studio erweitern, indem Sie eigene SharePoint\-Projektelementtypen erstellen und diese dann einer Projektvorlage zuordnen.  In dieser exemplarischen Vorgehensweise definieren Sie einen Projektelementtyp zum Erstellen einer Websitespalte. Anschließend erstellen Sie eine Projektvorlage, mit der ein neues Projekt erstellt werden kann, das ein Projektelement einer Websitespalte enthält.  
  
 Diese exemplarische Vorgehensweise enthält die folgenden Aufgaben:  
  
-   Erstellen einer Visual Studio\-Erweiterung, die einen neuen Typ von SharePoint\-Projektelement für eine Websitespalte definiert.  Der Projektelementtyp enthält eine einfache benutzerdefinierte Eigenschaft, die im **Eigenschaftenfenster** angezeigt wird.  
  
-   Erstellen einer [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-Projektvorlage für das Projektelement.  
  
-   Erstellen eines [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-Erweiterungspakets \(VSIX\) zum Bereitstellen der Projektvorlage und der Erweiterungsassembly.  
  
-   Debuggen und Testen des Projektelements  
  
 Dies ist eine eigenständige exemplarische Vorgehensweise.  Nachdem Sie diese exemplarische Vorgehensweise abgeschlossen haben, können Sie das Projektelement erweitern, indem Sie der Projektvorlage einen Assistenten hinzufügen.  Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines Projektelements "Websitespalte" mit einer Projektvorlage, Teil 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
> [!NOTE]  
>  Ein Beispiel mit den abgeschlossenen Projekten, Code und weiteren Dateien für diese exemplarische Vorgehensweise können Sie unter folgender Adresse herunterladen: [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=191369](http://go.microsoft.com/fwlink/?LinkId=191369).  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise werden auf dem Entwicklungscomputer die folgenden Komponenten benötigt:  
  
-   Unterstützte Editionen von Microsoft Windows, SharePoint und [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Weitere Informationen finden Sie unter [Anforderungen für die Entwicklung von SharePoint-Lösungen](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)].  Bei dieser exemplarischen Vorgehensweise wird mithilfe der **VSIX\-Projekt**\-Vorlage aus dem SDK ein VSIX\-Paket zum Bereitstellen des Projektelements erstellt.  Weitere Informationen finden Sie unter [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Kenntnisse des folgenden Konzepts sind hilfreich, wenn auch für die Durchführung der exemplarischen Vorgehensweise nicht erforderlich:  
  
-   Websitespalten in SharePoint  Weitere Informationen finden Sie unter [Spalten](http://go.microsoft.com/fwlink/?LinkId=183547).  
  
-   Projektvorlagen in Visual Studio.  Weitere Informationen finden Sie unter [Erstellen von benutzerdefinierten Projekt- und Elementvorlagen in Visual Studio](../ide/creating-project-and-item-templates.md).  
  
## Erstellen der Projekte  
 Zum Abschließen dieser exemplarischen Vorgehensweise müssen Sie drei Projekte erstellen:  
  
-   Ein VSIX\-Projekt.  In diesem Projekt wird das VSIX\-Paket zum Bereitstellen des Projektelements für die Websitespalte sowie die Projektvorlage erstellt.  
  
-   Ein Projektvorlagenprojekt.  In diesem Projekt wird eine Projektvorlage zum Erstellen eines neuen SharePoint\-Projekts mit dem Projektelement für die Websitespalte erstellt.  
  
-   Ein Klassenbibliotheksprojekt.  In diesem Projekt wird eine Visual Studio\-Erweiterung implementiert, die das Verhalten des SharePoint\-Projektelements definiert.  
  
 Beginnen Sie mit der exemplarischen Vorgehensweise, indem Sie beide Projekte erstellen.  
  
#### So erstellen Sie das VSIX\-Projekt  
  
1.  Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Wählen Sie in der Menüleiste **Datei**, **Neu**, **Projekt** aus.  
  
3.  Stellen Sie im oberen Bereich des Dialogfelds **Neues Projekt** sicher, dass in der Liste der .NET Framework\-Versionen **.NET Framework 4.5** ausgewählt ist.  
  
4.  Erweitern Sie den **Visual C\#**\-Knoten oder den **Visual Basic**\-Knoten, und wählen Sie dann den **Erweiterungen**\-Knoten aus.  
  
    > [!NOTE]  
    >  Der Knoten **Erweiterungen** ist nur verfügbar, wenn Sie das Visual Studio SDK installieren.  Weitere Informationen finden Sie weiter oben in diesem Thema im Abschnitt zu den erforderlichen Komponenten.  
  
5.  Wählen Sie in der Liste der Projektvorlagen **VSIX\-Projekt** aus.  
  
6.  Geben Sie im Feld **NameSiteColumnProjectItem** ein, und wählen Sie dann die Schaltfläche **OK** aus.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fügt das **SiteColumnProjectItem**\-Projekt zum **Projektmappen\-Explorer** hinzu.  
  
#### So erstellen Sie das Projektvorlagenprojekt  
  
1.  Öffnen Sie im **Projektmappen\-Explorer** das Kontextmenü für den Projektmappenknoten, wählen Sie **Hinzufügen** und dann **Neues Projekt** aus.  
  
    > [!NOTE]  
    >  In Visual Basic\-Projekten wird der Projektmappenknoten nur im **Projektmappen\-Explorer** angezeigt, wenn das Kontrollkästchen **Projektmappe immer anzeigen** in [NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/de-de/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca) aktiviert ist.  
  
2.  Stellen Sie im oberen Bereich des Dialogfelds **Neues Projekt** sicher, dass in der Liste der .NET Framework\-Versionen **.NET Framework 4.5** ausgewählt ist.  
  
3.  Erweitern Sie den **Visual C\#**\-Knoten oder den **Visual Basic**\-Knoten, und wählen Sie dann den **Erweiterungen**\-Knoten aus.  
  
4.  Wählen Sie in der Liste der Projektvorlagen **C\#\-Projektvorlage** oder **Visual Basic\-Projektvorlage** aus.  
  
5.  Geben Sie im Feld **Name** die Zeichenfolge **SiteColumnProjectTemplate** ein, und wählen Sie dann die Schaltfläche **OK** aus.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fügt der Projektmappe das Projekt **SiteColumnProjectTemplate** hinzu.  
  
6.  Löschen Sie die Class1\-Codedatei aus dem Projekt.  
  
7.  Wenn Sie ein Visual Basic\-Projekt erstellt haben, löschen Sie auch die folgenden Dateien aus dem Projekt:  
  
    -   MyApplication.Designer.vb  
  
    -   MyApplication.myapp  
  
    -   Resources.Designer.vb  
  
    -   Resources.resx  
  
    -   Settings.Designer.vb  
  
    -   Settings.settings  
  
#### So erstellen Sie das Erweiterungsprojekt  
  
1.  Öffnen Sie im **Projektmappen\-Explorer** das Kontextmenü für den Projektmappenknoten, wählen Sie **Hinzufügen** und dann **Neues Projekt** aus.  
  
2.  Stellen Sie im oberen Bereich des Dialogfelds **Neues Projekt** sicher, dass in der Liste der .NET Framework\-Versionen **.NET Framework 4.5** ausgewählt ist.  
  
3.  Erweitern Sie den **Visual C\#**\-Knoten oder den **Visual Basic**\-Knoten, wählen Sie den **Windows**\-Knoten und wählen Sie dann die **Klassenbibliothek**\-Vorlage aus.  
  
4.  Geben Sie im Feld **NameProjectItemTypeDefinition** ein, und wählen Sie dann die Schaltfläche **OK** aus.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fügt das Projekt **ProjectItemTypeDefinition** der Projektmappe hinzu und öffnet die Class1\-Codedatei.  
  
5.  Löschen Sie die Class1\-Codedatei aus dem Projekt.  
  
## Konfigurieren des Erweiterungsprojekts  
 Fügen Sie Codedateien und Assemblyverweise hinzu, um das Erweiterungsprojekt zu konfigurieren.  
  
#### So konfigurieren Sie das Projekt  
  
1.  Fügen Sie dem ProjectItemTypeDefinition\-Projekt die neue Codedatei **SiteColumnProjectItemTypeProvider** hinzu.  
  
2.  Wählen Sie in der Menüleiste die Optionen **Projekt** und **Verweis hinzufügen** aus.  
  
3.  Erweitern Sie im Dialogfeld **Verweis\-Manager \- ProjectItemTypeDefinition** den Knoten **Assemblys**, wählen Sie den Knoten **Framework**, und wählen Sie dann das Kontrollkästchen "System.ComponentModel.Composition".  
  
4.  Wählen Sie den Knoten **Erweiterungen** aus, aktivieren Sie das Kontrollkästchen neben der Microsoft.VisualStudio.SharePoint\-Assembly, und wählen Sie dann die Schaltfläche **OK** aus.  
  
## Definieren des neuen SharePoint\-Projektelementtyps  
 Erstellen Sie eine Klasse, die die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>\-Schnittstelle implementiert, um das Verhalten des neuen Projektelementtyps zu definieren.  Implementieren Sie diese Schnittstelle immer dann, wenn Sie einen neuen Projektelementtyp definieren möchten.  
  
#### So definieren Sie den neuen SharePoint\-Projektelementtyp  
  
1.  Ersetzen Sie in der Codedatei **SiteColumnProjectItemTypeProvider** den Standardcode durch folgenden Code, und speichern Sie die Datei.  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/vb/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.vb#1)]  
  
## Erstellen einer Visual Studio\-Projektvorlage  
 Durch das Erstellen einer Projektvorlage ermöglichen Sie anderen Entwicklern das Erstellen von SharePoint\-Projekten, die Websitespalten\-Projektelemente enthalten.  Eine SharePoint\-Projektvorlage enthält die Dateien, die für alle Projekte in Visual Studio erforderlich sind, z. B. CSPROJ\- oder VBPROJ\- und VSTEMPLATE\-Dateien, sowie spezifische Dateien für SharePoint\-Projekte.  Weitere Informationen finden Sie unter [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 Bei diesem Verfahren erstellen Sie ein leeres SharePoint\-Projekt, um Dateien zu generieren, die spezifisch für SharePoint\-Projekte sind.  Sie fügen diese Dateien dem SiteColumnProjectTemplate\-Projekt hinzu, damit sie in der Vorlage enthalten sind, die von diesem Projekt generiert wird.  Ferner konfigurieren Sie die Projektdatei "SiteColumnProjectTemplate", um anzugeben, an welcher Position im Dialogfeld **Neues Projekt** die Projektvorlage angezeigt wird.  
  
#### So erstellen Sie die Dateien für die Projektvorlage  
  
1.  Starten Sie eine zweite Instanz von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] mit Administratorrechten.  
  
2.  Erstellen Sie ein neues leeres SharePoint 2010\-Projekt namens **BaseSharePointProject**.  
  
    > [!IMPORTANT]  
    >  Wählen Sie im **Assistenten zum Anpassen von SharePoint** nicht die Option **Als Farmlösung bereitstellen**.  
  
3.  Fügen Sie dem Projekt ein leeres Projektelement hinzu, und nennen Sie es **Field1**.  
  
4.  Speichern Sie das Projekt, und schließen Sie die zweite Instanz von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
5.  Öffnen Sie in der [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-Instanz, in der die SiteColumnProjectItem\-Projektmappe im **Projektmappen\-Explorer** geöffnet ist, das Kontextmenü für den **SiteColumnProjectTemplate**\-Projektknoten, wählen Sie **Hinzufügen**, und wählen Sie dann **Vorhandenes Element**.  
  
6.  Öffnen Sie im Dialogfeld **Vorhandenes Element hinzufügen** die Liste der Dateierweiterungen, und wählen Sie **Alle Dateien \(\*.\*\)** aus.  
  
7.  Wählen Sie im Verzeichnis, in dem sich das BaseSharePointProject\-Projekt befindet, erst die KEY\-SNK\-Datei und anschließend die Schaltfläche **Hinzufügen** aus.  
  
    > [!NOTE]  
    >  In dieser exemplarischen Vorgehensweise wird diese KEY.SNK\-Datei von der Projektvorlage verwendet, die Sie erstellen, um die einzelnen Projekte zu signieren, die mit der Vorlage erstellt werden.  Informationen zum Erweitern dieses Beispiels durch das Erstellen einer neuen KEY.SNK\-Datei für die einzelnen Projektinstanzen finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines Projektelements "Websitespalte" mit einer Projektvorlage, Teil 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
8.  Wiederholen Sie die Schritte 5\-8, um die folgenden Dateien aus den angegebenen Unterordnern im Verzeichnis BaseSharePointProject hinzuzufügen:  
  
    -   \\Field1\\Elements.xml  
  
    -   \\Field1\\SharePointProjectItem.spdata  
  
    -   \\Features\\Feature1\\Feature1.feature  
  
    -   \\Features\\Feature1\\Feature1.Template.xml  
  
    -   \\Package\\Package.package  
  
    -   \\Package\\Package.Template.xml  
  
     Fügen Sie die Dateien unmittelbar zum SiteColumnProjectTemplate\-Projekt hinzu. Erstellen Sie die Unterordner Field1, Feature oder Package nicht erneut im Projekt.  Weitere Informationen zu diesen Dateien finden Sie unter [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
#### So konfigurieren Sie die Verwendung der Projektvorlage durch Entwickler im Dialogfeld "Neues Projekt"  
  
1.  Öffnen Sie im **Projektmappen\-Explorer** das Kontextmenü für das **SiteColumnProjectTemplate**\-Projekt, und wählen Sie dann **Projekt entladen** aus.  Wenn Sie aufgefordert werden, die Änderungen an den Dateien zu speichern, klicken Sie auf **Ja**.  
  
2.  Öffnen Sie erneut das Kontextmenü für den Knoten **SiteColumnProjectTemplate**, und wählen Sie dann **SiteColumnProjectTemplate.csproj bearbeiten** oder **SiteColumnProjectTemplate.vbproj bearbeiten** aus.  
  
3.  Suchen Sie das folgende `VSTemplate`\-Element in der Projektdatei.  
  
    ```  
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">  
    ```  
  
4.  Ersetzen Sie dieses Element durch das folgende XML.  
  
    ```  
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">  
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>  
    </VSTemplate>  
    ```  
  
     Das `OutputSubPath`\-Element gibt weitere Ordner in dem Pfad an, unter dem die Projektvorlage beim Erstellen des Projekts erstellt wird.  Mit den hier angegebenen Ordnern wird sichergestellt, dass die Projektvorlage nur dann verfügbar ist, wenn Kunden im Dialogfeld **Neues Projekt** den Knoten **SharePoint** erweitern und dann den Knoten **2010** auswählen.  
  
5.  Speichern und schließen Sie die Datei.  
  
6.  Öffnen Sie im **Projektmappen\-Explorer** das Kontextmenü für das Projekt **SiteColumnProjectTemplate**, und wählen Sie dann **Projekt erneut laden** aus.  
  
## Bearbeiten der Projektvorlagendateien  
 Bearbeiten Sie die folgenden Dateien im SiteColumnProjectTemplate\-Projekt, um das Verhalten der Projektvorlage zu definieren:  
  
-   AssemblyInfo.cs oder AssemblyInfo.vb  
  
-   Elements.xml  
  
-   SharePointProjectItem.spdata  
  
-   Feature1.feature  
  
-   Package.package  
  
-   SiteColumnProjectTemplate.vstemplate  
  
-   ProjectTemplate.csproj oder ProjectTemplate.vbproj  
  
 In den folgenden Verfahren fügen Sie einigen Dateien ersetzbare Parameter hinzu.  Ein ersetzbarer Parameter ist ein Token, das mit einem Dollarzeichen \($\) beginnt und endet.  Wenn ein Benutzer mit dieser Projektvorlage ein Projekt erstellt, werden diese Parameter im neuen Projekt von Visual Studio automatisch durch bestimmte Werte ersetzt.  Weitere Informationen finden Sie unter [Ersetzbare Parameter](../sharepoint/replaceable-parameters.md).  
  
#### So bearbeiten Sie die Datei AssemblyInfo.cs oder die Datei AssemblyInfo.vb  
  
1.  Im SiteColumnProjectTemplate\-Projekt öffnen Sie die Datei AssemblyInfo.cs oder AssemblyInfo.vb, und fügen dann darüber die folgende Anweisung hinzu:  
  
    ```vb  
    Imports System.Security  
    ```  
  
    ```csharp  
    using System.Security;  
    ```  
  
     Wenn die Eigenschaft **Sandkastenlösung** eines SharePoint\-Projekts auf **True** festgelegt ist, wird das <xref:System.Security.AllowPartiallyTrustedCallersAttribute> von Visual Studio der Codedatei AssemblyInfo hinzugefügt.  Der Namespace <xref:System.Security> wird von der Codedatei AssemblyInfo in Projektvorlage allerdings nicht standardmäßig importiert.  Sie müssen die Anweisung **using** bzw. die Anweisung **Imports** hinzufügen, um Compilerfehler zu verhindern.  
  
2.  Speichern und schließen Sie die Datei.  
  
#### So bearbeiten Sie die Datei Elements.xml  
  
1.  Ersetzen Sie im Projekt "SiteColumnProjectTemplate" den Inhalt der Datei "Elements.xml" durch das folgende XML.  
  
    ```  
  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <Field ID="{$guid5$}"   
          Name="$safeprojectname$"   
          DisplayName="$projectname$"   
          Type="Text"   
          Group="Custom Columns">  
      </Field>  
    </Elements>  
    ```  
  
     Mit dem neuen XML wird ein `Field`\-Element hinzugefügt, das den Namen der Websitespalte, den Basistyp sowie die Gruppe definiert, in der die Websitespalte im Katalog aufgelistet wird.  Weitere Informationen zum Inhalt dieser Datei finden Sie unter [Feld\-Definitionsschema](http://go.microsoft.com/fwlink/?LinkId=184290).  
  
2.  Speichern und schließen Sie die Datei.  
  
#### So bearbeiten Sie die Datei SharePointProjectItem.spdata  
  
1.  Ersetzen Sie im SiteColumnProjectTemplate\-Projekt den Inhalt der SharePointProjectItem.spdata\-Datei durch das folgende XML.  
  
    ```  
  
    <ProjectItem Type="Contoso.SiteColumn" DefaultFile="Elements.xml"   
                 xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">  
      <Files>  
        <ProjectItemFile Source="Elements.xml" Target="$safeprojectname$\" Type="ElementManifest" />  
      </Files>   
    </ProjectItem>  
    ```  
  
     Durch das neue XML werden folgende Änderungen an der Datei vorgenommen:  
  
    -   Ändert das `Type`\-Attribut des `ProjectItem`\-Elements in dieselbe Zeichenfolge, die an <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> in der Projektdefinition übergeben wird \(die `SiteColumnProjectItemTypeProvider`\-Klasse, die Sie zuvor in dieser exemplarischen Vorgehensweise erstellt haben\).  
  
    -   Entfernt die Attribute `SupportedTrustLevels` und `SupportedDeploymentScopes` aus dem `ProjectItem`\-Element.  Diese Attributwerte werden nicht benötigt, da die Vertrauensebenen und Bereitstellungsbereiche in der `SiteColumnProjectItemTypeProvider`\-Klasse im Projekt ProjectItemTypeDefinition angegeben werden.  
  
     Weitere Informationen zum Inhalt von SPDATA\-Dateien finden Sie unter [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md).  
  
2.  Speichern und schließen Sie die Datei.  
  
#### So bearbeiten Sie die Datei Feature1.feature  
  
1.  Ersetzen Sie im SiteColumnProjectTemplate\-Projekt den Inhalt der Feature1.feature\-Datei durch das folgende XML.  
  
    ```  
  
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
  
    -   Ändert die Werte der Attribute `Id` und `featureId` des `feature`\-Elements in `$guid4$`.  
  
    -   Ändert die Werte des `itemId`\-Attributs für das `projectItemReference`\-Element in `$guid2$`.  
  
     Weitere Informationen zu FEATURE\-Dateien finden Sie unter [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
2.  Speichern und schließen Sie die Datei.  
  
#### So bearbeiten Sie die Datei Package.package  
  
1.  Ersetzen Sie im SiteColumnProjectTemplate\-Projekt den Inhalt der Package.package\-Datei durch das folgende XML.  
  
    ```  
  
    <package xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0"   
             Id="$guid3$" solutionId="$guid3$" resetWebServer="false" name="$safeprojectname$"   
             xmlns="http://schemas.microsoft.com/VisualStudio/2008/SharePointTools/PackageModel">  
      <features>  
        <featureReference itemId="$guid4$" />  
      </features>  
    </package>  
    ```  
  
     Durch das neue XML werden folgende Änderungen an der Datei vorgenommen:  
  
    -   Ändert die Werte der Attribute `Id` und `solutionId` des `package`\-Elements in `$guid3$`.  
  
    -   Ändert die Werte des `itemId`\-Attributs für das `featureReference`\-Element in `$guid4$`.  
  
     Weitere Informationen zu PACKAGE\-Dateien finden Sie unter [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
2.  Speichern und schließen Sie die Datei.  
  
#### So bearbeiten Sie die Datei SiteColumnProjectTemplate.vstemplate  
  
1.  Ersetzen Sie im SiteColumnProjectTemplate\-Projekt die Inhalte der SiteColumnProjectTemplate.vstemplate\-Datei durch einen der folgenden XML\-Abschnitte.  
  
    -   Wenn Sie eine Visual C\#\-Projektvorlage erstellen, verwenden Sie das folgende XML:  
  
    ```  
  
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
  
    -   Wenn Sie eine Visual Basic\-Projektvorlage erstellen, verwenden Sie das folgende XML:  
  
    ```  
  
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
  
    -   Legt das `Name`\-Element auf den Wert **Websitespalte** fest. \(Dieser Name wird im Dialogfeld **Neues Projekt** angezeigt\).  
  
    -   Fügt die `ProjectItem`\-Elemente für alle Dateien hinzu, die in den einzelnen Projektinstanzen enthalten sind.  
  
    -   Verwendet den Namespace "http:\/\/schemas.microsoft.com\/developer\/vstemplate\/2005".  Andere Projektdateien in dieser Projektmappe verwenden den Namespace "http:\/\/schemas.microsoft.com\/developer\/msbuild\/2003".  Daher werden XML\-Schema\-Warnmeldungen generiert, die Sie aber bei dieser exemplarischen Vorgehensweise ignorieren können.  
  
     Weitere Informationen zum Inhalt von .vstemplate\-Dateien finden Sie unter [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md).  
  
2.  Speichern und schließen Sie die Datei.  
  
#### So bearbeiten Sie die Datei ProjectTemplate.csproj oder die Datei ProjectTemplate.vbproj  
  
1.  Ersetzen Sie im SiteColumnProjectTemplate\-Projekt den Inhalt der ProjectTemplate.csproj\- oder ProjectTemplate.vbproj\-Datei durch einen der folgenden XML\-Abschnitte.  
  
    -   Wenn Sie eine Visual C\#\-Projektvorlage erstellen, verwenden Sie das folgende XML:  
  
    ```  
  
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
  
    1.  Wenn Sie eine Visual Basic\-Projektvorlage erstellen, verwenden Sie das folgende XML:  
  
    ```  
  
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
  
    -   Verwendet das `TargetFrameworkVersion`\-Element, um .NET Framework 3.5 und nicht .NET Framework 4.5 festzulegen.  
  
    -   Fügt die Elemente `AssemblyOriginatorKeyFile` und `SignAssembly` hinzu, um die Projektausgabe zu signieren.  
  
    -   Fügt die `Reference`\-Elemente für Assemblyverweise hinzu, die von SharePoint\-Projekten verwendet werden.  
  
    -   Fügt Elemente für alle Standarddateien im Projekt wie Elements.xml oder SharePointProjectItem.spdata hinzu.  
  
2.  Speichern und schließen Sie die Datei.  
  
## Erstellen eines VSIX\-Pakets zum Bereitstellen der Projektvorlage  
 Erstellen Sie mithilfe des VSIX\-Projekts in der Lösung **SiteColumnProjectItem** ein VSIX\-Paket, um die Erweiterung bereitzustellen.  Konfigurieren Sie zuerst das VSIX\-Paket, indem Sie die im VSIX\-Projekt enthaltene Datei "source.extension.vsixmanifest" ändern.  Erstellen Sie anschließend das VSIX\-Paket, indem Sie die Lösung erstellen.  
  
#### So erstellen und konfigurieren Sie das VSIX\-Paket  
  
1.  Öffnen Sie im **Projektmappen\-Explorer** im Projekt **SiteColumnProjectItem** die source.extension.vsixmani\-Datei im Manifest\-Editor.  
  
     Die Datei "source.extension.vsixmanifest" bildet die Grundlage für die Datei "extension.vsixmanifest", die für alle VSIX\-Pakete erforderlich ist.  Weitere Informationen zu dieser Datei finden Sie unter [VSIX\-Erweiterungs\-Schemareferenz](http://msdn.microsoft.com/de-de/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  Geben Sie im Feld **Produktname** den Namen **Site Column** ein.  
  
3.  Geben Sie im Feld **Autor** den Namen **Contoso** ein.  
  
4.  Geben Sie im Feld **Beschreibung** die Beschreibung **A SharePoint project for creating site columns** ein.  
  
5.  Wählen Sie die Registerkarte **Objekte**, und wählen Sie dann die Schaltfläche **Neu** aus.  
  
     Das Dialogfeld **Neue Anlage hinzufügen** wird geöffnet.  
  
6.  Wählen Sie in der Liste **TypMicrosoft.VisualStudio.ProjectTemplate** aus.  
  
    > [!NOTE]  
    >  Dieser Wert entspricht dem `ProjectTemplate`\-Element in der Datei "extension.vsixmanifest".  Durch dieses Element wird der Unterordner im VSIX\-Paket identifiziert, der die Projektvorlage enthält.  Weitere Informationen finden Sie unter [NIB: ProjectTemplate Element \(VSX Schema\)](http://msdn.microsoft.com/de-de/87add64c-9dcd-495f-8815-209dab182cb1).  
  
7.  Wählen Sie in der Liste **Quelle** die Option **Ein Projekt in der aktuellen Projektmappe** aus.  
  
8.  Wählen Sie in der Liste **ProjektSiteColumnProjectTemplate** und dann die Schaltfläche **OK** aus.  
  
9. Wählen Sie die Schaltfläche **Neu** erneut aus.  
  
     Das Dialogfeld **Neue Anlage hinzufügen** wird geöffnet.  
  
10. Wählen Sie in der Liste **Typ** den Eintrag **Microsoft.VisualStudio.MefComponent** aus.  
  
    > [!NOTE]  
    >  Dieser Wert entspricht dem `MefComponent`\-Element in der Datei "extension.vsixmanifest".  Von diesem Element wird der Name einer Erweiterungsassembly im VSIX\-Paket angegeben.  Weitere Informationen finden Sie unter [NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/de-de/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
11. Wählen Sie in der Liste **Quelle** die Option **Ein Projekt in der aktuellen Projektmappe** aus.  
  
12. Wählen Sie in der Liste **Projekt** die Option **ProjectItemTypeDefinition** und dann die Schaltfläche **OK** aus.  
  
13. Wählen Sie in der Menüleiste **BuildProjektmappe erstellen** aus, und überprüfen Sie dann, ob das Projekt fehlerfrei kompiliert werden kann.  
  
## Testen der Projektvorlage  
 Jetzt können Sie die Projektvorlage testen.  Debuggen Sie die Projektmappe SiteColumnProjectItem zunächst in der experimentellen Instanz von Visual Studio.  Anschließend testen Sie das Projekt **Websitespalte** in der experimentellen Instanz von Visual Studio.  Erstellen und führen Sie zum Schluss das SharePoint\-Projekt aus, um sicherzustellen, dass die Websitespalte ordnungsgemäß funktioniert.  
  
#### So debuggen Sie die Projektmappe  
  
1.  Starten Sie Visual Studio erneut mit Administratoranmeldeinformationen, und öffnen Sie dann die Projektmappe "SiteColumnProjectItem".  
  
2.  Fügen Sie der SiteColumnProjectItemTypeProvider\-Codedatei in der ersten Zeile der `InitializeType`\-Methode einen Haltepunkt hinzu, und wählen Sie dann **F5**, um das Debuggen zu starten.  
  
     Die Erweiterung wird unter %UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\10.0Exp\\Extensions\\Contoso\\Websitespalte\\1.0 installiert, und eine experimentelle Instanz von Visual Studio wird gestartet.  Sie testen das Projektelement in dieser Instanz von Visual Studio.  
  
#### So testen Sie das Projekt in Visual Studio  
  
1.  Wählen Sie in der experimentellen Visual Studio\-Instanz in der Menüleiste **Datei**, **Neu** und **Projekt** aus.  
  
2.  Erweitern Sie den Knoten **Visual C\#** oder **Visual Basic** \(je nach der von der Projektvorlage unterstützten Sprache\), erweitern Sie den Knoten **SharePoint**, und wählen Sie dann den Knoten **2010** aus.  
  
3.  Wählen Sie in der Liste der Projektvorlagen die Vorlage **Websitespalte** aus.  
  
4.  Geben Sie im Textfeld **Name** den Eintrag **SiteColumnTest** ein, und klicken Sie dann auf die Schaltfläche **OK**.  
  
     Im **Projektmappen\-Explorer** wird ein neues Projekt mit einem Projektelement namens **Field1** angezeigt.  
  
5.  Überprüfen Sie, ob die Codeausführung in der anderen Instanz von Visual Studio an dem Haltepunkt gestoppt wird, den Sie zuvor in der `InitializeType`\-Methode festgelegt haben, und wählen Sie dann **F5**, um das Debuggen des Projekts fortzusetzen.  
  
6.  Wählen Sie im **Projektmappen\-Explorer** den Knoten **Field1** aus, und drücken Sie dann **F4**.  
  
     Das **Eigenschaftenfenster** wird geöffnet.  
  
7.  Überprüfen Sie, ob die **Beispieleigenschaft**\-Eigenschaft in der Eigenschaftenliste angezeigt wird.  
  
#### So testen Sie die Websitespalte in SharePoint  
  
1.  Wählen Sie im **Projektmappen\-Explorer** den Knoten **SiteColumnTest** aus.  
  
2.  Geben Sie im Fenster **Eigenschaften** im Textfeld neben der **Website\-URL**\-Eigenschaft den Eintrag **http:\/\/localhost** ein.  
  
     Dadurch wird auf dem Entwicklungscomputer die lokale SharePoint\-Website angegeben, die zum Debuggen verwendet werden soll.  
  
    > [!NOTE]  
    >  Die **Website\-URL**\-Eigenschaft ist standardmäßig leer, weil von der Projektvorlage für die Websitespalte kein Assistent zum Erfassen dieses Werts beim Erstellen des Projekts bereitgestellt wird.  Informationen zum Hinzufügen eines Assistenten, mit dem dieser Wert vom Entwickler abgefragt und anschließend die Eigenschaft im neuen Projekt konfiguriert wird, finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines Projektelements "Websitespalte" mit einer Projektvorlage, Teil 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
3.  Wählen Sie die Taste **F5** aus.  
  
     Die Websitespalte wird verpackt und auf der SharePoint\-Website bereitgestellt, die in der **Website\-URL**\-Eigenschaft des Projekts angegeben ist.  Im Webbrowser wird die Standardseite dieser Website geöffnet.  
  
    > [!NOTE]  
    >  Wenn das Dialogfeld **Skriptdebugging deaktiviert** angezeigt wird, wählen Sie die Schaltfläche **Ja** aus, um mit dem Debuggen des Projekts fortzufahren.  
  
4.  Wählen Sie im Menü **Websiteaktionen** die Option **Websiteeinstellungen** aus.  
  
5.  Wählen Sie auf der Seite **Websiteeinstellungen** unter der Liste **Galerien** den Link **Websitespalten** aus.  
  
6.  Überprüfen Sie in der Liste der Websitespalten, ob eine **Benutzerdefinierte Spalten**\-Gruppe eine Spalte namens **SiteColumnTest** enthält.  
  
7.  Schließen Sie den Webbrowser.  
  
## Bereinigen des Entwicklungscomputers  
 Nachdem Sie die Tests des Projekts abgeschlossen haben, entfernen Sie die Projektvorlage aus der experimentellen Instanz von Visual Studio.  
  
#### So bereinigen Sie den Entwicklungscomputer  
  
1.  Wählen Sie in der experimentellen Visual Studio\-Instanz in der Menüleiste **Erstellen** und **Erweiterungen und Update** aus.  
  
     Das Dialogfeld **Erweiterungen und Updates** wird geöffnet.  
  
2.  Wählen Sie in der Liste der Erweiterungen **Websitespalte** und dann die Schaltfläche **Deinstallieren** aus.  
  
3.  Wählen Sie im angezeigten Dialogfeld die Schaltfläche **Ja** aus, um zu bestätigen, dass Sie die Erweiterung deinstallieren möchten.  
  
4.  Wählen Sie die Schaltfläche **Schließen** aus, um die Deinstallation abzuschließen.  
  
5.  Schließen Sie beide Instanzen von Visual Studio \(die experimentelle Instanz und die Instanz von Visual Studio, in der die SiteColumnProjectItem\-Projektmappe geöffnet ist\).  
  
## Nächste Schritte  
 Nachdem Sie diese exemplarische Vorgehensweise abgeschlossen haben, können Sie der Projektvorlage einen Assistenten hinzufügen.  Beim Erstellen eines Websitespaltenprojekts wird der Benutzer vom Assistenten aufgefordert, die URL der Website anzugeben, die zum Debuggen verwendet werden soll. Darüber hinaus muss vom Benutzer angegeben werden, ob die neue Projektmappe als Sandkastenlösung bereitgestellt wird. Anschließend wird das Projekt vom Assistenten mit diesen Informationen konfiguriert.  Ferner werden vom Assistenten Informationen zur Spalte \(z. B. der Basistyp und die Gruppe, in der die Spalte in der Websitespaltengalerie aufgeführt werden soll\) gesammelt und der Datei Elements.xml im neuen Projekt hinzugefügt.  Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines Projektelements "Websitespalte" mit einer Projektvorlage, Teil 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
## Siehe auch  
 [Exemplarische Vorgehensweise: Erstellen eines Projektelements "Websitespalte" mit einer Projektvorlage, Teil 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
  