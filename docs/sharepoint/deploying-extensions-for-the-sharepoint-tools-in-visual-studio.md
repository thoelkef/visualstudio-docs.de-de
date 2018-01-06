---
title: "Bereitstellen von Erweiterungen für SharePoint-Tools in Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, deploying extensions
ms.assetid: 69927d95-acdf-4fd8-ac43-28e9a7fa8a38
caps.latest.revision: "40"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 18f1b473de12b53f3e1a7829d1f1c3b49862aef2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="deploying-extensions-for-the-sharepoint-tools-in-visual-studio"></a>Bereitstellen von Erweiterungen für die SharePoint-Tools in Visual Studio
  Erstellen Sie zum Bereitstellen einer SharePoint-Tools-Erweiterungs ein [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Erweiterungspaket (VSIX), die enthält die Erweiterungsassembly und alle anderen Dateien, die Sie mit der Erweiterung verteilen möchten. Ein VSIX-Paket ist eine komprimierte Datei, die den Standard (Open Packaging Conventions, OPC) folgt. VSIX-Pakete haben die VSIX-Erweiterung.  
  
 Nachdem Sie ein VSIX-Paket erstellt haben, können andere Benutzer die VSIX-Datei, um die Erweiterung installieren ausführen. Wenn ein Benutzer die Erweiterung installiert, werden alle Dateien in den Ordner %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0\Extensions installiert. Zum Bereitstellen der Erweiterung können Sie das VSIX-Paket zum Hochladen der [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkID=123847) -Website, oder Sie können verteilen Sie das Paket an Ihre Kunden durch andere Weise, wie z. B. das Paket auf einer Netzwerkfreigabe oder eine andere Website hostet.  
  
 Weitere Informationen zu VSIX-Pakete erstellen und bereitstellen, damit die [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkID=123847), finden Sie unter [Versand der Visual Studio-Erweiterungen](/visualstudio/extensibility/shipping-visual-studio-extensions).  
  
 Sie können ein VSIX-Paket erstellen, mit der **VSIX-Projekt** Vorlage in Visual Studio, oder Sie können ein VSIX-Paket manuell erstellen.  
  
## <a name="using-vsix-projects-to-create-vsix-packages"></a>VSIX-Pakete erstellen mithilfe von VSIX-Projekte  
 Sie können die **VSIX-Projekt** Vorlage, die von der Visual Studio-SDK zum Erstellen von VSIX-Pakete, für die SharePoint-tools-Erweiterungen bereitgestellt. Mithilfe eines VSIX-Projekts bietet mehrere Vorteile, über das manuelle Erstellen eines VSIX-Pakets:  
  
-   Wenn Sie das Projekt erstellen, generiert Visual Studio automatisch das VSIX-Paket. Aufgaben wie das Hinzufügen der Bereitstellungsdateien zum Paket und die [Content_Types] .xml-Datei für das Paket erstellen, sind für Sie erledigt.  
  
-   Sie können konfigurieren, dass das VSIX-Projekt, um die Buildausgabe des Erweiterungsprojekts und andere Dateien, z. B. Projektvorlagen und Elementvorlagen in das VSIX-Paket einschließen.  
  
 Weitere Informationen zur Verwendung eines VSIX-Projekts finden Sie unter [VSIX-Projektvorlage](/visualstudio/extensibility/vsix-project-template).  
  
### <a name="organizing-your-projects"></a>Organisieren von Projekten  
 VSIX-Projekten generiert standardmäßig nur VSIX-Pakete, nicht-Assemblys. Aus diesem Grund Sie in der Regel keine SharePoint-Tools-Erweiterung in ein VSIX-Projekt implementieren. Im Allgemeinen arbeiten Sie mit mindestens zwei Projekte:  
  
-   Ein VSIX-Projekt.  
  
-   Ein Klassenbibliotheksprojekt, das die Erweiterung implementiert.  
  
 Sie können auch mit zusätzlichen Projekte für bestimmte Typen von Erweiterungen arbeiten:  
  
-   Ein Klassenbibliotheksprojekt, das alle SharePoint-Befehle implementiert, die von der Erweiterung verwendet werden. Eine exemplarische Vorgehensweise, die dieses Szenario veranschaulicht, finden Sie unter [Exemplarische Vorgehensweise: Erweitern von Server-Explorer zum Anzeigen von Webparts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
-   Ein Projekt oder Elementvorlage Projekt, das eine Projektvorlage oder Elementvorlage erstellt, wenn die Erweiterung einen neuen Typ von SharePoint-Projektelements definiert. Eine exemplarische Vorgehensweise, die dieses Szenario veranschaulicht, finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer Custom Action Project Item mit einer Elementvorlage, Teil 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).  
  
-   Ein Klassenbibliotheksprojekt, das einen benutzerdefinierten Assistenten für eine Projektvorlage oder Elementvorlage implementiert, wenn die Erweiterung eine Vorlage enthält. Eine exemplarische Vorgehensweise, die dieses Szenario veranschaulicht, finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer Custom Action Project Item mit einer Elementvorlage, Teil 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).  
  
 Wenn Sie alle Projekte in der gleichen Visual Studio-Projektmappe einschließen, können Sie die Datei "Source.Extension.vsixmanifest" im VSIX-Projekt, um die Buildausgabe der Klassenbibliotheksprojekte einzuschließen ändern.  
  
### <a name="editing-the-vsix-manifest"></a>Das VSIX-Manifest bearbeiten  
 Bearbeiten Sie die Datei "Source.Extension.vsixmanifest" im VSIX-Projekt, um die Einträge für alle Elemente einzuschließen, die in der Erweiterung enthalten sein sollen. Wenn Sie die Datei "Source.Extension.vsixmanifest" aus dem Kontextmenü öffnen, wird die Datei in einem Designer, der eine Benutzeroberfläche zum Bearbeiten der XML-Codes in der Datei enthält. Weitere Informationen finden Sie unter [VSIX-Manifest-Designer](/visualstudio/extensibility/vsix-manifest-designer).  
  
 Sie müssen die Einträge in die Datei "Source.Extension.vsixmanifest" für die folgenden Elemente hinzufügen:  
  
-   Der Erweiterungsassembly.  
  
-   Die Assembly, die keine SharePoint-Befehle implementiert, die von der Erweiterung verwendet werden.  
  
-   Alle Projektvorlagen oder Elementvorlagen, die der Erweiterung zugeordnet sind.  
  
-   Ein benutzerdefinierter Assistent für eine Vorlage, die die Erweiterung zugeordnet ist.  
  
 Die folgenden Verfahren beschrieben, wie die vsixmanifest-Datei für jedes dieser Elemente Einträge hinzugefügt.  
  
##### <a name="to-include-the-extension-assembly"></a>Die Erweiterungsassembly einschließen  
  
1.  Klicken Sie im VSIX-Projekt, öffnen Sie das Kontextmenü für die Datei "Source.Extension.vsixmanifest", und wählen Sie dann **öffnen**.  
  
     Die Datei wird im Designer geöffnet.  
  
2.  Auf der **Bestand** Registerkarte im Editor wählen Sie die **neu** Schaltfläche.  
  
     Die **neue Anlage hinzufügen** Dialogfeld wird geöffnet.  
  
3.  In der **Typ** wählen **Microsoft.VisualStudio.MefComponent**.  
  
4.  In der **Quelle** aufzulisten, führen Sie einen der folgenden Schritte aus:  
  
    -   Wenn die Erweiterungsassembly in einem Projekt erstellt wird, ist in der gleichen Projektmappe wie das VSIX-Projekt, wählen Sie **ein Projekt in der aktuellen Projektmappe**. In der **Projekt** wählen Sie den Namen des Projekts.  
  
    -   Wenn die Erweiterungsassembly als Datei im Projekt enthalten ist, wählen Sie **Datei im Dateisystem**. In der **Pfad** aufzulisten, geben Sie den vollständigen Pfad zur Assemblydatei Erweiterung oder verwenden Sie die **Durchsuchen** Schaltfläche Suchen, und wählen die Assemblydatei.  
  
5.  Klicken Sie auf die Schaltfläche **OK** .  
  
##### <a name="to-include-a-sharepoint-command-assembly"></a>Die Assembly ein SharePoint-Befehl einschließen  
  
1.  Klicken Sie im VSIX-Projekt, öffnen Sie das Kontextmenü für die Datei "Source.Extension.vsixmanifest", und wählen Sie dann die **öffnen** Schaltfläche.  
  
     Die Datei wird im Designer geöffnet.  
  
2.  In der **Bestand** Abschnitt des Editors wählen Sie die **neu** Schaltfläche.  
  
     Die **neue Anlage hinzufügen** Dialogfeld wird geöffnet.  
  
3.  In der **Typ** geben **SharePoint.Commands.v4**.  
  
4.  In der **Quelle** aufzulisten, führen Sie einen der folgenden Schritte aus:  
  
    -   Wenn die Befehlsassembly aus einem Projekt erstellt wird, ist in der gleichen Projektmappe wie das VSIX-Projekt, wählen Sie **ein Projekt in der aktuellen Projektmappe**. In der **Projekt** wählen Sie den Namen des Projekts.  
  
    -   Wenn die Befehlsassembly als Datei im Projekt enthalten ist, wählen Sie **Datei im Dateisystem**. In der **Pfad** aufzulisten, geben Sie den vollständigen Pfad zur Assemblydatei Erweiterung oder verwenden Sie die **Durchsuchen** Schaltfläche Suchen, und wählen die Assemblydatei.  
  
5.  Klicken Sie auf die Schaltfläche **OK** .  
  
##### <a name="to-include-a-template-that-you-create"></a>Um eine Vorlage einschließen, die Sie erstellen  
  
1.  Klicken Sie im VSIX-Projekt, öffnen Sie das Kontextmenü für die Datei "Source.Extension.vsixmanifest", und wählen Sie dann die **öffnen** Schaltfläche.  
  
     Die Datei wird im Designer geöffnet.  
  
2.  In der **Bestand** Abschnitt des Editors wählen Sie die **neu** Schaltfläche.  
  
     Die **neue Anlage hinzufügen** Dialogfeld wird geöffnet.  
  
3.  In der **Typ** wählen **Microsoft.VisualStudio.ProjectTemplate** oder **Microsoft.VisualStudio.ItemTemplate**.  
  
4.  In der **Quelle** wählen **ein Projekt in der aktuellen Projektmappe**.  
  
5.  In der **Projekt** aus, wählen Sie den Namen des Projekts, und wählen Sie dann die **OK** Schaltfläche.  
  
6.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für das Projekt Projektvorlage oder Elementvorlage, und wählen Sie dann **Projekt entladen**.  
  
7.  Öffnen Sie erneut das Kontextmenü für den Projektknoten, und wählen Sie dann **bearbeiten***NameIhresVorlagenprojekts***csproj** oder **bearbeiten**  *NameIhresVorlagenprojekts***vbproj**.  
  
8.  Suchen Sie das folgende `VSTemplate`-Element in der Projektdatei.  
  
    ```  
    <VSTemplate Include="YourTemplateName.vstemplate">  
    ```  
  
9. Ersetzen Sie dieses Element durch das folgende XML.  
  
    ```  
    <VSTemplate Include="YourTemplateName.vstemplate">  
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>  
    </VSTemplate>  
    ```  
  
     Das `OutputSubPath`-Element gibt weitere Ordner in dem Pfad an, unter dem die Projektvorlage beim Erstellen des Projekts erstellt wird. Die hier angegebenen Ordnern wird sichergestellt, dass die Elementvorlage nur, wenn Kunden zur Verfügung der **neues Projekt hinzufügen** Dialogfeld erweitern Sie die **SharePoint** Knoten, und wählen Sie dann die **2010**  Knoten.  
  
10. Speichern und schließen Sie die Datei.  
  
11. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für das Projekt Projektvorlage oder Elementvorlage, und wählen Sie dann **Projekt erneut laden**.  
  
##### <a name="to-include-a-template-that-you-create-manually"></a>Um eine Vorlage einschließen, die Sie manuell erstellen  
  
1.  Fügen Sie einen neuen Ordner im VSIX-Projekt das Projekt, um die Vorlage enthält.  
  
2.  In diesem neuen Ordner erstellen Sie die folgenden Unterordner, und fügen Sie dann die Vorlagendatei (.zip), um die *Gebietsschema-ID* Ordner.  
  
     *YourTemplateFolder*  
  
     **SharePoint**  
  
     **SharePoint14**  
  
     *Die Gebietsschema-ID*  
  
     *YourTemplateName*ZIP  
  
     Angenommen, Sie haben eine Elementvorlage, die mit dem Namen ContosoCustomAction.zip, die das Gebietsschema Englisch (Vereinigte Staaten) unterstützt, möglicherweise der vollständige Pfad ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip sein.  
  
3.  In **Projektmappen-Explorer**, wählen Sie die Vorlagendatei (*YourTemplateName*.zip).  
  
4.  In der **Eigenschaften** legen die **Buildvorgang** Eigenschaft **Content**.  
  
5.  Öffnen Sie das Kontextmenü für die Datei "Source.Extension.vsixmanifest", und wählen Sie dann **öffnen**.  
  
     Die Datei wird im Designer geöffnet.  
  
6.  In der **Bestand** Abschnitt des Editors wählen Sie die **neu** Schaltfläche.  
  
     Die **neue Anlage hinzufügen** Dialogfeld wird geöffnet.  
  
7.  In der **Typ** wählen **Microsoft.VisualStudio.ItemTemplate** oder **Microsoft.VisualStudio.ProjectTemplate**.  
  
8.  In der **Quelle** wählen **Datei im Dateisystem**.  
  
9. In der **Pfad** Feld, geben Sie den vollständigen Pfad zu der Assembly (z. B. **ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip**, oder verwenden Sie die **Durchsuchen**Schaltfläche Suchen, und wählen die Assembly, und wählen Sie dann die **OK** Schaltfläche.  
  
##### <a name="to-include-a-wizard-for-a-project-template-or-item-template"></a>Um einen Assistenten für eine Projektvorlage oder Elementvorlage einzuschließen.  
  
1.  Klicken Sie im VSIX-Projekt, öffnen Sie das Kontextmenü für die Datei "Source.Extension.vsixmanifest", und wählen Sie dann **öffnen**.  
  
     Die Datei wird im Designer geöffnet.  
  
2.  In der **Bestand** Abschnitt des Editors wählen Sie die **neu** Schaltfläche.  
  
     Die **neue Anlage hinzufügen** Dialogfeld wird geöffnet.  
  
3.  In der **Typ** wählen **Microsoft.VisualStudio.Assembly**.  
  
4.  In der **Quelle** aufzulisten, führen Sie einen der folgenden Schritte aus:  
  
    -   Wenn die Assistenten-Assembly aus einem Projekt erstellt wird, ist in der gleichen Projektmappe wie das VSIX-Projekt, wählen Sie **ein Projekt in der aktuellen Projektmappe**. In der **Projekt** wählen Sie den Namen des Projekts.  
  
    -   Wenn die Assistenten-Assembly als Datei im Projekt enthalten ist, wählen Sie **Datei im Dateisystem**. In der **Pfad** Feld, geben Sie den vollständigen Pfad zur Assemblydatei oder verwenden Sie die **Durchsuchen** Schaltfläche Suchen, und wählen die Assembly.  
  
5.  Klicken Sie auf die Schaltfläche **OK** .  
  
### <a name="related-walkthroughs"></a>Verwandte Exemplarische Vorgehensweisen  
 Die folgende Tabelle enthält die exemplarischen Vorgehensweisen, die veranschaulichen, wie ein VSIX-Projekt zu verwenden, um verschiedene Typen von SharePoint-Tools-Erweiterungen bereitzustellen.  
  
|Erweiterungstyp|Verwandte Exemplarische Vorgehensweisen|  
|--------------------|--------------------------|  
|Eine Erweiterung, die nur die Erweiterungsassembly enthält.|[Exemplarische Vorgehensweise: Erweitern eines SharePoint-Projektelementtyps](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)<br /><br /> [Exemplarische Vorgehensweise: Erstellen einer SharePoint-Projekterweiterung](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)<br /><br /> [Exemplarische Vorgehensweise: Aufrufe in das SharePoint-Clientobjektmodell innerhalb einer Server-Explorererweiterung](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)|  
|Eine Erweiterung, die SharePoint-Befehle enthält.|[Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Bereitstellungsschritts für SharePoint-Projekte](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)<br /><br /> [Exemplarische Vorgehensweise: Erweitern des Server-Explorers für die Anzeige von Webparts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)<br /><br /> [Exemplarische Vorgehensweise: Erstellen eines Projektelements „Websitespalte“ mit einer Projektvorlage, Teil 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|  
|Eine Erweiterung, die Visual Studio-Vorlage enthält.|[Exemplarische Vorgehensweise: Erstellen eines Projektelements „Benutzerdefinierte Aktion“ mit einer Elementvorlage, Teil 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)<br /><br /> [Exemplarische Vorgehensweise: Erstellen eines Projektelements „Websitespalte“ mit einer Projektvorlage, Teil 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)|  
|Eine Erweiterung, die Vorlagen-Assistenten enthält|[Exemplarische Vorgehensweise: Erstellen eines Projektelements „Benutzerdefinierte Aktion“ mit einer Elementvorlage, Teil 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)<br /><br /> [Exemplarische Vorgehensweise: Erstellen eines Projektelements „Websitespalte“ mit einer Projektvorlage, Teil 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|  
  
## <a name="creating-vsix-packages-manually"></a>Manuelles Erstellen von VSIX-Pakete  
 Wenn Sie das VSIX-Paket für die SharePoint-Tools-Erweiterung manuell erstellen möchten, führen Sie die folgenden Schritte aus:  
  
1.  Erstellen Sie die Datei "Extension.vsixmanifest" und der [Content_Types] .xml-Datei in einen neuen Ordner ein. Weitere Informationen finden Sie unter [Aufbau eines VSIX-Pakets](/visualstudio/extensibility/anatomy-of-a-vsix-package).  
  
2.  In Windows-Explorer mit der rechten Maustaste in des Ordners, der die zwei XML-Dateien enthält, klicken Sie auf Senden an und klicken Sie dann auf komprimierten (gezippten) Ordner. Benennen Sie die resultierende ZIP-Datei in Filename.vsix, wobei Dateiname den Namen der verteilbaren Datei ist, die das Paket installiert wird.  
  
3.  Fügen Sie Ihrer Erweiterungsassembly im VSIX-Paket hinzu. Wenn die Erweiterung einen SharePoint-Befehl einschließt, können auch fügen Sie die Assembly hinzu, die den SharePoint-Befehl für das VSIX-Paket.  
  
4.  Ändern Sie die Datei "Extension.vsixmanifest":  
  
    -   Hinzufügen einer `Microsoft.VisualStudio.MefComponent` Element unter den `Assets` -Element, und legen den Wert des neuen Elements auf den relativen Pfad der Assembly, die die Erweiterung im VSIX-Paket implementiert. Weitere Informationen finden Sie unter [MEFComponent-Element (VSX-Schema)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
    -   Wenn die Erweiterung einen SharePoint-Befehl, die für SharePoint das Serverobjektmodell aufruft einschließt, fügen Sie eine `Microsoft.VisualStudio.Assembly` Element unter den `Assets` Element. Legen Sie den Wert des neuen Elements auf den relativen Pfad der Assembly, die den SharePoint-Befehl im VSIX-Paket implementiert. Weitere Informationen finden Sie unter [Asset-Element (VSX-Schema)](http://msdn.microsoft.com/en-us/9fcfc098-edc7-484b-9d4c-acd17829d737).  
  
    -   Wenn die Erweiterung einer Projektvorlage oder Elementvorlage enthält, fügen Sie eine `ProjectTemplate` oder `ItemTemplate` Element unter den `Assets` Element. Legen Sie den Wert des neuen Elements auf den relativen Pfad des Ordners, der die Vorlage im VSIX-Paket enthält. Weitere Informationen finden Sie unter [ProjectTemplate-Element (VSX-Schema)](http://msdn.microsoft.com/en-us/87add64c-9dcd-495f-8815-209dab182cb1) und [ItemTemplate-Element (VSX-Schema)](http://msdn.microsoft.com/en-us/1d489e54-c1c5-4f96-a510-6c2640867ff0).  
  
    -   Wenn die Erweiterung einen benutzerdefinierten Assistenten für eine Projektvorlage oder Elementvorlage enthält, fügen Sie ein `Assembly` Element unter den `Assets` Element. Legen Sie den Wert des neuen Elements auf den relativen Pfad der Assembly im VSIX-Paket, und legen Sie dann die `AssemblyName` -Attribut auf den vollständigen Assemblynamen (einschließlich der Version, Kultur und öffentliches Schlüsseltoken). Weitere Informationen finden Sie unter [Abhängigkeitselement (VSX-Schema)](http://msdn.microsoft.com/en-us/1f63f60a-98ad-48ec-8e44-4eba383d3e37).  
  
### <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt den Inhalt einer Datei "Extension.vsixmanifest" für eine SharePoint-Tools-Erweiterung. Die Erweiterung wird in einer Assembly implementiert, mit dem Namen Contoso.ProjectExtension.dll. Die Erweiterung enthält eine SharePoint-Befehl-Assembly mit dem Namen Contoso.ExtensionCommands.dll sowie eine Elementvorlage in einem Ordner mit dem Namen **ItemTemplates** im VSIX-Paket. In diesem Beispiel wird davon ausgegangen, dass beide Assemblys im gleichen Ordner wie die Datei "Extension.vsixmanifest" im VSIX-Paket sind.  
  
```  
<PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011">  
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
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern des SharePoint-Projektsystems](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Erweitern des SharePoint-Verbindungsknotens im Server-Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Aufrufe in die SharePoint-Objektmodelle](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Debuggen von Erweiterungen für die SharePoint-Tools in Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  