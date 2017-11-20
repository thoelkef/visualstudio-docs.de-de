---
title: "Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Bereitstellungsschritts für SharePoint-Projekte | Microsoft Docs"
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
helpviewer_keywords:
- SharePoint commands
- SharePoint development in Visual Studio, extending deployment
ms.assetid: 4ba2d120-06b8-4ef3-84eb-c6c50ced9d82
caps.latest.revision: "63"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b7375071522ea59c9c00a5fa94277a3817438d25
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects"></a>Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Bereitstellungsschritts für SharePoint-Projekte
  Wenn Sie ein SharePoint-Projekt bereitstellen, führt Visual Studio eine Reihe von Schritten zur Bereitstellung in einer bestimmten Reihenfolge. Visual Studio enthält viele integrierte Bereitstellungsschritte, aber Sie können auch eigene erstellen.  
  
 In dieser exemplarischen Vorgehensweise erstellen Sie einen benutzerdefinierter Bereitstellungsschritt um Lösungen auf einem Server zu aktualisieren, auf dem SharePoint ausgeführt wird. Visual Studio umfasst integrierte Bereitstellungsschritte für viele Vorgänge, solche zurückziehen oder Hinzufügen von Projektmappen, aber dieser umfasst jedoch keines Bereitstellungsschritts für das Aktualisieren von Projektmappen. Wird standardmäßig beim Bereitstellen einer SharePoint-Lösung, Visual Studio zuerst die Lösung zurückzieht (sofern es bereits bereitgestellt ist) und stellt die gesamte Lösung erneut bereit. Weitere Informationen über die integrierte Bereitstellungsschritte finden Sie unter [bereitstellen, veröffentlichen und Aktualisieren von SharePoint-Lösungspakete](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).  
  
 Diese exemplarische Vorgehensweise enthält die folgenden Aufgaben:  
  
-   Erstellen einer Visual Studio-Erweiterung, die zwei Hauptaufgaben ausführt:  
  
    -   Die Erweiterung definiert einen benutzerdefinierter Bereitstellungsschritt aus, um die SharePoint-Lösungen zu aktualisieren.  
  
    -   Die Erweiterung erstellt eine projekterweiterung, die eine neue Bereitstellungskonfiguration definiert, der eine Reihe von Bereitstellungsschritten, die für ein angegebenes Projekt ausgeführt werden. Die neue Bereitstellungskonfiguration schließt den benutzerdefinierten Bereitstellungsschritt und mehrere integrierte Bereitstellungsschritte.  
  
-   Erstellen zwei benutzerdefinierte SharePoint-Befehle, die die Erweiterungsassembly aufruft. SharePoint-Befehle sind Methoden, die von Erweiterungsassemblys APIs in das Serverobjektmodell für SharePoint verwendet aufgerufen werden können. Weitere Informationen finden Sie unter [Aufrufe in die SharePoint-Objektmodelle](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
-   Erstellen eines Visual Studio-Erweiterung (VSIX) zum beide Assemblys bereitstellen.  
  
-   Testen den neuen Bereitstellungsschritt.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Zum Durchführen dieser exemplarischen Vorgehensweise werden auf dem Entwicklungscomputer die folgenden Komponenten benötigt:  
  
-   Unterstützte Editionen von Windows, SharePoint und Visual Studio. Weitere Informationen finden Sie unter [Anforderungen für die Entwicklung von SharePoint-Lösungen](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Das Visual Studio SDK. Diese exemplarische Vorgehensweise verwendet die **VSIX-Projekt** Vorlage im SDK, um ein VSIX-Paket zum Bereitstellen der Erweiterung zu erstellen. Weitere Informationen finden Sie unter [Erweitern der SharePoint-Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Kenntnisse der folgenden Konzepte sind hilfreich, wenn auch für die Durchführung der exemplarischen Vorgehensweise nicht erforderlich:  
  
-   Verwenden das Serverobjektmodell für SharePoint. Weitere Informationen finden Sie unter [mithilfe des Objektmodells von SharePoint Foundation serverseitige](http://go.microsoft.com/fwlink/?LinkId=177796).  
  
-   SharePoint-Lösungen. Weitere Informationen finden Sie unter [Übersicht über Projektmappen](http://go.microsoft.com/fwlink/?LinkId=169422).  
  
-   Aktualisieren SharePoint-Lösungen. Weitere Informationen finden Sie unter [Aktualisierung einer Lösung](http://go.microsoft.com/fwlink/?LinkId=177802).  
  
## <a name="creating-the-projects"></a>Erstellen der Projekte  
 Zum Durchführen dieser exemplarischen Vorgehensweise müssen Sie drei Projekte erstellen:  
  
-   Ein VSIX-Projekt, um das VSIX-Paket zum Bereitstellen der Erweiterung zu erstellen.  
  
-   Ein Klassenbibliotheksprojekt, das die Erweiterung implementiert. Dieses Projekt muss .NET Framework 4.5 als Zielversion.  
  
-   Ein Klassenbibliotheksprojekt, das die benutzerdefinierten SharePoint-Befehle definiert. Dieses Projekt muss .NET Framework 3.5 als Zielversion.  
  
 Beginnen Sie mit der exemplarischen Vorgehensweise, indem Sie beide Projekte erstellen.  
  
#### <a name="to-create-the-vsix-project"></a>So erstellen Sie das VSIX-Projekt  
  
1.  Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Wählen Sie in der Menüleiste **Datei**, **Neu**, **Projekt**aus.  
  
3.  In der **neues Projekt** Dialogfeld erweitern Sie die **Visual C#-** oder **Visual Basic** Knoten, und wählen Sie dann die **Erweiterbarkeit** Knoten.  
  
    > [!NOTE]  
    >  Die **Erweiterbarkeit** Knoten ist nur verfügbar, wenn Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie weiter oben in diesem Thema im Abschnitt zu den erforderlichen Komponenten.  
  
4.  Wählen Sie am oberen Rand des Dialogfelds, **.NET Framework 4.5** in der Liste der Versionen von .NET Framework.  
  
5.  Wählen Sie die **VSIX-Projekt** Vorlage, nennen Sie das Projekt **UpgradeDeploymentStep**, und wählen Sie dann die **OK** Schaltfläche.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Fügt der **UpgradeDeploymentStep** Projekt **Projektmappen-Explorer**.  
  
#### <a name="to-create-the-extension-project"></a>So erstellen Sie das Erweiterungsprojekt  
  
1.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für den UpgradeDeploymentStep Projektmappenknoten, wählen Sie **hinzufügen**, und wählen Sie dann **neues Projekt**.  
  
2.  In der **neues Projekt** Dialogfeld erweitern Sie die **Visual C#-** oder **Visual Basic** Knoten, und wählen Sie dann die **Windows** Knoten.  
  
3.  Wählen Sie am oberen Rand des Dialogfelds, **.NET Framework 4.5** in der Liste der Versionen von .NET Framework.  
  
4.  Wählen Sie die **-Klassenbibliothek** -Projektvorlage aus, nennen Sie das Projekt **DeploymentStepExtension**, und wählen Sie dann die **OK** Schaltfläche.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Fügt der **DeploymentStepExtension** Projekt der Projektmappe und öffnet die Class1-Codedatei.  
  
5.  Löschen Sie die Class1-Codedatei aus dem Projekt.  
  
#### <a name="to-create-the-sharepoint-command-project"></a>So erstellen die SharePoint-Befehlsprojekt  
  
1.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für den UpgradeDeploymentStep Projektmappenknoten, wählen Sie **hinzufügen**, und wählen Sie dann **neues Projekt**.  
  
2.  In der **neues Projekt** Dialogfeld erweitern Sie **Visual C#-** oder **Visual Basic**, und wählen Sie dann die **Windows** Knoten.  
  
3.  Wählen Sie am oberen Rand des Dialogfelds, **.NET Framework 3.5** in der Liste der Versionen von .NET Framework.  
  
4.  Wählen Sie die **-Klassenbibliothek** -Projektvorlage aus, nennen Sie das Projekt **"SharePointCommands"**, und wählen Sie dann die **OK** Schaltfläche.  
  
     Visual Studio fügt die **"SharePointCommands"** Projekt der Projektmappe und öffnet die Class1-Codedatei.  
  
5.  Löschen Sie die Class1-Codedatei aus dem Projekt.  
  
## <a name="configuring-the-projects"></a>Konfigurieren der Projekte  
 Bevor Sie Code zum Erstellen des benutzerdefinierten Bereitstellungsschritts schreiben, müssen Sie Codedateien und Assemblyverweise hinzufügen und müssen Sie die Projekte konfigurieren.  
  
#### <a name="to-configure-the-deploymentstepextension-project"></a>So konfigurieren Sie das Projekt DeploymentStepExtension  
  
1.  In der **DeploymentStepExtension** Projekt, fügen Sie zwei Codedateien mit den folgenden Namen benötigt:  
  
    -   UpgradeStep  
  
    -   DeploymentConfigurationExtension  
  
2.  Öffnen Sie das Kontextmenü für das Projekt DeploymentStepExtension, und wählen Sie dann **Verweis hinzufügen**.  
  
3.  Auf der **Framework** Registerkarte, aktivieren Sie das Kontrollkästchen für die System.ComponentModel.Compositions-Assembly.  
  
4.  Auf der **Erweiterungen** Registerkarte das Kontrollkästchen für die Microsoft.VisualStudio.SharePoint-Assembly, und wählen Sie dann die **OK** Schaltfläche.  
  
#### <a name="to-configure-the-sharepointcommands-project"></a>So konfigurieren Sie das SharePointCommands-Projekt  
  
1.  In der **"SharePointCommands"** Projekt, fügen Sie eine Codedatei mit dem Namen Befehle hinzu.  
  
2.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **"SharePointCommands"** Projektknoten, und wählen Sie dann **Verweis hinzufügen**.  
  
3.  Auf der **Erweiterungen** Registerkarte, wählen Sie die Kontrollkästchen für die folgenden Assemblys, und wählen Sie dann auf die **OK** Schaltfläche  
  
    -   Microsoft.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
## <a name="defining-the-custom-deployment-step"></a>Definieren der benutzerdefinierten Bereitstellungsschritts  
 Erstellen Sie eine Klasse, die die Bereitstellung eines Upgrades für-Schritt definiert. Den Bereitstellungsschritt implementiert die Klasse definiert die <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> Schnittstelle. Implementieren Sie diese Schnittstelle, wenn einen benutzerdefinierter Bereitstellungsschritt definiert werden sollen.  
  
#### <a name="to-define-the-custom-deployment-step"></a>Um den benutzerdefinierten Bereitstellungsschritt zu definieren  
  
1.  In der **DeploymentStepExtension** Projekt, öffnen Sie die Codedatei UpgradeStep und fügen Sie den folgenden Code hinein.  
  
    > [!NOTE]  
    >  Nachdem Sie diesen Code hinzufügen, muss das Projekt einige Kompilierungsfehler, aber natürlich werden hinzugefügt, wenn Code in späteren Schritten.  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs#1)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb#1)]  
  
## <a name="creating-a-deployment-configuration-that-includes-the-custom-deployment-step"></a>Erstellen einer Bereitstellungskonfiguration, enthält die benutzerdefinierten Bereitstellungsschritts  
 Erstellen Sie eine projekterweiterung für die neue Bereitstellungskonfiguration, gehören verschiedene integrierte Bereitstellungsschritte und die neue Bereitstellung eines Upgrades für-Schritt. Erstellen von dieser Erweiterung können Sie SharePoint-Entwicklern, die Bereitstellung eines Upgrades für-Schritt im SharePoint-Projekte zu verwenden.  
  
 So erstellen die Bereitstellungskonfiguration, die Klasse implementiert die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> Schnittstelle. Implementieren Sie diese Schnittstelle, wenn Sie eine Erweiterung für SharePoint-Projekt erstellen möchten.  
  
#### <a name="to-create-the-deployment-configuration"></a>Die Bereitstellungskonfiguration erstellen  
  
1.  
  
2.  In der **DeploymentStepExtension** Projekt, öffnen Sie die Codedatei DeploymentConfigurationExtension und fügen Sie den folgenden Code hinein.  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/deploymentconfigurationextension.cs#2)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/deploymentconfigurationextension.vb#2)]  
  
## <a name="creating-the-custom-sharepoint-commands"></a>Erstellen der benutzerdefinierten SharePoint-Befehle  
 Erstellen Sie zwei benutzerdefinierte Befehle, die für SharePoint in das Serverobjektmodell aufrufen. Ein Befehl bestimmt, ob bereits eine Projektmappe bereitgestellt wird. mit dem anderen Befehl wird eine Lösung aktualisiert.  
  
#### <a name="to-define-the-sharepoint-commands"></a>So definieren Sie die SharePoint-Befehle  
  
1.  In der **"SharePointCommands"** Projekt, öffnen Sie die Codedatei Commands und fügen Sie den folgenden Code hinein.  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs#4)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb#4)]  
  
## <a name="checkpoint"></a>Checkpoint  
 An diesem Punkt in der exemplarischen Vorgehensweise alle der Code für den benutzerdefinierten Bereitstellungsschritt und die SharePoint-Befehle sind jetzt in den Projekten. Erstellen Sie sie, um sicherzustellen, dass sie fehlerfrei kompiliert werden.  
  
#### <a name="to-build-the-projects"></a>Erstellen der Projekte  
  
1.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **DeploymentStepExtension** Projekt, und wählen Sie dann **erstellen**.  
  
2.  Öffnen Sie das Kontextmenü für die **"SharePointCommands"** Projekt, und wählen Sie dann **erstellen**.  
  
## <a name="creating-a-vsix-package-to-deploy-the-extension"></a>Erstellen ein VSIX-Paket zum Bereitstellen der Erweiterung  
 Zum Bereitstellen der Erweiterung erstellen Sie anhand des VSIX-Projekts in der Lösung ein VSIX-Paket. Konfigurieren Sie zuerst das VSIX-Paket, indem der Datei source.extension.vsixmanifest im VSIX-Projekts ändern. Dann erstellen Sie das VSIX-Paket, indem Sie beim Erstellen der Projektmappe.  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>So erstellen und konfigurieren Sie das VSIX-Paket  
  
1.  In **Projektmappen-Explorer**unter der **UpgradeDeploymentStep** Projekt, öffnen Sie das Kontextmenü für die **"Source.Extension.vsixmanifest"** , und wählen Sie dann  **Open**.  
  
     Die Datei wird von Visual Studio im Manifest-Editor geöffnet. Die Datei "source.extension.vsixmanifest" bildet die Grundlage für die Datei "extension.vsixmanifest", die für alle VSIX-Pakete erforderlich ist. Weitere Informationen zu dieser Datei finden Sie unter [VSIX-Erweiterung Schemareferenz 1.0](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  In der **Produktname** geben **Bereitstellungsschritts für SharePoint-Projekte aktualisieren**.  
  
3.  In der **Autor** geben **Contoso**.  
  
4.  In der **Beschreibung** geben **stellt einen benutzerdefinierte Bereitstellung eines Upgrades für-Schritt, die in SharePoint-Projekten verwendet werden kann**.  
  
5.  In der **Bestand** Registerkarte im Editor wählen Sie die **neu** Schaltfläche.  
  
     Die **neue Anlage hinzufügen** Dialogfeld wird angezeigt.  
  
6.  In der **Typ** wählen **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Dieser Wert entspricht dem `MefComponent`-Element in der Datei "extension.vsixmanifest". Von diesem Element wird der Name einer Erweiterungsassembly im VSIX-Paket angegeben. Weitere Informationen finden Sie unter [MEFComponent-Element (VSX-Schema)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
7.  In der **Quelle** wählen **ein Projekt in der aktuellen Projektmappe**.  
  
8.  In der **Projekt** wählen **DeploymentStepExtension**, und wählen Sie dann die **OK** Schaltfläche.  
  
9. Wählen Sie im manifest-Editor die **neu** erneut.  
  
     Die **neue Anlage hinzufügen** Dialogfeld wird angezeigt.  
  
10. In der **Typ** aus, geben Sie **SharePoint.Commands.v4**.  
  
    > [!NOTE]  
    >  Dieses Element gibt eine benutzerdefinierte Erweiterung, die Sie in der Visual Studio-Erweiterung einschließen möchten. Weitere Informationen finden Sie unter [Asset-Element (VSX-Schema)](http://msdn.microsoft.com/en-us/9fcfc098-edc7-484b-9d4c-acd17829d737).  
  
11. In der **Quelle** wählen **ein Projekt in der aktuellen Projektmappe**.  
  
12. In der **Projekt** wählen **"SharePointCommands"**, und wählen Sie dann die **OK** Schaltfläche.  
  
13. Wählen Sie in der Menüleiste **erstellen**, **Projektmappe**, und stellen Sie sicher, dass die Lösung ohne Fehler kompiliert wird.  
  
14. Stellen Sie sicher, dass der Buildausgabeordner für das Projekt UpgradeDeploymentStep jetzt die Datei UpgradeDeploymentStep.VSIX enthält.  
  
     Standardmäßig handelt es sich beim Buildausgabeordner um den Ordner "...\bin\Debug" in dem Ordner mit der Projektdatei.  
  
## <a name="preparing-to-test-the-upgrade-deployment-step"></a>So testen Sie die Bereitstellung eines Upgrades für-Schritt vorbereiten  
 Zum Testen des Bereitstellung eines Upgrades für-Schritt müssen Sie zuerst eine beispiellösung zur SharePoint-Website bereitstellen. Starten Sie durch die Erweiterung in der experimentellen Instanz von Visual Studio debuggen. Erstellen Sie eine Listendefinition und einer Listeninstanz zu verwenden, um den Bereitstellungsschritt zu testen und dann auf der SharePoint-Website bereitgestellt werden. Als Nächstes ändern Sie die Listendefinition und einer Listeninstanz und erneut bereitstellen Sie, um zu veranschaulichen, wie der standardmäßige Bereitstellung Lösungen auf der SharePoint-Website überschrieben.  
  
 Weiter unten in dieser exemplarischen Vorgehensweise bearbeiten Sie die Listendefinition und einer Listeninstanz, und klicken Sie dann führen Sie ein upgrade sie auf der SharePoint-Website.  
  
#### <a name="to-start-debugging-the-extension"></a>So debuggen Sie die Erweiterung  
  
1.  Starten Sie Visual Studio mit Administratoranmeldeinformationen, und öffnen Sie die Projektmappe "UpgradeDeploymentStep".  
  
2.  Klicken Sie im Projekt DeploymentStepExtension UpgradeStep-Codedatei öffnen, und fügen Sie einen Haltepunkt an der ersten Codezeile in der `CanExecute` und `Execute` Methoden.  
  
3.  Starten Sie durch Auswählen der F5-Taste, oder, in der Menüleiste **Debuggen**, **Debuggen**.  
  
4.  Visual Studio die Erweiterung %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Upgrade Bereitstellungsschritts für SharePoint Projects\1.0 und eine experimentelle Instanz von Visual Studio wird gestartet. Sie testen den Bereitstellung eines Upgrades für-Schritt in dieser Instanz von Visual Studio.  
  
#### <a name="to-create-a-sharepoint-project-with-a-list-definition-and-a-list-instance"></a>So erstellen Sie ein SharePoint-Projekt mit einer Listendefinition und einer Listeninstanz  
  
1.  Wählen Sie in der experimentellen Instanz von Visual Studio in der Menüleiste **Datei**, **neu**, **Projekt**.  
  
2.  In der **neues Projekt** Dialogfeld erweitern Sie die **Visual C#-** Knoten oder die **Visual Basic** Knoten, erweitern Sie die **SharePoint** Knoten, und wählen Sie dann die **2010** Knoten.  
  
3.  Stellen Sie im oberen Bereich des Dialogfelds sicher, dass **.NET Framework 3.5** erscheint in der Liste der Versionen von .NET Framework.  
  
     Projekte für [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] und [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] erfordern diese Version von .NET Framework.  
  
4.  Wählen Sie in der Liste der Projektvorlagen **SharePoint 2010-Projekt**, nennen Sie das Projekt **EmployeesListDefinition**, und wählen Sie dann die **OK** Schaltfläche.  
  
5.  In der **Assistent zum Anpassen von SharePoint**, geben Sie die URL der Site, die Sie zum Debuggen verwenden möchten.  
  
6.  Klicken Sie unter **was der Vertrauensebene für diese SharePoint-Lösung ist**, wählen Sie die **als farmlösung bereitstellen** Optionsfeld.  
  
    > [!NOTE]  
    >  Die Bereitstellung eines Upgrades für-Schritt unterstützt keine sandkastenlösungen.  
  
7.  Wählen Sie die **Fertig stellen** Schaltfläche.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]erstellt das Projekt EmployeesListDefinition.  
  
8.  Öffnen Sie das Kontextmenü für das EmployeesListDefinition-Projekt, wählen Sie **hinzufügen**, und wählen Sie dann **neues Element**.  
  
9. In der **neues Element hinzufügen - EmployeesListDefinition** Dialogfeld erweitern Sie die **SharePoint** Knoten, und wählen Sie dann die **2010** Knoten.  
  
10. Wählen Sie die **Liste** Elementvorlage, nennen Sie das Element **Mitarbeiterliste**, und wählen Sie dann die **hinzufügen** Schaltfläche.  
  
     Der Assistent zum Anpassen von SharePoint wird angezeigt.  
  
11. Auf der **Listeneinstellungen auswählen** Seite, überprüfen Sie die folgenden Einstellungen, und wählen Sie dann die **Fertig stellen** Schaltfläche:  
  
    1.  **Mitarbeiterliste** wird angezeigt, der **welchen Namen möchten Sie für Ihre Liste anzuzeigen?** Feld.  
  
    2.  Die **erstellen Sie eine anpassbare Liste basierend auf:** Optionsfeld ausgewählt wird.  
  
    3.  **Standardwert (leer)** ausgewählt wird, der **erstellen Sie eine anpassbare Liste basierend auf:** Liste.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Das Listenelement für Mitarbeiter mit einer Titelspalte und eine leere Instanz erstellt und der Liste-Designer geöffnet.  
  
12. In den Listen-Designer auf die **Spalten** Registerkarte, und wählen Sie die **Geben Sie einen neuen oder vorhandenen Spaltennamen** Zeile aus, und fügen Sie die folgenden Spalten in der **Spalte Anzeigename** Liste:  
  
    1.  Vorname  
  
    2.  Firma  
  
    3.  Telefon (geschäftlich)  
  
    4.  -E-Mail  
  
13. Speichern Sie alle Dateien zu und schließen Sie dann mit dem Listen-Designer.  
  
14. In **Projektmappen-Explorer**, erweitern Sie die **Mitarbeiterliste** Knoten, und erweitern Sie dann die **Mitarbeiter Listeninstanz** untergeordneten Knoten.  
  
15. Ersetzen Sie in der Datei "Elements.xml" das Standard-XML in dieser Datei durch folgendes XML. Dieser XML-Code ändert den Namen der Liste, um **Mitarbeiter** und fügt Informationen für ein Mitarbeiter, Jim Hance benannt wurde.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
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
  
16. Speichern Sie und schließen Sie die Datei "Elements.xml".  
  
17. Öffnen Sie das Kontextmenü für das Projekt EmployeesListDefinition, und wählen Sie dann **öffnen** oder **Eigenschaften**.  
  
     Die Eigenschaften-Designer wird geöffnet.  
  
18. Auf der **SharePoint** Registerkarte Deaktivieren der **nach Debuggen automatisch zurückziehen** Kontrollkästchen, und speichern Sie die Eigenschaften.  
  
#### <a name="to-deploy-the-list-definition-and-list-instance"></a>Zur Bereitstellung der Listendefinition und einer Listeninstanz  
  
1.  In **Projektmappen-Explorer**, wählen Sie die **EmployeesListDefinition** Projektknoten aus.  
  
2.  In der **Eigenschaften** Fenster, stellen Sie sicher, dass die **aktive Bereitstellungskonfiguration** -Eigenschaftensatz auf **Standard**.  
  
3.  Drücken Sie die F5-Taste, oder wählen Sie in der Menüleiste **Debuggen**, **Debuggen**.  
  
4.  Stellen Sie sicher, dass das Projekt erfolgreich erstellt wurde, auf die SharePoint-Website im Webbrowser wird geöffnet, die die **listet** Element in der Schnellstartleiste enthält das neue **Mitarbeiter** Liste, und dass die  **Mitarbeiter** Liste den Eintrag für Jim Hance enthält.  
  
5.  Schließen Sie den Webbrowser.  
  
#### <a name="to-modify-the-list-definition-and-list-instance-and-redeploy-them"></a>Die Listendefinition und einer Listeninstanz ändern und erneut bereitstellen  
  
1.  Öffnen Sie im Projekt EmployeesListDefinition, die Datei "Elements.xml"-Datei, die ein untergeordnetes Element des der **Mitarbeiter Listeninstanz** Projektelement.  
  
2.  Entfernen Sie die `Data` Element und seine untergeordneten Elemente auf den Eintrag für Jim Hance aus der Liste zu entfernen.  
  
     Wenn Sie fertig sind, sollte die Datei die folgenden XML-Code enthalten.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <ListInstance Title="Employees"  
                    OnQuickLaunch="TRUE"  
                    TemplateType="10000"  
                    Url="Lists/Employees"  
                    Description="Simple list to test upgrade deployment step">  
      </ListInstance>  
    </Elements>  
    ```  
  
3.  Speichern Sie und schließen Sie die Datei "Elements.xml".  
  
4.  Öffnen Sie das Kontextmenü für die **Mitarbeiterliste** Projektelement, und wählen Sie dann **öffnen** oder **Eigenschaften**.  
  
5.  Wählen Sie in der Liste-Designer die **Ansichten** Registerkarte.  
  
6.  In der **ausgewählte Spalten** wählen **Anlagen**, und wählen Sie dann die < Taste gedrückt, um diese Spalte die **verfügbaren Spalten** Liste.  
  
7.  Wiederholen Sie den vorherigen Schritt zum Verschieben der **geschäftliche Telefonnummer** Spalte aus der **ausgewählte Spalten** Liste der **verfügbaren Spalten** Liste.  
  
     Diese Aktion entfernt diese Felder aus der Standardansicht des der **Mitarbeiter** Liste auf der SharePoint-Website.  
  
8.  Starten Sie durch Auswählen der F5-Taste, oder, in der Menüleiste **Debuggen**, **Debuggen**.  
  
9. Überprüfen Sie, ob die **Bereitstellungskonflikte** Dialogfeld wird angezeigt.  
  
     Dieses Dialogfeld wird angezeigt, wenn Visual Studio zum Bereitstellen einer Lösung (die Listeninstanz) versucht, einer SharePoint-Website, auf die betreffende Projektmappe bereits bereitgestellt wurde. Dieses Dialogfeld wird nicht angezeigt, wenn Sie die Bereitstellung eines Upgrades für-Schritt weiter unten in dieser exemplarischen Vorgehensweise ausführen.  
  
10. In der **Bereitstellungskonflikte** Dialogfeld Wählen Sie die **automatisch lösen** Optionsfeld.  
  
     Visual Studio löscht die Listeninstanz auf SharePoint-Website, stellt das Listenelement in das Projekt und öffnet dann die SharePoint-Website.  
  
11. In der **listet** Abschnitt der Schnellstartleiste, wählen Sie die **Mitarbeiter** aus, und klicken Sie dann überprüfen Sie die folgenden Details:  
  
    -   Die **Anlagen** und **Telefon (privat)** Spalten nicht in dieser Ansicht der Liste angezeigt werden.  
  
    -   Die Liste ist leer. Wenn Sie verwendet die **Standard** Bereitstellungskonfiguration, die Lösung erneut bereitzustellen, die **Mitarbeiter** Liste wurde ersetzt durch die neue leere Liste in Ihrem Projekt.  
  
## <a name="testing-the-deployment-step"></a>Testen des Bereitstellungsschritts  
 Sie können nun die Bereitstellung eines Upgrades für-Schritt testen. Fügen Sie zunächst ein Element, um die Listeninstanz in SharePoint. Ändern Sie die Listendefinition und einer Listeninstanz und vergewissern Sie sich, dass der Schritt der Bereitstellung eines Upgrades für das neue Element überschrieben werden nicht auf die SharePoint-Website zu aktualisieren.  
  
#### <a name="to-manually-add-an-item-to-the-list"></a>Ein Element der Liste manuell hinzufügen  
  
1.  Im Menüband auf der SharePoint-Website unter der **Listentools** Registerkarte, und wählen Sie die **Elemente** Registerkarte.  
  
2.  In der **neu** Gruppe **neues Element**.  
  
     Als Alternative können Sie wählen Sie die **neues Element hinzufügen** Link in der Elementliste selbst.  
  
3.  In der **Mitarbeiter - neues Element** Fenster, in der **Titel** geben **Einrichtungs-Manager**.  
  
4.  In der **Vorname** geben **Andy**.  
  
5.  In der **Unternehmen** geben **Contoso**.  
  
6.  Wählen Sie die **speichern** Schaltfläche, stellen Sie sicher, dass das neue Element in der Liste angezeigt wird, und schließen Sie den Webbrowser.  
  
     Weiter unten in dieser exemplarischen Vorgehensweise verwenden Sie dieses Element aus, um sicherzustellen, dass der Schritt der Bereitstellung eines Upgrades für den Inhalt dieser Liste überschreiben nicht.  
  
#### <a name="to-test-the-upgrade-deployment-step"></a>So testen Sie die Bereitstellung eines Upgrades für-Schritt  
  
1.  In der experimentellen Instanz von Visual Studio in **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **EmployeesListDefinition** Projektknoten, und wählen Sie dann **Eigenschaften**.  
  
     Die Eigenschaften-Editor/Designer wird geöffnet.  
  
2.  Auf der **SharePoint** Registerkarte, legen Sie die **aktive Bereitstellungskonfiguration** Eigenschaft **Upgrade**.  
  
     Diese benutzerdefinierte Bereitstellungskonfiguration umfasst die neue Bereitstellung eines Upgrades für-Schritt.  
  
3.  Öffnen Sie das Kontextmenü für die **Mitarbeiterliste** Projektelement, und wählen Sie dann **Eigenschaften** oder **öffnen**.  
  
     Die Eigenschaften-Editor/Designer wird geöffnet.  
  
4.  Auf der **Ansichten** Registerkarte, und wählen Sie die **E-Mail** Spalte, und wählen Sie dann die  **<**  Taste gedrückt, um diese Spalte aus der **ausgewählte Spalten**Liste der **verfügbaren Spalten** Liste.  
  
     Diese Aktion entfernt diese Felder aus der Standardansicht des der **Mitarbeiter** Liste auf der SharePoint-Website.  
  
5.  Starten Sie durch Auswählen der F5-Taste, oder, in der Menüleiste **Debuggen**, **Debuggen**.  
  
6.  Überprüfen Sie, ob die Codeausführung in der anderen Instanz von Visual Studio an dem Haltepunkt unterbrochen wird, den Sie zuvor in der `CanExecute`-Methode festgelegt haben.  
  
7.  Wählen Sie die F5-Taste erneut aus, oder wählen Sie in der Menüleiste **Debuggen**, **Fortfahren**.  
  
8.  Stellen Sie sicher, dass der Code an dem Haltepunkt unterbrochen wird, die Sie zuvor im Festlegen der `Execute` Methode.  
  
9. Drücken Sie die F5-Taste, oder wählen Sie in der Menüleiste **Debuggen**, **Fortfahren** ein letztes Mal.  
  
     Im Webbrowser wird die SharePoint-Website geöffnet.  
  
10. In der **listet** Abschnitt der Schnellstartbereich, wählen Sie die **Mitarbeiter** aus, und klicken Sie dann überprüfen Sie die folgenden Details:  
  
    -   Das Element, das Sie manuell hinzugefügt haben, zuvor (für Andy, einrichtungs-Manager) ist weiterhin in der Liste.  
  
    -   Die **geschäftliche Telefonnummer** und **e-Mail-Adresse** Spalten nicht in dieser Ansicht der Liste angezeigt werden.  
  
     Die **Upgrade** Bereitstellungskonfiguration ändert das vorhandene **Mitarbeiter** Listeninstanz auf SharePoint-Website. Bei Verwendung der **Standard** Bereitstellungskonfiguration anstelle von der **Upgrade** Konfiguration wäre einen Bereitstellungskonflikt auftreten. Visual Studio würde den Konflikt lösen, indem Sie ersetzen die **Mitarbeiter** Liste aus, und das Element für Andy, die einrichtungs-Manager werden gelöscht.  
  
## <a name="cleaning-up-the-development-computer"></a>Bereinigen des Entwicklungscomputers  
 Nachdem Sie die Tests des Bereitstellung eines Upgrades für-Schritt abgeschlossen haben, entfernen Sie die Listeninstanz und die Listendefinition aus SharePoint-Website, und entfernen Sie die Bereitstellung-Schritt-Erweiterung aus Visual Studio.  
  
#### <a name="to-remove-the-list-instance-from-the-sharepoint-site"></a>So entfernen Sie die Listeninstanz aus der SharePoint-Website  
  
1.  Öffnen Sie die **Mitarbeiter** Liste auf der SharePoint-Website, wenn die Liste nicht bereits geöffnet ist.  
  
2.  Wählen Sie im Menüband auf der SharePoint-Website, die **Listentools** Registerkarte, und wählen Sie dann die **Liste** Registerkarte.  
  
3.  In der **Einstellungen** gruppieren, wählen Sie die **Listeneinstellungen** Element.  
  
4.  Klicken Sie unter **Berechtigungen und Verwaltung**, wählen Sie die **diese Liste löschen** Befehl, wählen Sie **OK** zu bestätigen, dass Sie verwenden möchten, senden Sie die Liste in den Papierkorb verschoben, und schließen Sie dann im Web Browser.  
  
#### <a name="to-remove-the-list-definition-from-the-sharepoint-site"></a>So entfernen die Listendefinition aus SharePoint-Website  
  
1.  Wählen Sie in der experimentellen Instanz von Visual Studio in der Menüleiste **erstellen**, **zurückziehen**.  
  
     Visual Studio wird die Listendefinition aus SharePoint-Website.  
  
#### <a name="to-uninstall-the-extension"></a>So deinstallieren Sie die Erweiterung  
  
1.  Wählen Sie in der experimentellen Instanz von Visual Studio in der Menüleiste **Tools**, **Erweiterungen und Updates**.  
  
     Das Dialogfeld **Erweiterungen und Updates** wird geöffnet.  
  
2.  Wählen Sie in der Liste der Erweiterungen, **Bereitstellungsschritts für SharePoint-Projekte aktualisieren**, und wählen Sie dann die **Deinstallieren** Befehl.  
  
3.  Wählen Sie im angezeigten Dialogfeld **Ja** zu bestätigen, dass Sie verwenden möchten, Deinstallieren der Erweiterung, und wählen Sie dann **jetzt neu starten** um die Deinstallation abzuschließen.  
  
4.  Schließen Sie beide Instanzen von Visual Studio (die experimentelle Instanz und die Instanz von Visual Studio, in dem die UpgradeDeploymentStep Projektmappe geöffnet ist).  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern von SharePoint-Packen und -Bereitstellen](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
  
  