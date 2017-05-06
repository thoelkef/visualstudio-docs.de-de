---
title: "Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "project items [SharePoint development in Visual Studio], creating template wizards"
  - "SharePoint project items, creating template wizards"
  - "SharePoint development in Visual Studio, defining new project item types"
ms.assetid: 2d8165d3-4af9-4a5e-bdba-8b2a06b1dc8d
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2
  Nachdem Sie einen benutzerdefinierten Typ des SharePoint\-Projektelements definiert und diesen einer Elementvorlage in Visual Studio zugeordnet haben, empfiehlt es sich, außerdem einen Assistenten für die Vorlage bereitzustellen.  Mit dem Assistenten können Sie Informationen von Benutzern erfassen, wenn diese mit der Vorlage eine neue Instanz des Projektelements zu einem Projekt hinzufügen.  Mit den gesammelten Informationen kann das Projektelement initialisiert werden.  
  
 In dieser exemplarischen Vorgehensweise fügen Sie dem Projektelement Benutzerdefinierte Aktion einen Assistenten hinzu. Das Projektelement wird in [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md) veranschaulicht.  Wenn ein Benutzer einem SharePoint\-Projekt ein Projektelement Benutzerdefinierte Aktion hinzufügt, werden vom Assistenten Informationen über die benutzerdefinierte Aktion \(wie deren Speicherort und das zu navigieren, URL, wenn es ein Endbenutzer auswählt\) und der Datei Elements.xml im neuen Projektelement hinzu.  
  
 Diese exemplarische Vorgehensweise enthält die folgenden Aufgaben:  
  
-   Erstellen eines Assistenten für einen benutzerdefinierten SharePoint\-Projektelementtyp, dem eine Elementvorlage zugeordnet ist.  
  
-   Definieren einer benutzerdefinierten Assistenten\-Benutzeroberfläche, die der von integrierten Assistenten für SharePoint\-Projektelemente in Visual Studio ähnelt  
  
-   Initialisieren von SharePoint\-Projektdateien mit im Assistenten gesammelten Daten mithilfe von ersetzbaren Parametern  
  
-   Debuggen und Testen des Assistenten  
  
> [!NOTE]  
>  Sie können ein Beispiel herunterladen, das die abgeschlossenen Projekten, Code und andere Dateien für diese exemplarische Vorgehensweise vom folgenden Speicherort enthält: [Projektdateien für SharePoint\-Tool\-Erweiterbarkeits\-exemplarische Vorgehensweisen](http://go.microsoft.com/fwlink/?LinkId=191369).  
  
## Vorbereitungsmaßnahmen  
 Um diese exemplarische Vorgehensweise ausführen zu können, müssen Sie zuerst die Projektmappe CustomActionProjectItem erstellen, indem Sie die [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md) durcharbeiten.  
  
 Zum Durchführen dieser exemplarischen Vorgehensweise werden auf dem Entwicklungscomputer außerdem die folgenden Komponenten benötigt:  
  
-   Unterstützte Editionen von Windows, SharePoint und Visual Studio.  Weitere Informationen finden Sie unter [Anforderungen für die Entwicklung von SharePoint-Lösungen](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Das Visual Studio SDK.  Bei dieser exemplarischen Vorgehensweise wird mithilfe der Vorlage **VSIX Project** aus dem SDK ein VSIX\-Paket zum Bereitstellen des Projektelements erstellt.  Weitere Informationen finden Sie unter [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Kenntnisse der folgenden Konzepte sind hilfreich, wenn auch für die Durchführung der exemplarischen Vorgehensweise nicht erforderlich:  
  
-   Assistenten für Projekt\- und Elementvorlagen in Visual Studio.  Weitere Informationen finden Sie unter [Gewusst wie: Verwenden von Assistenten mit Projektvorlagen](~/extensibility/how-to-use-wizards-with-project-templates.md) und der <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>\-Schnittstelle.  
  
-   Benutzerdefinierte Aktionen in SharePoint.  Weitere Informationen finden Sie im Thema zu [benutzerdefinierten Aktionen](http://go.microsoft.com/fwlink/?LinkId=177800) \(möglicherweise in englischer Sprache\).  
  
## Erstellen des Assistentenprojekts  
 Um diese exemplarische Vorgehensweise abzuschließen, müssen Sie ein Projekt der Projektmappe hinzufügen die in [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md) erstellt haben.  In diesem Projekt implementieren Sie die <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>\-Schnittstelle, und Sie definieren die Assistenten\-Benutzeroberfläche.  
  
#### So erstellen Sie das Assistentenprojekt  
  
1.  In Visual Studio öffnen Sie die Projektmappe CustomActionProjectItem  
  
2.  In **Projektmappen\-Explorer** öffnen Sie das Kontextmenü für den Projektmappenknoten, wählen Sie **Hinzufügen** aus und wählen dann **Neues Projekt** aus.  
  
    > [!NOTE]  
    >  In Visual Basic\-Projekten wird der Projektmappenknoten nur im **Projektmappen\-Explorer** angezeigt, wenn das Kontrollkästchen **Projektmappe immer anzeigen** in [NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/de-de/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca) aktiviert ist.  
  
3.  Im Dialogfeld **Neues Projekt** erweitern Sie die **Visual C\#** oder Knoten **Visual Basic**, und wählen Sie dann den Knoten **Fenster** aus.  
  
4.  **Neues Projekt** am oberen Rand des Dialogfelds sicher, dass **.NET Framework 4.5** in der Liste der Versionen von .NET Framework ausgewählt ist.  
  
5.  Wählen Sie die **WPF\-Benutzersteuerelementbibliothek** Projektvorlage aus, nennen Sie das Projekt **ItemTemplateWizard**, und wählen Sie dann die Schaltfläche **OK** aus.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fügt der Projektmappe das Projekt **ItemTemplateWizard** hinzu.  
  
6.  Löschen Sie das Element UserControl1 aus dem Projekt.  
  
## Konfigurieren des Assistentenprojekts  
 Bevor Sie den Assistenten erstellen, müssen Sie ein Fenster \(Windows Presentation Foundation\), eine Codedatei und Assemblyverweise zum Projekt hinzufügen.  
  
#### So konfigurieren Sie ein Assistentenprojekt  
  
1.  In **Projektmappen\-Explorer** öffnen Sie das Kontextmenü im **ItemTemplateWizard** Projektknoten, und wählen Sie dann **Eigenschaften** aus.  
  
2.  In **Projekt\-Designer** stellen Sie sicher, dass das Zielframework in .NET Framework 4.5 festgelegt ist.  
  
     Für Visual C\#projekte können Sie diesen Wert auf der Registerkarte **Anwendung** festlegen.  In Visual Basic\-Projekten können Sie diesen Wert auf der Registerkarte **Kompilieren** festlegen.  Weitere Informationen finden Sie unter [Gewusst wie: .NET Framework-Version als Ziel](~/ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
3.  Im **ItemTemplateWizard** Projekt fügen Sie ein **Fenster \(WPF\)**\-Element zum Projekt hinzu, und benennen Sie dann das Element **WizardWindow**.  
  
4.  Fügen Sie zwei Codedateien hinzu, die CustomActionWizard und Zeichenfolgen benannt werden.  
  
5.  Öffnen Sie das Kontextmenü für das **ItemTemplateWizard** Projekt, und wählen Sie dann **Verweis hinzufügen** aus.  
  
6.  **Verweis\-Manager – ItemTemplateWizard** im Dialogfeld unter dem Knoten **Assemblys**, wählen Sie den Knoten **Erweiterungen** aus.  
  
7.  Aktivieren Sie die Kontrollkästchen neben den folgenden Assemblys aus, und wählen Sie dann die Schaltfläche **OK** aus:  
  
    -   EnvDTE  
  
    -   Microsoft.VisualStudio.Shell.11.0  
  
    -   Microsoft.VisualStudio.TemplateWizardInterface  
  
8.  In **Projektmappen\-Explorer** im Ordner **Verweise** für das Projekt ItemTemplateWizard, wählen Sie den **EnvDTE** Verweis aus.  
  
    > [!NOTE]  
    >  In Visual Basic\-Projekten wird der Ordner **Verweise** nur angezeigt, wenn das Kontrollkästchen **Projektmappe immer anzeigen** in [NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/de-de/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca) aktiviert ist.  
  
9. Im Fenster **Eigenschaften** ändern Sie den Wert der \- Eigenschaft auf **Interoptypen einbettenFalse**.  
  
## Definieren der Standardspeicherort\- und ID\-Zeichenfolgen für benutzerdefinierte Aktionen  
 Jede benutzerdefinierte Aktion verfügt über einen Speicherort und eine ID, die im `GroupID`\-Attribut und im `Location`\-Attribut des `CustomAction`\-Elements in der Datei Elements.xml angegeben werden.  In diesem Schritt definieren Sie im Projekt ItemTemplateWizard einige gültige Zeichenfolgen für diese Attribute.  Wenn Sie diese exemplarische Vorgehensweise abgeschlossen haben, werden diese Zeichenfolgen in die Datei Elements.xml im Projektelement Benutzerdefinierte Aktion geschrieben, wenn Benutzer im Assistenten einen Speicherort und eine ID angeben.  
  
 Zur Vereinfachung wird in diesem Beispiel nur eine Teilmenge der verfügbaren Standardspeicherorte und Standard\-IDs unterstützt.  Eine vollständige Liste finden Sie unter [Default Custom Action Locations and IDs](http://go.microsoft.com/fwlink/?LinkId=181964).  
  
#### So definieren Sie die Standardspeicherort\- und ID\-Zeichenfolgen  
  
1.  geöffnet.  
  
2.  Im **ItemTemplateWizard** Projekt ersetzen Sie den Code in der Codedatei Strings durch den folgenden Code.  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#6](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/cs/itemtemplatewizard/strings.cs#6)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#6](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/vb/itemtemplatewizard/strings.vb#6)]  
  
## Erstellen der Assistenten\-Benutzeroberfläche  
 Fügen Sie XAML hinzu, um die Benutzeroberfläche des Assistenten zu definieren, und fügen Sie Code hinzu, um einige Steuerelemente im Assistenten an die ID\-Zeichenfolgen zu binden.  Der Assistent, den Sie erstellen, ähnelt dem integrierten Assistenten für SharePoint\-Projekte in Visual Studio.  
  
#### So erstellen Sie die Assistenten\-Benutzeroberfläche  
  
1.  Im **ItemTemplateWizard** Projekt öffnen Sie das Kontextmenü für die Datei **WizardWindow.xaml**, und wählen Sie dann **Öffnen**, um das Fenster im Designer zu öffnen.  
  
2.  In der XAML\-Ansicht ersetzen Sie aktuelle XAML durch folgenden XAML\-Code.  Mit dem XAML wird eine Benutzeroberfläche einschließlich Überschrift, Steuerelementen zum Angeben des Verhaltens für eine benutzerdefinierte Aktion sowie Navigationsschaltflächen unten im Fenster definiert.  
  
    > [!NOTE]  
    >  das Projekt verfügt über mehrere Compilerfehler, nachdem Sie diesen Code hinzufügen.  Diese Fehler werden durch Code behoben, den Sie in späteren Schritten hinzufügen.  
  
     [!code-xml[SPExtensibility.ProjectItem.CustomAction#9](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/cs/itemtemplatewizard/wizardwindow.xaml#9)]  
  
    > [!NOTE]  
    >  Das Fenster, das in XAML erstellt wird, wird von der <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> Basisklasse abgeleitet.  Wenn Sie Visual Studio ein benutzerdefiniertes WPF\-Dialogfeld hinzufügen, wird empfohlen, das Dialogfeld von dieser Klasse, um ein einheitliches Aussehen mit anderen Dialogfeldern in Visual Studio verfügen ableiten und Probleme zu vermeiden, die andernfalls möglicherweise mit modale Dialogfelder auftreten.  Weitere Informationen finden Sie unter [Erstellen und Verwalten von modalen Dialogfeldern](../extensibility/creating-and-managing-modal-dialog-boxes.md).  
  
3.  Wenn Sie ein Visual Basic\-Projekt entwickeln, entfernen Sie den `ItemTemplateWizard`\-Namespace aus `WizardWindow`\-Klassennamen im \- Attribut des \- Elements `x:Class``Window`.  Dieses Element ist in der ersten Zeile des XAML.  Wenn Sie fertig sind, sollte die erste Zeile dem folgenden Code ähneln:  
  
    ```  
    <Window x:Class="WizardWindow"  
    ```  
  
4.  In der CodeBehind\-Datei für die Datei WizardWindow.xaml, ersetzen Sie den aktuellen Code durch den folgenden Code.  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#7](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/cs/itemtemplatewizard/wizardwindow.xaml.cs#7)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#7](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/vb/itemtemplatewizard/wizardwindow.xaml.vb#7)]  
  
## Implementieren des Assistenten  
 Definieren Sie die Funktionen des Assistenten, indem Sie die <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>\-Schnittstelle implementieren.  
  
#### So implementieren Sie den Assistenten  
  
1.  Im **ItemTemplateWizard** Projekt öffnen Sie die **CustomActionWizard** Codedatei, und ersetzen Sie dann den aktuellen Code in dieser Datei durch den folgenden Code:  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#8](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/cs/itemtemplatewizard/customactionwizard.cs#8)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#8](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/vb/itemtemplatewizard/customactionwizard.vb#8)]  
  
## Checkpoint  
 Ab diesem Punkt in der exemplarischen Vorgehensweise wurde der gesamte für den Assistenten benötigte Code in das Projekt eingefügt.  Erstellen Sie das Projekt, um sicherzustellen, dass es ohne Fehler kompiliert wird.  
  
#### So erstellen Sie das Projekt  
  
1.  Klicken Sie auf der Menüleiste wählen Sie **Erstellen**, **Projektmappe erstellen** aus.  
  
## Zuordnen des Assistenten zur Elementvorlage  
 Nachdem Sie den Assistenten implementiert haben, müssen Sie sie mit der **Benutzerdefinierte Aktion**\-Elementvorlage zuordnen, indem Sie drei Hauptschritte ausführen:  
  
1.  Signieren der Assistenten\-Assembly mit einem starkem Namen  
  
2.  Abrufen des öffentlichen Schlüsseltokens der Assistenten\-Assembly  
  
3.  Hinzufügen eines Verweises auf die Assistentenassembly in der Datei VSTEMPLATE für die Elementvorlage **Benutzerdefinierte Aktion**  
  
#### So signieren Sie die Assistenten\-Assembly mit einem starkem Namen  
  
1.  In **Projektmappen\-Explorer** öffnen Sie das Kontextmenü im **ItemTemplateWizard** Projektknoten, und wählen Sie dann **Eigenschaften** aus.  
  
2.  Aktivieren Sie auf der Registerkarte **Signierung** das Kontrollkästchen **Assembly signieren**.  
  
3.  In der Liste **Schlüsseldatei mit starkem Namen auswählen** wählen **\<New...\>** Sie aus.  
  
4.  Im Dialogfeld **Schlüssel für einen starken Namen erstellen** geben Sie einen Namen ein **Schlüsseldatei mit Kennwort schützen**, deaktivieren Sie das Kontrollkästchen, und wählen Sie dann die Schaltfläche **OK** aus.  
  
5.  Klicken Sie auf der Menüleiste wählen Sie **Erstellen**, **Projektmappe erstellen** aus.  
  
#### So rufen Sie das öffentliche Schlüsseltoken der Assistenten\-Assembly ab  
  
1.  In einem Visual Studio\-Eingabeaufforderungsfenster führen Sie den folgenden Befehl aus und *PathToWizardAssembly* mit dem vollständigen Pfad zur erstellten Assembly ItemTemplateWizard.dll für das Projekt ItemTemplateWizard auf dem Entwicklungscomputer ersetzen.  
  
    ```  
    sn.exe -T PathToWizardAssembly  
    ```  
  
     Das öffentliche Schlüsseltoken für die Assembly ItemTemplateWizard.dll wird in das Fenster der Visual Studio\-Eingabeaufforderung geschrieben.  
  
2.  Lassen Sie das Fenster der Visual Studio\-Eingabeaufforderung geöffnet.  Sie benötigen das öffentliche Schlüsseltoken, um die folgende Prozedur abzuschließen.  
  
#### So fügen Sie einen Verweis auf die Assistenten\-Assembly in der VSTEMPLATE\-Datei hinzu  
  
1.  In **Projektmappen\-Explorer** erweitern Sie den **ItemTemplate** Projektknoten, und öffnen Sie dann die Datei ItemTemplate.vstemplate.  
  
2.  Fügen Sie das folgende `WizardExtension`\-Element zwischen dem `</TemplateContent>`\-Tag und dem `</VSTemplate>`\-Tag am Ende der Datei hinzu.  Ersetzen Sie den *YourToken*`PublicKeyToken`\-Wert des Attributs durch das öffentliche Schlüsseltoken, das Sie im vorherigen Verfahren abgerufen haben.  
  
    ```  
    <WizardExtension>  
      <Assembly>ItemTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=YourToken</Assembly>  
      <FullClassName>ItemTemplateWizard.CustomActionWizard</FullClassName>  
    </WizardExtension>  
    ```  
  
     Weitere Informationen über das `WizardExtension`\-Element finden Sie unter [WizardExtension-Element &#40;Visual Studio-Vorlagen&#41;](../extensibility/wizardextension-element-visual-studio-templates.md).  
  
3.  Speichern und schließen Sie die Datei.  
  
## Hinzufügen von ersetzbaren Parametern zur Datei Elements.xml in der Elementvorlage  
 Fügen Sie der Datei Elements.xml im Projekt ItemTemplate\-Projekt mehrere ersetzbare Parameter hinzu.  Diese Parameter werden in der `PopulateReplacementDictionary`\-Methode in der zuvor definierten `CustomActionWizard`\-Klasse initialisiert.  Wenn ein Benutzer einem Projekt ein Projektelement Benutzerdefinierte Aktion hinzufügt, werden diese Parameter von Visual Studio in der Datei Elements.xml im neuen Projektelement automatisch durch die Werte ersetzt, die im Assistenten angegeben wurden.  
  
 Ein ersetzbarer Parameter ist ein Token, das mit einem Dollarzeichen \($\) beginnt und endet.  Zusätzlich zum Definieren eigener ersetzbaren Parameter, können Sie integrierte Parameter verwenden, die das SharePoint\-Projektsystem definiert und initialisiert.  Weitere Informationen finden Sie unter [Ersetzbare Parameter](../sharepoint/replaceable-parameters.md).  
  
#### So fügen Sie der Datei Elements.xml ersetzbare Parameter hinzu  
  
1.  im Projekt ItemTemplate ersetzen Sie den Inhalt der Datei Elements.xml durch folgendes XML.  
  
    ```  
  
    <Elements Id="$guid8$" xmlns="http://schemas.microsoft.com/sharepoint/">  
      <CustomAction Id="$IdValue$"  
                    GroupId="$GroupIdValue$"  
                    Location="$LocationValue$"  
                    Sequence="1000"  
                    Title="$TitleValue$"  
                    Description="$DescriptionValue$" >  
        <UrlAction Url="$UrlValue$"/>  
      </CustomAction>  
    </Elements>  
    ```  
  
     Durch das neue XML werden die Werte der Attribute `Id`, `GroupId`, `Location`, `Description` und `Url` in ersetzbare Parameter geändert.  
  
2.  Speichern und schließen Sie die Datei.  
  
## Hinzufügen des Assistenten zum VSIX\-Paket  
 In der source.extension.vsixmanifest\-Datei im VSIX\-Projekt, fügen Sie einen Verweis auf das Assistentenprojekt hinzu, damit es mit dem VSIX\-Paket bereitgestellt hat, das das Projektelement enthält.  
  
#### So fügen Sie den Assistenten dem VSIX\-Paket hinzu  
  
1.  In **Projektmappen\-Explorer** öffnen Sie das Kontextmenü aus der Datei **source.extension.vsixmanifest** im Projekt CustomActionProjectItem, und wählen Sie dann **Öffnen**, um die Datei im Manifest\-Editor zu öffnen.  
  
2.  im Manifest\-Editor **Objekte** wählen Sie die Registerkarte aus, und wählen Sie die Schaltfläche **Neu** aus.  
  
     Das Dialogfeld wird angezeigt. **Neue Anlage hinzufügen**  
  
3.  In der Liste wählen Sie **TypMicrosoft.VisualStudio.Assembly** aus.  
  
4.  In der Liste wählen Sie **QuelleEin Projekt in der aktuellen Projektmappe** aus.  
  
5.  In der Liste wählen Sie **ProjektItemTemplateWizard** aus und wählen dann die Schaltfläche **OK** aus.  
  
6.  Klicken Sie auf der Menüleiste wählen Sie **Erstellen**, **Projektmappe erstellen** aus, und überprüfen Sie, ob die Projektmappe fehlerfrei kompiliert.  
  
## Testen des Assistenten  
 Sie können den Assistenten jetzt testen.  Erstellen Sie zunächst, die Projektmappe CustomActionProjectItem in der experimentellen Instanz von Visual Studio debuggen.  Testen Sie den Assistenten für das Projektelement Benutzerdefinierte Aktion in einem SharePoint\-Projekt in der experimentellen Instanz von Visual Studio.  Erstellen und führen Sie zum Schluss das SharePoint\-Projekt aus, um sicherzustellen, dass die benutzerdefinierte Aktion ordnungsgemäß funktioniert.  
  
#### So starten, um die Projektmappe zu debuggen  
  
1.  Starten Sie Visual Studio erneut mit Administratorrechten, und öffnen Sie die Projektmappe CustomActionProjectItem.  
  
2.  Öffnen Sie im Projekt ItemTemplateWizard die CustomActionWizard\-Codedatei, und fügen Sie dann der ersten Codezeile in der \- Methode `RunStarted` hinzu.  
  
3.  Klicken Sie auf der Menüleiste wählen Sie **Debuggen**, **Ausnahmen** aus.  
  
4.  Im Dialogfeld **Ausnahmen**, überprüfen Sie, ob die **Ausgelöst** und Kontrollkästchen **Vom Benutzercode unbehandelt** für **Common Language Runtime\-Ausnahmen** gelöscht werden, und wählen Sie dann die Schaltfläche **OK** aus.  
  
5.  Starten Sie das Debuggen, indem Sie die F5\-TASTE, oder auf der Menüleiste auswählen und **Debuggen**, **Debuggen starten** auswählen.  
  
     Visual Studio installiert die Erweiterung in %UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\11.0Exp\\Extensions\\Contoso\\Custom Action Project Item\\1.0 und startet eine experimentelle Instanz von Visual Studio.  Sie testen das Projektelement in dieser Instanz von Visual Studio.  
  
#### So testen Sie den Assistenten in Visual Studio  
  
1.  Klicken Sie in der experimentellen Instanz von Visual Studio, in der Menüleiste, wählen Sie **Datei**, **Neu**, **Projekt** aus.  
  
2.  Erweitern Sie den **Visual C\#** oder Knoten **Visual Basic** \(abhängig von der Sprache der Elementvorlage unterstützten\), erweitern Sie den Knoten **SharePoint**, und wählen Sie dann den Knoten **2010** aus.  
  
3.  In der Liste der Projektvorlagen, wählen Sie **SharePoint 2010\-Projekt** aus, nennen Sie das Projekt **CustomActionWizardTest**, und wählen Sie dann die Schaltfläche **OK** aus.  
  
4.  In **Assistent zum Anpassen von SharePoint** geben Sie die URL der Website, die Sie zum Debuggen verwenden möchten, und wählen Sie dann die Schaltfläche **Fertig stellen** aus.  
  
5.  In **Projektmappen\-Explorer** öffnen Sie das Kontextmenü für den Projektknoten, wählen Sie **Hinzufügen** aus und wählen dann **Neues Element** aus.  
  
6.  Im **Neues Element hinzufügen – CustomItemWizardTest** Dialogfeld **SharePoint** erweitern Sie den Knoten, und erweitern Sie dann den Knoten **2010**.  
  
7.  In der Liste der Projektelemente, aktivieren Sie das **Benutzerdefinierte Aktion**\-Element aus, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.  
  
8.  Überprüfen Sie, ob die Codeausführung in der anderen Instanz von Visual Studio an dem Haltepunkt unterbrochen wird, den Sie zuvor in der `RunStarted`\-Methode festgelegt haben.  
  
9. Fahren Sie fort, um das Projekt zu debuggen, indem Sie die F5\-TASTE, oder auf der Menüleiste auswählen und **Debuggen**, **Weiter** auswählen.  
  
     Der Assistent zum Anpassen von SharePoint wird angezeigt.  
  
10. Die **Speicherort** wählen Sie das **Liste Bearbeiten** Optionsfeld.  
  
11. In der Liste wählen Sie **Gruppen\-IDKommunikation** aus.  
  
12. Im Feld geben Sie **TitelSharePoint\-Developer Center** ein.  
  
13. Im Feld geben Sie **BeschreibungÖffnet die SharePoint\-Developer Center\-Website** ein.  
  
14. Im Feld geben Sie **URLhttp:\/\/msdn.microsoft.com\/sharepoint\/default.aspx** ein und klicken Sie dann auf die Schaltfläche **Fertig stellen** aus.  
  
     isual Studio fügt ein Element, das **CustomAction1** dem Projekt mit dem Namen hinzu und öffnet die Datei Elements.xml im Editor.  Vergewissern Sie sich, dass Elements.xml die Werte enthält, die Sie im Assistenten angegeben haben.  
  
#### So testen Sie die benutzerdefinierte Aktion in SharePoint  
  
1.  Klicken Sie in der experimentellen Instanz von Visual Studio, wählen Sie die F5\-TASTE, oder auf der Menüleiste aus, wählen Sie **Debuggen**, **Debuggen starten** aus.  
  
     Die benutzerdefinierte Aktion wird verpackt und auf der SharePoint\-Website bereitgestellt, die von der Eigenschaft **Website\-URL** des Projekts angegeben wird, und der Webbrowser wird die Standardseite dieser Website.  
  
    > [!NOTE]  
    >  Wenn das Dialogfeld **Skriptdebugging deaktiviert** angezeigt wird, wählen Sie die Schaltfläche **Ja** aus.  
  
2.  Im Listenbereich der SharePoint\-Website, wählen Sie den **Aufgaben** Link aus.  
  
     Die **Aufgaben – Alle Aufgaben** Seite angezeigt wird.  
  
3.  Klicken Sie auf der **Listentools** Menübandregisterkarte, wählen Sie die Registerkarte und dann **Liste**, in der Gruppe **Einstellungen** auswählen, **Listeneinstellungen** aus.  
  
     Die Seite **Listeneinstellungen** angezeigt wird.  
  
4.  Die **Kommunikation**, das am oberen Rand der Seite vorangeht, wählen Sie den **SharePoint Developer Center** Link, überprüfen Sie, ob der Browser die Website http:\/\/msdn.microsoft.com\/sharepoint\/default.aspx öffnet, und schließen dann den Browser aus.  
  
## Bereinigen des Entwicklungscomputers  
 Nachdem Sie die Tests des Projektelements abgeschlossen haben, entfernen Sie die Projektelementvorlage aus der experimentellen Instanz von Visual Studio.  
  
#### So bereinigen Sie den Entwicklungscomputer  
  
1.  Klicken Sie in der experimentellen Instanz von Visual Studio, in der Menüleiste, wählen Sie **Tools**, **Erweiterungen und Updates** aus.  
  
     Das Dialogfeld wird geöffnet. **Erweiterungen und Updates**  
  
2.  In der Liste der Erweiterungen, wählen Sie die **Projektelement "Benutzerdefinierte Aktion"** Erweiterung aus, und wählen Sie dann die Schaltfläche **Deinstallieren** aus.  
  
3.  Im Dialogfeld, das angezeigt wird, wählen Sie die Schaltfläche **Ja**, um zu bestätigen, dass Sie die Erweiterung deinstallieren möchten, und wählen Sie dann die Schaltfläche **Jetzt neu starten**, um die Deinstallation abzuschließen.  
  
4.  Schließen Sie beide Instanzen von Visual Studio \(die experimentelle Instanz und die Instanz von Visual Studio, in der die Projektmappe geöffnet ist\).  
  
## Siehe auch  
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)   
 [Gewusst wie: Verwenden von Assistenten mit Projektvorlagen](~/extensibility/how-to-use-wizards-with-project-templates.md)   
 [Standardspeicherorte und \-IDs für benutzerdefinierte Aktionen](http://go.microsoft.com/fwlink/?LinkId=181964)  
  
  