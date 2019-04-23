---
title: 'Exemplarische Vorgehensweise: Erstellen eine benutzerdefinierte Aktion das Projektelement, mit einer Elementvorlage, Teil 1 | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, creating custom templates
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7397da630a5fd6f2c649d6f448627d7c77c55128
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60059122"
---
# <a name="walkthrough-create-a-custom-action-project-item-with-an-item-template-part-1"></a>Exemplarische Vorgehensweise: Erstellen eines Projektelements benutzerdefinierte Aktion mit einer Elementvorlage, Teil 1
  Sie können das SharePoint-Projektsystem in Visual Studio erweitern, indem Sie eigene Projektelementtypen erstellen. In dieser exemplarischen Vorgehensweise erstellen Sie ein Projektelement, die ein SharePoint-Projekt zum Erstellen einer benutzerdefinierten Aktion auf einer SharePoint-Website hinzugefügt werden können. Die benutzerdefinierte Aktion Fügt ein Menüelement der **Websiteaktionen** im Menü der SharePoint-Website.

 Diese exemplarische Vorgehensweise enthält die folgenden Aufgaben:

- Erstellen einer Visual Studio-Erweiterung, die einen neuen Typ von SharePoint-Projektelement für eine benutzerdefinierte Aktion definiert. Mit dem neuen Projektelementtyp werden mehrere benutzerdefinierte Funktionen implementiert:

  - Ein Kontextmenü, über das weitere auf das Projektelement bezogene Aufgaben ausgewählt werden können, z. B. für das Anzeigen eines Designers für die benutzerdefinierte Aktion in Visual Studio.

  - Code, der ausgeführt wird, wenn ein Entwickler bestimmte Eigenschaften des Projektelements oder des Projekts ändert, in dem es enthalten ist.

  - Ein benutzerdefiniertes Symbol, das neben dem Projektelement im **Projektmappen-Explorer**.

- Erstellen einer Visual Studio-Elementvorlage für das Projektelement.

- Erstellen eines Visual Studio-Erweiterungspakets (VSIX) zum Bereitstellen der Projektelementvorlage und der Erweiterungsassembly.

- Debuggen und Testen des Projektelements

  Dies ist eine eigenständige exemplarische Vorgehensweise. Nachdem Sie diese exemplarische Vorgehensweise abgeschlossen haben, können Sie das Projektelement erweitern, indem Sie der Elementvorlage einen Assistenten hinzufügen. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen ein Projektelements benutzerdefinierte Aktion mit einer Elementvorlage, Teil 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).

> [!NOTE]
>  Sie können ein Beispiel von [Github](https://github.com/SharePoint/PnP/tree/master/Samples/Workflow.Activities) , die zeigt, wie benutzerdefinierte Aktivitäten für einen Workflow zu erstellen.

## <a name="prerequisites"></a>Vorraussetzungen
 Zum Durchführen dieser exemplarischen Vorgehensweise werden auf dem Entwicklungscomputer die folgenden Komponenten benötigt:

- Unterstützte Editionen von Microsoft Windows, SharePoint und Visual Studio.

- Die [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. Diese exemplarische Vorgehensweise verwendet die **VSIX-Projekt** Vorlage in das SDK zum Erstellen eines VSIX-Pakets zum Bereitstellen des Projektelements. Weitere Informationen finden Sie unter [Erweitern der SharePoint-Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  Kenntnisse der folgenden Konzepte sind hilfreich, wenn auch für die Durchführung der exemplarischen Vorgehensweise nicht erforderlich:

- Benutzerdefinierte Aktionen in SharePoint. Weitere Informationen finden Sie unter [benutzerdefinierte Aktion](http://go.microsoft.com/fwlink/?LinkId=177800).

- Elementvorlagen in Visual Studio. Weitere Informationen finden Sie unter [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md).

## <a name="create-the-projects"></a>Erstellen Sie die Projekte
 Zum Abschließen dieser exemplarischen Vorgehensweise müssen Sie drei Projekte erstellen:

- Ein VSIX-Projekt. Von diesem Projekt wird das VSIX-Paket zum Bereitstellen des SharePoint-Projektelements erstellt.

- Ein Elementvorlagenprojekt. Von diesem Projekt wird eine Elementvorlage erstellt, mit der das SharePoint-Projektelement einem SharePoint-Projekt hinzugefügt werden kann.

- Ein Klassenbibliotheksprojekt. Dieses Projekt implementiert eine Visual Studio-Erweiterung, die das Verhalten des SharePoint-Projektelements definiert.

  Beginnen Sie mit der exemplarischen Vorgehensweise, indem Sie beide Projekte erstellen.

#### <a name="to-create-the-vsix-project"></a>So erstellen Sie das VSIX-Projekt

1. Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Klicken Sie in der Menüleiste auf **Datei** > **Neu** > **Projekt**.

3. In der Liste am oberen Rand der **neues Projekt** Dialogfeld Feld, stellen Sie sicher, dass **.NET Framework 4.5** ausgewählt ist.

4. In der **neues Projekt** Dialogfeld erweitern Sie die **Visual C#-** oder **Visual Basic** Knoten, und wählen Sie dann die **Erweiterbarkeit** Knoten.

    > [!NOTE]
    >  Die **Erweiterbarkeit** Knoten ist nur verfügbar, wenn Sie Visual Studio SDK installieren. Weitere Informationen finden Sie weiter oben in diesem Thema im Abschnitt zu den erforderlichen Komponenten.

5. Wählen Sie die **VSIX-Projekt** Vorlage.

6. In der **Namen** geben **"CustomActionProjectItem"**, und wählen Sie dann die **OK** Schaltfläche.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Fügt der **"CustomActionProjectItem"** Projekt **Projektmappen-Explorer**.

#### <a name="to-create-the-item-template-project"></a>So erstellen Sie das Elementvorlagenprojekt

1. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für den Projektmappenknoten, wählen **hinzufügen**, und wählen Sie dann **neues Projekt**.

2. In der Liste am oberen Rand der **neues Projekt** Dialogfeld Feld, stellen Sie sicher, dass **.NET Framework 4.5** ausgewählt ist.

3. In der **neues Projekt** Dialogfeld erweitern Sie die **Visual C#-** oder **Visual Basic** Knoten, und wählen Sie dann die **Erweiterbarkeit** Knoten.

4. Wählen Sie in der Liste der Projektvorlagen, die **C#-Elementvorlage** oder **Visual Basic-Elementvorlage** Vorlage.

5. In der **Namen** geben **ItemTemplate**, und wählen Sie dann die **OK** Schaltfläche.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Fügt der **ItemTemplate** Projekt der Projektmappe.

#### <a name="to-create-the-extension-project"></a>So erstellen Sie das Erweiterungsprojekt

1. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für den Projektmappenknoten, wählen **hinzufügen**, und wählen Sie dann **neues Projekt**.

2. In der Liste am oberen Rand der **neues Projekt** Dialogfeld Feld, stellen Sie sicher, dass **.NET Framework 4.5** ausgewählt ist.

3. In der **neues Projekt** Dialogfeld erweitern Sie die **Visual C#-** oder **Visual Basic** Knoten, wählen die **Windows** Knoten, und wählen Sie dann die  **Klassenbibliothek** Projektvorlage.

4. In der **Namen** geben **ProjectItemDefinition**, und wählen Sie dann die **OK** Schaltfläche.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Fügt der **ProjectItemDefinition** -Projekt zur Projektmappe und öffnet die Class1-Codedatei.

5. Löschen Sie die Class1-Codedatei aus dem Projekt.

## <a name="configure-the-extension-project"></a>Konfigurieren Sie das Erweiterungsprojekt
 Bevor Sie Code zum Erstellen des SharePoint-Projektelementtyps schreiben, müssen Sie dem Erweiterungsprojekt Codedateien und Assemblyverweise hinzufügen.

#### <a name="to-configure-the-project"></a>So konfigurieren Sie das Projekt

1. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **ProjectItemDefinition** Projekts **hinzufügen**, wählen Sie dann **neues Element**.

2. Wählen Sie in der Liste der Projektelemente, **Codedatei**.

3. In der **Namen** Geben Sie den Namen **CustomAction** mit der entsprechenden Dateierweiterung ein, und wählen Sie dann die **hinzufügen** Schaltfläche.

4. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **ProjectItemDefinition** Projekt, und wählen Sie dann **Verweis hinzufügen**.

5. In der **Verweis-Manager – ProjectItemDefinition** Dialogfeld auf die **Assemblys** Knoten, und wählen Sie dann die **Framework** Knoten.

6. Aktivieren Sie das Kontrollkästchen neben jeder der folgenden Assemblys:

    - System.ComponentModel.Composition

    - System.Windows.Forms

7. Wählen Sie die **Erweiterungen** Knoten, wählen Sie das Kontrollkästchen neben der Microsoft.VisualStudio.Sharepoint-Assembly aus, und wählen Sie dann die **OK** Schaltfläche.

## <a name="define-the-new-sharepoint-project-item-type"></a>Definieren Sie die neuen SharePoint-Projektelementtyp
 Erstellen Sie eine Klasse, die die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>-Schnittstelle implementiert, um das Verhalten des neuen Projektelementtyps zu definieren. Implementieren Sie diese Schnittstelle immer dann, wenn Sie einen neuen Projektelementtyp definieren möchten.

#### <a name="to-define-the-new-sharepoint-project-item-type"></a>So definieren Sie den neuen SharePoint-Projektelementtyp

1. Öffnen Sie im Projekt ProjectItemDefinition die CustomAction-Codedatei.

2. Ersetzen Sie den Code in dieser Datei durch den folgenden Code:

     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#1](../sharepoint/codesnippet/CSharp/customactionprojectitem/projectitemtypedefinition/customaction.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#1](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/projectitemdefinition/customaction.vb#1)]

## <a name="create-an-icon-for-the-project-item-in-solution-explorer"></a>Erstellen Sie ein Symbol für das Projektelement im Projektmappen-Explorer
 Wenn Sie ein benutzerdefiniertes SharePoint-Projektelement erstellen, können Sie dem Projektelement ein Bild (ein Symbol oder eine Bitmap) zuordnen. Dieses Bild wird angezeigt, klicken Sie neben dem Projektelement im **Projektmappen-Explorer**.

 In der folgenden Vorgehensweise erstellen Sie ein Symbol für das Projektelement und betten das Symbol in die Erweiterungsassembly ein. Auf dieses Symbol wird durch das <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute> der zuvor erstellten `CustomActionProjectItemTypeProvider`-Klasse verwiesen.

#### <a name="to-create-a-custom-icon-for-the-project-item"></a>So erstellen Sie ein benutzerdefiniertes Symbol für das Projektelement

1. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **ProjectItemDefinition** Projekts **hinzufügen**, und wählen Sie dann **neues Element...** .

2. Wählen Sie in der Liste der Projektelemente, die **Symboldatei** Element.

    > [!NOTE]
    >  In Visual Basic-Projekten müssen Sie auswählen der **allgemeine** Knoten zum Anzeigen der **Symboldatei** Element.

3. In der **Namen** geben **CustomAction_SolutionExplorer.ico**, und wählen Sie dann die **hinzufügen** Schaltfläche.

     Das Symbol "Neu" geöffnet, der **Bildbearbeitung**.

4. Bearbeiten Sie die 16x16-Version der Symboldatei so, dass sich das Symbol leicht von anderen unterscheiden lässt, und speichern Sie dann die Symboldatei.

5. In **Projektmappen-Explorer**, wählen Sie **CustomAction_SolutionExplorer.ico**.

6. In der **Eigenschaften** Fenster, wählen Sie den Pfeil neben der **Buildvorgang** Eigenschaft.

7. Wählen Sie in der angezeigten Liste **eingebettete Ressource**.

## <a name="checkpoint"></a>Checkpoint
 Ab diesem Punkt in der exemplarischen Vorgehensweise wurde der gesamte für das Projektelement benötigte Code in das Projekt eingefügt. Erstellen Sie das Projekt, um zu überprüfen, ob es fehlerfrei kompiliert wird.

#### <a name="to-build-your-project"></a>So erstellen Sie das Projekt

1. Öffnen Sie das Kontextmenü für die **ProjectItemDefinition** Projekt, und wählen **erstellen**.

## <a name="create-a-visual-studio-item-template"></a>Erstellen Sie eine Visual Studio-Elementvorlage
 Um Ihr Projektelement anderen Entwicklern zur Verfügung stellen zu können, müssen Sie eine Projektvorlage oder eine Elementvorlage erstellen. Mithilfe dieser Vorlagen können Entwickler in Visual Studio eine Instanz des Projekts erstellen, indem sie ein neues Projekt erstellen oder ein Element zu einem vorhandenen Projekt hinzufügen. Konfigurieren Sie für diese exemplarische Vorgehensweise das Projektelement mithilfe des Projekts ItemTemplate.

#### <a name="to-create-the-item-template"></a>So erstellen Sie die Elementvorlage

1. Löschen Sie die Class1-Codedatei aus dem ItemTemplate-Projekt.

2. Öffnen Sie im Projekt ItemTemplate die *ItemTemplate.vstemplate* Datei.

3. Ersetzen Sie den Inhalt der Datei durch das folgende XML, speichern Sie anschließend die Datei, und schließen Sie sie.

    > [!NOTE]
    >  Das folgende XML ist für eine Visual C#-Elementvorlage bestimmt. Wenn Sie eine Visual Basic-Elementvorlage erstellen, ersetzen Sie den Wert des `ProjectType`-Elements durch `VisualBasic`.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <VSTemplate Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">
      <TemplateData>
        <DefaultName>CustomAction</DefaultName>
        <Name>Custom Action</Name>
        <Description>SharePoint Custom Action by Contoso</Description>
        <ProjectType>CSharp</ProjectType>
        <SortOrder>1000</SortOrder>
        <Icon>ItemTemplate.ico</Icon>
        <ProvideDefaultName>true</ProvideDefaultName>
      </TemplateData>
      <TemplateContent>
        <ProjectItem ReplaceParameters="true" TargetFileName="$fileinputname$\Elements.xml">Elements.xml</ProjectItem>
        <ProjectItem ReplaceParameters="true" TargetFileName="$fileinputname$\SharePointProjectItem.spdata">CustomAction.spdata</ProjectItem>
      </TemplateContent>
    </VSTemplate>
    ```

     Diese Datei definiert den Inhalt und das Verhalten der Elementvorlage. Weitere Informationen zum Inhalt dieser Datei finden Sie unter [Visual Studio Template Schema Reference](/visualstudio/extensibility/visual-studio-template-schema-reference).

4. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **ItemTemplate** Projekts **hinzufügen**, und wählen Sie dann **neues Element**.

5. In der **neues Element hinzufügen** Dialogfeld auf die **Textdatei** Vorlage.

6. In der **Namen** geben **CustomAction.spdata**, und wählen Sie dann die **hinzufügen** Schaltfläche.

7. Hinzufügen der folgenden XML-Code der *CustomAction.spdata* -Datei, und speichern und schließen Sie die Datei.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <ProjectItem Type="Contoso.CustomAction" DefaultFile="Elements.xml"
     xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">
      <Files>
        <ProjectItemFile Source="Elements.xml" Target="$fileinputname$\" Type="ElementManifest" />
      </Files>
    </ProjectItem>
    ```

     Diese Datei enthält Informationen zu den Dateien, die im Projektelement enthalten sind. Das `Type`-Attribut des `ProjectItem`-Elements muss auf die gleiche Zeichenfolge festgelegt werden, die in der Projektelementdefinition (die <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>-Klasse, die Sie zuvor in dieser exemplarischen Vorgehensweise erstellt haben) an `CustomActionProjectItemTypeProvider` übergeben wird. Weitere Informationen über den Inhalt des *SPDATA* finden Sie unter [SharePoint-Projektelementschema](../sharepoint/sharepoint-project-item-schema-reference.md).

8. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **ItemTemplate** Projekts **hinzufügen**, und wählen Sie dann **neues Element**.

9. In der **neues Element hinzufügen** Dialogfeld auf die **XML-Datei** Vorlage.

10. In der **Namen** geben **"Elements.xml"**, und wählen Sie dann die **hinzufügen** Schaltfläche.

11. Ersetzen Sie den Inhalt von der *"Elements.xml"* -Datei mit den folgenden XML-Code, und speichern und schließen Sie die Datei.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <Elements Id="$guid8$" xmlns="http://schemas.microsoft.com/sharepoint/">
      <CustomAction Id="Replace this with a GUID or some other unique string"
                    GroupId="SiteActions"
                    Location="Microsoft.SharePoint.StandardMenu"
                    Sequence="1000"
                    Title="Replace this with your title"
                    Description="Replace this with your description" >
        <UrlAction Url="~site/Lists/Tasks/AllItems.aspx"/>
      </CustomAction>
    </Elements>
    ```

     Diese Datei definiert eine benutzerdefinierte Standardaktion, die auf ein Menüelement erstellt die **Websiteaktionen** im Menü der SharePoint-Website. Wenn ein Benutzer das Menüelement auswählt, wird die im `UrlAction`-Element angegebene URL im Webbrowser geöffnet. Weitere Informationen zu den XML-Elementen, die zum Definieren einer benutzerdefinierten Aktion können, finden Sie unter [benutzerdefinierten Aktionsdefinitionen](http://go.microsoft.com/fwlink/?LinkId=177801).

12. Öffnen Sie optional die *ItemTemplate.ico* Datei, und ändern diese, damit sie einen Entwurf aufweist, die Sie erkennen können. Dieses Symbol wird neben dem Projektelement im Anzeigen der **neues Element hinzufügen** Dialogfeld.

13. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **ItemTemplate** Projekt, und wählen Sie dann **Projekt entladen**.

14. Öffnen Sie das Kontextmenü für die **ItemTemplate** Projekt erneut, und wählen Sie dann **ItemTemplate.csproj bearbeiten** oder **ItemTemplate.vbproj bearbeiten**.

15. Suchen Sie das folgende `VSTemplate`-Element in der Projektdatei.

    ```xml
    <VSTemplate Include="ItemTemplate.vstemplate">
    ```

16. Ersetzen Sie dieses `VSTemplate`-Element durch das folgende XML, und speichern und schließen Sie dann die Datei.

    ```xml
    <VSTemplate Include="ItemTemplate.vstemplate">
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>
    </VSTemplate>
    ```

     Das `OutputSubPath`-Element gibt weitere Ordner in dem Pfad an, unter dem die Elementvorlage beim Erstellen des Projekts erstellt wird. Hier angegebenen Ordnern wird sichergestellt, dass die Item-Vorlage verfügbar sind, nur, wenn Kunden die **neues Element hinzufügen** Dialogfeld erweitern Sie die **SharePoint** Knoten, und wählen Sie dann die **2010**  Knoten.

17. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **ItemTemplate** Projekt, und wählen Sie dann **Projekt erneut laden**.

## <a name="create-a-vsix-package-to-deploy-the-project-item"></a>Erstellen Sie ein VSIX-Paket zum Bereitstellen des Projektelements
 Zum Bereitstellen der Erweiterung erstellen Sie anhand des VSIX-Projekts in der Lösung ein VSIX-Paket. Konfigurieren Sie zuerst das VSIX-Paket, indem Sie die im VSIX-Projekt enthaltene Datei "source.extension.vsixmanifest" ändern. Erstellen Sie anschließend das VSIX-Paket, indem Sie die Lösung erstellen.

#### <a name="to-configure-and-create-the-vsix-package"></a>So erstellen und konfigurieren Sie das VSIX-Paket

1. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **"Source.Extension.vsixmanifest"** -Datei im Projekt "CustomActionProjectItem", und wählen Sie dann **öffnen**.

     Die Datei wird von Visual Studio im Manifest-Editor geöffnet. Die Datei "source.extension.vsixmanifest" bildet die Grundlage für die Datei "extension.vsixmanifest", die für alle VSIX-Pakete erforderlich ist. Weitere Informationen zu dieser Datei finden Sie unter [Referenz zum VSIX-Erweiterungsschema 1.0](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).

2. In der **Produktname** geben **Custom Action Project Item**.

3. In der **Autor** geben **Contoso**.

4. In der **Beschreibung** geben **ein SharePoint-Projektelements, das eine benutzerdefinierte Aktion darstellt**.

5. Auf der **Assets** Registerkarte die **neu** Schaltfläche.

     Die **neue Anlage hinzufügen** Dialogfeld wird angezeigt.

6. In der **Typ** wählen **Microsoft.VisualStudio.ItemTemplate**.

    > [!NOTE]
    >  Dieser Wert entspricht dem `ItemTemplate`-Element in der Datei "extension.vsixmanifest". Dieses Element identifiziert den Unterordner im VSIX-Paket, der die Projektelementvorlage enthält. Weitere Informationen finden Sie unter [ItemTemplate-Element (VSX-Schema)](/previous-versions/visualstudio/visual-studio-2010/dd393681\(v\=vs.100\)).

7. In der **Quelle** wählen **ein Projekt in der aktuellen Projektmappe**.

8. In der **Projekt** wählen **ItemTemplate**, und wählen Sie dann die **OK** Schaltfläche.

9. In der **Assets** Registerkarte die **neu** erneut.

     Die **neue Anlage hinzufügen** Dialogfeld wird angezeigt.

10. In der **Typ** wählen **Microsoft.VisualStudio.MefComponent**.

    > [!NOTE]
    >  Dieser Wert entspricht dem `MefComponent`-Element in der Datei "extension.vsixmanifest". Von diesem Element wird der Name einer Erweiterungsassembly im VSIX-Paket angegeben. Weitere Informationen finden Sie unter [MEFComponent-Element (VSX-Schema)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

11. In der **Quelle** wählen **ein Projekt in der aktuellen Projektmappe**.

12. In der **Projekt** wählen **ProjectItemDefinition**.

13. Klicken Sie auf die Schaltfläche **OK** .

14. Wählen Sie auf der Menüleiste **erstellen** > **Projektmappe**, und klicken Sie dann stellen Sie sicher, dass das Projekt ohne Fehler kompiliert wird.

15. Überprüfen Sie, ob der Buildausgabeordner für das Projekt "CustomActionProjectItem" die Datei "CustomActionProjectItem.vsix" enthält.

     Standardmäßig ist der Buildausgabeordner der Ordner "\bin\Debug" in dem Ordner, der das Projekt "CustomActionProjectItem" enthält.

## <a name="test-the-project-item"></a>Das Projektelement testen
 Jetzt können Sie das Projektelement testen. Debuggen Sie die Projektmappe CustomActionProjectItem zunächst in der experimentellen Instanz von Visual Studio. Testen Sie anschließend die **benutzerdefinierte Aktion** -Projektelement in einem SharePoint-Projekt in der experimentellen Instanz von Visual Studio. Erstellen und führen Sie zum Schluss das SharePoint-Projekt aus, um sicherzustellen, dass die benutzerdefinierte Aktion ordnungsgemäß funktioniert.

#### <a name="to-start-debugging-the-solution"></a>So debuggen Sie die Projektmappe

1. Starten Sie Visual Studio erneut mit Administratoranmeldeinformationen, und öffnen Sie dann die Projektmappe "CustomActionProjectItem".

2. Öffnen Sie die CustomAction-Codedatei, und fügen Sie dann in der ersten Codezeile in der `InitializeType`-Methode einen Haltepunkt ein.

3. Wählen Sie die **F5** Schlüssel mit dem Debuggen beginnen.

     Die Erweiterung wird unter "%UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\Custom Action Project Item\1.0" installiert, und eine experimentelle Instanz von Visual Studio wird gestartet. Sie testen das Projektelement in dieser Instanz von Visual Studio.

#### <a name="to-test-the-project-item-in-visual-studio"></a>So testen Sie das Projektelement in Visual Studio

1. Wählen Sie in der experimentellen Instanz von Visual Studio auf der Menüleiste **Datei** > **neu** > **Projekt**.

2. Erweitern Sie **Visual C#-** oder **Visual Basic** (abhängig von der die Elementvorlage unterstützten Sprache), erweitern Sie **SharePoint**, und wählen Sie dann die **2010**  Knoten.

3. Wählen Sie in der Liste der Projektvorlagen das Projekt **SharePoint 2010-Projekt**.

4. In der **Namen** geben **CustomActionTest**, und wählen Sie dann die **OK** Schaltfläche.

5. In der **SharePoint Customization Wizard**, geben Sie die URL der Website, die Sie für das Debuggen verwenden möchten, und wählen Sie dann die **Fertig stellen** Schaltfläche.

6. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für den Projektknoten, wählen **hinzufügen**, und wählen Sie dann **neues Element**.

7. In der **neues Element hinzufügen** Dialogfeld auf die **2010** unter den Knoten der **SharePoint** Knoten.

     Überprüfen Sie, ob die **benutzerdefinierte Aktion** Element in der Liste der Projektelemente angezeigt wird.

8. Wählen Sie die **benutzerdefinierte Aktion** Element aus, und wählen Sie dann die **hinzufügen** Schaltfläche.

     Visual Studio fügt ein Element mit dem Namen **CustomAction1** auf Ihr Projekt und öffnet die *"Elements.xml"* Datei im Editor.

9. Überprüfen Sie, ob die Codeausführung in der anderen Instanz von Visual Studio an dem Haltepunkt unterbrochen wird, den Sie zuvor in der `InitializeType`-Methode festgelegt haben.

10. Wählen Sie die **F5** Schlüssel, um das Debuggen des Projekts fortzusetzen.

11. In der experimentellen Instanz von Visual Studio in **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **CustomAction1** Knoten, und wählen Sie dann **View Designer für benutzerdefinierte**.

12. Stellen Sie sicher, dass ein Meldungsfeld wird angezeigt, und wählen Sie dann die **OK** Schaltfläche.

     Sie können dieses Kontextmenü verwenden, um zusätzliche Optionen oder Befehle für Entwickler bereitzustellen, z. B. zum Anzeigen eines Designers für die benutzerdefinierte Aktion.

13. Wählen Sie auf der Menüleiste **Ansicht** > **Ausgabe**.

     Die **Ausgabe** Fenster wird geöffnet.

14. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **CustomAction1** Element, und klicken Sie dann ändern Sie den Namen **MyCustomAction**.

     In der **Ausgabe** Fenster eine bestätigungsmeldung wird angezeigt. Diese Meldung wird von dem <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemNameChanged>-Ereignishandler ausgegeben, den Sie in der `CustomActionProjectItemTypeProvider`-Klasse definiert haben. Sie können dieses Ereignis und andere Projektelementereignisse behandeln, um ein benutzerdefiniertes Verhalten bei Änderungen des Projektelements durch den Entwickler zu implementieren.

#### <a name="to-test-the-custom-action-in-sharepoint"></a>So testen Sie die benutzerdefinierte Aktion in SharePoint

1. Öffnen Sie in der experimentellen Instanz von Visual Studio die *"Elements.xml"* -Datei, die ein untergeordnetes Element der **MyCustomAction** Projektelement.

2. In der *"Elements.xml"* Datei, die folgenden Änderungen vornehmen und speichern Sie die Datei:

    - Legen Sie im `CustomAction`-Element das `Id`-Attribut auf eine GUID oder eine andere eindeutige Zeichenfolge fest, wie im folgenden Beispiel gezeigt:

        ```xml
        Id="cd85f6a7-af2e-44ab-885a-0c795b52121a"
        ```

    - Legen Sie im `CustomAction`-Element das `Title`-Attribut fest, wie im folgenden Beispiel gezeigt:

        ```xml
        Title="SharePoint Developer Center"
        ```

    - Legen Sie im `CustomAction`-Element das `Description`-Attribut fest, wie im folgenden Beispiel gezeigt:

        ```xml
        Description="Opens the SharePoint Developer Center Web site."
        ```

    - Legen Sie im `UrlAction`-Element das `Url`-Attribut fest, wie im folgenden Beispiel gezeigt:

        ```xml
        Url="https://docs.microsoft.com/sharepoint/dev/"
        ```

3. Drücken Sie die Taste **F5**.

     Die benutzerdefinierte Aktion wird verpackt und bereitgestellt werden, auf die SharePoint-Website, die im angegebenen die **Website-URL** -Eigenschaft des Projekts. Im Webbrowser wird die Standardseite dieser Website geöffnet.

    > [!NOTE]
    >  Wenn die **Skriptdebugging deaktiviert** wählen Sie im angezeigten Dialogfeld die **Ja** Schaltfläche, um das Debuggen des Projekts fortzusetzen.

4. Auf der **Websiteaktionen** Menü wählen **SharePoint Developer Center**, stellen Sie sicher, dass der Browser die Website geöffnet wird https://docs.microsoft.com/sharepoint/dev/, und schließen Sie dann den Webbrowser.

## <a name="clean-up-the-development-computer"></a>Bereinigung auf dem Entwicklungscomputer
 Nachdem Sie die Tests des Projektelements abgeschlossen haben, entfernen Sie die Projektelementvorlage aus der experimentellen Instanz von Visual Studio.

#### <a name="to-clean-up-the-development-computer"></a>So bereinigen Sie den Entwicklungscomputer

1. Wählen Sie in der experimentellen Instanz von Visual Studio auf der Menüleiste **Tools** > **Erweiterungen und Updates**.

     Das Dialogfeld **Erweiterungen und Updates** wird geöffnet.

2. Wählen Sie in der Liste der Erweiterungen, **Custom Action Project Item**, und wählen Sie dann die **Deinstallieren** Schaltfläche.

3. Wählen Sie in das Dialogfeld, das angezeigt wird, die **Ja** , um zu bestätigen, dass Sie die Erweiterung deinstallieren möchten.

4. Wählen Sie die **jetzt neu starten** Schaltfläche, um die Deinstallation abzuschließen.

5. Schließen Sie die experimentelle Instanz von Visual Studio und die Instanz, in der die Projektmappe "CustomActionProjectItem" geöffnet ist.

## <a name="next-steps"></a>Nächste Schritte
 Nachdem Sie diese exemplarische Vorgehensweise abgeschlossen haben, können Sie der Elementvorlage einen Assistenten hinzufügen. Wenn ein Benutzer einem SharePoint-Projekt ein Projektelement für die benutzerdefinierte Aktion hinzufügt, wird der Assistent sammelt Informationen zu der Aktion (z. B. den Speicherort und die URL, zu der navigiert werden soll, wenn die Aktion ausgewählt wird) und fügt diese Informationen, um die *"Elements.xml"*-Datei in das neue Projektelement. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen ein Projektelements benutzerdefinierte Aktion mit einer Elementvorlage, Teil 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).

## <a name="see-also"></a>Siehe auch

- [Exemplarische Vorgehensweise: Erstellen eines Projektelements benutzerdefinierte Aktion mit einer Elementvorlage, Teil 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)
- [Definieren von benutzerdefinierten SharePoint-Projektelementtypen](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Erstellen von Elementvorlagen und Projektvorlagen für SharePoint-Projektelemente](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Verwenden Sie die SharePoint-Projektdiensts](../sharepoint/using-the-sharepoint-project-service.md)
- [Schemareferenz zu Visual Studio-Vorlagen](/visualstudio/extensibility/visual-studio-template-schema-reference)
- [Bildbearbeitung für Symbole](/cpp/windows/image-editor-for-icons)
- [Erstellen eines Symbols oder anderen Bilds &#40;Bildbearbeitung für Symbole&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)