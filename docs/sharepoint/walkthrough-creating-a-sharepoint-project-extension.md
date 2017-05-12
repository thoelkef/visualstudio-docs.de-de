---
title: "Walkthrough: Creating a SharePoint Project Extension"
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
  - "projects [SharePoint development in Visual Studio], extending"
  - "SharePoint development in Visual Studio, extending projects"
  - "SharePoint projects, extending"
ms.assetid: 5547e2ed-47a3-48f1-9619-42149c03df76
caps.latest.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 25
---
# Walkthrough: Creating a SharePoint Project Extension
  Diese exemplarische Vorgehensweise veranschaulicht, wie eine Erweiterung für ein SharePoint\-Projekt erstellt wird.  Sie können eine Projekterweiterung verwenden, um auf Ereignisse auf Projektebene wie zu reagieren, wenn ein Projekt hinzugefügt, gelöscht oder umbenannt wurde.  Sie können auch benutzerdefinierte Eigenschaften hinzufügen oder auf die Änderung eines Eigenschaftswerts reagieren.  Im Gegensatz zu Projektelementerweiterungen können Projekterweiterungen einem bestimmten SharePoint\-Projekttyp nicht zugeordnet werden.  Wenn Sie eine Projekterweiterung erstellen, wird die Erweiterung bei jedem Öffnen eines SharePoint\-Projekts in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] geladen.  
  
 In dieser exemplarischen Vorgehensweise erstellen wir eine benutzerdefinierte boolesche Eigenschaft, die jedem in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] erstellten SharePoint\-Projekt hinzugefügt wird.  Bei der Festlegung auf **True** wird dem Projekt von der neuen Eigenschaft ein Ressourcenordner für Bilder hinzugefügt oder zugewiesen.  Bei der Festlegung auf **False** wird der Bilderordner ggf. entfernt.  Weitere Informationen finden Sie unter [Gewusst wie: Hinzufügen und Entfernen zugeordneter Ordner](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
 Diese exemplarische Vorgehensweise enthält die folgenden Aufgaben:  
  
-   Erstellen einer Erweiterung [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] für SharePoint\-Projekte, mit der folgende Aufgaben ausgeführt werden können:  
  
    -   Hinzufügen einer benutzerdefinierten Projekteigenschaft zum Eigenschaftenfenster  Die Eigenschaft gilt für jedes SharePoint\-Projekt.  
  
    -   Verwenden des SharePoint\-Projektobjektmodells zum Hinzufügen eines zugeordneten Ordners zu einem Projekt  
  
    -   Verwenden des Automatisierungsobjektmodells von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] zum Löschen eines zugeordneten Ordners aus dem Projekt  
  
-   Erstellen eines [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-Erweiterungspakets \(VSIX\) zur Bereitstellung der Erweiterungsassembly der Projekteigenschaft  
  
-   Debuggen und Testen der Projekteigenschaft  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise werden auf dem Entwicklungscomputer die folgenden Komponenten benötigt:  
  
-   Unterstützte Editionen von [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)], SharePoint und [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Weitere Informationen finden Sie unter [Anforderungen für die Entwicklung von SharePoint-Lösungen](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)].  In dieser exemplarischen Vorgehensweise wird die Vorlage **VSIX Project** im [!INCLUDE[TLA2#tla_sdk](../sharepoint/includes/tla2sharptla-sdk-md.md)] verwendet, um ein VSIX\-Paket zur Bereitstellung der Projekteigenschaftenerweiterung zu erstellen.  Weitere Informationen finden Sie unter [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
## Erstellen der Projekte  
 Zum Abschließen dieser exemplarischen Vorgehensweise müssen Sie zwei Projekte erstellen:  
  
-   Ein VSIX\-Projekt für die Erstellung des VSIX\-Pakets zum Bereitstellen der Projekterweiterung.  
  
-   Ein Klassenbibliotheksprojekt, in das die Projekterweiterung implementiert wird.  
  
 Beginnen Sie mit der exemplarischen Vorgehensweise, indem Sie beide Projekte erstellen.  
  
#### So erstellen Sie das VSIX\-Projekt  
  
1.  Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Wählen Sie in der Menüleiste **Datei**, **Neu**, **Projekt** aus.  
  
3.  Im Dialogfeld **Neues Projekt** erweitern Sie die **Visual C\#** oder Knoten **Visual Basic**, und wählen Sie dann den Knoten **Erweiterungen** aus.  
  
    > [!NOTE]  
    >  Dieser Knoten ist nur verfügbar, wenn Sie das Visual Studio SDK installieren.  Weitere Informationen finden Sie weiter oben in diesem Thema im Abschnitt zu den erforderlichen Komponenten.  
  
4.  am oberen Rand des Dialogfelds wählen Sie **.NET Framework 4.5** in der Liste der Versionen von .NET Framework aus, und wählen Sie dann die Vorlage aus. **VSIX\-Projekt**  
  
5.  Im Feld geben Sie **NameProjectExtensionPackage** ein und klicken Sie dann auf die Schaltfläche **OK** aus.  
  
     Das **ProjectExtensionPackage** Projekt wird in **Projektmappen\-Explorer**.  
  
#### So erstellen Sie das Erweiterungsprojekt  
  
1.  In **Projektmappen\-Explorer** öffnen Sie das Kontextmenü für den Projektmappenknoten, wählen Sie **Hinzufügen** aus und wählen dann **Neues Projekt** aus.  
  
    > [!NOTE]  
    >  In [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]\-Projekten wird der Projektmappenknoten in **Projektmappen\-Explorer**, wenn das Kontrollkästchen **Projektmappe immer anzeigen** in [NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/de-de/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca) ausgewählt ist.  
  
2.  Im Dialogfeld **Neues Projekt** erweitern Sie die **Visual C\#** oder Knoten **Visual Basic**, und wählen Sie dann **Fenster** aus.  
  
3.  am oberen Rand des Dialogfelds wählen Sie **.NET Framework 4.5** in der Liste der Versionen von .NET Framework aus, und wählen Sie dann die **Klassenbibliothek** Projektvorlage aus.  
  
4.  Im Feld geben Sie **NameProjectExtension** ein und klicken Sie dann auf die Schaltfläche **OK** aus.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fügt das Projekt **ProjectExtension** zur aktuellen Projektmappe hinzu und öffnet die Class1\-Codedatei.  
  
5.  Löschen Sie die Class1\-Codedatei aus dem Projekt.  
  
## Konfigurieren des Projekts  
 Bevor Sie Code zum Erstellen der Projekterweiterung schreiben, fügen Sie dem Erweiterungsprojekt Codedateien und Assemblyverweise hinzu.  
  
#### So konfigurieren Sie das Projekt  
  
1.  Fügen Sie eine Codedatei hinzu, die **CustomProperty** zum Namen trägt.  
  
2.  Öffnen Sie das Kontextmenü für das **ProjectExtension** Projekt, und wählen Sie dann **Verweis hinzufügen** aus.  
  
3.  Im Dialogfeld **Verweis\-Manager – CustomProperty** wählen Sie den Knoten **Framework** aus, und wählen Sie dann das Kontrollkästchen neben den System.ComponentModel.Compositions\- und System.Windows.Forms aus.  
  
4.  Wählen Sie den Knoten aus **Erweiterungen**, aktivieren Sie das Kontrollkästchen neben den Microsoft.VisualStudio.SharePoint\- und EnvDTE\-Assemblys aus, und wählen Sie dann die Schaltfläche **OK** aus.  
  
5.  In **Projektmappen\-ExplorerVerweise** unter dem Ordner für das Projekt **ProjectExtension**, wählen Sie **EnvDTE** aus.  
  
6.  Ändern Sie im Fenster **Eigenschaften** den Wert der Eigenschaft **Interoptypen einbetten** in **False**.  
  
## Definieren der neuen SharePoint\-Projekteigenschaft  
 Erstellen Sie eine Klasse, die die Projekterweiterung und das Verhalten der neuen Projekteigenschaft definiert.  Zur Definition der neuen Projekterweiterung wird von der Klasse die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>\-Schnittstelle implementiert.  Implementieren Sie diese Schnittstelle, wenn Sie eine Erweiterung für ein SharePoint\-Projekt erstellen möchten.  Fügen Sie der Klasse auch <xref:System.ComponentModel.Composition.ExportAttribute> hinzu.  Anhand dieses Attributs kann [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>\-Implementierung erkennen und laden.  Übergeben Sie den <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>\-Typ an den Konstruktor des Attributs.  
  
#### So definieren Sie die neue SharePoint\-Projekteigenschaft  
  
1.  Fügen Sie folgenden Code in die CustomProperty\-Codedatei ein.  
  
     [!code-csharp[SPExt_ProjectExtension#1](../snippets/csharp/VS_Snippets_OfficeSP/spext_projectextension/cs/projectextension/customproperty.cs#1)]
     [!code-vb[SPExt_ProjectExtension#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spext_projectextension/vb/projectextension/customproperty.vb#1)]  
  
## Erstellen der Lösung  
 Erstellen Sie als Nächstes die Lösung, um sicherzustellen, dass sie ohne Fehler kompiliert wird.  
  
#### So erstellen Sie die Projektmappe  
  
1.  Klicken Sie auf der Menüleiste wählen Sie **Erstellen**, **Projektmappe erstellen** aus.  
  
## Erstellen eines VSIX\-Pakets zur Bereitstellung der Projekteigenschaftenerweiterung  
 Zur Bereitstellung der Projekterweiterung verwenden Sie das VSIX\-Projekt in der Lösung, um ein VSIX\-Paket zu erstellen.  Konfigurieren Sie zuerst das VSIX\-Paket, indem Sie die im VSIX\-Projekt enthaltene Datei "source.extension.vsixmanifest" ändern.  Erstellen Sie anschließend das VSIX\-Paket, indem Sie die Lösung erstellen.  
  
#### So erstellen und konfigurieren Sie das VSIX\-Paket  
  
1.  In **Projektmappen\-Explorer** öffnen Sie das Kontextmenü für die source.extension.vsixmanifest\-Datei, und wählen Sie dann die Schaltfläche **Öffnen** aus.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] öffnet die Datei im Manifest\-Designer.  Die Informationen, die auf der Registerkarte **Metadaten** auch angezeigt wird, werden in **Erweiterungen und Updates**. Alle VSIX\-Pakete benötigen die Datei " extension.vsixmanifest ".  Weitere Informationen zu dieser Datei finden Sie unter [VSIX\-Erweiterungs\-Schemareferenz](http://msdn.microsoft.com/de-de/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  Im Feld geben Sie **ProduktnameBenutzerdefinierte Projekteigenschaft** ein.  
  
3.  Im Feld geben Sie **AutorContoso** ein.  
  
4.  Im Feld geben Sie **BeschreibungEine benutzerdefinierte SharePoint\-Projekteigenschaft, die die Zuordnung des Imageressourcenordners dem Projekt umschaltet** ein.  
  
5.  Wählen Sie die Registerkarte **Objekte** aus, und wählen Sie dann die Schaltfläche **Neu** aus.  
  
     Das Dialogfeld wird angezeigt. **Neue Anlage hinzufügen**  
  
6.  In der Liste wählen Sie **TypMicrosoft.VisualStudio.MefComponent** aus.  
  
    > [!NOTE]  
    >  Dieser Wert entspricht dem `MEFComponent`\-Element in der Datei "extension.vsixmanifest".  Von diesem Element wird der Name einer Erweiterungsassembly im VSIX\-Paket angegeben.  Weitere Informationen finden Sie unter [NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/de-de/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
7.  In der Liste **Quelle** wählen Sie das Optionsfeld **Ein Projekt in der aktuellen Projektmappe**.  
  
8.  In der Liste wählen Sie **ProjektProjectExtension** aus.  
  
     Dieser Wert bestimmt den Namen der Assembly, die Sie im Projekt erstellen.  
  
9. Wählen Sie **OKNeue Anlage hinzufügen**, um das Dialogfeld zu schließen.  
  
10. Klicken Sie auf der Menüleiste wählen Sie **Datei**, wenn Sie **Alle speichern** Ende, und schließen Sie dann den Manifest\-Designer.  
  
11. Klicken Sie auf der Menüleiste wählen Sie **Erstellen**, **Projektmappe erstellen** aus, und überprüfen Sie, dass das Projekt ohne Fehler kompiliert wird.  
  
12. In **Projektmappen\-Explorer** öffnen Sie das Kontextmenü für das **ProjectExtensionPackage** Projekt, und wählen Sie die Schaltfläche **Ordner in Datei\-Explorer öffnen** aus.  
  
13. In **Explorer** öffnen Sie den Buildausgabeordner für das ProjectExtensionPackage\-Projekt, und überprüfen Sie, ob der Ordner eine Datei enthält, die ProjectExtensionPackage.vsix ".  
  
     Standardmäßig ist der Buildausgabeordner der  Ordner "\\bin\\Debug" im Ordner mit der Projektdatei.  
  
## Testen der Projekteigenschaft  
 Sie sind nun bereit, die benutzerdefinierte Projekteigenschaft testen.  Es ist am einfachsten, die neue Projekteigenschaftenerweiterung in einer experimentellen Instanz von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] zu debuggen und zu testen.  Diese Instanz von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] wird erstellt, wenn Sie ein VSIX oder eines anderen Erweiterungsprojekts.  Nachdem Sie das Projekt debuggen, können Sie die Erweiterung auf dem System installieren und anschließend fortfahren, um es in einer regulären Instanz von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] zu debuggen und zu testen.  
  
#### So debuggen und testen Sie die Erweiterung in einer experimentellen Instanz von Visual Studio  
  
1.  Starten Sie neu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] mit Administratorrechten, und öffnen Sie dann die öffnen.  
  
2.  Starten Sie einen Debugbuild des Projekts entweder, indem Sie die **F5** Schlüssel oder, auf der Menüleiste auswählen und **Debuggen**, **Debuggen starten** auswählen.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] installiert die Erweiterung in %UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\11.0Exp\\Extensions\\Contoso\\Custom Project Property\\1.0 und startet eine experimentelle Instanz von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
3.  Klicken Sie in der experimentellen Instanz von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], erstellen Sie ein SharePoint\-Projekt für eine Farmlösung, und verwenden Sie die Standardwerte für die anderen Werte im Assistenten.  
  
    1.  Wählen Sie in der Menüleiste **Datei**, **Neu**, **Projekt** aus.  
  
    2.  **Neues Projekt** am oberen Rand des Dialogfelds wählen Sie **.NET Framework 3.5** in der Liste der Versionen von .NET Framework aus.  
  
         SharePoint\-Toolerweiterungen benötigen Funktionen in dieser Version [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)].  
  
    3.  **Vorlagen** unter dem Knoten erweitern Sie den **Visual C\#** oder Knoten **Visual Basic**, wählen Sie den Knoten **SharePoint** aus, und wählen Sie dann den Knoten **2010** aus.  
  
    4.  Wählen Sie die **SharePoint 2010\-Projekt** Vorlage aus, und geben Sie dann **ModuleTest** als Namen des Projekts ein.  
  
4.  In **Projektmappen\-Explorer** wählen Sie den **ModuleTest** Projektknoten aus.  
  
     Ein neue benutzerdefinierte Eigenschaft zur Zuweisung des Bilderordners wird im Fenster **Eigenschaften** mit dem Standardwert **False** angezeigt.  
  
5.  Ändern Sie den Wert dieser Eigenschaft auf **True**.  
  
     Dem SharePoint\-Projekt wird ein Ressourcenordner für Bilder hinzugefügt.  
  
6.  Ändern Sie den Wert dieser Eigenschaft zurück zu **False**.  
  
     Wenn Sie die Schaltfläche **Ja** im Dialogfeld **Löschen Sie den Ordner Images?** auswählen, wird der Ressourcenordner für Bilder aus dem SharePoint\-Projekt gelöscht.  
  
7.  Schließen Sie die experimentelle Instanz von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
## Siehe auch  
 [Extending SharePoint Projects](../sharepoint/extending-sharepoint-projects.md)   
 [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Converting Between SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
  