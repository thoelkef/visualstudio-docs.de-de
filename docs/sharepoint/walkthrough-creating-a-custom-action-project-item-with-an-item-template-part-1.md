---
title: "Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1 | Microsoft Docs"
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
  - "SharePoint project items, defining your own types"
  - "project items [SharePoint development in Visual Studio], defining your own types"
  - "SharePoint development in Visual Studio, defining new project item types"
ms.assetid: 41ed9c1c-4239-4d80-934b-975fde744288
caps.latest.revision: 152
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 151
---
# Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1
  Sie können das SharePoint\-Projektsystem in Visual Studio erweitern, indem Sie eigene Projektelementtypen erstellen.  In dieser exemplarischen Vorgehensweise erstellen Sie ein Projektelement, das einem SharePoint\-Projekt hinzugefügt werden kann, um eine benutzerdefinierte Aktion auf einer SharePoint\-Website zu erstellen.  Die benutzerdefinierte Aktion fügt dem Menü **Websiteaktionen** der SharePoint\-Website ein Menüelement hinzu.  
  
 Diese exemplarische Vorgehensweise enthält die folgenden Aufgaben:  
  
-   Erstellen einer Visual Studio\-Erweiterung, die einen neuen Typ von SharePoint\-Projektelement für eine benutzerdefinierte Aktion definiert.  Mit dem neuen Projektelementtyp werden mehrere benutzerdefinierte Funktionen implementiert:  
  
    -   Ein Kontextmenü, über das weitere auf das Projektelement bezogene Aufgaben ausgewählt werden können, z. B. für das Anzeigen eines Designers für die benutzerdefinierte Aktion in Visual Studio.  
  
    -   Code, der ausgeführt wird, wenn ein Entwickler bestimmte Eigenschaften des Projektelements oder des Projekts ändert, in dem es enthalten ist.  
  
    -   Ein benutzerdefiniertes Symbol, das neben dem Projektelement im **Projektmappen\-Explorer** angezeigt wird.  
  
-   Erstellen einer Visual Studio\-Elementvorlage für das Projektelement.  
  
-   Erstellen eines Visual Studio\-Erweiterungspakets \(VSIX\) zum Bereitstellen der Projektelementvorlage und der Erweiterungsassembly.  
  
-   Debuggen und Testen des Projektelements  
  
 Dies ist eine eigenständige exemplarische Vorgehensweise.  Nachdem Sie diese exemplarische Vorgehensweise abgeschlossen haben, können Sie das Projektelement erweitern, indem Sie der Elementvorlage einen Assistenten hinzufügen.  Weitere Informationen finden Sie unter [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).  
  
> [!NOTE]  
>  Ein Beispiel mit den abgeschlossenen Projekten, Code und weiteren Dateien für diese exemplarische Vorgehensweise können Sie unter folgender Adresse herunterladen:  [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=191369](http://go.microsoft.com/fwlink/?LinkId=191369).  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise werden auf dem Entwicklungscomputer die folgenden Komponenten benötigt:  
  
-   Unterstützte Editionen von Microsoft Windows, SharePoint und Visual Studio.  Weitere Informationen finden Sie unter [Anforderungen für die Entwicklung von SharePoint-Lösungen](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)].  Diese exemplarische Vorgehensweise verwendet die Vorlage **VSIX Project** im SDK, um ein VSIX\-Paket zum Bereitstellen des Projektelements zu erstellen.  Weitere Informationen finden Sie unter [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Kenntnisse der folgenden Konzepte sind hilfreich, wenn auch für die Durchführung der exemplarischen Vorgehensweise nicht erforderlich:  
  
-   Benutzerdefinierte Aktionen in SharePoint.  Weitere Informationen finden Sie unter [Benutzerdefinierte Aktion](http://go.microsoft.com/fwlink/?LinkId=177800).  
  
-   Elementvorlagen in Visual Studio.  Weitere Informationen finden Sie unter [Erstellen von benutzerdefinierten Projekt- und Elementvorlagen in Visual Studio](../ide/creating-project-and-item-templates.md).  
  
## Erstellen der Projekte  
 Zum Abschließen dieser exemplarischen Vorgehensweise müssen Sie drei Projekte erstellen:  
  
-   Ein VSIX\-Projekt.  Von diesem Projekt wird das VSIX\-Paket zum Bereitstellen des SharePoint\-Projektelements erstellt.  
  
-   Ein Elementvorlagenprojekt.  Von diesem Projekt wird eine Elementvorlage erstellt, mit der das SharePoint\-Projektelement einem SharePoint\-Projekt hinzugefügt werden kann.  
  
-   Ein Klassenbibliotheksprojekt.  Dieses Projekt implementiert eine Visual Studio\-Erweiterung, die das Verhalten des SharePoint\-Projektelements definiert.  
  
 Beginnen Sie mit der exemplarischen Vorgehensweise, indem Sie beide Projekte erstellen.  
  
#### So erstellen Sie das VSIX\-Projekt  
  
1.  Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Wählen Sie in der Menüleiste **Datei**, **Neu**, **Projekt** aus.  
  
3.  Überprüfen Sie in der Liste am oberen Rand des Dialogfelds **Neues Projekt**, ob **.NET Framework 4.5** ausgewählt ist.  
  
4.  Erweitern Sie im Dialogfeld **Neues Projekt** den Knoten **Visual C\#** oder **Visual Basic**, und wählen Sie dann den Knoten **Erweiterungen** aus.  
  
    > [!NOTE]  
    >  Der Knoten **Erweiterungen** ist nur verfügbar, wenn Sie das Visual Studio SDK installieren.  Weitere Informationen finden Sie weiter oben in diesem Thema im Abschnitt zu den erforderlichen Komponenten.  
  
5.  Wählen Sie die Vorlage **VSIX\-Projekt** aus.  
  
6.  Geben Sie im Feld **NameCustomActionProjectItem** ein, und wählen Sie dann die Schaltfläche **OK** aus.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fügt das Projekt **CustomActionProjectItem** zum **Projektmappen\-Explorer** hinzu.  
  
#### So erstellen Sie das Elementvorlagenprojekt  
  
1.  Öffnen Sie im **Projektmappen\-Explorer** das Kontextmenü für den Projektmappenknoten, wählen Sie **Hinzufügen** und dann **Neues Projekt** aus.  
  
    > [!NOTE]  
    >  In Visual Basic\-Projekten wird der Projektmappenknoten nur im **Projektmappen\-Explorer** angezeigt, wenn das Kontrollkästchen **Projektmappe immer anzeigen** in [NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/de-de/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca) aktiviert ist.  
  
2.  Überprüfen Sie in der Liste am oberen Rand des Dialogfelds **Neues Projekt**, ob **.NET Framework 4.5** ausgewählt ist.  
  
3.  Erweitern Sie im Dialogfeld **Neues Projekt** den Knoten **Visual C\#** oder **Visual Basic**, und wählen Sie dann den Knoten **Erweiterungen** aus.  
  
4.  Wählen Sie in der Liste der Projektvorlagen **C\#\-Elementvorlage** oder **Visual Basic\-Elementvorlage** aus.  
  
5.  Geben Sie im Feld **NameItemTemplate** ein, und wählen Sie dann die Schaltfläche **OK** aus.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fügt der Projektmappe das Projekt **ItemTemplate** hinzu.  
  
#### So erstellen Sie das Erweiterungsprojekt  
  
1.  Öffnen Sie im **Projektmappen\-Explorer** das Kontextmenü für den Projektmappenknoten, wählen Sie **Hinzufügen** und dann **Neues Projekt** aus.  
  
2.  Überprüfen Sie in der Liste am oberen Rand des Dialogfelds **Neues Projekt**, ob **.NET Framework 4.5** ausgewählt ist.  
  
3.  Erweitern Sie im Dialogfeld **Neues Projekt** den Knoten **Visual C\#** oder **Visual Basic**, wählen Sie den Knoten **Windows** und dann die Projektvorlage **Klassenbibliothek** aus.  
  
4.  Geben Sie im Feld **NameProjectItemDefinition** ein, und wählen Sie dann die Schaltfläche **OK** aus.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fügt das Projekt **ProjectItemDefinition** der Projektmappe hinzu und öffnet die Class1\-Codedatei.  
  
5.  Löschen Sie die Class1\-Codedatei aus dem Projekt.  
  
## Konfigurieren des Erweiterungsprojekts  
 Bevor Sie Code zum Erstellen des SharePoint\-Projektelementtyps schreiben, müssen Sie dem Erweiterungsprojekt Codedateien und Assemblyverweise hinzufügen.  
  
#### So konfigurieren Sie das Projekt  
  
1.  Öffnen Sie im **Projektmappen\-Explorer** das Kontextmenü für das Projekt **ProjectItemDefinition**. Wählen Sie **Hinzufügen** und dann **Neues Element** aus.  
  
2.  Wählen Sie in der Liste der Projektelemente **Codedatei** aus.  
  
3.  Geben Sie im Feld **Name** den Namen **CustomAction** mit der entsprechenden Dateinamenerweiterung ein, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.  
  
4.  Öffnen Sie im **Projektmappen\-Explorer** das Kontextmenü für das Projekt **ProjectItemDefinition**, und wählen Sie dann **Verweis hinzufügen** aus.  
  
5.  Wählen Sie im Dialogfeld **Verweis\-Manager – ProjectItemDefinition** den Knoten **Assemblys** und dann den Knoten **Framework** aus.  
  
6.  Aktivieren Sie das Kontrollkästchen neben jeder der folgenden Assemblys:  
  
    -   System.ComponentModel.Composition  
  
    -   System.Windows.Forms  
  
7.  Wählen Sie den Knoten **Erweiterungen** aus, aktivieren Sie das Kontrollkästchen neben der Microsoft.VisualStudio.Sharepoint\-Assembly, und wählen Sie dann die Schaltfläche **OK** aus.  
  
## Definieren des neuen SharePoint\-Projektelementtyps  
 Erstellen Sie eine Klasse, die die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>\-Schnittstelle implementiert, um das Verhalten des neuen Projektelementtyps zu definieren.  Implementieren Sie diese Schnittstelle immer dann, wenn Sie einen neuen Projektelementtyp definieren möchten.  
  
#### So definieren Sie den neuen SharePoint\-Projektelementtyp  
  
1.  Öffnen Sie im Projekt ProjectItemDefinition die CustomAction\-Codedatei.  
  
2.  Ersetzen Sie den Code in dieser Datei durch den folgenden Code:  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/cs/projectitemtypedefinition/customaction.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/vb/projectitemdefinition/customaction.vb#1)]  
  
## Erstellen eines Symbols für das Projektelement im Projektmappen\-Explorer  
 Wenn Sie ein benutzerdefiniertes SharePoint\-Projektelement erstellen, können Sie dem Projektelement ein Bild \(ein Symbol oder eine Bitmap\) zuordnen.  Dieses Bild wird neben dem Projektelement im **Projektmappen\-Explorer** angezeigt.  
  
 In der folgenden Vorgehensweise erstellen Sie ein Symbol für das Projektelement und betten das Symbol in die Erweiterungsassembly ein.  Auf dieses Symbol wird durch das <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute> der zuvor erstellten `CustomActionProjectItemTypeProvider`\-Klasse verwiesen.  
  
#### So erstellen Sie ein benutzerdefiniertes Symbol für das Projektelement  
  
1.  Öffnen Sie im **Projektmappen\-Explorer** das Kontextmenü für das Projekt **ProjectItemDefinition**. Wählen Sie **Hinzufügen** und dann **Neues Element...** aus.  
  
2.  Wählen Sie in der Liste der Projektelemente, das Element **Symboldatei** aus.  
  
    > [!NOTE]  
    >  In Visual Basic\-Projekten müssen Sie den Knoten **Allgemein** auswählen, um das Element **Symboldatei** anzuzeigen.  
  
3.  Geben Sie im Feld **NameCustomAction\_SolutionExplorer.ico** ein, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.  
  
     Das neue Symbol wird in der **Bildbearbeitung** geöffnet.  
  
4.  Bearbeiten Sie die 16x16\-Version der Symboldatei so, dass sich das Symbol leicht von anderen unterscheiden lässt, und speichern Sie dann die Symboldatei.  
  
5.  Wählen Sie im **Projektmappen\-Explorer** den Eintrag **CustomAction\_SolutionExplorer.ico** aus.  
  
6.  Wählen Sie im Fenster **Eigenschaften** den Pfeil neben der Eigenschaft **Buildvorgang** aus.  
  
7.  Wählen Sie in der angezeigten Liste **Eingebettete Ressource** aus.  
  
## Checkpoint  
 Ab diesem Punkt in der exemplarischen Vorgehensweise wurde der gesamte für das Projektelement benötigte Code in das Projekt eingefügt.  Erstellen Sie das Projekt, um zu überprüfen, ob es fehlerfrei kompiliert wird.  
  
#### So erstellen Sie das Projekt  
  
1.  Öffnen Sie das Kontextmenü für das Projekt **ProjectItemDefinition**, und wählen Sie dann **Build** aus.  
  
## Erstellen einer Visual Studio\-Elementvorlage  
 Um Ihr Projektelement anderen Entwicklern zur Verfügung stellen zu können, müssen Sie eine Projektvorlage oder eine Elementvorlage erstellen.  Mithilfe dieser Vorlagen können Entwickler in Visual Studio eine Instanz des Projekts erstellen, indem sie ein neues Projekt erstellen oder ein Element zu einem vorhandenen Projekt hinzufügen.  Konfigurieren Sie für diese exemplarische Vorgehensweise das Projektelement mithilfe des Projekts ItemTemplate.  
  
#### So erstellen Sie die Elementvorlage  
  
1.  Löschen Sie die Class1\-Codedatei aus dem ItemTemplate\-Projekt.  
  
2.  Öffnen Sie im Projekt ItemTemplate die Datei ItemTemplate.vstemplate.  
  
3.  Ersetzen Sie den Inhalt der Datei durch das folgende XML, speichern Sie anschließend die Datei, und schließen Sie sie.  
  
    > [!NOTE]  
    >  Das folgende XML ist für eine Visual C\#\-Elementvorlage bestimmt.  Wenn Sie eine Visual Basic\-Elementvorlage erstellen, ersetzen Sie den Wert des `ProjectType`\-Elements durch `VisualBasic`.  
  
    ```  
  
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
  
     Diese Datei definiert den Inhalt und das Verhalten der Elementvorlage.  Weitere Informationen zum Inhalt dieser Datei finden Sie unter [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md).  
  
4.  Öffnen Sie im **Projektmappen\-Explorer** das Kontextmenü für das Projekt **ItemTemplate**, wählen Sie **Hinzufügen** und dann **Neues Element** aus.  
  
5.  Wählen Sie im Dialogfeld **Neues Element hinzufügen** die Vorlage **Textdatei** aus.  
  
6.  Geben Sie im Feld **NameCustomAction.spdata** ein, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.  
  
7.  Fügen Sie der Datei CustomAction.spdata das folgende XML hinzu. Speichern und schließen Sie anschließend die Datei.  
  
    ```  
  
    <ProjectItem Type="Contoso.CustomAction" DefaultFile="Elements.xml"   
     xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">  
      <Files>  
        <ProjectItemFile Source="Elements.xml" Target="$fileinputname$\" Type="ElementManifest" />  
      </Files>  
    </ProjectItem>  
    ```  
  
     Diese Datei enthält Informationen zu den Dateien, die im Projektelement enthalten sind.  Das `Type`\-Attribut des `ProjectItem`\-Elements muss auf die gleiche Zeichenfolge festgelegt werden, die in der Projektelementdefinition \(die `CustomActionProjectItemTypeProvider`\-Klasse, die Sie zuvor in dieser exemplarischen Vorgehensweise erstellt haben\) an <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> übergeben wird.  Weitere Informationen zum Inhalt von SPDATA\-Dateien finden Sie unter [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md).  
  
8.  Öffnen Sie im **Projektmappen\-Explorer** das Kontextmenü für das Projekt **ItemTemplate**, wählen Sie **Hinzufügen** und dann **Neues Element** aus.  
  
9. Wählen Sie im Dialogfeld **Neues Element hinzufügen** die Vorlage **XML\-Datei** aus.  
  
10. Geben Sie im Feld **NameElements.xml** ein, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.  
  
11. Ersetzen Sie den Inhalt der Datei Elements.xml durch das folgende XML, speichern Sie anschließend die Datei, und schließen Sie sie.  
  
    ```  
  
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
  
     Diese Datei definiert eine benutzerdefinierte Standardaktion, die im Menü **Websiteaktionen** der SharePoint\-Website ein Menüelement erstellt.  Wenn ein Benutzer das Menüelement auswählt, wird die im `UrlAction`\-Element angegebene URL im Webbrowser geöffnet.  Weitere Informationen zu den XML\-Elementen, die zum Definieren von benutzerdefinierten Aktionen verwendet werden können, finden Sie im Thema zu [benutzerdefinierten Aktionsdefinitionen](http://go.microsoft.com/fwlink/?LinkId=177801).  
  
12. \(Optional.\) Öffnen Sie die Datei ItemTemplate.ico, und ändern Sie sie, sodass sie einen Entwurf aufweist, den Sie erkennen können.  Dieses Symbol wird neben dem Projektelement im Dialogfeld **Neues Element hinzufügen** angezeigt.  
  
13. Öffnen Sie im **Projektmappen\-Explorer** das Kontextmenü für das Projekt **ItemTemplate**, und wählen Sie dann **Projekt entladen** aus.  
  
14. Öffnen Sie erneut das Kontextmenü für das Projekt **ItemTemplate**, und wählen Sie dann **ItemTemplate.csproj bearbeiten** oder **ItemTemplate.vbproj bearbeiten** aus.  
  
15. Suchen Sie das folgende `VSTemplate`\-Element in der Projektdatei.  
  
    ```  
    <VSTemplate Include="ItemTemplate.vstemplate">  
    ```  
  
16. Ersetzen Sie dieses `VSTemplate`\-Element durch das folgende XML, und speichern und schließen Sie dann die Datei.  
  
    ```  
    <VSTemplate Include="ItemTemplate.vstemplate">  
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>  
    </VSTemplate>  
    ```  
  
     Das `OutputSubPath`\-Element gibt weitere Ordner in dem Pfad an, unter dem die Elementvorlage beim Erstellen des Projekts erstellt wird.  Mit den hier angegebenen Ordnern wird sichergestellt, dass die Elementvorlage nur dann verfügbar ist, wenn Kunden im Dialogfeld **Neues Element hinzufügen** den Knoten **SharePoint** erweitern und dann den Knoten **2010** auswählen.  
  
17. Öffnen Sie im **Projektmappen\-Explorer** das Kontextmenü für das Projekt **ItemTemplate**, und wählen Sie dann **Projekt erneut entladen** aus.  
  
## Erstellen eines VSIX\-Pakets zum Bereitstellen des Projektelements  
 Zum Bereitstellen der Erweiterung erstellen Sie anhand des VSIX\-Projekts in der Lösung ein VSIX\-Paket.  Konfigurieren Sie zuerst das VSIX\-Paket, indem Sie die im VSIX\-Projekt enthaltene Datei "source.extension.vsixmanifest" ändern.  Erstellen Sie anschließend das VSIX\-Paket, indem Sie die Lösung erstellen.  
  
#### So erstellen und konfigurieren Sie das VSIX\-Paket  
  
1.  Öffnen Sie im **Projektmappen\-Explorer** das Kontextmenü für die Datei **source.extension.vsixmanifest** im CustomActionProjectItem\-Projekt, und wählen Sie dann **Öffnen** aus.  
  
     Die Datei wird von Visual Studio im Manifest\-Editor geöffnet.  Die Datei "source.extension.vsixmanifest" bildet die Grundlage für die Datei "extension.vsixmanifest", die für alle VSIX\-Pakete erforderlich ist.  Weitere Informationen zu dieser Datei finden Sie unter [VSIX\-Erweiterungs\-Schemareferenz](http://msdn.microsoft.com/de-de/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  Geben Sie im Feld **Produktname** die Zeichenfolge **Custom Action Project Item** ein.  
  
3.  Geben Sie im Feld **Autor** den Namen **Contoso** ein.  
  
4.  Geben Sie im Feld **Beschreibung** folgende Zeichenfolge ein: **A SharePoint project item that represents a custom action**.  
  
5.  Wählen Sie auf der Registerkarte **Objekte** die Schaltfläche **Neu** aus.  
  
     Das Dialogfeld **Neue Anlage hinzufügen** wird geöffnet.  
  
6.  Wählen Sie in der Liste **TypMicrosoft.VisualStudio.ItemTemplate** aus.  
  
    > [!NOTE]  
    >  Dieser Wert entspricht dem `ItemTemplate`\-Element in der Datei "extension.vsixmanifest".  Dieses Element identifiziert den Unterordner im VSIX\-Paket, der die Projektelementvorlage enthält.  Weitere Informationen finden Sie unter [NIB: ItemTemplate Element \(VSX Schema\)](http://msdn.microsoft.com/de-de/1d489e54-c1c5-4f96-a510-6c2640867ff0).  
  
7.  Wählen Sie in der Liste **Quelle** die Option **Ein Projekt in der aktuellen Projektmappe** aus.  
  
8.  Wählen Sie in der Liste **Projekt** die Option **ItemTemplate** und dann die Schaltfläche **OK** aus.  
  
9. Wählen Sie auf der Registerkarte **Objekte** die Schaltfläche **Neu** aus.  
  
     Das Dialogfeld **Neue Anlage hinzufügen** wird geöffnet.  
  
10. Wählen Sie in der Liste **Typ** den Eintrag **Microsoft.VisualStudio.MefComponent** aus.  
  
    > [!NOTE]  
    >  Dieser Wert entspricht dem `MefComponent`\-Element in der Datei "extension.vsixmanifest".  Von diesem Element wird der Name einer Erweiterungsassembly im VSIX\-Paket angegeben.  Weitere Informationen finden Sie unter [NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/de-de/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
11. Wählen Sie in der Liste **Quelle** die Option **Ein Projekt in der aktuellen Projektmappe** aus.  
  
12. Wählen Sie in der Liste **Projekt** den Eintrag **ProjectItemDefinition** aus.  
  
13. Klicken Sie auf die Schaltfläche **OK**.  
  
14. Wählen Sie in der Menüleiste **BuildProjektmappe erstellen** aus, und überprüfen Sie dann, ob das Projekt fehlerfrei kompiliert werden kann.  
  
15. Überprüfen Sie, ob der Buildausgabeordner für das Projekt "CustomActionProjectItem" die Datei "CustomActionProjectItem.vsix" enthält.  
  
     Standardmäßig ist der Buildausgabeordner der Ordner "\\bin\\Debug" in dem Ordner, der das Projekt "CustomActionProjectItem" enthält.  
  
## Testen des Projektelements  
 Jetzt können Sie das Projektelement testen.  Debuggen Sie die Projektmappe CustomActionProjectItem zunächst in der experimentellen Instanz von Visual Studio.  Testen Sie anschließend das Projektelement **Benutzerdefinierte Aktion** in einem SharePoint\-Projekt in der experimentellen Instanz von Visual Studio.  Erstellen und führen Sie zum Schluss das SharePoint\-Projekt aus, um sicherzustellen, dass die benutzerdefinierte Aktion ordnungsgemäß funktioniert.  
  
#### So debuggen Sie die Projektmappe  
  
1.  Starten Sie Visual Studio erneut mit Administratoranmeldeinformationen, und öffnen Sie dann die Projektmappe "CustomActionProjectItem".  
  
2.  Öffnen Sie die CustomAction\-Codedatei, und fügen Sie dann in der ersten Codezeile in der `InitializeType`\-Methode einen Haltepunkt ein.  
  
3.  Drücken Sie die Taste **F5**, um das Debugging zu starten.  
  
     Die Erweiterung wird unter "%UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\10.0Exp\\Extensions\\Contoso\\Custom Action Project Item\\1.0" installiert, und eine experimentelle Instanz von Visual Studio wird gestartet.  Sie testen das Projektelement in dieser Instanz von Visual Studio.  
  
#### So testen Sie das Projektelement in Visual Studio  
  
1.  Wählen Sie in der experimentellen Visual Studio\-Instanz in der Menüleiste **Datei**, **Neu** und **Projekt** aus.  
  
2.  Erweitern Sie **Visual C\#** oder **Visual Basic** \(entsprechend der von der Elementvorlage unterstützten Sprache\), erweitern Sie **SharePoint**, und wählen Sie anschließend den Knoten **2010** aus.  
  
3.  Wählen Sie in der Liste der Projektvorlagen **SharePoint 2010\-Projekt** aus.  
  
4.  Geben Sie im Feld **NameCustomActionTest** ein, und wählen dann die Schaltfläche **OK** aus.  
  
5.  Geben Sie im **Assistenten zum Anpassen von SharePoint** die URL der Website ein, die Sie zum Debuggen verwenden möchten, und wählen Sie dann die Schaltfläche **Fertig stellen** aus.  
  
6.  Öffnen Sie im **Projektmappen\-Explorer** das Kontextmenü für den Projektknoten, wählen Sie **Hinzufügen** und dann **Neues Element** aus.  
  
7.  Wählen Sie im Dialogfeld **Neues Element hinzufügen** unter dem Knoten **SharePoint** den Knoten **2010** aus.  
  
     Vergewissern Sie sich, dass das Element **Benutzerdefinierte Aktion** in der Liste der Projektelemente angezeigt wird.  
  
8.  Wählen Sie das Element **Benutzerdefinierte Aktion** und dann die Schaltfläche **Hinzufügen** aus.  
  
     Visual Studio fügt dem Projekt ein Element mit dem Namen **CustomAction1** hinzu und öffnet die Datei "Elements.xml" im Editor.  
  
9. Überprüfen Sie, ob die Codeausführung in der anderen Instanz von Visual Studio an dem Haltepunkt unterbrochen wird, den Sie zuvor in der `InitializeType`\-Methode festgelegt haben.  
  
10. Wählen Sie die Taste **F5** aus, um mit dem Debuggen des Projekts fortzufahren.  
  
11. Öffnen Sie in der experimentellen Instanz von Visual Studio im **Projektmappen\-Explorer** das Kontextmenü für den Knoten **CustomAction1**, und wählen Sie dann **Designer für benutzerdefinierte Ansicht anzeigen** aus.  
  
12. Vergewissern Sie sich, dass ein Meldungsfeld angezeigt wird, und wählen Sie die Schaltfläche **OK** aus.  
  
     Sie können dieses Kontextmenü verwenden, um zusätzliche Optionen oder Befehle für Entwickler bereitzustellen, z. B. zum Anzeigen eines Designers für die benutzerdefinierte Aktion.  
  
13. Wählen Sie in der Menüleiste **Ansicht**, **Ausgabe** aus.  
  
     Das **Ausgabefenster** wird geöffnet.  
  
14. Öffnen Sie im **Projektmappen\-Explorer** das Kontextmenü für das Element **CustomAction1**, und ändern Sie dann den Namen in **MyCustomAction**.  
  
     Im Fenster **Ausgabe** wird eine Bestätigungsmeldung angezeigt.  Diese Meldung wird von dem <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemNameChanged>\-Ereignishandler ausgegeben, den Sie in der `CustomActionProjectItemTypeProvider`\-Klasse definiert haben.  Sie können dieses Ereignis und andere Projektelementereignisse behandeln, um ein benutzerdefiniertes Verhalten bei Änderungen des Projektelements durch den Entwickler zu implementieren.  
  
#### So testen Sie die benutzerdefinierte Aktion in SharePoint  
  
1.  Öffnen Sie in der experimentellen Instanz von Visual Studio die Datei "Elements.xml". Diese Datei ist ein untergeordnetes Element des Projektelements **MyCustomAction**.  
  
2.  Nehmen Sie in der Datei "Elements.xml" die folgenden Änderungen vor, und speichern Sie anschließend die Datei:  
  
    -   Legen Sie im `CustomAction`\-Element das `Id`\-Attribut auf eine GUID oder eine andere eindeutige Zeichenfolge fest, wie im folgenden Beispiel gezeigt:  
  
        ```  
        Id="cd85f6a7-af2e-44ab-885a-0c795b52121a"  
        ```  
  
    -   Legen Sie im `CustomAction`\-Element das `Title`\-Attribut fest, wie im folgenden Beispiel gezeigt:  
  
        ```  
        Title="SharePoint Developer Center"  
        ```  
  
    -   Legen Sie im `CustomAction`\-Element das `Description`\-Attribut fest, wie im folgenden Beispiel gezeigt:  
  
        ```  
        Description="Opens the SharePoint Developer Center Web site."  
        ```  
  
    -   Legen Sie im `UrlAction`\-Element das `Url`\-Attribut fest, wie im folgenden Beispiel gezeigt:  
  
        ```  
        Url="http://msdn.microsoft.com/sharepoint/default.aspx"  
        ```  
  
3.  Drücken Sie die Taste F5.  
  
     Die benutzerdefinierte Aktion wird verpackt und auf der SharePoint\-Website bereitgestellt, die in der **Website\-URL**\-Eigenschaft des Projekts angegeben ist.  Im Webbrowser wird die Standardseite dieser Website geöffnet.  
  
    > [!NOTE]  
    >  Wenn das Dialogfeld **Skriptdebugging deaktiviert** angezeigt wird, wählen Sie die Schaltfläche **Ja** aus, um mit dem Debuggen des Projekts fortzufahren.  
  
4.  Wählen Sie im Menü **WebsiteaktionenSharePoint Developer Center** aus, überprüfen Sie, ob der Browser die Website "http:\/\/msdn.microsoft.com\/sharepoint\/default.aspx" öffnet, und schließen Sie dann den Webbrowser.  
  
## Bereinigen des Entwicklungscomputers  
 Nachdem Sie die Tests des Projektelements abgeschlossen haben, entfernen Sie die Projektelementvorlage aus der experimentellen Instanz von Visual Studio.  
  
#### So bereinigen Sie den Entwicklungscomputer  
  
1.  Wählen Sie in der experimentellen Visual Studio\-Instanz in der Menüleiste **Erstellen** und **Erweiterungen und Update** aus.  
  
     Das Dialogfeld **Erweiterungen und Updates** wird geöffnet.  
  
2.  Wählen Sie in der Liste der Erweiterungen **Custom Action Project Item** und dann die Schaltfläche **Deinstallieren** aus.  
  
3.  Wählen Sie im angezeigten Dialogfeld die Schaltfläche **Ja** aus, um zu bestätigen, dass Sie die Erweiterung deinstallieren möchten.  
  
4.  Wählen Sie die Schaltfläche **Jetzt neu starten** aus, um die Deinstallation abzuschließen.  
  
5.  Schließen Sie die experimentelle Instanz von Visual Studio und die Instanz, in der die Projektmappe "CustomActionProjectItem" geöffnet ist.  
  
## Nächste Schritte  
 Nachdem Sie diese exemplarische Vorgehensweise abgeschlossen haben, können Sie der Elementvorlage einen Assistenten hinzufügen.  Wenn ein Benutzer einem SharePoint\-Projekt ein Projektelement "Benutzerdefinierte Aktion" hinzufügt, werden vom Assistenten Informationen zur benutzerdefinierten Aktion gesammelt \(z. B. der Speicherort und die URL, die bei der Auswahl dieser Aktion geöffnet wird\). Diese Informationen werden der Datei "Elements.xml" im neuen Projektelement hinzugefügt.  Weitere Informationen finden Sie unter [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).  
  
## Siehe auch  
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)   
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)   
 [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)   
 [Image Editor for Icons](/visual-cpp/windows/image-editor-for-icons)   
 [Creating an Icon or Other Image &#40;Image Editor for Icons&#41;](/visual-cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)  
  
  