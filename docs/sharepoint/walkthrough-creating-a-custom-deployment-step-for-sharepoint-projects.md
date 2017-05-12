---
title: "Walkthrough: Creating a Custom Deployment Step for SharePoint Projects"
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
  - "SharePoint commands"
  - "SharePoint development in Visual Studio, extending deployment"
ms.assetid: 4ba2d120-06b8-4ef3-84eb-c6c50ced9d82
caps.latest.revision: 63
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 62
---
# Walkthrough: Creating a Custom Deployment Step for SharePoint Projects
  Wenn Sie ein SharePoint\-Projekt bereitstellen, führt Visual Studio eine Reihe von Bereitstellungsschritten in einer bestimmten Reihenfolge aus.  Visual Studio enthält viele integrierte Bereitstellungsschritte, Sie können aber auch eigene Schritte erstellen.  
  
 In dieser exemplarischen Vorgehensweise erstellen Sie einen benutzerdefinierten Bereitstellungsschritt, um Projektmappen auf einem Server zu aktualisieren, der SharePoint ausgeführt wird.  Visual Studio beinhaltet integrierte Bereitstellungsschritte für viele Aufgaben, solche Zurücknehmen oder Hinzufügen Lösungen, jedoch kein Bereitstellungsschritt zum Aktualisieren von Projektmappen.  Beim Bereitstellen einer SharePoint\-Lösung, normalerweise zuerst die Projektmappe \(sofern bereits bereitgestellt\) zurück und stellt dann die gesamte Projektmappe erneut bereit.  Weitere Informationen zu den integrierten Bereitstellungsschritten finden Sie unter [Bereitstellen, Veröffentlichen und Aktualisieren von SharePoint-Lösungspaketen](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).  
  
 Diese exemplarische Vorgehensweise enthält die folgenden Aufgaben:  
  
-   Erstellen einer Visual Studio\-Erweiterung, die zwei Hauptaufgaben ausführt:  
  
    -   Die Erweiterung wird ein benutzerdefinierter Bereitstellungsschritt definiert, um SharePoint\-Lösungen zu aktualisieren.  
  
    -   Die Erweiterung wird eine Projekterweiterung erstellt, die eine neue Bereitstellungskonfiguration definiert, die ein Satz von Bereitstellungsschritten ist, der für ein bestimmtes Projekt ausgeführt werden.  Die neue Bereitstellungskonfiguration beinhaltet den benutzerdefinierten Bereitstellungsschritt und mehrere integrierte Bereitstellungsschritte.  
  
-   Zwei benutzerdefinierte SharePoint\-Befehle erstellen, die die Erweiterungsassembly aufruft.  SharePoint\-Befehle sind Methoden, die von Erweiterungsassemblys aufgerufen werden können, um APIs im Serverobjektmodell für SharePoint zu verwenden.  Weitere Informationen finden Sie unter [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
-   Erstellen eines Visual Studio\-Erweiterungspakets \(VSIX\) zum Bereitstellen beider Assemblys.  
  
-   Testen des neuen Bereitstellungsschritts.  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise werden auf dem Entwicklungscomputer die folgenden Komponenten benötigt:  
  
-   Unterstützte Editionen von Windows, SharePoint und Visual Studio.  Weitere Informationen finden Sie unter [Anforderungen für die Entwicklung von SharePoint-Lösungen](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Das Visual Studio SDK.  Diese exemplarische Vorgehensweise verwendet die Vorlage **VSIX Project** im SDK, um ein VSIX\-Paket zum Bereitstellen der Erweiterung zu erstellen.  Weitere Informationen finden Sie unter [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Kenntnisse der folgenden Konzepte sind hilfreich, wenn auch für die Durchführung der exemplarischen Vorgehensweise nicht erforderlich:  
  
-   Verwenden des Serverobjektmodells für SharePoint.  Weitere Informationen finden Sie im Thema zur [Verwendung des serverseitigen SharePoint Foundation\-Objektmodells](http://go.microsoft.com/fwlink/?LinkId=177796) \(möglicherweise in englischer Sprache\).  
  
-   SharePoint\-Lösungen.  Weitere Informationen finden Sie in der [Lösungsübersicht](http://go.microsoft.com/fwlink/?LinkId=169422) \(möglicherweise in englischer Sprache\).  
  
-   Aktualisieren von SharePoint\-Lösungen.  Weitere Informationen finden Sie im Thema zum [Aktualisieren einer Lösung](http://go.microsoft.com/fwlink/?LinkId=177802) \(möglicherweise in englischer Sprache\).  
  
## Erstellen der Projekte  
 Um diese exemplarische Vorgehensweise abzuschließen, müssen Sie drei Projekte erstellen:  
  
-   Ein VSIX\-Projekt für die Erstellung des VSIX\-Pakets zum Bereitstellen der Erweiterung.  
  
-   Ein Klassenbibliotheksprojekt, von dem die Erweiterung implementiert wird.  Dieses Projekt muss .NET Framework 4.5 abzielen.  
  
-   Ein Klassenbibliotheksprojekt, das die benutzerdefinierten SharePoint\-Befehle definiert.  Dieses Projekt muss .NET Framework 3.5 abzielen.  
  
 Beginnen Sie mit der exemplarischen Vorgehensweise, indem Sie beide Projekte erstellen.  
  
#### So erstellen Sie das VSIX\-Projekt  
  
1.  Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Wählen Sie in der Menüleiste **Datei**, **Neu**, **Projekt** aus.  
  
3.  Im Dialogfeld **Neues Projekt** erweitern Sie die **Visual C\#** oder Knoten **Visual Basic**, und wählen Sie dann den Knoten **Erweiterungen** aus.  
  
    > [!NOTE]  
    >  Der Knoten **Erweiterungen** ist nur verfügbar, wenn Sie das Visual Studio SDK installieren.  Weitere Informationen finden Sie weiter oben in diesem Thema im Abschnitt zu den erforderlichen Komponenten.  
  
4.  am oberen Rand des Dialogfelds wählen Sie **.NET Framework 4.5** in der Liste der Versionen von .NET Framework aus.  
  
5.  Wählen Sie die **VSIX\-Projekt** Vorlage aus, geben Sie das Projekt **UpgradeDeploymentStep**, und wählen Sie dann die Schaltfläche **OK** aus.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fügt das **UpgradeDeploymentStep**\-Projekt zum **Projektmappen\-Explorer** hinzu.  
  
#### So erstellen Sie das Erweiterungsprojekt  
  
1.  In **Projektmappen\-Explorer** öffnen Sie das Kontextmenü für den UpgradeDeploymentStep\-Projektmappenknoten, wählen Sie **Hinzufügen** aus und wählen dann **Neues Projekt** aus.  
  
    > [!NOTE]  
    >  In Visual Basic\-Projekten wird der Projektmappenknoten nur im **Projektmappen\-Explorer** angezeigt, wenn das Kontrollkästchen **Projektmappe immer anzeigen** in [NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/de-de/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca) aktiviert ist.  
  
2.  Im Dialogfeld **Neues Projekt** erweitern Sie die **Visual C\#** oder Knoten **Visual Basic**, und wählen Sie dann den Knoten **Fenster** aus.  
  
3.  am oberen Rand des Dialogfelds wählen Sie **.NET Framework 4.5** in der Liste der Versionen von .NET Framework aus.  
  
4.  Wählen Sie die **Klassenbibliothek** Projektvorlage aus, nennen Sie das Projekt **DeploymentStepExtension**, und wählen Sie dann die Schaltfläche **OK** aus.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fügt das Projekt **DeploymentStepExtension** der Projektmappe hinzu und öffnet die standardmäßige Class1\-Codedatei.  
  
5.  Löschen Sie die Class1\-Codedatei aus dem Projekt.  
  
#### So erstellen Sie das SharePoint\-Befehlsprojekt  
  
1.  In **Projektmappen\-Explorer** öffnen Sie das Kontextmenü für den UpgradeDeploymentStep\-Projektmappenknoten, wählen Sie **Hinzufügen** aus und wählen dann **Neues Projekt** aus.  
  
    > [!NOTE]  
    >  In Visual Basic\-Projekten wird der Projektmappenknoten nur im **Projektmappen\-Explorer** angezeigt, wenn das Kontrollkästchen **Projektmappe immer anzeigen** in [NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/de-de/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca) aktiviert ist.  
  
2.  Im Dialogfeld **Neues Projekt** erweitern Sie **Visual C\#** oder **Visual Basic**, und wählen Sie dann den Knoten **Fenster** aus.  
  
3.  am oberen Rand des Dialogfelds wählen Sie **.NET Framework 3.5** in der Liste der Versionen von .NET Framework aus.  
  
4.  Wählen Sie die **Klassenbibliothek** Projektvorlage aus, nennen Sie das Projekt **SharePointCommands**, und wählen Sie dann die Schaltfläche **OK** aus.  
  
     Visual Studio fügt der Projektmappe das Projekt **SharePointCommands** hinzu und öffnet die Class1\-Standardcodedatei.  
  
5.  Löschen Sie die Class1\-Codedatei aus dem Projekt.  
  
## Konfigurieren der Projekte  
 Bevor Sie Code schreiben, um den benutzerdefinierten Bereitstellungsschritt zu erstellen, müssen Sie Codedateien und Assemblyverweise hinzufügen, und Sie müssen die Projekte konfigurieren.  
  
#### So konfigurieren Sie das Projekt "DeploymentStepExtension"  
  
1.  Im **DeploymentStepExtension** Projekt fügen Sie zwei Codedateien hinzu, die die folgenden Namen aufweisen:  
  
    -   UpgradeStep  
  
    -   DeploymentConfigurationExtension  
  
2.  Öffnen Sie das Kontextmenü im Projekt "DeploymentStepExtension", und wählen Sie dann **Verweis hinzufügen** aus.  
  
3.  **Framework** auf der Registerkarte das Kontrollkästchen für die System.ComponentModel.Compositions\-Assembly aus.  
  
4.  **Erweiterungen** auf der Registerkarte das Kontrollkästchen für die Microsoft.VisualStudio.SharePoint\-Assembly aus, und wählen Sie dann die Schaltfläche **OK** aus.  
  
#### So konfigurieren Sie das SharePointCommands\-Projekt  
  
1.  Im **SharePointCommands** Projekt fügen Sie eine Codedatei hinzu, die Commands genannt wird.  
  
2.  In **Projektmappen\-Explorer** öffnen Sie das Kontextmenü im **SharePointCommands** Projektknoten, und wählen Sie dann **Verweis hinzufügen** aus.  
  
3.  **Erweiterungen** auf der Registerkarte die Kontrollkästchen für die folgenden Assemblys aus, und klicken Sie dann auf die Schaltfläche **OK** auswählen  
  
    -   Microsoft.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
## Definieren des benutzerdefinierten Bereitstellungsschritts  
 Erstellen Sie eine Klasse, die den Upgradebereitstellungsschritt definiert.  Um den Bereitstellungsschritt zu definieren, implementiert die Klasse die <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep>\-Schnittstelle.  Implementieren Sie diese Schnittstelle immer dann, wenn Sie einen benutzerdefinierten Bereitstellungsschritt definieren möchten.  
  
#### So definieren Sie den benutzerdefinierten Bereitstellungsschritt  
  
1.  Im **DeploymentStepExtension** Projekt öffnen Sie die UpgradeStep\-Codedatei, und fügen Sie dann den folgenden Code in die ein.  
  
    > [!NOTE]  
    >  Nachdem Sie diesen Code hinzufügen, weist das Projekt mehrere Compilerfehler, aber sie wechseln weg, wenn Sie Code in späteren Schritten hinzufügen.  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/CS/deploymentstepextension/upgradestep.cs#1)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/vb/deploymentstepextension/upgradestep.vb#1)]  
  
## Erstellen einer Bereitstellungskonfiguration, die den benutzerdefinierten Bereitstellungsschritt beinhaltet  
 Erstellen Sie eine Projekterweiterung für die neue Bereitstellungskonfiguration, die mehrere integrierte Bereitstellungsschritte und den neuen Upgradebereitstellungsschritt umfasst.  Mit dieser Erweiterung erstellen, unterstützen Sie SharePoint\-Entwicklern, den Upgradebereitstellungsschritt in SharePoint\-Projekten zu verwenden.  
  
 Um die Bereitstellungskonfiguration zu erstellen, implementiert die Klasse die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>\-Schnittstelle.  Implementieren Sie diese Schnittstelle immer dann, wenn Sie eine SharePoint\-Projekterweiterung erstellen möchten.  
  
#### So erstellen Sie die Bereitstellungskonfiguration  
  
1.  Im **DeploymentStepExtension** Projekt öffnen Sie die DeploymentConfigurationExtension\-Codedatei, und fügen Sie dann den folgenden Code in die ein.  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/CS/deploymentstepextension/deploymentconfigurationextension.cs#2)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/vb/deploymentstepextension/deploymentconfigurationextension.vb#2)]  
  
## Erstellen der benutzerdefinierten SharePoint\-Befehle  
 Erstellen Sie zwei benutzerdefinierte Befehle, die in das Serverobjektmodell für SharePoint aufrufen.  Ein Befehl ermittelt, ob bereits eine Projektmappe bereitgestellt wurde. Der zweite Befehl aktualisiert eine Projektmappe.  
  
#### So definieren Sie die SharePoint\-Befehle  
  
1.  Im **SharePointCommands** Projekt öffnen Sie die Codedatei Commands, und fügen Sie dann den folgenden Code in die ein.  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/CS/SharePointCommands/Commands.cs#4)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/vb/sharepointcommands/commands.vb#4)]  
  
## Checkpoint  
 An diesem Punkt in der exemplarischen Vorgehensweise ist der gesamte für den benutzerdefinierten Bereitstellungsschritt und die SharePoint\-Befehle benötigte Code in die Projekte eingebunden.  Erstellen Sie sie, um sicherzustellen, dass sie ohne Fehler kompiliert werden.  
  
#### Um die Projekte erstellen  
  
1.  In **Projektmappen\-Explorer** öffnen Sie das Kontextmenü für das **DeploymentStepExtension** Projekt, und wählen Sie dann **Erstellen** aus.  
  
2.  Öffnen Sie das Kontextmenü für das **SharePointCommands** Projekt, und wählen Sie dann **Erstellen** aus.  
  
## Erstellen eines VSIX\-Pakets zum Bereitstellen der Erweiterung  
 Zum Bereitstellen der Erweiterung erstellen Sie anhand des VSIX\-Projekts in der Lösung ein VSIX\-Paket.  Konfigurieren Sie zuerst das VSIX\-Paket, indem Sie die source.extension.vsixmanifest\-Datei im VSIX\-Projekt ändern.  Erstellen Sie anschließend das VSIX\-Paket, indem Sie die Projektmappe erstellen.  
  
#### So erstellen und konfigurieren Sie das VSIX\-Paket  
  
1.  In **Projektmappen\-Explorer** unter dem **UpgradeDeploymentStep** Projekt, öffnen Sie das Kontextmenü für die Datei **source.extension.vsixmanifest**, und wählen Sie dann **Öffnen** aus.  
  
     Die Datei wird von Visual Studio im Manifest\-Editor geöffnet.  Die Datei "source.extension.vsixmanifest" bildet die Grundlage für die Datei, die alle VSIX\-Pakete benötigen.  Weitere Informationen zu dieser Datei finden Sie unter [VSIX\-Erweiterungs\-Schemareferenz](http://msdn.microsoft.com/de-de/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  Im Feld geben Sie **ProduktnameUpgrade Deployment Step for SharePoint Projects** ein.  
  
3.  Im Feld geben Sie **AutorContoso** ein.  
  
4.  Im Feld geben Sie **BeschreibungStellt einen benutzerdefinierten Upgradebereitstellungsschritt bereit, der in SharePoint\-Projekten verwendet werden kann** ein.  
  
5.  Auf der Registerkarte **Objekte** des Editors, wählen Sie die Schaltfläche **Neu** aus.  
  
     Das Dialogfeld wird angezeigt. **Neue Anlage hinzufügen**  
  
6.  In der Liste wählen Sie **TypMicrosoft.VisualStudio.MefComponent** aus.  
  
    > [!NOTE]  
    >  Dieser Wert entspricht dem `MefComponent`\-Element in der Datei "extension.vsixmanifest".  Von diesem Element wird der Name einer Erweiterungsassembly im VSIX\-Paket angegeben.  Weitere Informationen finden Sie unter [NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/de-de/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
7.  In der Liste wählen Sie **QuelleEin Projekt in der aktuellen Projektmappe** aus.  
  
8.  In der Liste wählen Sie **ProjektDeploymentStepExtension** aus und wählen dann die Schaltfläche **OK** aus.  
  
9. im Manifest\-Editor wählen Sie die Schaltfläche **Neu** erneut aus.  
  
     Das Dialogfeld wird angezeigt. **Neue Anlage hinzufügen**  
  
10. In der Liste **Typ** geben Sie **SharePoint.Commands.v4** ein.  
  
    > [!NOTE]  
    >  Dieses Element gibt eine benutzerdefinierte Erweiterung an, die Sie in die Visual Studio\-Erweiterung einschließen möchten.  Weitere Informationen finden Sie unter [Vermögensteil \(VSX Schema\)](http://msdn.microsoft.com/de-de/9fcfc098-edc7-484b-9d4c-acd17829d737).  
  
11. In der Liste wählen Sie **QuelleEin Projekt in der aktuellen Projektmappe** aus.  
  
12. In der Liste wählen Sie **ProjektSharePointCommands** aus und wählen dann die Schaltfläche **OK** aus.  
  
13. Klicken Sie auf der Menüleiste wählen Sie **Erstellen**, **Projektmappe erstellen** aus, und überprüfen Sie, ob die Projektmappe fehlerfrei kompiliert.  
  
14. Stellen Sie sicher, dass der Buildausgabeordner für das Projekt UpgradeDeploymentStep jetzt die Datei UpgradeDeploymentStep.vsix enthält.  
  
     Standardmäßig ist der Buildausgabeordner der  Ordner "\\bin\\Debug" im Ordner mit der Projektdatei.  
  
## Vorbereiten des Tests für den Upgradebereitstellungsschritt  
 Um den Upgradebereitstellungsschritt zu testen, müssen Sie zuerst eine Beispielprojektmappe auf der SharePoint\-Website bereitstellen.  Debuggen Sie die Erweiterung zunächst in der experimentellen Instanz von Visual Studio.  Anschließend erstellen Sie eine Listendefinition und eine Listeninstanz, um zu verwenden, um den Bereitstellungsschritt zu testen, und stellen Sie diese auf der SharePoint\-Website bereit.  Als Nächstes ändern Sie die Listendefinition und die Listeninstanz und stellen Sie sie erneut, um zu veranschaulichen, wie der Standardbereitstellungsprozess Projektmappen auf der SharePoint\-Website überschreibt.  
  
 Später in dieser exemplarischen Vorgehensweise, ändern Sie die Listendefinition und die Listeninstanz, und aktualisieren Sie sie dann auf der SharePoint\-Website.  
  
#### So debuggen Sie die Erweiterung  
  
1.  Starten Sie Visual Studio erneut mit Administratorrechten, und öffnen Sie dann die UpgradeDeploymentStep.  
  
2.  Öffnen Sie im Projekt "DeploymentStepExtension" die UpgradeStep\-Codedatei, und fügen Sie anschließend einen Haltepunkt der ersten Codezeile in den `CanExecute` und `Execute`\-Methoden hinzu.  
  
3.  Starten Sie das Debuggen, indem Sie die F5\-TASTE, oder auf der Menüleiste auswählen und **Debuggen**, **Debuggen starten** auswählen.  
  
4.  Visual Studio installiert die Erweiterung in %UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\11.0Exp\\Extensions\\Contoso\\Upgrade Deployment Step for SharePoint Projects\\1.0 und startet eine experimentelle Instanz von Visual Studio.  Sie testen den Upgradebereitstellungsschritt in dieser Instanz von Visual Studio.  
  
#### Um ein SharePoint\-Projekt mit einer Listendefinition und einer Liste zu erstellen führen Sie als Beispiel an  
  
1.  Klicken Sie in der experimentellen Instanz von Visual Studio, in der Menüleiste, wählen Sie **Datei**, **Neu**, **Projekt** aus.  
  
2.  Im Dialogfeld **Neues Projekt** erweitern Sie den Knoten **Visual C\#Visual Basic** oder den Knoten, erweitern Sie den Knoten **SharePoint**, und wählen Sie dann den Knoten **2010** aus.  
  
3.  am oberen Rand des Dialogfelds sicher, dass **.NET Framework 3.5** in der Liste der Versionen von .NET Framework wird angezeigt.  
  
     Projekte für [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] und [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] erfordern diese Version von .NET Framework.  
  
4.  In der Liste der Projektvorlagen, wählen Sie **SharePoint 2010\-Projekt** aus, nennen Sie das Projekt **EmployeesListDefinition**, und wählen Sie dann die Schaltfläche **OK** aus.  
  
5.  In **Assistent zum Anpassen von SharePoint** geben Sie die URL der Website ein, die Sie zum Debuggen verwenden möchten.  
  
6.  Die **Was die Vertrauensebene für diese SharePoint\-Lösung ist** wählen Sie das Optionsfeld **Als Farmlösung bereitstellen**.  
  
    > [!NOTE]  
    >  Der Upgradebereitstellungsschritt unterstützt keine Sandkastenlösungen.  
  
7.  Wählen Sie die Schaltfläche **Fertig stellen** aus.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] erstellt das Projekt EmployeesListDefinition\-Projekt.  
  
8.  Öffnen Sie das Kontextmenü für das Projekt EmployeesListDefinition\-Projekt, wählen Sie **Hinzufügen** aus und wählen dann **Neues Element** aus.  
  
9. Im **Neues Element hinzufügen – EmployeesListDefinition** Dialogfeld **SharePoint** erweitern Sie den Knoten, und wählen Sie dann den Knoten **2010** aus.  
  
10. Wählen Sie die **Liste**\-Elementvorlage aus, geben Sie das Element **Mitarbeiterliste**, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.  
  
     Der Assistent zum Anpassen von SharePoint wird  
  
11. **Listeneinstellungen auswählen** auf der Seite die folgenden Einstellungen, und wählen Sie dann die Schaltfläche **Fertig stellen** aus:  
  
    1.  **Mitarbeiterliste** wird im **Welcher Name soll für Ihre Liste angezeigt werden?** Feld.  
  
    2.  Das **Erstellen Sie eine anpassbare Liste basierend auf:** Optionsfeld ausgewählt wird.  
  
    3.  **Standard \(leer\)** wird in der Liste **Erstellen Sie eine anpassbare Liste basierend auf:** ausgewählt.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] erstellt das Mitarbeiter\-Listenelement mit einer Titelspalte und ein einzelnes leeren Instanz und den Listen\-Designer.  
  
12. Im Listen\-Designer auf der Registerkarte **Spalten**, wählen Sie die Zeile **Neuen oder vorhandenen Spaltennamen eingeben** aus, und fügen Sie dann die folgenden Spalten in der Liste **Anzeigename der Spalte** hinzu:  
  
    1.  Vorname  
  
    2.  Firma  
  
    3.  Geschäfts\-Telefon  
  
    4.  E\-Mail  
  
13. Speichern Sie alle Dateien, und schließen Sie dann den Listen\-Designer.  
  
14. In **Projektmappen\-ExplorerMitarbeiterliste** erweitern Sie den Knoten, und erweitern Sie dann den untergeordneten Knoten **Mitarbeiter\-Listen\-Instanz**.  
  
15. In der Datei Elements.xml ersetzen Sie das Standard\-XML in dieser Datei durch folgendes XML.  Dieses XML ändert den Namen der Liste in **Mitarbeiter** und werden Informationen für einen Mitarbeiter hinzu, mit dem Namen Jim Hance verfügt.  
  
    ```  
  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <ListInstance Title="Employees"  
                    OnQuickLaunch="TRUE"  
                    TemplateType="10000"  
                    Url="Lists/Employees"  
                    Description="Simple list to test upgrade deployment step">  
        <Data>  
          <Rows>  
            <Row>  
              <Field Name="Title">Hance</Field>  
              <Field Name="FirstName">Jim</Field>  
              <Field Name="Company">Contoso</Field>  
              <Field Name="Business Phone">555-555-5555</Field>  
              <Field Name="E-Mail">jim@contoso.com</Field>  
            </Row>  
          </Rows>  
        </Data>  
      </ListInstance>  
    </Elements>  
    ```  
  
16. Speichern und schließen Sie die Datei Elements.xml.  
  
17. Öffnen Sie das Kontextmenü für das Projekt EmployeesListDefinition\-Projekt, und wählen Sie dann **Öffnen** oder **Eigenschaften** aus.  
  
     Der Eigenschaft\-Designer wird geöffnet.  
  
18. Klicken Sie auf der Registerkarte **SharePoint** deaktivieren Sie das Kontrollkästchen **Nach Debuggen automatisch zurückziehen**, und speichern Sie dann die Eigenschaften.  
  
#### So stellen Sie die Listendefinition und die Listeninstanz bereit  
  
1.  In **Projektmappen\-Explorer** wählen Sie den **EmployeesListDefinition** Projektknoten aus.  
  
2.  Stellen Sie im **Eigenschaftenfenster** sicher, dass die Eigenschaft **Aktive Bereitstellungskonfiguration** auf **Standard** festgelegt ist \(dies ist die Standardeinstellung\).  
  
3.  Wählen Sie die F5\-TASTE, oder auf der Menüleiste aus, wählen Sie **Debuggen**, **Debuggen starten** aus.  
  
4.  Überprüfen Sie, ob das Projekt erfolgreich erstellt der Webbrowser zur SharePoint\-Website geöffnet wird, dass das **Listen**\-Element in der Schnellstartleiste die neue Liste **Mitarbeiter** umfasst und dass die Liste **Mitarbeiter** den Eintrag für Jim Hance umfasst.  
  
5.  Schließen Sie den Webbrowser.  
  
#### So ändern Sie die Listendefinition und stellen die Listeninstanz erneut bereit  
  
1.  im Projekt EmployeesListDefinition\-Projekt öffnen Sie die Datei Elements.xml, die ein untergeordnetes Element des Projektelements ist. **Mitarbeiter\-Listen\-Instanz**  
  
2.  Entfernen Sie das `Data`\-Element und die untergeordneten Elemente, um den Eintrag für Jim Hance aus der Liste zu entfernen.  
  
     Wenn Sie Ende, die Datei das folgende XML enthalten sollen.  
  
    ```  
  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <ListInstance Title="Employees"  
                    OnQuickLaunch="TRUE"  
                    TemplateType="10000"  
                    Url="Lists/Employees"  
                    Description="Simple list to test upgrade deployment step">  
      </ListInstance>  
    </Elements>  
    ```  
  
3.  Speichern und schließen Sie die Datei Elements.xml.  
  
4.  Öffnen Sie das Kontextmenü für das **Mitarbeiterliste** Projektelement, und wählen Sie dann **Öffnen** oder **Eigenschaften** aus.  
  
5.  Im Listen\-Designer **Ansichten** wählen Sie die Registerkarte aus.  
  
6.  In der Liste wählen Sie **Ausgewählte SpaltenAnlagen** aus und wählen dann \< die Schlüssel aus, sicher, dass die Spalte zur Liste **Verfügbare Spalten** zu bewegen.  
  
7.  Wiederholen Sie den vorherigen Schritt, um die Spalte **Rufnummer \(geschäftlich\)** aus der Liste **Ausgewählte Spalten** auf die Liste **Verfügbare Spalten** zu verschieben.  
  
     Durch diese Aktion werden diese Felder nicht mehr in der Standardansicht der Liste **Employees** auf der SharePoint\-Website angezeigt.  
  
8.  Starten Sie das Debuggen, indem Sie die F5\-TASTE, oder auf der Menüleiste auswählen und **Debuggen**, **Debuggen starten** auswählen.  
  
9. Überprüfen Sie, ob das Dialogfeld **Bereitstellungskonflikte** angezeigt wird.  
  
     Dieses Dialogfeld wird angezeigt, wenn Visual Studio versucht, eine Projektmappe \(die Listeninstanz\) auf einer SharePoint\-Website bereitzustellen, auf die diese Projektmappe bereitgestellt wurde.  Dieses Dialogfeld wird nicht angezeigt, wenn Sie den Upgradebereitstellungsschritt später in dieser exemplarischen Vorgehensweise ausführen.  
  
10. Im Dialogfeld **Bereitstellungskonflikte** wählen Sie das Optionsfeld **Automatisch beheben**.  
  
     Visual Listeninstanz auf der SharePoint\-Website wird gelöscht, das Listenelement im Projekt bereit und öffnet dann die SharePoint\-Website.  
  
11. Im **Listen**\-Abschnitt der Schnellstartleiste, wählen Sie die Liste **Mitarbeiter** aus, und überprüfen Sie dann die folgenden Informationen:  
  
    -   Die **Anlagen** und **Rufnummer \(privat\)** Spalten werden nicht in dieser Ansicht der Liste.  
  
    -   Die Liste ist leer.  Als Sie die Projektmappe mit der Bereitstellungskonfiguration **Standard** erneut bereitgestellt haben, wurde die Liste **Employees** durch die neue leere Liste im Projekt ersetzt.  
  
## Testen des Bereitstellungsschritts  
 Jetzt können Sie den Upgradebereitstellungsschritt testen.  Fügen Sie zuerst der Listeninstanz in SharePoint ein Element hinzu.  Anschließend ändern Sie die Listendefinition und eine Listeninstanz, aktualisieren Sie sie auf der SharePoint\-Website, und bestätigen Sie, dass nicht durch den Upgradebereitstellungsschritt überschrieben wird.  
  
#### So fügen Sie manuell ein neues Listenelement hinzu  
  
1.  Klicken Sie im Menüband auf der SharePoint\-Website, unter der Registerkarte **Listentools**, wählen Sie die Registerkarte **Elemente** aus.  
  
2.  In der Gruppe **Neu** wählen Sie **Neues Element** aus.  
  
     Alternativ können Sie den **Neues Element hinzufügen** Link in der Elementliste selbst auswählen.  
  
3.  **Mitarbeiter – Neues Element** im Fenster im Feld **Titel**, geben Sie **Feature\-Manager** ein.  
  
4.  Im Feld geben Sie **VornameAndy** ein.  
  
5.  Im Feld geben Sie **FirmaContoso** ein.  
  
6.  Wählen Sie die Schaltfläche **Speichern** aus, überprüfen Sie, dass der neue Element in der Liste angezeigt wird, und schließen Sie dann den Webbrowser.  
  
     Später in dieser exemplarischen Vorgehensweise, verwenden Sie dieses Element, um sicherzustellen, dass der Upgradebereitstellungsschritt den Inhalt dieser Liste nicht überschreibt.  
  
#### So testen Sie den Upgradebereitstellungsschritt  
  
1.  Klicken Sie in der experimentellen Instanz von Visual Studio, in **Projektmappen\-Explorer**, öffnen Sie das Kontextmenü für den **EmployeesListDefinition** Projektknoten, und wählen Sie dann **Eigenschaften** aus.  
  
     Der Eigenschaft\-Editor\/der Designer wird geöffnet.  
  
2.  Klicken Sie auf der Registerkarte **SharePoint** legen Sie die \- Eigenschaft auf **Aktive BereitstellungskonfigurationUpgrade** fest.  
  
     Diese benutzerdefinierte Bereitstellungskonfiguration umfasst den neuen Upgradebereitstellungsschritt.  
  
3.  Öffnen Sie das Kontextmenü für das **Mitarbeiterliste** Projektelement, und wählen Sie dann **Eigenschaften** oder **Öffnen** aus.  
  
     Der Eigenschaft\-Editor\/der Designer wird geöffnet.  
  
4.  **Ansichten** auf der Registerkarte die Spalte **E\-Mail** aus, und wählen Sie dann die **\<** Schlüssel, um sich die Spalte aus der Liste in die Liste **Ausgewählte SpaltenVerfügbare Spalten** zu bewegen.  
  
     Durch diese Aktion werden diese Felder nicht mehr in der Standardansicht der Liste **Employees** auf der SharePoint\-Website angezeigt.  
  
5.  Starten Sie das Debuggen, indem Sie die F5\-TASTE, oder auf der Menüleiste auswählen und **Debuggen**, **Debuggen starten** auswählen.  
  
6.  Überprüfen Sie, ob die Codeausführung in der anderen Instanz von Visual Studio an dem Haltepunkt unterbrochen wird, den Sie zuvor in der `CanExecute`\-Methode festgelegt haben.  
  
7.  Wählen Sie die F5\-TASTE erneut, oder auf der Menüleiste aus, wählen Sie **Debuggen**, **Weiter** aus.  
  
8.  Überprüfen Sie, ob der Code an dem Haltepunkt unterbrochen wird, den Sie zuvor in der `Execute`\-Methode festgelegt haben.  
  
9. Wählen Sie die F5\-TASTE, oder auf der Menüleiste aus, wählen Sie **Debuggen**, **Weiter** ein letztes Mal aus.  
  
     Im Webbrowser wird die SharePoint\-Website.  
  
10. Im **Listen**\-Abschnitt des Schnellstartbereichs, wählen Sie die Liste **Mitarbeiter** aus, und überprüfen Sie dann die folgenden Informationen:  
  
    -   Das Element, das Sie zuvor hinzugefügt haben \(manuell für Andy, der Funktionsmanager\) ist immer noch in der Liste.  
  
    -   Die **Rufnummer \(geschäftlich\)** und **E\-Mail\-Adresse** Spalten werden nicht in dieser Ansicht der Liste.  
  
     Die Bereitstellungskonfiguration **Upgrade** ändert die vorhandene **Employees**\-Listeninstanz auf der SharePoint\-Website.  Wenn Sie die Bereitstellungskonfiguration **Standard** anstelle der Konfiguration **Upgrade** verwendet hätten, wäre ein Bereitstellungskonflikt aufgetreten.  Visual Studio würde den Konflikt lösen, indem es die Liste **Mitarbeiter** ersetzt, und das \- Element für Andy, der Funktionsmanager, würde gelöscht.  
  
## Bereinigen des Entwicklungscomputers  
 Nach dem Abschluss der Tests für den Upgradebereitstellungsschritt entfernen Sie die Listeninstanz und die Listendefinition von der SharePoint\-Website. Entfernen Sie dann die Bereitstellungsschritterweiterung aus Visual Studio.  
  
#### So entfernen Sie die Listeninstanz von der SharePoint\-Website  
  
1.  Öffnen Sie die Liste **Mitarbeiter** auf der SharePoint\-Website, wenn die Liste nicht bereits geöffnet ist.  
  
2.  Klicken Sie im Menüband auf der SharePoint\-Website, wählen Sie die Registerkarte **Listentools** aus, und wählen Sie dann die Registerkarte aus. **Liste**  
  
3.  In der Gruppe **EinstellungenListeneinstellungen** wählen Sie das Element aus.  
  
4.  Die **Berechtigungen und Verwaltung** wählen Sie den Befehl **Diese Liste löschen**, wählen **OK**, um zu bestätigen, dass Sie die Liste an den Papierkorb senden möchten, und schließen dann den Webbrowser aus.  
  
#### So entfernen Sie die Listendefinition von der SharePoint\-Website  
  
1.  Klicken Sie in der experimentellen Instanz von Visual Studio, in der Menüleiste, wählen Sie **Erstellen**, **Zurückziehen** aus.  
  
     Visual Studio nimmt die Listendefinition von der SharePoint\-Website zurück.  
  
#### So deinstallieren Sie die Erweiterung  
  
1.  Klicken Sie in der experimentellen Instanz von Visual Studio, in der Menüleiste, wählen Sie **Tools**, **Erweiterungen und Updates** aus.  
  
     Das Dialogfeld wird geöffnet. **Erweiterungen und Updates**  
  
2.  In der Liste der Erweiterungen, wählen Sie **Aktualisieren Sie Bereitstellungsschritt für SharePoint\-Projekte** aus und wählen dann den Befehl **Deinstallieren** aus.  
  
3.  Im Dialogfeld, das angezeigt wird, wählen Sie **Ja**, um zu bestätigen, dass Sie die Erweiterung deinstallieren möchten, und wählen Sie dann **Jetzt neu starten**, um die Deinstallation abzuschließen.  
  
4.  Schließen Sie beide Instanzen von Visual Studio \(die experimentelle Instanz und die Instanz von Visual Studio, in der die Projektmappe "UpgradeDeploymentStep" geöffnet ist\).  
  
## Siehe auch  
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
  
  