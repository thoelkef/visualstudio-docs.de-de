---
title: Bereitstellen von Erweiterungen für SharePoint-Tools in Visual Studio | Microsoft-Dokumentation
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying extensions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 53e36d993e72da759c87e7d2d2f908818b3d9024
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60068547"
---
# <a name="deploy-extensions-for-the-sharepoint-tools-in-visual-studio"></a>Bereitstellen von Erweiterungen für SharePoint-Tools in Visual Studio

Zum Bereitstellen einer SharePoint-Tools-Erweiterungs erstellen Sie eine [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] -Erweiterung (VSIX)-Paket mit der Erweiterungsassembly und alle anderen Dateien, die Sie mit der Erweiterung verteilen möchten. Ein VSIX-Paket ist eine komprimierte Datei, die den Open Packaging Conventions (OPC) Standard folgt. VSIX-Paketen haben die *VSIX* Erweiterung.

Nachdem Sie ein VSIX-Paket erstellt haben, können andere Benutzer die VSIX-Datei, um Ihre Erweiterung zu installieren ausführen. Wenn ein Benutzer die Erweiterung installiert wird, werden alle Dateien im Ordner %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0\Extensions installiert. Um die Erweiterung bereitzustellen, können Sie das VSIX-Paket zum Hochladen der [Visual Studio Marketplace](https://marketplace.visualstudio.com/) -Website, oder Sie können verteilen Sie das Paket für Ihre Kunden andere Weise, wie z. B. das Paket auf einer Netzwerkfreigabe oder einige andere Web-hosting Website.

Weitere Informationen zum Erstellen von VSIX-Pakete und sie zum Bereitstellen der [Visual Studio Marketplace](https://marketplace.visualstudio.com/), finden Sie unter [Auslieferung von Visual Studio-Erweiterungen](../extensibility/shipping-visual-studio-extensions.md).

 Sie können ein VSIX-Paket erstellen, mit der **VSIX-Projekt** Vorlage in Visual Studio, oder Sie können manuell ein VSIX-Paket erstellen.

## <a name="use-vsix-projects-to-create-vsix-packages"></a>Verwenden Sie die VSIX-Projekte zum Erstellen von VSIX-Paketen

Sie können die **VSIX-Projekt** Vorlage, die von Visual Studio-SDK zum VSIX-Pakete zu erstellen, für die SharePoint-tools-Erweiterungen bereitgestellt. Mithilfe eines VSIX-Projekts bietet mehrere Vorteile, über ein VSIX-Paket manuell zu erstellen:

- Visual Studio generiert automatisch das VSIX-Paket aus, wenn Sie das Projekt erstellen. Aufgaben wie dem Paket die Bereitstellungsdateien hinzufügen und das Erstellen der [Content_Types] .xml-Datei für das Paket sind für Sie erledigt.

- Sie können konfigurieren, dass das VSIX-Projekt, um die Buildausgabe des Erweiterungsprojekts und andere Dateien, z. B. Projektvorlagen und Elementvorlagen in VSIX-Paket einschließen.

Weitere Informationen zur Verwendung eines VSIX-Projekts finden Sie unter [VSIX-Projektvorlage](../extensibility/vsix-project-template.md).

### <a name="organize-your-projects"></a>Organisieren Sie Ihre Projekte

Standardmäßig generiert die VSIX-Projekte nur VSIX-Pakete, nicht Assemblys. Aus diesem Grund wird in der Regel keine SharePoint-Tools-Erweiterung in einer VSIX-Projekt implementiert. Im Allgemeinen arbeiten Sie mit mindestens zwei Projekte:

- Ein VSIX-Projekt.

- Ein Klassenbibliotheksprojekt, das die Erweiterung implementiert.

Sie können auch mit zusätzliche Projekte für bestimmte Typen von Erweiterungen arbeiten:

- Ein Klassenbibliotheksprojekt, das alle SharePoint-Befehle implementiert werden, die durch die Erweiterung verwendet werden. Eine exemplarische Vorgehensweise, die dieses Szenario veranschaulicht, finden Sie unter [Exemplarische Vorgehensweise: Erweitern Sie Server-Explorer, um die Anzeige von Webparts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

- Eine Projektvorlage oder Elementvorlage-Projekt, das eine Item-Vorlage oder die Projektvorlage erstellt werden, wenn die Erweiterung eine neue Art von SharePoint-Projektelements definiert. Eine exemplarische Vorgehensweise, die dieses Szenario veranschaulicht, finden Sie unter [Exemplarische Vorgehensweise: Erstellen ein Projektelements benutzerdefinierte Aktion mit einer Elementvorlage, Teil 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).

- Ein Klassenbibliotheksprojekt, das ein benutzerdefiniertes Assistenten für eine Item-Vorlage oder die Projektvorlage, implementiert wird, wenn die Erweiterung eine Vorlage enthält. Eine exemplarische Vorgehensweise, die dieses Szenario veranschaulicht, finden Sie unter [Exemplarische Vorgehensweise: Erstellen ein Projektelements benutzerdefinierte Aktion mit einer Elementvorlage, Teil 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).

Wenn Sie alle Projekte in der gleichen Visual Studio-Projektmappe einschließen, können Sie die Datei source.extension.vsixmanifest im VSIX-Projekts an die Buildausgabe der Klassenbibliotheksprojekte ändern.

### <a name="edit-the-vsix-manifest"></a>Das VSIX-Manifest bearbeiten

Sie müssen die Datei source.extension.vsixmanifest im VSIX-Projekt, um Einträge für alle Elemente einzuschließen, die Sie in der Erweiterung verwenden möchten, bearbeiten. Wenn Sie die Datei "Source.Extension.vsixmanifest" aus dem Kontextmenü öffnen, wird die Datei in einem Designer, der eine Benutzeroberfläche bereitstellt, für die Bearbeitung des XML-Code in der Datei angezeigt. Weitere Informationen finden Sie unter [VSIX-Manifest-Designer](../extensibility/vsix-manifest-designer.md).

Sie müssen die Einträge in die Datei "Source.Extension.vsixmanifest" für die folgenden Elemente hinzufügen:

- Der Erweiterungsassembly.

- Die Assembly, die keine SharePoint-Befehle implementiert werden, die durch die Erweiterung verwendet werden.

- Alle Projektvorlagen oder Elementvorlagen, die mit der Erweiterung zugeordnet sind.

- Ein benutzerdefinierter Assistent für eine Vorlage, die Ihre Erweiterung zugeordnet ist.

Die folgenden Verfahren wird beschrieben, wie Einträge in die vsixmanifest-Datei für jedes dieser Elemente hinzufügen.

#### <a name="to-include-the-extension-assembly"></a>Die Erweiterungsassembly einschließen

1. Klicken Sie im VSIX-Projekt, öffnen Sie das Kontextmenü für die Datei "Source.Extension.vsixmanifest", und wählen Sie dann **öffnen**.

     Die Datei wird im Designer geöffnet.

2. Auf der **Assets** Registerkarte des Editors wählen Sie die **neu** Schaltfläche.

     Die **neue Anlage hinzufügen** Dialogfeld wird geöffnet.

3. In der **Typ** wählen **Microsoft.VisualStudio.MefComponent**.

4. In der **Quelle** aufzulisten, führen Sie eine der folgenden Schritte aus:

    - Wenn die Erweiterungsassembly in einem Projekt erstellt wird, in der gleichen Projektmappe wie das VSIX-Projekt ist, wählen Sie **ein Projekt in der aktuellen Projektmappe**. In der **Projekt** Liste, wählen Sie den Namen des Projekts.

    - Wenn die Erweiterungsassembly als eine Datei in Ihrem Projekt enthalten ist, wählen Sie **Datei im Dateisystem**. In der **Pfad** aufzulisten, geben Sie den vollständigen Pfad zur Assemblydatei Erweiterung oder verwenden Sie die **Durchsuchen** zu suchen, und wählen Sie die Assemblydatei.

5. Klicken Sie auf die Schaltfläche **OK** .

#### <a name="to-include-a-sharepoint-command-assembly"></a>Eine SharePoint-Befehl Assembly

1. Klicken Sie im VSIX-Projekt, öffnen Sie das Kontextmenü für die Datei "Source.Extension.vsixmanifest", und wählen Sie dann die **öffnen** Schaltfläche.

     Die Datei wird im Designer geöffnet.

2. In der **Assets** Abschnitt wählen Sie im Editor die **neu** Schaltfläche.

     Die **neue Anlage hinzufügen** Dialogfeld wird geöffnet.

3. In der **Typ** geben **SharePoint.Commands.v4**.

4. In der **Quelle** aufzulisten, führen Sie eine der folgenden Schritte aus:

    - Wenn die Befehlsassembly aus einem Projekt erstellt wird, in der gleichen Projektmappe wie das VSIX-Projekt ist, wählen Sie **ein Projekt in der aktuellen Projektmappe**. In der **Projekt** Liste, wählen Sie den Namen des Projekts.

    - Wenn die Befehlsassembly als eine Datei in Ihrem Projekt enthalten ist, wählen Sie **Datei im Dateisystem**. In der **Pfad** aufzulisten, geben Sie den vollständigen Pfad zur Assemblydatei Erweiterung oder verwenden Sie die **Durchsuchen** zu suchen, und wählen Sie die Assemblydatei.

5. Klicken Sie auf die Schaltfläche **OK** .

#### <a name="to-include-a-template-that-you-create"></a>Um eine Vorlage enthalten, die Sie erstellen

1. Klicken Sie im VSIX-Projekt, öffnen Sie das Kontextmenü für die Datei "Source.Extension.vsixmanifest", und wählen Sie dann die **öffnen** Schaltfläche.

     Die Datei wird im Designer geöffnet.

2. In der **Assets** Abschnitt wählen Sie im Editor die **neu** Schaltfläche.

     Die **neue Anlage hinzufügen** Dialogfeld wird geöffnet.

3. In der **Typ** wählen **Microsoft.VisualStudio.ProjectTemplate** oder **Microsoft.VisualStudio.ItemTemplate**.

4. In der **Quelle** wählen **ein Projekt in der aktuellen Projektmappe**.

5. In der **Projekt** aus, wählen Sie den Namen des Projekts, und wählen Sie dann die **OK** Schaltfläche.

6. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für Ihre Projektvorlage oder Elementvorlage-Projekt, und wählen Sie dann **Projekt entladen**.

7. Öffnen Sie erneut das Kontextmenü für den Projektknoten, und wählen Sie dann **bearbeiten**_NameIhresVorlagenprojekts_**csproj** oder **bearbeiten**  _NameIhresVorlagenprojekts_**vbproj**.

8. Suchen Sie das folgende `VSTemplate`-Element in der Projektdatei.

    ```xml
    <VSTemplate Include="YourTemplateName.vstemplate">
    ```

9. Ersetzen Sie dieses Element durch das folgende XML.

    ```xml
    <VSTemplate Include="YourTemplateName.vstemplate">
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>
    </VSTemplate>
    ```

     Das `OutputSubPath`-Element gibt weitere Ordner in dem Pfad an, unter dem die Projektvorlage beim Erstellen des Projekts erstellt wird. Hier angegebenen Ordnern wird sichergestellt, dass die Item-Vorlage verfügbar sind, nur, wenn Kunden die **neues Projekt hinzufügen** Dialogfeld erweitern Sie die **SharePoint** Knoten, und wählen Sie dann die **2010**  Knoten.

10. Speichern und schließen Sie die Datei.

11. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für das Projekt Projektvorlage oder Elementvorlage, und wählen Sie dann **Projekt erneut laden**.

#### <a name="to-include-a-template-that-you-create-manually"></a>Um eine Vorlage enthalten, die Sie manuell erstellen

1. Fügen Sie einen neuen Ordner im VSIX-Projekt dem Projekt die Vorlage enthält.

2. Unter diesen neuen Ordner, die folgenden Unterordner erstellen und dann die Vorlagendatei (.zip) zum Hinzufügen der *Gebietsschema-ID* Ordner.

     *YourTemplateFolder*

     **SharePoint**

     **SharePoint14**

     *Die Gebietsschema-ID*

     *YourTemplateName*.zip

     Kann z. B., wenn Sie eine Item-Vorlage, die mit dem Namen ContosoCustomAction.zip, die das Gebietsschema Englisch (Vereinigte Staaten) unterstützt haben, der vollständige Pfad *ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip*.

3. In **Projektmappen-Explorer**, wählen Sie die Vorlagendatei (*YourTemplateName*ZIP).

4. In der **Eigenschaften** legen die **Buildvorgang** Eigenschaft **Content**.

5. Öffnen Sie das Kontextmenü für die Datei "Source.Extension.vsixmanifest", und wählen Sie dann **öffnen**.

     Die Datei wird im Designer geöffnet.

6. In der **Assets** Abschnitt wählen Sie im Editor die **neu** Schaltfläche.

     Die **neue Anlage hinzufügen** Dialogfeld wird geöffnet.

7. In der **Typ** wählen **Microsoft.VisualStudio.ItemTemplate** oder **Microsoft.VisualStudio.ProjectTemplate**.

8. In der **Quelle** wählen **Datei im Dateisystem**.

9. In der **Pfad** Geben Sie den vollständigen Pfad zur Assembly (z. B. *ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip*, oder verwenden Sie die **Durchsuchen**Schaltfläche, um zu ermitteln, und wählen Sie die Assembly, und wählen Sie dann die **OK** Schaltfläche.

#### <a name="to-include-a-wizard-for-a-project-template-or-item-template"></a>Um einen Assistenten für eine Projektvorlage oder Elementvorlage einzuschließen.

1. Klicken Sie im VSIX-Projekt, öffnen Sie das Kontextmenü für die Datei "Source.Extension.vsixmanifest", und wählen Sie dann **öffnen**.

     Die Datei wird im Designer geöffnet.

2. In der **Assets** Abschnitt wählen Sie im Editor die **neu** Schaltfläche.

     Die **neue Anlage hinzufügen** Dialogfeld wird geöffnet.

3. In der **Typ** wählen **Microsoft.VisualStudio.Assembly**.

4. In der **Quelle** aufzulisten, führen Sie eine der folgenden Schritte aus:

    - Wenn Sie die Assistenten-Assembly aus einem Projekt erstellt wird, in der gleichen Projektmappe wie das VSIX-Projekt ist, wählen Sie **ein Projekt in der aktuellen Projektmappe**. In der **Projekt** Liste, wählen Sie den Namen des Projekts.

    - Wenn Sie die Assistenten-Assembly als eine Datei in Ihrem Projekt enthalten ist, wählen Sie **Datei im Dateisystem**. In der **Pfad** Feld, geben Sie den vollständigen Pfad zur Assemblydatei oder verwenden Sie die **Durchsuchen** zu suchen und wählen die Assembly.

5. Klicken Sie auf die Schaltfläche **OK** .

### <a name="related-walkthroughs"></a>Exemplarischen Vorgehensweisen

Die folgende Tabelle enthält exemplarische Vorgehensweisen, die veranschaulichen, wie Sie ein VSIX-Projekt zu verwenden, um verschiedene Arten von SharePoint-Tools-Erweiterungen bereitzustellen.

|Erweiterungstyp|Exemplarischen Vorgehensweisen|
|--------------------|--------------------------|
|Eine Erweiterung, die nur die Erweiterungsassembly enthält.|[Exemplarische Vorgehensweise: Erweitern eines SharePoint-Projektelementtyps](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)<br /><br /> [Exemplarische Vorgehensweise: Erstellen einer SharePoint-projekterweiterung](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)<br /><br /> [Exemplarische Vorgehensweise: Rufen Sie in der SharePoint-Clientobjektmodell innerhalb einer Server-explorererweiterung](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)|
|Eine Erweiterung, die SharePoint-Befehle enthält.|[Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Bereitstellungsschritts für SharePoint-Projekte](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)<br /><br /> [Exemplarische Vorgehensweise: Erweitern Sie Server-Explorer, um die Anzeige von Webparts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)<br /><br /> [Exemplarische Vorgehensweise: Erstellen eines Projektelements Spalte mit einer Projektvorlage, Teil 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|
|Eine Erweiterung, die Visual Studio-Vorlage enthält.|[Exemplarische Vorgehensweise: Erstellen eines Projektelements benutzerdefinierte Aktion mit einer Elementvorlage, Teil 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)<br /><br /> [Exemplarische Vorgehensweise: Erstellen eines Projektelements Spalte mit einer Projektvorlage, Teil 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)|
|Eine Erweiterung, die Vorlagen-Assistenten enthält|[Exemplarische Vorgehensweise: Erstellen eines Projektelements benutzerdefinierte Aktion mit einer Elementvorlage, Teil 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)<br /><br /> [Exemplarische Vorgehensweise: Erstellen eines Projektelements Spalte mit einer Projektvorlage, Teil 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|

## <a name="create-vsix-packages-manually"></a>Manuelles Erstellen von VSIX-Paketen

Wenn Sie das VSIX-Paket für die SharePoint-Tools-Erweiterung manuell erstellen möchten, führen Sie die folgenden Schritte aus:

1. Erstellen Sie die Datei "extension.vsixmanifest" und der [Content_Types] .xml-Datei in einem neuen Ordner ein. Weitere Informationen finden Sie unter [Anatomie eines VSIX-Pakets](../extensibility/anatomy-of-a-vsix-package.md).

2. Im Windows-Explorer mit der rechten Maustaste in des Ordners, der die zwei XML-Dateien enthält, klicken Sie auf Senden an und klicken Sie dann auf komprimierten (gezippten) Ordner. Benennen Sie die resultierende ZIP-Datei, in Filename.vsix, wobei der Dateiname der Name der verteilbaren Datei ist, die das Paket installiert wird.

3. Fügen Sie die Erweiterungsassembly im VSIX-Paket hinzu. Wenn die Erweiterung einen SharePoint-Befehl enthält, sollten Sie die fügen Sie Assembly hinzu, die die SharePoint-Befehl aus, um das VSIX-Paket implementiert auch.

4. Ändern Sie die Datei "extension.vsixmanifest":

    - Hinzufügen einer `Microsoft.VisualStudio.MefComponent` Element unter den `Assets` Element, und legen Sie dann den Wert des neuen Elements auf den relativen Pfad der Assembly, die die Erweiterung im VSIX-Paket implementiert. Weitere Informationen finden Sie unter [MEFComponent-Element (VSX-Schema)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

    - Wenn die Erweiterung einen SharePoint-Befehl, die das Serverobjektmodell für SharePoint enthält aufruft, fügen Sie eine `Microsoft.VisualStudio.Assembly` Element unter der `Assets` Element. Legen Sie den Wert des neuen Elements, auf den relativen Pfad der Assembly, die SharePoint-Befehls im VSIX-Paket implementiert. Weitere Informationen finden Sie unter [Asset-Element (VSX-Schema)](https://msdn.microsoft.com/9fcfc098-edc7-484b-9d4c-acd17829d737).

    - Wenn die Erweiterung einer Projektvorlage oder Elementvorlage enthält, fügen Sie eine `ProjectTemplate` oder `ItemTemplate` Element unter den `Assets` Element. Legen Sie den Wert des neuen Elements, auf den relativen Pfad des Ordners, der die Vorlage im VSIX-Paket enthält. Weitere Informationen finden Sie unter ["ProjectTemplate"-Element (VSX-Schema)](/previous-versions/visualstudio/visual-studio-2010/dd393735\(v\=vs.100\)) und [ItemTemplate-Element (VSX-Schema)](/previous-versions/visualstudio/visual-studio-2010/dd393681\(v\=vs.100\)).

    - Wenn die Erweiterung ein benutzerdefiniertes Assistenten für eine Projektvorlage oder Elementvorlage enthält, fügen Sie eine `Assembly` Element unter den `Assets` Element. Legen Sie den Wert des neuen Elements auf den relativen Pfad der Assembly im VSIX-Paket, und legen Sie dann die `AssemblyName` -Attribut auf den vollständigen Assemblynamen (einschließlich Version, Kultur und öffentliches Schlüsseltoken). Weitere Informationen finden Sie unter [Abhängigkeitselement (VSX-Schema)](https://msdn.microsoft.com/1f63f60a-98ad-48ec-8e44-4eba383d3e37).

### <a name="example"></a>Beispiel

Das folgende Beispiel zeigt den Inhalt einer Datei "Extension.vsixmanifest" für eine SharePoint-Tools-Erweiterung. Die Erweiterung wird in einer Assembly implementiert, mit dem Namen Contoso.ProjectExtension.dll. Die Erweiterung enthält eine Assembly der SharePoint-Befehl mit dem Namen Contoso.ExtensionCommands.dll sowie eine Elementvorlage in einem Ordner mit dem Namen **"ItemTemplates"** im VSIX-Paket. In diesem Beispiel wird davon ausgegangen, dass beide Assemblys im gleichen Ordner wie die Datei "extension.vsixmanifest" im VSIX-Paket befinden.

```xml
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

- [Erweitern von SharePoint-Projektsystem](../sharepoint/extending-the-sharepoint-project-system.md)
- [Erweitern des SharePoint-Verbindungsknotens im Server-Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Rufen Sie in der SharePoint-Objektmodelle](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Debuggen von Erweiterungen für SharePoint-Tools in Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)
