---
title: "Deploying Extensions for the SharePoint Tools in Visual Studio | Microsoft Docs"
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
  - "SharePoint development in Visual Studio, deploying extensions"
ms.assetid: 69927d95-acdf-4fd8-ac43-28e9a7fa8a38
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# Deploying Extensions for the SharePoint Tools in Visual Studio
  Erstellen Sie zum Bereitstellen einer SharePoint\-Tools\-Erweiterung ein [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-Erweiterungspaket \(VSIX\), das die Erweiterungsassembly und alle weiteren Dateien enthält, die Sie mit der Erweiterung verteilen möchten.  Ein VSIX\-Paket ist eine komprimierte Datei, die dem OPC \(Open Packaging Conventions\)\-Standard folgt.  VSIX\-Pakete haben die Erweiterung ".vsix".  
  
 Nachdem Sie ein VSIX\-Paket erstellt haben, können andere Benutzer die VSIX\-Datei ausführen, um die Erweiterung zu installieren.  Wenn ein Benutzer die Erweiterung installiert, werden alle Dateien im Ordner "%UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\11.0\\Extensions" installiert.  Um die Erweiterung bereitzustellen, können Sie das VSIX\-Paket auf die [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkID=123847)\-Website \(möglicherweise in englischer Sprache\) hochladen. Außerdem können Sie das Paket auch auf andere Weise an Kunden verteilen, z. B. per Hosten des Pakets auf einer Netzwerkfreigabe oder einer anderen Website.  
  
 Weitere Informationen zur Erstellung von VSIX\-Paketen und deren Bereitstellung in [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkID=123847) finden Sie unter [Lieferung von Visual Studio-Erweiterungen](../extensibility/shipping-visual-studio-extensions.md).  
  
 Sie können ein VSIX\-Paket erstellen, indem Sie in Visual Studio die Vorlage **VSIX\-Projekt** verwenden oder das VSIX\-Paket manuell erstellen.  
  
## Verwenden von VSIX\-Projekten zum Erstellen von VSIX\-Paketen  
 Sie können die vom Visual Studio SDK bereitgestellte Vorlage **VSIX\-Projekt** verwenden, um VSIX\-Pakete für SharePoint\-Tools\-Erweiterungen zu erstellen.  Die Verwendung eines VSIX\-Projekts bietet gegenüber der manuellen Erstellung eines VSIX\-Pakets mehrere Vorteile:  
  
-   Visual Studio erzeugt beim Erstellen des Projekts automatisch das VSIX\-Paket.  Aufgaben wie das Hinzufügen der Bereitstellungsdateien zum Paket und das Erstellen der Datei "\[Content\_Types\].xml" für das Paket werden für Sie ausgeführt.  
  
-   Sie können das VSIX\-Projekt so konfigurieren, dass es im VSIX\-Paket die Buildausgabe des Erweiterungsprojekts und anderer Dateien enthält, z. B. Projektvorlagen und Elementvorlagen.  
  
 Weitere Informationen zur Verwendung eines VSIX\-Projekts finden Sie unter [VSIX-Projektvorlage](../extensibility/vsix-project-template.md).  
  
### Organisieren der Projekte  
 Standardmäßig werden von VSIX\-Projekten nur VSIX\-Pakete generiert, keine Assemblys.  Daher implementieren Sie i. d. R. keine SharePoint\-Toolerweiterungen in einem VSIX\-Projekt.  Im Allgemeinen arbeiten Sie mit mindestens zwei Projekten:  
  
-   Ein VSIX\-Projekt.  
  
-   Ein Klassenbibliotheksprojekt, von dem die Erweiterung implementiert wird.  
  
 Bei bestimmten Erweiterungstypen können Sie auch mit weiteren Projekten arbeiten:  
  
-   Ein Klassenbibliotheksprojekt zur Implementierung aller SharePoint\-Befehle, die von der Erweiterung verwendet werden.  Eine exemplarische Vorgehensweise, die dieses Szenario veranschaulicht, finden Sie unter [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
-   Ein Elementvorlagen\- oder Projektvorlagenprojekt, mit dem eine Elementvorlage oder eine Projektvorlage erstellt wird, wenn von der Erweiterung ein neuer SharePoint\-Projektelementvorlagentyp definiert wird.  Eine exemplarische Vorgehensweise, die dieses Szenario veranschaulicht, finden Sie unter [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).  
  
-   Ein Klassenbibliotheksprojekt, das einen benutzerdefinierten Assistenten für eine Projektvorlage oder eine Elementvorlage implementiert, wenn die Erweiterung eine Vorlage enthält.  Eine exemplarische Vorgehensweise, die dieses Szenario veranschaulicht, finden Sie unter [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).  
  
 Wenn Sie alle Projekte in dieselbe Visual Studio\-Projektmappe einbinden, können Sie die Datei "source.extension.vsixmanifest" im VSIX\-Projekt so ändern, dass sie die Buildausgabe der Klassenbibliotheksprojekte enthält.  
  
### Bearbeiten des VSIX\-Manifests  
 Sie müssen die source.extension.vsixmanifest\-Datei im VSIX\-Projekt bearbeiten, um Einträge für alle Elemente einzuschließen, die Sie in der Erweiterung verwenden möchten.  Wenn Sie die source.extension.vsixmanifest\-Datei im Kontextmenü öffnen, wird die Datei in einem Designer, der eine Benutzeroberfläche zum Bearbeiten des XML in der Datei bereitstellt.  Weitere Informationen finden Sie unter [VSIX-Manifest-Designer](../extensibility/media/vsix-manifest-designer.png).  
  
 Für die folgenden Elemente müssen Einträge in der source.extension.vsixmanifest\-Datei hinzugefügt werden:  
  
-   Die Erweiterungsassembly.  
  
-   Die Assembly, von der alle SharePoint\-Befehle implementiert werden, die von der Erweiterung verwendet werden.  
  
-   Alle Projektvorlagen oder Elementvorlagen, die der Erweiterung zugeordnet sind.  
  
-   Ein benutzerdefinierter Assistent für eine Vorlage, die der Erweiterung zugeordnet ist.  
  
 In den folgenden Verfahren wird beschrieben, wie Sie der .vsixmanifest\-Datei Einträge für jedes dieser Elemente hinzufügen.  
  
##### So binden Sie die Erweiterungsassembly ein  
  
1.  im VSIX\-Projekt öffnen Sie das Kontextmenü für die source.extension.vsixmanifest\-Datei, und wählen Sie dann **Öffnen** aus.  
  
     Die Datei wird im Designer  
  
2.  Klicken Sie auf der Registerkarte des Editors **Objekte**, wählen Sie die Schaltfläche **Neu** aus.  
  
     Das Dialogfeld wird geöffnet. **Neue Anlage hinzufügen**  
  
3.  In der Liste wählen Sie **TypMicrosoft.VisualStudio.MefComponent** aus.  
  
4.  In der Liste **Quelle** führen Sie einen der folgenden Schritte aus:  
  
    -   Wenn die Erweiterungsassembly aus einem Projekt erstellt wird, das in der gleichen Projektmappe wie das VSIX\-Projekt enthalten ist, wählen Sie **Ein Projekt in der aktuellen Projektmappe** aus.  In der Liste **Projekt** den Namen des Projekts.  
  
    -   Wenn die Erweiterungsassembly enthalten ist, als Datei im Projekt, **Datei im Dateisystem** auswählen.  In der Liste **Pfad** geben Sie den vollständigen Pfad zur Erweiterungsassemblydatei, oder verwenden Sie die Schaltfläche **Durchsuchen**, um die Assemblydatei auszuwählen.  
  
5.  Klicken Sie auf die Schaltfläche **OK**.  
  
##### So binden Sie eine SharePoint\-Befehlsassembly ein  
  
1.  im VSIX\-Projekt öffnen Sie das Kontextmenü für die source.extension.vsixmanifest\-Datei, und wählen Sie dann die Schaltfläche **Öffnen** aus.  
  
     Die Datei wird im Designer geöffnet.  
  
2.  Im **Objekte**\-Abschnitt des Editors, wählen Sie die Schaltfläche **Neu** aus.  
  
     Das Dialogfeld wird geöffnet. **Neue Anlage hinzufügen**  
  
3.  Im Feld geben Sie **TypSharePoint.Commands.v4** ein.  
  
4.  In der Liste **Quelle** führen Sie einen der folgenden Schritte aus:  
  
    -   Wenn die Befehlsassembly aus einem Projekt erstellt wird, das in der gleichen Projektmappe wie das VSIX\-Projekt enthalten ist, wählen Sie **Ein Projekt in der aktuellen Projektmappe** aus.  In der Liste **Projekt** den Namen des Projekts.  
  
    -   Wenn die Befehlsassembly enthalten ist, als Datei im Projekt, **Datei im Dateisystem** auswählen.  In der Liste **Pfad** geben Sie den vollständigen Pfad zur Erweiterungsassemblydatei, oder verwenden Sie die Schaltfläche **Durchsuchen**, um die Assemblydatei auszuwählen.  
  
5.  Klicken Sie auf die Schaltfläche **OK**.  
  
##### So fügen Sie eine Vorlage einschließen, die Sie erstellen  
  
1.  im VSIX\-Projekt öffnen Sie das Kontextmenü für die source.extension.vsixmanifest\-Datei, und wählen Sie dann die Schaltfläche **Öffnen** aus.  
  
     Die Datei wird im Designer geöffnet.  
  
2.  Im **Objekte**\-Abschnitt des Editors, wählen Sie die Schaltfläche **Neu** aus.  
  
     Das Dialogfeld wird geöffnet. **Neue Anlage hinzufügen**  
  
3.  In der Liste wählen Sie **TypMicrosoft.VisualStudio.ProjectTemplate** oder **Microsoft.VisualStudio.ItemTemplate** aus.  
  
4.  In der Liste wählen Sie **QuelleEin Projekt in der aktuellen Projektmappe** aus.  
  
5.  In der Liste **Projekt** den Namen des Projekts, und wählen Sie dann die Schaltfläche **OK** aus.  
  
6.  In **Projektmappen\-Explorer** öffnen Sie das Kontextmenü für das Projektvorlagen\- oder Elementvorlagenprojekt, und wählen Sie dann **Projekt entladen** aus.  
  
7.  Öffnen Sie das Kontextmenü für den Projektknoten erneut, und wählen Sie dann **Bearbeiten***auf***.csproj** oder **Bearbeiten***auf***.vbproj** aus.  
  
8.  Suchen Sie das folgende `VSTemplate`\-Element in der Projektdatei.  
  
    ```  
    <VSTemplate Include="YourTemplateName.vstemplate">  
    ```  
  
9. Ersetzen Sie dieses Element durch das folgende XML.  
  
    ```  
    <VSTemplate Include="YourTemplateName.vstemplate">  
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>  
    </VSTemplate>  
    ```  
  
     Das `OutputSubPath`\-Element gibt weitere Ordner in dem Pfad an, unter dem die Projektvorlage beim Erstellen des Projekts erstellt wird.  Die Ordner, die hier angegeben werden, sicherstellen, dass die Elementvorlage nur wenn Kunden **Neues Projekt hinzufügen** das Dialogfeld öffnen, erweitern Sie den Knoten **SharePoint** auswählen und dann den Knoten **2010** verfügbar ist.  
  
10. Speichern und schließen Sie die Datei.  
  
11. In **Projektmappen\-Explorer** öffnen Sie das Kontextmenü für das Projektvorlagen\- oder Elementvorlagenprojekt, und wählen Sie dann **Projekt erneut laden** aus.  
  
##### So schließen Sie eine manuell erstellte Vorlage ein  
  
1.  Fügen Sie im VSIX\-Projekt einen neuen Ordner hinzu, der die Vorlage enthalten soll.  
  
2.  Erstellen Sie in diesem neuen Ordner die folgenden Unterordner, und fügen Sie die Vorlagendatei \(.zip\) dann dem Ordner mit der *Gebietsschema\-ID* hinzu.  
  
     *IhrVorlagenordner*  
  
     **SharePoint**  
  
     **SharePoint14**  
  
     *Gebietsschema\-ID*  
  
     *YourTemplateName*.zip  
  
     Wenn Sie z. B. eine Elementvorlage mit dem Namen "ContosoCustomAction.zip" verwenden, die das Gebietsschema für "Englisch \(USA\)" unterstützt, kann der vollständige Pfad beispielsweise "ItemTemplates\\SharePoint\\SharePoint14\\1033\\ContosoCustomAction.zip" lauten.  
  
3.  In **Projektmappen\-Explorer** wählen Sie aus *YourTemplateName* die Vorlagendatei \(.zip\).  
  
4.  Legen Sie im Fenster **Eigenschaften** die **Build Action**\-Eigenschaft auf **Inhalt** fest.  
  
5.  Öffnen Sie das Kontextmenü für die source.extension.vsixmanifest\-Datei, und wählen Sie dann **Öffnen** aus.  
  
     Die Datei wird im Designer geöffnet.  
  
6.  Im **Objekte**\-Abschnitt des Editors, wählen Sie die Schaltfläche **Neu** aus.  
  
     Das Dialogfeld wird geöffnet. **Neue Anlage hinzufügen**  
  
7.  In der Liste wählen Sie **TypMicrosoft.VisualStudio.ItemTemplate** oder **Microsoft.VisualStudio.ProjectTemplate** aus.  
  
8.  In der Liste wählen Sie **QuelleDatei im Dateisystem** aus.  
  
9. Klicken Sie im Feld **Pfad** den vollständigen Pfad zur Assembly ein \(beispielsweise, verwenden **ItemTemplates\\SharePoint\\SharePoint14\\1033\\ContosoCustomAction.zip** oder die Schaltfläche **Durchsuchen**, um die Assembly zu suchen und auszuwählen und dann die Schaltfläche **OK** aus.  
  
##### So schließen Sie einen Assistenten für eine Projektvorlage oder eine Elementvorlage ein  
  
1.  im VSIX\-Projekt öffnen Sie das Kontextmenü für die source.extension.vsixmanifest\-Datei, und wählen Sie dann **Öffnen** aus.  
  
     Die Datei wird im Designer geöffnet.  
  
2.  Im **Objekte**\-Abschnitt des Editors, wählen Sie die Schaltfläche **Neu** aus.  
  
     Das Dialogfeld wird geöffnet. **Neue Anlage hinzufügen**  
  
3.  In der Liste wählen Sie **TypMicrosoft.VisualStudio.Assembly** aus.  
  
4.  In der Liste **Quelle** führen Sie einen der folgenden Schritte aus:  
  
    -   Wenn die Assistenten\-Assembly aus einem Projekt erstellt wird, das in der gleichen Projektmappe wie das VSIX\-Projekt enthalten ist, wählen Sie **Ein Projekt in der aktuellen Projektmappe** aus.  In der Liste **Projekt** den Namen des Projekts.  
  
    -   Wenn die Assistenten\-Assembly enthalten ist, als Datei im Projekt, **Datei im Dateisystem** auswählen.  Klicken Sie im Feld **Pfad** den vollständigen Pfad zur Assemblydatei ein, oder verwenden Sie die Schaltfläche **Durchsuchen**, um die Assembly zu suchen und auszuwählen.  
  
5.  Klicken Sie auf die Schaltfläche **OK**.  
  
### Verwandte exemplarische Vorgehensweisen  
 In der folgenden Tabelle sind exemplarische Vorgehensweisen aufgeführt, in denen veranschaulicht wird, wie Sie mit einem VSIX\-Projekt verschiedene Typen von SharePoint\-Toolerweiterungen bereitstellen.  
  
|Erweiterungstyp|Verwandte exemplarische Vorgehensweisen|  
|---------------------|---------------------------------------------|  
|Eine Erweiterung, die nur die Erweiterungsassembly enthält.|[Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)<br /><br /> [Walkthrough: Creating a SharePoint Project Extension](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)<br /><br /> [Walkthrough: Calling into the SharePoint Client Object Model in a Server Explorer Extension](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)|  
|Eine Erweiterung, die SharePoint\-Befehle enthält.|[Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)<br /><br /> [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)<br /><br /> [Exemplarische Vorgehensweise: Erstellen eines Projektelements "Websitespalte" mit einer Projektvorlage, Teil 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|  
|Eine Erweiterung, die eine Visual Studio\-Vorlage enthält.|[Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)<br /><br /> [Exemplarische Vorgehensweise: Erstellen eines Projektelements "Websitespalte" mit einer Projektvorlage, Teil 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)|  
|Eine Erweiterung, die den Vorlagen\-Assistenten enthält.|[Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)<br /><br /> [Exemplarische Vorgehensweise: Erstellen eines Projektelements "Websitespalte" mit einer Projektvorlage, Teil 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|  
  
## Manuelles Erstellen von VSIX\-Paketen  
 Führen Sie die folgenden Schritte aus, wenn Sie das VSIX\-Paket für die SharePoint\-Tools\-Erweiterung manuell erstellen möchten:  
  
1.  Erstellen Sie die Datei "extension.vsixmanifest", die Datei "\[Content\_Types\].xml" und die VSIX\-Paketdatei \(VSIX\-Datei\).  Weitere Informationen finden Sie unter [Anatomie eines VSIX-Pakets](../extensibility/anatomy-of-a-vsix-package.md) und [Gewusst wie: Manuelles Verpacken einer Erweiterung &#40;VSIX-Bereitstellung&#41;](~/misc/how-to-manually-package-an-extension-vsix-deployment.md).  
  
2.  Fügen Sie dem VSIX\-Paket die Erweiterungsassembly hinzu.  Falls die Erweiterung einen SharePoint\-Befehl enthält, müssen Sie auch die Assembly hinzufügen, die den SharePoint\-Befehl im VSIX\-Paket implementiert.  
  
3.  Ändern Sie die Datei "extension.vsixmanifest":  
  
    -   Fügen Sie ein `Microsoft.VisualStudio.MefComponent`\-Element unter dem `Assets`\-Element hinzu, und legen Sie dann den Wert des neuen Elements auf den relativen Pfad der Assembly fest, die die Erweiterung im VSIX\-Paket implementiert.  Weitere Informationen finden Sie unter [NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/de-de/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
    -   Wenn die Erweiterung einen SharePoint\-Befehl umfasst, in der das Serverobjektmodell für SharePoint aufruft, fügen Sie ein `Microsoft.VisualStudio.Assembly`\-Element unter dem `Assets`\-Element hinzu.  Legen Sie den Wert des neuen Elements auf den relativen Pfad der Assembly fest, die den SharePoint\-Befehl im VSIX\-Paket implementiert.  Weitere Informationen finden Sie unter [Vermögensteil \(VSX Schema\)](http://msdn.microsoft.com/de-de/9fcfc098-edc7-484b-9d4c-acd17829d737).  
  
    -   Wenn die Erweiterung eine Projektvorlage oder eine Elementvorlage umfasst, fügen Sie ein `ProjectTemplate` oder `ItemTemplate`\-Element unter dem `Assets`\-Element hinzu.  Legen Sie den Wert des neuen Elements auf den relativen Pfad des Ordners fest, der die Vorlage im VSIX\-Paket enthält.  Weitere Informationen finden Sie unter [NIB: ProjectTemplate Element \(VSX Schema\)](http://msdn.microsoft.com/de-de/87add64c-9dcd-495f-8815-209dab182cb1) und [NIB: ItemTemplate Element \(VSX Schema\)](http://msdn.microsoft.com/de-de/1d489e54-c1c5-4f96-a510-6c2640867ff0).  
  
    -   Wenn die Erweiterung einen benutzerdefinierten Assistenten für eine Projektvorlage oder eine Elementvorlage umfasst, fügen Sie ein `Assembly`\-Element unter dem `Assets`\-Element hinzu.  Legen Sie den Wert des neuen Elements auf den relativen Pfad der Assembly im VSIX\-Paket fest, und legen Sie dann das `AssemblyName`\-Attribut zum vollständigen Assemblynamen fest \(einschließlich Version, Kultur und öffentlichem Schlüsseltoken\).  Weitere Informationen finden Sie unter [Abhängigkeits\-Element \(VSX Schema\)](http://msdn.microsoft.com/de-de/1f63f60a-98ad-48ec-8e44-4eba383d3e37).  
  
### Beispiel  
 Im folgenden Beispiel wird der Inhalt einer extension.vsixmanifest\-Datei für eine SharePoint\-Toolerweiterung veranschaulicht.  Die Erweiterung wird in einer Assembly Contoso.ProjectExtension.dll implementiert, die genannt wird.  Die Erweiterung umfasst eine SharePoint\-Befehlsassembly, die Contoso.ExtensionCommands.dll sowie eine Elementvorlage unter dem Ordner namens, der **ItemTemplates** im VSIX\-Paket.  In diesem Beispiel wird davon ausgegangen, dass sich beide Assemblys im gleichen Ordner wie die Datei "extension.vsixmanifest" im VSIX\-Paket befinden.  
  
```  
<PackageManifest Version=”2.0.0” xmlns=”http://schemas.microsoft.com/developer/vsx-schema/2011”>  
  <Metadata>  
    <Identity Id="CustomActionProjectItem.Microsoft.b99efe4d-cef3-4afd-b9af-034ca0c52743" Version="1.0" Language="en-US" Publisher="Microsoft" />  
    <DisplayName>CustomActionProjectItem</DisplayName>  
    <Description>Empty VSIX Project.</Description>  
  </Metadata>  
  <Installation>  
    <InstallationTarget Id="Microsoft.VisualStudio.Pro" Version="11.0" />  
  </Installation>  
  <Dependencies>  
    <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" Version="4.5" />  
  </Dependencies>  
  <Assets>  
    <Asset Type="Microsoft.VisualStudio.ItemTemplate" Path="ItemTemplates" />  
    <Asset Type="Microsoft.VisualStudio.MefComponent" Path="ProjectItemDefinition.dll" />  
  </Assets>  
</PackageManifest>  
  
```  
  
## Siehe auch  
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Debugging Extensions for the SharePoint Tools in Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  