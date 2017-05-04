---
title: "Exemplarische Vorgehensweise: Erstellen eines Projektelements &quot;Websitespalte&quot; mit einer Projektvorlage, Teil&#160;2 | Microsoft Docs"
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
  - "Projektelemente [SharePoint-Entwicklung in Visual Studio], Erstellen von Vorlagen-Assistenten"
  - "SharePoint-Projektelemente, Erstellen von Vorlagen-Assistenten"
  - "SharePoint-Entwicklung in Visual Studio, Definieren neuer Projektelementtypen"
ms.assetid: da14207d-ac09-41ba-b387-c7f881b2a366
caps.latest.revision: 54
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# Exemplarische Vorgehensweise: Erstellen eines Projektelements &quot;Websitespalte&quot; mit einer Projektvorlage, Teil&#160;2
  Nachdem Sie einen benutzerdefinierten Typ des SharePoint\-Projektelements definiert und diesen einer Projektvorlage in Visual Studio zugeordnet haben, empfiehlt es sich, außerdem einen Assistenten für die Vorlage bereitzustellen.  Mithilfe des Assistenten können Sie Informationen von Benutzern sammeln, während diese Ihre Vorlage verwenden, um ein neues Projekt zu erstellen, das das Projektelement enthält.  Mit den gesammelten Informationen kann das Projektelement initialisiert werden.  
  
 In dieser exemplarischen Vorgehensweise fügen Sie der Projektvorlage für Websitespalten einen Assistenten hinzu. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines Projektelements "Websitespalte" mit einer Projektvorlage, Teil 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).  Beim Erstellen eines Projekts für Websitespalten werden vom Assistenten Informationen zur Websitespalte \(z. B. Basistyp und Gruppe, in der die Spalte in der Websitespaltengalerie aufgeführt werden soll\) gesammelt und der Datei Elements.xml im neuen Projekt hinzugefügt.  
  
 Diese exemplarische Vorgehensweise enthält die folgenden Aufgaben:  
  
-   Erstellen eines Assistenten für einen benutzerdefinierten SharePoint\-Projektelementtyp, dem eine Projektvorlage zugeordnet ist.  
  
-   Definieren Sie eine benutzerdefinierte Assistenten\-Benutzeroberfläche, die den integrierten Visual Studio\-Assistenten für SharePoint\-Projekte ähnelt.  
  
-   Erstellen zweier *SharePoint\-Befehle* für Aufrufe in die lokale SharePoint\-Website während der Assistent ausgeführt wird.  SharePoint\-Befehle sind Methoden, mit denen Visual Studio\-Erweiterungsassemblys APIs im SharePoint\-Serverobjektmodell aufrufen können.  Weitere Informationen finden Sie unter [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
-   Initialisieren von SharePoint\-Projektdateien mit im Assistenten gesammelten Daten mithilfe von ersetzbaren Parametern  
  
-   Erstellen einer neuen SNK\-Datei in jeder neuen Projektinstanz für Websitespalten.  Mit dieser Datei wird die Projektausgabe signiert, sodass die SharePoint\-Projektmappenassembly im globalen Assemblycache bereitgestellt werden kann.  
  
-   Debuggen und Testen des Assistenten  
  
> [!NOTE]  
>  Ein Beispiel mit den abgeschlossenen Projekten, Code und weiteren Dateien für diese exemplarische Vorgehensweise können Sie unter folgender Adresse herunterladen:  [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=191369](http://go.microsoft.com/fwlink/?LinkId=191369).  
  
## Vorbereitungsmaßnahmen  
 Um diese exemplarische Vorgehensweise ausführen zu können, müssen Sie zuerst die Projektmappe SiteColumnProjectItem erstellen, indem Sie die [Exemplarische Vorgehensweise: Erstellen eines Projektelements "Websitespalte" mit einer Projektvorlage, Teil 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md) durcharbeiten.  
  
 Zum Durchführen dieser exemplarischen Vorgehensweise werden auf dem Entwicklungscomputer außerdem die folgenden Komponenten benötigt:  
  
-   Unterstützte Editionen von Windows, SharePoint und Visual Studio.  Weitere Informationen finden Sie unter [Anforderungen für die Entwicklung von SharePoint-Lösungen](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Das Visual Studio SDK.  Bei dieser exemplarischen Vorgehensweise wird mithilfe der **VSIX Project**\-Vorlage aus dem SDK ein VSIX\-Paket zum Bereitstellen des Projektelements erstellt.  Weitere Informationen finden Sie unter [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Kenntnisse der folgenden Konzepte sind hilfreich, wenn auch für die Durchführung der exemplarischen Vorgehensweise nicht erforderlich:  
  
-   Assistenten für Projekt\- und Elementvorlagen in Visual Studio.  Weitere Informationen finden Sie unter [Gewusst wie: Verwenden von Assistenten mit Projektvorlagen](../Topic/How%20to:%20Use%20Wizards%20with%20Project%20Templates.md) und der <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>\-Schnittstelle.  
  
-   Websitespalten in SharePoint  Weitere Informationen finden Sie unter [Spalten](http://go.microsoft.com/fwlink/?LinkId=183547).  
  
##  <a name="wizardcomponents"></a> Grundlegendes zu den Assistenten\-Komponenten  
 Der Assistent, der in dieser exemplarischen Vorgehensweise veranschaulicht wird, enthält mehrere Komponenten.  In der folgenden Tabelle werden diese Komponenten beschrieben.  
  
|Komponente|Beschreibung|  
|----------------|------------------|  
|Implementieren des Assistenten|Mit der `SiteColumnProjectWizard`\-Klasse wird die <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>\-Schnittstelle implementiert.  Diese Schnittstelle definiert die Methoden, die von Visual Studio aufgerufen werden, wenn der Assistent gestartet wird, wenn der Assistent beendet wird und gelegentlich, während der Assistent ausgeführt wird.|  
|Benutzeroberfläche des Assistenten|Dies ist ein WPF\-basiertes Fenster mit dem Namen `WizardWindow`.  Dieses Fenster enthält zwei Benutzersteuerelemente: `Page2` und `Page1`.  Diese Benutzersteuerelemente stellen die beiden Seiten des Assistenten dar.<br /><br /> In dieser exemplarischen Vorgehensweise wird die Benutzeroberfläche des Assistenten von der <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A>\-Methode der diesbezüglichen Implementierung dargestellt.|  
|Datenmodell des Assistenten|Hierbei handelt es sich um die Vermittlerklasse `SiteColumnWizardModel`, die eine Ebene zwischen der Benutzeroberfläche und der Implementierung des Assistenten bereitstellt.  In diesem Beispiel wird mithilfe der Klasse eine Abstrahierung zwischen der Implementierung und der Benutzeroberfläche des Assistenten vorgenommen. Diese Klasse ist keine erforderliche Komponenten von Assistenten.<br /><br /> In dieser exemplarischen Vorgehensweise wird von der Implementierung des Assistenten beim Anzeigen der entsprechenden Benutzeroberfläche `SiteColumnWizardModel`\-Objekt an das Fenster des Assistenten übergeben.  Die Methoden dieses Objekts dienen der Benutzeroberfläche des Assistenten zum Speichern der Werte von Steuerelementen in der Benutzeroberfläche sowie zum Durchführen von Aufgaben wie die Validierung der eingegebenen Website\-URL.  Nachdem der Assistent vom Benutzer beendet wurde, wird der abschließende Zustand der Benutzeroberfläche von der Implementierung des Assistenten mit dem `SiteColumnWizardModel`\-Objekt bestimmt.|  
|Projektsignierungs\-Manager|Mit der Hilfsklasse `ProjectSigningManager` wird von der Implementierung des Assistenten eine neue key.snk\-Datei in jeder neuen Projektinstanz erstellt.|  
|SharePoint\-Befehle|Mit diesen Methoden werden vom Datenmodell des Assistenten während der Ausführung des Assistenten Aufrufe in die lokale SharePoint\-Website durchgeführt.  Da SharePoint\-Befehle .NET Framework 3.5 zum Ziel haben müssen, werden diese Befehle in einer anderen Assembly als der übrige Code des Assistenten implementiert.|  
  
## Erstellen der Projekte  
 Um diese exemplarische Vorgehensweise ausführen zu können, müssen Sie der Projektmappe SiteColumnProjectItem, die Sie in [Exemplarische Vorgehensweise: Erstellen eines Projektelements "Websitespalte" mit einer Projektvorlage, Teil 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md) erstellt haben, mehrere Projekte hinzufügen:  
  
-   Ein WPF\-Projekt.  In diesem Projekt implementieren Sie die <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>\-Schnittstelle, und Sie definieren die Assistenten\-Benutzeroberfläche.  
  
-   Ein Klassenbibliotheksprojekt, mit dem die benutzerdefinierten SharePoint\-Befehle definiert werden.  Für dieses Projekt muss .NET Framework 3.5 als Zielversion verwendet werden.  
  
 Beginnen Sie mit der exemplarischen Vorgehensweise, indem Sie beide Projekte erstellen.  
  
#### So erstellen Sie das WPF\-Projekt  
  
1.  Öffnen Sie in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] die Projektmappe "SiteColumnProjectItem".  
  
2.  Öffnen Sie im **Projektmappen\-Explorer** das Kontextmenü des **SiteColumnProjectItem**\-Knotens, und wählen Sie **Hinzufügen** und dann **Neues Projekt** aus.  
  
    > [!NOTE]  
    >  In Visual Basic\-Projekten wird der Projektmappenknoten nur angezeigt, wenn das Kontrollkästchen **Projektmappe immer anzeigen** im [NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/de-de/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca) aktiviert ist.  
  
3.  Stellen Sie im oberen Bereich des Dialogfelds **Neues Projekt hinzufügen** sicher, dass in der Liste der .NET Framework\-Versionen **.NET Framework 4.5** ausgewählt ist.  
  
4.  Erweitern Sie den **Visual C\#**\-Knoten oder den **Visual Basic**\-Knoten, und wählen Sie den **Windows**\-Knoten aus.  
  
5.  Wählen Sie aus der Liste der Projektvorlagen **WPF\-Benutzersteuerelementbibliothek** aus, nennen Sie das Projekt **ProjectTemplateWizard**, und wählen Sie dann die Schaltfläche **OK** aus.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fügt das Projekt **ProjectTemplateWizard** der Projektmappe hinzu und öffnet die Standarddatei "UserControl1.xaml".  
  
6.  Löschen Sie die Datei UserControl1.xaml aus dem Projekt.  
  
#### So erstellen Sie das SharePoint\-Befehlsprojekt  
  
1.  Öffnen Sie im **Projektmappen\-Explorer** das Kontextmenü für den SiteColumnProjectItem\-Knoten, und wählen Sie **Hinzufügen** und dann **Neues Projekt**  aus.  
  
2.  Wählen Sie im oberen Bereich des Dialogfelds **Neues Projekt hinzufügen** in der Liste der .NET Framework\-Versionen **.NET Framework 3.5** aus.  
  
3.  Erweitern Sie den **Visual C\#**\-Knoten oder den **Visual Basic**\-Knoten, und wählen Sie dann den **Windows**\-Knoten aus.  
  
4.  Wählen Sie die Projektvorlage **Klassenbibliothek** aus, nennen Sie das Projekt **SharePointCommands**, und wählen Sie dann die Schaltfläche **OK** aus.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fügt das Projekt **SharePointCommands** zur Projektmappe hinzu und öffnet die Standardcodedatei "Class1".  
  
5.  Löschen Sie die Class1\-Codedatei aus dem Projekt.  
  
## Konfigurieren der Projekte  
 Bevor Sie den Assistenten erstellen, müssen Sie den Projekten einige Codedateien und Assemblyverweise hinzufügen.  
  
#### So konfigurieren Sie ein Assistentenprojekt  
  
1.  Öffnen Sie im **Projektmappen\-Explorer** das Kontextmenü für den **ProjectTemplateWizard**\-Projektknoten, und wählen Sie dann **Eigenschaften** aus.  
  
2.  Wählen Sie im **Projekt\-Designer** für ein Visual C\#\-Projekt die Registerkarte **Anwendung** bzw. für ein Visual Basic\-Projekt die Registerkarte **Kompilieren** aus.  
  
3.  Stellen Sie sicher, dass für das Zielframework .NET Framework 4.5 und nicht .NET Framework 4.5 Client Profile festgelegt ist.  
  
     Weitere Informationen finden Sie unter [Gewusst wie: .NET Framework-Version als Ziel](../Topic/How%20to:%20Target%20a%20Version%20of%20the%20.NET%20Framework.md).  
  
4.  Öffnen Sie das Kontextmenü des Projekts **ProjectTemplateWizard**, und wählen Sie **Hinzufügen** und dann **Neues Element** aus.  
  
5.  Wählen Sie das **Fenster \(WPF\)**\-Element aus, nennen Sie das Element **WizardWindow**, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.  
  
6.  Fügen Sie dem Projekt zwei **Benutzersteuerelement \(WPF\)**\-Elemente hinzu, und nennen Sie diese **Page1** und **Page2**.  
  
7.  Fügen Sie dem Projekt vier Codedateien mit den folgenden Namen hinzu:  
  
    -   SiteColumnProjectWizard  
  
    -   SiteColumnWizardModel  
  
    -   ProjectSigningManager  
  
    -   CommandIds  
  
8.  Öffnen Sie das Kontextmenü des **ProjectTemplateWizard**\-Projektknotens, und wählen Sie dann **Verweis hinzufügen** aus.  
  
9. Erweitern Sie den **Assemblys**\-Knoten, wählen Sie den **Erweiterungen**\-Knoten aus, und aktivieren Sie dann die Kontrollkästchen neben den folgenden Assemblys:  
  
    -   EnvDTE  
  
    -   Microsoft.VisualStudio.OLE.Interop  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.Shell.11.0  
  
    -   Microsoft.VisualStudio.Shell.Interop.10.0  
  
    -   Microsoft.VisualStudio.Shell.Interop.11.0  
  
    -   Microsoft.VisualStudio.TemplateWizardInterface  
  
10. Wählen Sie die Schaltfläche **OK** aus, um die Assemblys dem Projekt hinzuzufügen.  
  
11. Wählen Sie im **Projektmappen\-Explorer** im Ordner **Verweise** für das Projekt **ProjectTemplateWizard** die **EnvDTE**\-Assembly aus.  
  
    > [!NOTE]  
    >  In Visual Basic\-Projekten wird der Ordner **Verweise** nur angezeigt, wenn das Kontrollkästchen **Projektmappe immer anzeigen** in [NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/de-de/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca) aktiviert ist.  
  
12. Ändern Sie im Fenster **Eigenschaften** den Wert der Eigenschaft **Interoptypen einbetten** in **False**.  
  
13. Wenn Sie ein Visual Basic\-Projekt entwickeln, importieren Sie mit dem **Projekt\-Designer** den ProjectTemplateWizard\-Namespace in das Projekt.  
  
     Weitere Informationen finden Sie unter [Gewusst wie: Hinzufügen oder Entfernen von importierten Namespaces &#40;Visual Basic&#41;](../Topic/How%20to:%20Add%20or%20Remove%20Imported%20Namespaces%20(Visual%20Basic).md).  
  
#### So konfigurieren Sie das SharePointCommands\-Projekt  
  
1.  Wählen Sie im **Projektmappen\-Explorer** den **SharePointCommands**\-Projektknoten aus.  
  
2.  Wählen Sie in der Menüleiste **Projekt** und dann **Vorhandenes Element hinzufügen** aus.  
  
3.  Wechseln Sie im Dialogfeld **Vorhandenes Element hinzufügen** zu dem Ordner, der die Codedateien für das Projekt "ProjectTemplateWizard" enthält, und wählen Sie dann die Codedatei **CommandIds** aus.  
  
4.  Wählen Sie den Pfeil neben der Schaltfläche **Hinzufügen** aus. Wählen Sie anschließend im daraufhin angezeigten Menü die Option **Als Link hinzufügen** aus.  
  
     Die Codedatei wird dem Projekt **SharePointCommands** von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] als Link hinzugefügt.  Die Codedatei befindet sich im Projekt **ProjectTemplateWizard**, der darin enthaltene Code wird jedoch auch im Projekt **SharePointCommands** kompiliert.  
  
5.  Fügen Sie im Projekt **SharePointCommands** eine weitere Codedatei mit dem Namen "Commands" hinzu.  
  
6.  Wählen Sie das Projekt "SharePointCommands" und anschließend in der Menüleiste **Projekt** sowie **Verweis hinzufügen** aus.  
  
7.  Erweitern Sie den **Assemblys**\-Knoten, wählen Sie den **Erweiterungen**\-Knoten aus, und aktivieren Sie dann die Kontrollkästchen neben den folgenden Assemblys:  
  
    -   Microsoft.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
8.  Wählen Sie die Schaltfläche **OK** aus, um die Assemblys dem Projekt hinzuzufügen.  
  
## Erstellen von Assistentenmodellen, Signatur\-Managern und SharePoint\-Befehls\-IDs  
 Fügen Sie dem Projekt ProjectTemplateWizard Code hinzu, um die folgenden Komponenten im Beispiel zu implementieren:  
  
-   Die SharePoint\-Befehls\-IDs.  Durch diese Zeichenfolgen werden die vom Assistenten verwendeten SharePoint\-Befehle identifiziert.  Im weiteren Verlauf dieser exemplarischen Vorgehensweise fügen Sie Code zum Projekt "SharePointCommands" hinzu, um die Befehle zu implementieren.  
  
-   Das Datenmodell des Assistenten.  
  
-   Der Signatur\-Manager für Projekte.  
  
 Weitere Informationen zu diesen Komponenten finden Sie unter [Grundlegendes zu den Assistenten\-Komponenten](#wizardcomponents).  
  
#### So definieren Sie die SharePoint\-Befehls\-IDs  
  
1.  Öffnen Sie im Projekt "ProjectTemplateWizard" die Codedatei "CommandIds", und ersetzen Sie den gesamten Inhalt dieser Datei durch den folgenden Code.  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#5](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/commandids.cs#5)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#5](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/vb/projecttemplatewizard/commandids.vb#5)]  
  
#### So erstellen Sie das Assistentenmodell  
  
1.  Öffnen Sie die Codedatei "SiteColumnWizardModel", und ersetzen Sie den gesamten Inhalt dieser Datei durch den folgenden Code.  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#6](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/sitecolumnwizardmodel.cs#6)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#6](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/vb/projecttemplatewizard/sitecolumnwizardmodel.vb#6)]  
  
#### So erstellen Sie den Signatur\-Manager für Projekte  
  
1.  Öffnen Sie die Codedatei "ProjectSigningManager", und ersetzen Sie dann den gesamten Inhalt dieser Datei durch den folgenden Code.  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#8](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/projectsigningmanager.cs#8)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#8](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/vb/projecttemplatewizard/projectsigningmanager.vb#8)]  
  
## Erstellen der Assistenten\-Benutzeroberfläche  
 Fügen Sie XAML hinzu, um die Benutzeroberfläche des Fensters für den Assistenten zu definieren, sowie die beiden Benutzersteuerelemente, die die Benutzeroberfläche für die Seiten des Assistenten bereitstellen, und fügen Sie Code hinzu, um das Verhalten des Fensters und der Benutzersteuerelemente zu definieren.  Der erstellte Assistent ähnelt dem integrierten Assistenten für SharePoint\-Projekte in Visual Studio.  
  
> [!NOTE]  
>  In den folgenden Schritten treten mehrere Compilerfehler im Projekt auf, nachdem Sie diesem XAML oder Code hinzugefügt haben.  Diese Fehler werden durch Code behoben, den Sie in späteren Schritten hinzufügen.  
  
#### So erstellen Sie die Benutzeroberfläche für das Fenster des Assistenten  
  
1.  Öffnen Sie im Projekt "ProjectTemplateWizard" das Kontextmenü der Datei "WizardWindow.xaml", und wählen Sie dann **Öffnen** aus, um das Fenster im Designer anzuzeigen.  
  
2.  Ersetzen Sie in der XAML\-Ansicht des Designers das aktuelle XAML durch das folgende XAML.  Mit dem XAML wird eine Benutzeroberfläche einschließlich einer Überschrift, einem <xref:System.Windows.Controls.Grid> mit den Seiten des Assistenten sowie Navigationsschaltflächen unten im Fenster definiert.  
  
     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#10](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/wizardwindow.xaml#10)]  
  
    > [!NOTE]  
    >  Das mit dieser XAML erstellte Fenster wird von der <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>\-Basisklasse abgeleitet.  Wenn Sie Visual Studio ein benutzerdefiniertes WPF\-Dialogfeld hinzufügen, wird empfohlen, das Dialogfeld von dieser Klasse abzuleiten, um ein einheitliches Aussehen mit anderen Dialogfeldern von Visual Studio sicherzustellen und Probleme mit modalen Dialogfeldern zu vermeiden, die andernfalls auftreten können.  Weitere Informationen finden Sie unter [Erstellen und Verwalten von modalen Dialogfeldern](../extensibility/creating-and-managing-modal-dialog-boxes.md).  
  
3.  Wenn Sie ein Visual Basic\-Projekt entwickeln, entfernen Sie den `ProjectTemplateWizard`\-Namespace aus dem `WizardWindow`\-Klassennamen im `x:Class`\-Attribut des `Window`\-Elements.  Dieses Element befindet sich in der ersten XAML\-Zeile.  Anschließend sollte die erste Zeile wie im folgenden Beispiel dargestellt lauten.  
  
    ```  
    <Window x:Class="WizardWindow"  
    ```  
  
4.  Öffnen Sie die CodeBehind\-Datei für die Datei WizardWindow.xaml.  
  
5.  Ersetzen Sie den Inhalt dieser Datei mit Ausnahme der `using`\-Deklarationen am Dateianfang durch den folgenden Code.  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#4](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/wizardwindow.xaml.cs#4)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#4](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/vb/projecttemplatewizard/wizardwindow.xaml.vb#4)]  
  
#### So erstellen Sie die Benutzeroberfläche für die erste Seite des Assistenten  
  
1.  Öffnen Sie im Projekt "ProjectTemplateWizard" das Kontextmenü der Datei "Page1.xaml", und wählen Sie dann **Öffnen** aus, um das Benutzersteuerelement im Designer anzuzeigen.  
  
2.  Ersetzen Sie in der XAML\-Ansicht des Designers das aktuelle XAML durch das folgende XAML.  Vom XAML wird eine Benutzeroberfläche mit einem Textfeld definiert, in dem Benutzer die URL der lokalen Websites eingeben können, die sie zum Debuggen verwenden möchten.  Die Benutzeroberfläche weist zudem Optionsfelder auf, mit denen Benutzer angeben können, ob es sich um ein Sandkastenprojekt handelt.  
  
     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#11](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/page1.xaml#11)]  
  
3.  Wenn Sie ein Visual Basic\-Projekt entwickeln, entfernen Sie den `ProjectTemplateWizard`\-Namespace aus dem `Page1`\-Klassennamen im `x:Class`\-Attribut des `UserControl`\-Elements.  Dies erfolgt in der ersten Zeile des XAML.  Anschließend sollte die erste Zeile wie folgt aussehen.  
  
    ```  
    <UserControl x:Class="Page1"  
    ```  
  
4.  Ersetzen Sie den Inhalt der Datei "Page1.xaml" mit Ausnahme der `using`\-Deklarationen am Dateianfang durch den folgenden Code.  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/page1.xaml.cs#2)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/vb/projecttemplatewizard/page1.xaml.vb#2)]  
  
#### So erstellen Sie die Benutzeroberfläche für die zweite Seite des Assistenten  
  
1.  Öffnen Sie im Projekt "ProjectTemplateWizard" das Kontextmenü der Datei "Page2.xaml", und wählen Sie dann **Öffnen** aus.  
  
     Das Benutzersteuerelement wird im Designer geöffnet.  
  
2.  Ersetzen Sie in der XAML\-Ansicht das aktuelle durch folgendes XAML.  Mit dem XAML wird eine Benutzeroberfläche einschließlich einer Dropdownliste zum Auswählen des Basistyps der Websitespalte, eines Kombinationsfelds zum Angeben der integrierten oder benutzerdefinierten Gruppe, unter der die Websitespalte im Katalog angezeigt werden soll, sowie eines Textfelds zum Angeben des Namens der Websitespalte definiert.  
  
     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#12](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/page2.xaml#12)]  
  
3.  Wenn Sie ein Visual Basic\-Projekt entwickeln, entfernen Sie den `ProjectTemplateWizard`\-Namespace aus dem `Page2`\-Klassennamen im `x:Class`\-Attribut des `UserControl`\-Elements.  Dies erfolgt in der ersten Zeile des XAML.  Anschließend sollte die erste Zeile wie folgt aussehen.  
  
    ```  
    <UserControl x:Class="Page2"  
    ```  
  
4.  Ersetzen Sie den Inhalt der CodeBehind\-Datei für die Datei "Page2.xaml" mit Ausnahme der `using`\-Deklarationen am Dateianfang durch den folgenden Code.  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#3](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/page2.xaml.cs#3)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#3](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/vb/projecttemplatewizard/page2.xaml.vb#3)]  
  
## Implementieren des Assistenten  
 Definieren Sie die wichtigsten Funktionen des Assistenten, indem Sie die <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>\-Schnittstelle implementieren.  Diese Schnittstelle definiert die Methoden, die von Visual Studio aufgerufen werden, wenn der Assistent gestartet wird, wenn der Assistent beendet wird und gelegentlich, während der Assistent ausgeführt wird.  
  
#### So implementieren Sie den Assistenten  
  
1.  Öffnen Sie die Codedatei SiteColumnProjectWizard im Projekt ProjectTemplateWizard.  
  
2.  Ersetzen Sie den gesamten Inhalt der Datei durch folgenden Code:  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#7](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/sitecolumnprojectwizard.cs#7)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#7](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/vb/projecttemplatewizard/sitecolumnprojectwizard.vb#7)]  
  
## Erstellen der SharePoint\-Befehle  
 Erstellen Sie zwei benutzerdefinierte Befehle, die einen Aufruf in das SharePoint\-Serverobjektmodell durchführen.  Mit einem Befehl wird angegeben, ob die Website\-URL, die vom Benutzer im Assistenten eingegeben wird, gültig ist.  Mit dem anderen Befehl werden alle Feldtypen von der angegebenen SharePoint\-Website abgerufen, sodass Benutzer auswählen können, welcher Typ als Basis für die neue Websitespalte verwendet werden soll.  
  
#### So definieren Sie die SharePoint\-Befehle  
  
1.  Öffnen Sie die Codedatei Commands im Projekt **SharePointCommands**.  
  
2.  Ersetzen Sie den gesamten Inhalt der Datei durch folgenden Code:  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#9](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/sharepointcommands/commands.cs#9)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#9](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/vb/sharepointcommands/commands.vb#9)]  
  
## Checkpoint  
 Ab diesem Punkt in der exemplarischen Vorgehensweise wurde der gesamte für den Assistenten benötigte Code in das Projekt eingefügt.  Erstellen Sie das Projekt, um sicherzustellen, dass es ohne Fehler kompiliert wird.  
  
#### So erstellen Sie das Projekt  
  
1.  Wählen Sie in der Menüleiste **Erstellen**, **Projektmappe erstellen**.  
  
## Entfernen der Datei key.snk aus der Projektvorlage  
 In der [Exemplarische Vorgehensweise: Erstellen eines Projektelements "Websitespalte" mit einer Projektvorlage, Teil 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md) enthält die Projektvorlage, die Sie erstellt haben, eine key.snk\-Datei, mit der die einzelnen Projektinstanzen für Websitespalten signiert werden.  Diese key.snk\-Datei wird nicht mehr benötigt, da vom Assistenten nun eine neue key.snk\-Datei für jedes Projekt generiert wird.  Entfernen Sie die key.snk\-Datei aus der Projektvorlage, und entfernen Sie die Verweise auf die Datei.  
  
#### So entfernen Sie die key.snk\-Datei aus der Projektvorlage  
  
1.  Öffnen Sie im **Projektmappen\-Explorer** unter dem **SiteColumnProjectTemplate**\-Knoten das Kontextmenü der Datei **key.snk**, und wählen Sie dann **Löschen** aus.  
  
2.  Wählen Sie im daraufhin angezeigten Bestätigungsdialogfeld die Schaltfläche **OK** aus.  
  
3.  Öffnen Sie unter dem **SiteColumnProjectTemplate**\-Knoten die Datei "SiteColumnProjectTemplate.vstemplate", und entfernen Sie dann das folgende Element daraus.  
  
    ```  
    <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>  
    ```  
  
4.  Speichern und schließen Sie die Datei.  
  
5.  Öffnen Sie unter dem **SiteColumnProjectTemplate**\-Knoten die Datei "ProjectTemplate.csproj" oder "ProjectTemplate.vbproj", und entfernen Sie dann das folgende `PropertyGroup`\-Element daraus.  
  
    ```  
    <PropertyGroup>  
      <SignAssembly>true</SignAssembly>  
      <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>  
    </PropertyGroup>  
    ```  
  
6.  Entfernen Sie das folgende `None`\-Element:  
  
    ```  
    <None Include="key.snk" />  
    ```  
  
7.  Speichern und schließen Sie die Datei.  
  
## Zuordnen des Assistenten zur Projektvorlage  
 Nach der Implementierung des Assistenten muss dieser der Projektvorlage **Websitespalte** zugeordnet werden.  Hierzu müssen drei Verfahren ausgeführt werden:  
  
1.  Signieren der Assistenten\-Assembly mit einem starkem Namen  
  
2.  Abrufen des öffentlichen Schlüsseltokens der Assistenten\-Assembly  
  
3.  Fügen Sie der VSTEMPLATE\-Datei für die Projektvorlage **Websitespalte** einen Verweis auf die Assistenten\-Assembly hinzu.  
  
#### So signieren Sie die Assistenten\-Assembly mit einem starkem Namen  
  
1.  Öffnen Sie im **Projektmappen\-Explorer** das Kontextmenü des Projekts **ProjectTemplateWizard**, und wählen Sie dann **Eigenschaften** aus.  
  
2.  Aktivieren Sie auf der Registerkarte **Signierung** das Kontrollkästchen **Assembly signieren**.  
  
3.  Wählen Sie in der Liste **Schlüsseldatei mit starkem Namen auswählen** die Option **\<Neu...\>** aus.  
  
4.  Geben Sie im Dialogfeld **Schlüssel für einen starken Namen erstellen** einen Namen für die neue Schlüsseldatei ein, deaktivieren Sie das Kontrollkästchen **Schlüsseldatei mit Kennwort schützen**, und wählen Sie dann die Schaltfläche **OK** aus.  
  
5.  Öffnen Sie das Kontextmenü des Projekts **ProjectTemplateWizard**, und wählen Sie dann **Erstellen** aus, um die Datei "ProjectTemplateWizard.dll" zu erstellen.  
  
#### So rufen Sie das öffentliche Schlüsseltoken der Assistenten\-Assembly ab  
  
1.  Wählen Sie im **Startmenü** nacheinander **Alle Programme**, **Microsoft Visual Studio**, **Visual Studio\-Tools** und dann **Developer\-Eingabeaufforderung für VS2012** aus.  
  
     Ein Visual Studio\-Eingabeaufforderungsfenster wird geöffnet.  
  
2.  Ersetzen Sie durch Ausführen des folgenden Befehls den *PathToWizardAssembly* durch den vollständigen Pfad zur erstellten "ProjectTemplateWizard.dll"\-Assembly für das Projekt "ProjectTemplateWizard" auf dem Entwicklungscomputer:  
  
    ```  
    sn.exe -T PathToWizardAssembly  
    ```  
  
     Das öffentliche Schlüsseltoken für die Assembly ProjectTemplateWizard.dll wird in das Fenster der Visual Studio\-Eingabeaufforderung geschrieben.  
  
3.  Lassen Sie das Fenster der Visual Studio\-Eingabeaufforderung geöffnet.  Sie benötigen das öffentliche Schlüsseltoken während der nächsten Prozedur.  
  
#### So fügen Sie einen Verweis auf die Assistenten\-Assembly in der VSTEMPLATE\-Datei hinzu  
  
1.  Erweitern Sie im **Projektmappen\-Explorer** den Projektknoten **SiteColumnProjectTemplate**, und öffnen Sie die Datei SiteColumnProjectTemplate.vstemplate.  
  
2.  Fügen Sie das folgende `WizardExtension`\-Element zwischen dem `</TemplateContent>`\-Tag und dem `</VSTemplate>`\-Tag am Ende der Datei hinzu.  Ersetzen Sie den *your token*\-Wert im `PublicKeyToken`\-Attribut durch das öffentliche Schlüsseltoken, das Sie in der vorherigen Prozedur abgerufen haben.  
  
    ```  
    <WizardExtension>  
      <Assembly>ProjectTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=your token</Assembly>  
      <FullClassName>ProjectTemplateWizard.SiteColumnProjectWizard</FullClassName>  
    </WizardExtension>  
    ```  
  
     Weitere Informationen über das `WizardExtension`\-Element finden Sie unter [WizardExtension-Element &#40;Visual Studio-Vorlagen&#41;](../extensibility/wizardextension-element-visual-studio-templates.md).  
  
3.  Speichern und schließen Sie die Datei.  
  
## Hinzufügen von ersetzbaren Parametern zur Datei Elements.xml in der Projektvorlage  
 Fügen Sie der Datei Elements.xml im Projekt SiteColumnProjectTemplate mehrere ersetzbare Parameter hinzu.  Diese Parameter werden in der `RunStarted`\-Methode in der zuvor definierten `SiteColumnProjectWizard`\-Klasse initialisiert.  Wenn ein Websitespaltenprojekt von einem Benutzer erstellt wird, werden diese Parameter von Visual Studio in der Datei Elements.xml im neuen Projektelement automatisch durch die Werte ersetzt, die im Assistenten angegeben wurden.  
  
 Ein ersetzbarer Parameter ist ein Token, das mit einem Dollarzeichen \($\) beginnt und endet.  Zusätzlich zu den selbst definierten ersetzbaren Parametern können Sie auch integrierte Parameter verwenden, die vom SharePoint\-Projektsystem definiert und initialisiert werden.  Weitere Informationen finden Sie unter [Ersetzbare Parameter](../sharepoint/replaceable-parameters.md).  
  
#### So fügen Sie der Datei Elements.xml ersetzbare Parameter hinzu  
  
1.  Ersetzen Sie im Projekt "SiteColumnProjectTemplate" den Inhalt der Datei "Elements.xml" durch das folgende XML.  
  
    ```  
  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <Field ID="{$guid5$}"   
             Name="$fieldname$"   
             DisplayName="$fieldname$"   
             Type="$selectedfieldtype$"   
             Group="$selectedgrouptype$">  
      </Field>  
    </Elements>  
    ```  
  
     Durch das neue XML werden die Werte der Attribute `Name`, `DisplayName`, `Type` und `Group` in benutzerdefinierte ersetzbare Parameter geändert.  
  
2.  Speichern und schließen Sie die Datei.  
  
## Hinzufügen des Assistenten zum VSIX\-Paket  
 Um den Assistenten mit dem VSIX\-Paket und der Projektvorlage für Websitespalten bereitzustellen, fügen Sie der Datei source.extension.vsixmanifest im VSIX\-Projekt Verweise auf das Assistentenprojekt und das SharePoint\-Befehlsprojekt hinzu.  
  
#### So fügen Sie den Assistenten dem VSIX\-Paket hinzu  
  
1.  Öffnen Sie im **Projektmappen\-Explorer** im Projekt **SiteColumnProjectItem** das Kontextmenü der Datei **source.extension.vsixmanifest**, und wählen Sie dann **Öffnen** aus.  
  
     Die Datei wird von Visual Studio im Manifest\-Editor geöffnet.  
  
2.  Wählen Sie im Editor auf der Registerkarte **Objekte** die Schaltfläche **Neu** aus.  
  
     Das Dialogfeld **Neue Anlage hinzufügen** wird geöffnet.  
  
3.  Wählen Sie in der Liste **Typ** die Option **Microsoft.VisualStudio.Assembly** aus.  
  
4.  Wählen Sie in der Liste **Quelle** die Option **Ein Projekt in der aktuellen Projektmappe** aus.  
  
5.  Wählen Sie in der Liste **Projekt** die Option **ProjectTemplateWizard** und dann die Schaltfläche **OK** aus.  
  
6.  Wählen Sie im Editor auf der Registerkarte **Objekte** erneut die Schaltfläche **Neu** aus.  
  
     Das Dialogfeld **Neue Anlage hinzufügen** wird geöffnet.  
  
7.  Geben Sie in der Liste **Typ** die Zeichenfolge **SharePoint.Commands.v4** ein.  
  
8.  Wählen Sie in der Liste **Quelle** die Option **Ein Projekt in der aktuellen Projektmappe** aus.  
  
9. Wählen Sie in der Liste **Projekt** das Projekt **SharePointCommands** und dann die Schaltfläche **OK** aus.  
  
10. Wählen Sie in der Menüleiste **Erstellen** und **Projektmappe erstellen** aus, und überprüfen Sie dann, ob die Projektmappe fehlerfrei erstellt wird.  
  
## Testen des Assistenten  
 Sie können den Assistenten jetzt testen.  Debuggen Sie die Projektmappe SiteColumnProjectItem zunächst in der experimentellen Instanz von Visual Studio.  Anschließend testen Sie den Assistenten für das Websitespaltenprojekt in der experimentellen Instanz von Visual Studio.  Erstellen und führen Sie zum Schluss das Projekt aus, um sicherzustellen, dass die Websitespalte ordnungsgemäß funktioniert.  
  
#### So debuggen Sie die Projektmappe  
  
1.  Starten Sie Visual Studio erneut mit Administratoranmeldeinformationen, und öffnen Sie dann die Projektmappe "SiteColumnProjectItem".  
  
2.  Öffnen Sie im Projekt "ProjectTemplateWizard" die Codedatei "SiteColumnProjectWizard", und fügen Sie dann der ersten Codezeile in der `RunStarted`\-Methode einen Haltepunkt hinzu.  
  
3.  Wählen Sie in der Menüleiste **Debuggen** und **Ausnahmen** aus.  
  
4.  Stellen Sie im Dialogfeld **Ausnahmen** sicher, dass die Kontrollkästchen **Ausgelöst** und **Vom Benutzercode unbehandelt** für **Common Language Runtime\-Ausnahmen** deaktiviert sind, und wählen Sie dann die Schaltfläche **OK** aus.  
  
5.  Drücken Sie die **F5**\-Taste oder wählen Sie in der Menüleiste **Debuggen** und **Debugging starten** aus, um das Debuggen zu starten.  
  
     Die Erweiterung wird unter "%UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\11.0Exp\\Extensions\\Contoso\\Websitespalte\\1.0 installiert", und eine experimentelle Instanz von Visual Studio wird gestartet.  Sie testen das Projektelement in dieser Instanz von Visual Studio.  
  
#### So testen Sie den Assistenten in Visual Studio  
  
1.  Wählen Sie in der experimentellen Visual Studio\-Instanz in der Menüleiste **Datei**, **Neu** und **Projekt** aus.  
  
2.  Erweitern Sie den **Visual C\#**\-Knoten oder den **Visual Basic**\-Knoten \(je nach der von der Projektvorlage unterstützten Sprache\), erweitern Sie den **SharePoint**\-Knoten, und wählen Sie dann den **2010**\-Knoten aus.  
  
3.  Wählen Sie in der Liste der Projektvorlagen **Websitespalte** aus, nennen Sie das Projekt **SiteColumnWizardTest**, und wählen Sie dann die Schaltfläche **OK** aus.  
  
4.  Überprüfen Sie, ob die Codeausführung in der anderen Instanz von Visual Studio an dem Haltepunkt unterbrochen wird, den Sie zuvor in der `RunStarted`\-Methode festgelegt haben.  
  
5.  Setzen Sie das Debuggen fort, indem Sie die **F5**\-Taste drücken oder in der Menüleiste **Debuggen** und **Fortsetzen** auswählen.  
  
6.  Geben Sie im **Assistenten zum Anpassen von SharePoint** die URL der Website ein, die Sie zum Debuggen verwenden möchten, und wählen Sie dann die Schaltfläche **Weiter** aus.  
  
7.  Wählen Sie auf der zweiten Seite des **Assistenten zum Anpassen von SharePoint** folgende Elemente aus:  
  
    -   Wählen Sie in der Liste **Typ** die Option **Boolesch** aus.  
  
    -   Wählen Sie in der Liste **Gruppe** die Option **Benutzerdefinierte Ja\/Nein\-Spalten** aus.  
  
    -   Geben Sie im Feld **Name** die Bezeichnung "Meine Ja\/Nein\-Spalte" ein, und wählen Sie dann die Schaltfläche **Fertig stellen** aus.  
  
     Im **Projektmappen\-Explorer** wird ein neues Projekt angezeigt, das ein Projektelement mit dem Namen **Field1** aufweist, und im Editor von Visual Studio wird die Datei "Elements.xml" des Projekts geöffnet.  
  
8.  Vergewissern Sie sich, dass Elements.xml die Werte enthält, die Sie im Assistenten angegeben haben.  
  
#### So testen Sie die Websitespalte in SharePoint  
  
1.  Drücken Sie in der experimentellen Instanz von Visual Studio die F5\-Taste.  
  
     Die Websitespalte wird verpackt und auf der SharePoint\-Website bereitgestellt, die in der **Website\-URL**\-Eigenschaft des Projekts angegeben ist.  Im Webbrowser wird die Standardseite dieser Website geöffnet.  
  
    > [!NOTE]  
    >  Wenn das Dialogfeld **Skriptdebugging deaktiviert** angezeigt wird, wählen Sie die Schaltfläche **Ja** aus, um mit dem Debuggen des Projekts fortzufahren.  
  
2.  Wählen Sie im Menü **Websiteaktionen** die Option **Websiteeinstellungen** aus.  
  
3.  Wählen Sie auf der Seite "Websiteeinstellungen" unter **Galerien** den Link **Websitespalten** aus.  
  
4.  Überprüfen Sie in der Liste der Websitespalten, ob eine **Benutzerdefinierte Ja\/Nein\-Spalten**\-Gruppe mit der Spalte **Eigene Ja\/Nein\-Spalte** vorhanden ist, und schließen Sie dann den Webbrowser.  
  
## Bereinigen des Entwicklungscomputers  
 Nachdem Sie die Tests des Projektelements abgeschlossen haben, entfernen Sie die Projektvorlage aus der experimentellen Instanz von Visual Studio.  
  
#### So bereinigen Sie den Entwicklungscomputer  
  
1.  Wählen Sie in der experimentellen Visual Studio\-Instanz in der Menüleiste **Erstellen** und **Erweiterungen und Update** aus.  
  
     Das Dialogfeld **Erweiterungen und Updates** wird geöffnet.  
  
2.  Wählen Sie in der Liste der Erweiterungen **Websitespalte** und dann die Schaltfläche **Deinstallieren** aus.  
  
3.  Wählen Sie im angezeigten Dialogfeld die Schaltfläche **Ja** aus, um das Deinstallieren der Erweiterung zu bestätigen, und wählen Sie dann die Schaltfläche **Jetzt neu starten** aus, um die Deinstallation abzuschließen.  
  
4.  Schließen Sie die experimentelle Instanz von Visual Studio und die Instanz, in der die Projektmappe "CustomActionProjectItem" geöffnet ist.  
  
     Weitere Informationen zum Bereitstellen von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-Erweiterungen finden Sie unter [Lieferung von Visual Studio-Erweiterungen](../extensibility/shipping-visual-studio-extensions.md).  
  
## Siehe auch  
 [Exemplarische Vorgehensweise: Erstellen eines Projektelements "Websitespalte" mit einer Projektvorlage, Teil 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)   
 [Gewusst wie: Verwenden von Assistenten mit Projektvorlagen](../Topic/How%20to:%20Use%20Wizards%20with%20Project%20Templates.md)  
  
  