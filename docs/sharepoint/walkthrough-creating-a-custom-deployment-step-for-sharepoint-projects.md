---
title: Erstellen von benutzerdefinierten Bereitstellungsschritts für SharePoint-Projekte
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands
- SharePoint development in Visual Studio, extending deployment
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7488bb8b54751c7780cb9751309d227e5d5cb758
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/30/2019
ms.locfileid: "66401092"
---
# <a name="walkthrough-create-a-custom-deployment-step-for-sharepoint-projects"></a>Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Bereitstellungsschritts für SharePoint-Projekte
  Wenn Sie ein SharePoint-Projekt bereitstellen, führt Visual Studio eine Reihe von Schritten zur Bereitstellung in einer bestimmten Reihenfolge. Visual Studio enthält viele integrierte Bereitstellungsschritte, aber Sie können auch eigene erstellen.

 In dieser exemplarischen Vorgehensweise erstellen Sie ein benutzerdefinierten Bereitstellungsschritts um Lösungen auf einem Server zu aktualisieren, auf dem SharePoint ausgeführt wird. Visual Studio umfasst integrierte Bereitstellungsschritte für viele Aufgaben, diese deinstallieren und zurückziehen oder Hinzufügen von Lösungen, aber einen Bereitstellungsschritt zum Aktualisieren von Lösungen nicht enthalten sind. In der Standardeinstellung beim Bereitstellen einer SharePoint-Lösung, Visual Studio zuerst die Lösung zurückzieht (Wenn sie bereits bereitgestellt wurde) und stellt die gesamte Lösung erneut bereit. Weitere Informationen zu den Schritten zur integrierten Bereitstellung, finden Sie unter [bereitstellen, veröffentlichen und Aktualisieren von SharePoint-Lösungspakete](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).

 Diese exemplarische Vorgehensweise enthält die folgenden Aufgaben:

- Erstellen einer Visual Studio-Erweiterung, die zwei Hauptaufgaben ausführt:

    - Die Erweiterung definiert ein benutzerdefinierten Bereitstellungsschritts um SharePoint-Lösungen zu aktualisieren.

    - Die Erweiterung erstellt eine projekterweiterung, die eine neue Bereitstellungskonfiguration definiert, der eine Reihe von Bereitstellungsschritten, die für ein bestimmtes Projekt ausgeführt werden. Die neue Bereitstellungskonfiguration enthält die benutzerdefinierten Bereitstellungsschritts und mehrere integrierte Bereitstellungsschritte.

- Erstellen Sie zwei benutzerdefinierte SharePoint-Befehle, die die Erweiterungsassembly aufruft. SharePoint-Befehle sind Methoden, die von Erweiterungsassemblys APIs im Server-Objektmodell für SharePoint verwenden aufgerufen werden können. Weitere Informationen finden Sie unter [rufen Sie in der SharePoint-Objektmodelle](../sharepoint/calling-into-the-sharepoint-object-models.md).

- Erstellen eines Visual Studio-Erweiterung (VSIX) zum beide Assemblys bereitstellen.

- Testen den neuen Bereitstellungsschritt.

## <a name="prerequisites"></a>Vorraussetzungen
 Zum Durchführen dieser exemplarischen Vorgehensweise werden auf dem Entwicklungscomputer die folgenden Komponenten benötigt:

- Unterstützte Editionen von Windows, SharePoint und Visual Studio.

- Das Visual Studio SDK. Diese exemplarische Vorgehensweise verwendet die **VSIX-Projekt** Vorlage in das SDK zum Erstellen eines VSIX-Pakets zum Bereitstellen der Erweiterung. Weitere Informationen finden Sie unter [Erweitern der SharePoint-Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  Kenntnisse der folgenden Konzepte sind hilfreich, wenn auch für die Durchführung der exemplarischen Vorgehensweise nicht erforderlich:

- Verwenden das Serverobjektmodell für SharePoint. Weitere Informationen finden Sie unter [mithilfe des Objektmodells von SharePoint Foundation Server-Side](http://go.microsoft.com/fwlink/?LinkId=177796).

- SharePoint-Lösungen. Weitere Informationen finden Sie unter [Übersicht über Lösungen](http://go.microsoft.com/fwlink/?LinkId=169422).

- Aktualisieren von SharePoint-Lösungen. Weitere Informationen finden Sie unter [aktualisieren eine Lösung](http://go.microsoft.com/fwlink/?LinkId=177802).

## <a name="create-the-projects"></a>Erstellen Sie die Projekte
 Um diese exemplarische Vorgehensweise abzuschließen, müssen Sie drei Projekte erstellen:

- Ein VSIX-Projekt zum Erstellen des VSIX-Pakets zum Bereitstellen der Erweiterung.

- Ein Klassenbibliotheksprojekt, das die Erweiterung implementiert. Dieses Projekt muss .NET Framework 4.5 als Ziel.

- Ein Klassenbibliotheksprojekt, das die benutzerdefinierten SharePoint-Befehle definiert. Dieses Projekt muss .NET Framework 3.5 als Ziel.

  Beginnen Sie mit der exemplarischen Vorgehensweise, indem Sie beide Projekte erstellen.

#### <a name="to-create-the-vsix-project"></a>So erstellen Sie das VSIX-Projekt

1. Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Klicken Sie in der Menüleiste auf **Datei** > **Neu** > **Projekt**.

3. In der **neues Projekt** Dialogfeld erweitern Sie die **Visual C#-** oder **Visual Basic** Knoten, und wählen Sie dann die **Erweiterbarkeit** Knoten.

    > [!NOTE]
    > Die **Erweiterbarkeit** Knoten ist nur verfügbar, wenn Sie Visual Studio SDK installieren. Weitere Informationen finden Sie weiter oben in diesem Thema im Abschnitt zu den erforderlichen Komponenten.

4. Wählen Sie am oberen Rand des Dialogfelds, **.NET Framework 4.5** in der Liste der Versionen von .NET Framework.

5. Wählen Sie die **VSIX-Projekt** Vorlage, nennen Sie das Projekt **UpgradeDeploymentStep**, und wählen Sie dann die **OK** Schaltfläche.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Fügt der **UpgradeDeploymentStep** Projekt **Projektmappen-Explorer**.

#### <a name="to-create-the-extension-project"></a>So erstellen Sie das Erweiterungsprojekt

1. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für den UpgradeDeploymentStep-Projektmappenknoten, wählen **hinzufügen**, und wählen Sie dann **neues Projekt**.

2. In der **neues Projekt** Dialogfeld erweitern Sie die **Visual C#-** oder **Visual Basic** Knoten, und wählen Sie dann die **Windows** Knoten.

3. Wählen Sie am oberen Rand des Dialogfelds, **.NET Framework 4.5** in der Liste der Versionen von .NET Framework.

4. Wählen Sie die **Klassenbibliothek** -Projektvorlage aus, nennen Sie das Projekt **DeploymentStepExtension**, und wählen Sie dann die **OK** Schaltfläche.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Fügt der **DeploymentStepExtension** -Projekt zur Projektmappe und öffnet die Class1-Codedatei.

5. Löschen Sie die Class1-Codedatei aus dem Projekt.

#### <a name="to-create-the-sharepoint-command-project"></a>Zum Erstellen des Projekts der SharePoint-Befehl

1. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für den UpgradeDeploymentStep-Projektmappenknoten, wählen **hinzufügen**, und wählen Sie dann **neues Projekt**.

2. In der **neues Projekt** Dialogfeld erweitern Sie **Visual C#-** oder **Visual Basic**, und wählen Sie dann die **Windows** Knoten.

3. Wählen Sie am oberen Rand des Dialogfelds, **.NET Framework 3.5** in der Liste der Versionen von .NET Framework.

4. Wählen Sie die **Klassenbibliothek** -Projektvorlage aus, nennen Sie das Projekt **SharePointCommands**, und wählen Sie dann die **OK** Schaltfläche.

     Visual Studio fügt die **SharePointCommands** -Projekt zur Projektmappe und öffnet die Class1-Codedatei.

5. Löschen Sie die Class1-Codedatei aus dem Projekt.

## <a name="configure-the-projects"></a>Konfigurieren Sie die Projekte
 Bevor Sie Code zum Erstellen von benutzerdefinierten Bereitstellungsschritts schreiben, müssen Sie Codedateien und Assemblyverweise hinzufügen, und Sie müssen die Projekte konfigurieren.

#### <a name="to-configure-the-deploymentstepextension-project"></a>So konfigurieren Sie das Projekt DeploymentStepExtension

1. In der **DeploymentStepExtension** fügen zwei Codedateien mit den folgenden Namen:

    - UpgradeStep

    - DeploymentConfigurationExtension

2. Öffnen Sie das Kontextmenü für das Projekt DeploymentStepExtension, und wählen Sie dann **Verweis hinzufügen**.

3. Auf der **Framework** wählen Sie das Kontrollkästchen für die System.ComponentModel.Compositions-Assembly.

4. Auf der **Erweiterungen** Registerkarte aktivieren Sie das Kontrollkästchen für die der Microsoft.VisualStudio.SharePoint-Assembly, und wählen Sie dann die **OK** Schaltfläche.

#### <a name="to-configure-the-sharepointcommands-project"></a>So konfigurieren Sie das SharePointCommands-Projekt

1. In der **SharePointCommands** Projekt, fügen Sie eine Codedatei mit dem Namen Befehle.

2. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **SharePointCommands** Projektknoten, und wählen Sie dann **Verweis hinzufügen**.

3. Auf der **Erweiterungen** Registerkarte, die Kontrollkästchen für die folgenden Assemblys, und wählen Sie auf die **OK** Schaltfläche

    - Microsoft.SharePoint

    - Microsoft.VisualStudio.SharePoint.Commands

## <a name="define-the-custom-deployment-step"></a>Definieren der benutzerdefinierten Bereitstellungsschritts
 Erstellen Sie eine Klasse, die den Schritt der Bereitstellung eines Upgrades definiert. Zum Definieren des Bereitstellungsschritts, der die Klasse implementiert die <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> Schnittstelle. Implementieren Sie diese Schnittstelle, wenn einen benutzerdefinierter Bereitstellungsschritt definiert werden sollen.

#### <a name="to-define-the-custom-deployment-step"></a>Um den benutzerdefinierten Bereitstellungsschritt zu definieren

1. In der **DeploymentStepExtension** Projekt, öffnen Sie die Codedatei UpgradeStep und fügen Sie den folgenden Code hinein.

    > [!NOTE]
    > Nachdem Sie diesen Code hinzufügen, muss das Projekt einige Kompilierungsfehler, aber allerdings verschwinden fügen Sie Code bei in späteren Schritten fest.

     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs#1)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb#1)]

## <a name="create-a-deployment-configuration-that-includes-the-custom-deployment-step"></a>Erstellen Sie eine Bereitstellungskonfiguration, die den benutzerdefinierten Bereitstellungsschritt enthält.
 Erstellen Sie eine projekterweiterung für die neue Bereitstellungskonfiguration umfasst mehrere integrierte Bereitstellungsschritte und der neue Schritt der Bereitstellung des Upgrades. Erstellen Sie diese Erweiterung, können Sie die SharePoint-Entwicklern den Schritt der Bereitstellung eines Upgrades in der SharePoint-Projekte verwenden.

 Zum Erstellen der Bereitstellungskonfiguration, die Klasse implementiert die <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> Schnittstelle. Implementieren Sie diese Schnittstelle, wenn Sie eine Erweiterung für SharePoint-Projekt erstellen möchten.

#### <a name="to-create-the-deployment-configuration"></a>Um die Konfiguration der Bereitstellung zu erstellen.

1. In der **DeploymentStepExtension** Projekt, öffnen Sie die Codedatei DeploymentConfigurationExtension und fügen Sie den folgenden Code hinein.

     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/deploymentconfigurationextension.cs#2)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/deploymentconfigurationextension.vb#2)]

## <a name="create-the-custom-sharepoint-commands"></a>Erstellen Sie die benutzerdefinierten SharePoint-Befehle
 Erstellen Sie zwei benutzerdefinierte Befehle, die das Serverobjektmodell für die SharePoint aufrufen. Ein Befehl ermittelt, ob es sich bei eine Lösung bereits bereitgestellt wurde. der zweite Befehl aktualisiert eine Lösung.

#### <a name="to-define-the-sharepoint-commands"></a>So definieren Sie die SharePoint-Befehle

1. In der **SharePointCommands** Projekt, öffnen Sie die Codedatei Commands und fügen Sie den folgenden Code hinein.

     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs#4)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb#4)]

## <a name="checkpoint"></a>Checkpoint
 An diesem Punkt in der exemplarischen Vorgehensweise haben alle der Code für den benutzerdefinierten Bereitstellungsschritt und die SharePoint-Befehle sind jetzt in den Projekten. Erstellen Sie diese, um sicherzustellen, dass sie fehlerfrei kompiliert werden.

#### <a name="to-build-the-projects"></a>Um die Projekte zu erstellen.

1. In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **DeploymentStepExtension** Projekt, und wählen Sie dann **erstellen**.

2. Öffnen Sie das Kontextmenü für die **SharePointCommands** Projekt, und wählen Sie dann **erstellen**.

## <a name="create-a-vsix-package-to-deploy-the-extension"></a>Erstellen Sie ein VSIX-Paket zum Bereitstellen der Erweiterung
 Zum Bereitstellen der Erweiterung erstellen Sie anhand des VSIX-Projekts in der Lösung ein VSIX-Paket. Konfigurieren Sie zuerst das VSIX-Paket durch Ändern der Datei source.extension.vsixmanifest im VSIX-Projekt ein. Klicken Sie dann erstellen Sie das VSIX-Paket, indem Sie beim Erstellen der Projektmappe.

#### <a name="to-configure-and-create-the-vsix-package"></a>So erstellen und konfigurieren Sie das VSIX-Paket

1. In **Projektmappen-Explorer**unter der **UpgradeDeploymentStep** Projekt, öffnen Sie das Kontextmenü für die **"Source.Extension.vsixmanifest"** Datei, und wählen Sie dann auf  **Open**.

     Die Datei wird von Visual Studio im Manifest-Editor geöffnet. Die Datei "source.extension.vsixmanifest" bildet die Grundlage für die Datei "extension.vsixmanifest", die für alle VSIX-Pakete erforderlich ist. Weitere Informationen zu dieser Datei finden Sie unter [Referenz zum VSIX-Erweiterungsschema 1.0](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).

2. In der **Produktname** geben **Bereitstellungsschritt für SharePoint-Projekte aktualisieren**.

3. In der **Autor** geben **Contoso**.

4. In der **Beschreibung** geben **stellt einen benutzerdefinierte Upgrade Bereitstellungsschritt, der in der SharePoint-Projekte verwendet werden kann**.

5. In der **Assets** Registerkarte des Editors wählen Sie die **neu** Schaltfläche.

     Die **neue Anlage hinzufügen** Dialogfeld wird angezeigt.

6. In der **Typ** wählen **Microsoft.VisualStudio.MefComponent**.

    > [!NOTE]
    > Dieser Wert entspricht dem `MefComponent`-Element in der Datei "extension.vsixmanifest". Von diesem Element wird der Name einer Erweiterungsassembly im VSIX-Paket angegeben. Weitere Informationen finden Sie unter [MEFComponent-Element (VSX-Schema)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

7. In der **Quelle** wählen **ein Projekt in der aktuellen Projektmappe**.

8. In der **Projekt** wählen **DeploymentStepExtension**, und wählen Sie dann die **OK** Schaltfläche.

9. Wählen Sie im manifest-Editor die **neu** erneut.

     Die **neue Anlage hinzufügen** Dialogfeld wird angezeigt.

10. In der **Typ** aus, geben Sie **SharePoint.Commands.v4**.

    > [!NOTE]
    > Dieses Element gibt eine benutzerdefinierte Erweiterung, die in der Visual Studio-Erweiterung enthalten sein sollen. Weitere Informationen finden Sie unter [Asset-Element (VSX-Schema)](https://msdn.microsoft.com/9fcfc098-edc7-484b-9d4c-acd17829d737).

11. In der **Quelle** wählen **ein Projekt in der aktuellen Projektmappe**.

12. In der **Projekt** wählen **SharePointCommands**, und wählen Sie dann die **OK** Schaltfläche.

13. Wählen Sie auf der Menüleiste **erstellen** > **Projektmappe**, und klicken Sie dann stellen Sie sicher, dass die Projektmappe ohne Fehler kompiliert wird.

14. Stellen Sie sicher, dass der Buildausgabeordner für das Projekt UpgradeDeploymentStep jetzt die Datei UpgradeDeploymentStep.VSIX enthält.

     Standardmäßig handelt es sich beim Buildausgabeordner um den Ordner "...\bin\Debug" in dem Ordner mit der Projektdatei.

## <a name="prepare-to-test-the-upgrade-deployment-step"></a>Zum Testen des Upgradebereitstellungsschritt vorbereiten
 Um den Schritt der Bereitstellung eines Upgrades zu testen, müssen Sie zuerst eine beispiellösung zur SharePoint-Website bereitstellen. Starten Sie, indem Sie die Erweiterung in der experimentellen Instanz von Visual Studio debuggen. Erstellen Sie dann eine Listendefinition und Listeninstanz zu verwenden, um den Bereitstellungsschritt zu testen, und klicken Sie dann auf die SharePoint-Website bereitstellen. Als Nächstes ändern Sie die Listendefinition und Listeninstanz und erneut bereitstellen Sie, um zu veranschaulichen, wie der Standard-Bereitstellungsprozess-Lösungen in der SharePoint-Website wird überschrieben.

 Klicken Sie weiter unten in dieser exemplarischen Vorgehensweise ändern Sie die Listendefinition und Listeninstanz, und klicken Sie dann führen Sie ein upgrade sie auf der SharePoint-Website.

#### <a name="to-start-debugging-the-extension"></a>So debuggen Sie die Erweiterung

1. Starten Sie Visual Studio mit Administratorrechten, und öffnen Sie die Projektmappe UpgradeDeploymentStep.

2. Öffnen Sie die Codedatei UpgradeStep DeploymentStepExtension im Projekt und dann fügen Sie einen Haltepunkt auf der ersten Zeile des Codes in der `CanExecute` und `Execute` Methoden.

3. Starten Sie das Debuggen durch Auswählen der **F5** -Taste oder wählen Sie auf der Menüleiste die Optionen **Debuggen** > **Debuggen starten**.

4. Visual Studio wird die Erweiterung installiert wird, um %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Upgrade Bereitstellungsschritt für SharePoint Projects\1.0 und eine experimentelle Instanz von Visual Studio. Testen Sie den Schritt der Bereitstellung eines Upgrades in dieser Instanz von Visual Studio.

#### <a name="to-create-a-sharepoint-project-with-a-list-definition-and-a-list-instance"></a>Zum Erstellen eines SharePoint-Projekts mit einer Listendefinition und einer Listeninstanz

1. Wählen Sie in der experimentellen Instanz von Visual Studio auf der Menüleiste **Datei** > **neu** > **Projekt**.

2. In der **neues Projekt** Dialogfeld erweitern Sie die **Visual C#-** Knoten oder die **Visual Basic** Knoten erweitern Sie die **SharePoint** Knoten, und wählen Sie dann die **2010** Knoten.

3. Stellen Sie am oberen Rand des Dialogfelds, sicher, dass **.NET Framework 3.5** wird in der Liste der Versionen von .NET Framework.

    Projekte für [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] und [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] erfordern diese Version von .NET Framework.

4. Wählen Sie in der Liste der Projektvorlagen das Projekt **SharePoint 2010-Projekt**, nennen Sie das Projekt **EmployeesListDefinition**, und wählen Sie dann die **OK** Schaltfläche.

5. In der **SharePoint Customization Wizard**, geben Sie die URL der Website, die zum Debuggen verwendet werden sollen.

6. Klicken Sie unter **was der Vertrauensebene für diese SharePoint-Lösung ist**, wählen Sie die **als farmlösung bereitstellen** Optionsfeld aus.

   > [!NOTE]
   > Der Schritt der Bereitstellung eines Upgrades unterstützt nicht Sandbox-Lösungen.

7. Wählen Sie die **Fertig stellen** Schaltfläche.

    [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] erstellt das Projekt EmployeesListDefinition.

8. Öffnen Sie das Kontextmenü für das EmployeesListDefinition-Projekt, wählen **hinzufügen**, und wählen Sie dann **neues Element**.

9. In der **neues Element hinzufügen - EmployeesListDefinition** Dialogfeld erweitern Sie die **SharePoint** Knoten, und wählen Sie dann die **2010** Knoten.

10. Wählen Sie die **Liste** Elementvorlagen, nennen Sie das Element **Liste Employees**, und wählen Sie dann die **hinzufügen** Schaltfläche.

     SharePoint Customization Wizard angezeigt wird.

11. Auf der **Listeneinstellungen auswählen** Seite überprüfen Sie die folgenden Einstellungen, und wählen Sie dann die **Fertig stellen** Schaltfläche:

    1. **Mitarbeiterliste** wird in der **welchen Namen möchten Sie für der Liste angezeigt werden soll?** Feld.

    2. Die **erstellen Sie eine anpassbare Liste basierend auf:** Optionsfeld ausgewählt wird.

    3. **Standardwert (leer)** wird ausgewählt, der **erstellen Sie eine anpassbare Liste basierend auf:** Liste.

       [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] das Element der Liste der Mitarbeiter mit einem Titel und der Spalte eine einzelne, leere Instanz erstellt, und die Liste-Designer geöffnet.

12. In der Liste-Designer auf die **Spalten** Registerkarte die **Geben Sie einen neuen oder vorhandenen Spaltennamen** Zeile aus, und fügen Sie die folgenden Spalten in der **Anzeigename der Spalte** Liste:

    1. Vorname

    2. Firma

    3. Telefon (geschäftlich)

    4. E-Mail

13. Speichern Sie alle Dateien zu und schließen Sie dann dem Listen-Designer.

14. In **Projektmappen-Explorer**, erweitern Sie die **Liste Employees** Knoten, und erweitern Sie dann die **Mitarbeiter Listeninstanz** untergeordneten Knoten.

15. In der *"Elements.xml"* Datei, ersetzen Sie die standardmäßige XML-Code in dieser Datei durch folgendes XML. Dieser XML-Code ändert den Namen der Liste der **Mitarbeiter** und Informationen für einen Mitarbeiter, die Bezeichnung Jim Hance hinzugefügt.

    ```xml
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

16. Speichern und schließen Sie die *"Elements.xml"* Datei.

17. Öffnen Sie das Kontextmenü für das Projekt EmployeesListDefinition, und wählen Sie dann **öffnen** oder **Eigenschaften**.

     Die Eigenschaften-Designer wird geöffnet.

18. Auf der **SharePoint** Registerkarte die **nach Debuggen automatisch zurückziehen** Kontrollkästchen, und speichern Sie die Eigenschaften.

#### <a name="to-deploy-the-list-definition-and-list-instance"></a>Die Listendefinition und Listeninstanz bereitstellen

1. In **Projektmappen-Explorer**, wählen Sie die **EmployeesListDefinition** Projektknoten.

2. In der **Eigenschaften** Fenster, stellen Sie sicher, dass die **aktive Bereitstellungskonfiguration** -Eigenschaftensatz auf **Standard**.

3. Wählen Sie die **F5** Taste, oder wählen Sie auf der Menüleiste **Debuggen** > **Debuggen starten**.

4. Stellen Sie sicher, dass das Projekt erfolgreich erstellt, um die SharePoint-Website im Webbrowser wird geöffnet, die die **listet** Element in der Schnellstartleiste enthält die neue **Mitarbeiter** Liste, und dass die  **Mitarbeiter** Liste den Eintrag Jim Hance enthält.

5. Schließen Sie den Webbrowser.

#### <a name="to-modify-the-list-definition-and-list-instance-and-redeploy-them"></a>Die Listendefinition und Listeninstanz ändern und erneut bereitstellen

1. Öffnen Sie im Projekt EmployeesListDefinition der *"Elements.xml"* -Datei, die ein untergeordnetes Element des der **Mitarbeiter Listeninstanz** Projektelement.

2. Entfernen Sie die `Data` Element und seine untergeordneten Elemente, um den Eintrag für Jim Hance aus der Liste zu entfernen.

     Wenn Sie fertig sind, sollte die Datei den folgenden XML-Code enthalten.

    ```xml
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

3. Speichern und schließen Sie die *"Elements.xml"* Datei.

4. Öffnen Sie das Kontextmenü für die **Liste Employees** Projektelement, und wählen Sie dann **öffnen** oder **Eigenschaften**.

5. Wählen Sie im Designer Liste der **Ansichten** Registerkarte.

6. In der **ausgewählte Spalten** wählen **Anlagen**, und wählen Sie dann die < Taste, um diese Spalte wechseln die **verfügbaren Spalten** Liste.

7. Wiederholen Sie den vorherigen Schritt zum Verschieben der **Telefon (geschäftlich)** Spalte aus der **ausgewählte Spalten** Liste der **verfügbaren Spalten** Liste.

     Diese Aktion werden diese Felder in der Standardansicht der **Mitarbeiter** Liste auf der SharePoint-Website.

8. Starten Sie das Debuggen durch Auswählen der **F5** -Taste oder wählen Sie auf der Menüleiste die Optionen **Debuggen** > **Debuggen starten**.

9. Überprüfen Sie, ob die **Bereitstellungskonflikte** Dialogfeld wird angezeigt.

     Dieses Dialogfeld wird angezeigt, wenn Visual Studio versucht, die Bereitstellung einer Lösung (die Listeninstanz) auf einer SharePoint-Website, die Lösung bereits bereitgestellt wurde. Dieses Dialogfeld wird nicht angezeigt, wenn Sie den Upgrade Bereitstellungsschritt, der später in dieser exemplarischen Vorgehensweise ausführen.

10. In der **Bereitstellungskonflikte** Dialogfeld auf die **automatisch lösen** Optionsfeld aus.

     Visual Studio löscht die Listeninstanz auf der SharePoint-Website, stellt das Listenelement im Projekt und öffnet dann die SharePoint-Website.

11. In der **listet** Abschnitt wählen Sie die Schnellstartleiste der **Mitarbeiter** aus, und klicken Sie dann überprüfen Sie die folgenden Details:

    - Die **Anlagen** und **Telefon (privat)** Spalten nicht in dieser Ansicht der Liste angezeigt werden.

    - Die Liste ist leer. Sie bei Verwendung der **Standard** Konfiguration der Bereitstellung die Lösung erneut bereitstellen der **Mitarbeiter** Liste wurde durch die neue leere Liste in Ihrem Projekt ersetzt.

## <a name="test-the-deployment-step"></a>Testen Sie den Bereitstellungsschritt
 Sie können nun zum Testen des Upgradebereitstellungsschritt bereit. Fügen Sie zunächst ein Element, um die Listeninstanz in SharePoint. Ändern Sie dann die Listendefinition und Listeninstanz, aktualisieren sie auf der SharePoint-Website und bestätigen Sie, dass der Schritt der Bereitstellung eines Upgrades auf das neue Element überschreiben nicht.

#### <a name="to-manually-add-an-item-to-the-list"></a>Ein Element manuell zur Liste hinzufügen

1. Im Menüband auf der SharePoint-Website unter der **Listentools** Registerkarte die **Elemente** Registerkarte.

2. In der **neu** Gruppe **neues Element**.

     Als Alternative können Sie die **neues Element hinzufügen** -Link in der Elementliste selbst.

3. In der **Mitarbeiter - neues Element** Fenster in der **Titel** geben **Einrichtungs-Manager**.

4. In der **Vorname** geben **Andy**.

5. In der **Unternehmen** geben **Contoso**.

6. Wählen Sie die **speichern** Schaltfläche, stellen Sie sicher, dass das neue Element in der Liste angezeigt wird, und schließen Sie dann den Webbrowser.

     Weiter unten in dieser exemplarischen Vorgehensweise verwenden Sie dieses Element aus, um sicherzustellen, dass der Schritt der Bereitstellung eines Upgrades auf den Inhalt dieser Liste überschreiben nicht.

#### <a name="to-test-the-upgrade-deployment-step"></a>So testen Sie den Schritt der Bereitstellung eines Upgrades

1. In der experimentellen Instanz von Visual Studio in **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die **EmployeesListDefinition** Projektknoten, und wählen Sie dann **Eigenschaften**.

    Die Eigenschaften-Editor/Designer wird geöffnet.

2. Auf der **SharePoint** Registerkarte die **aktive Bereitstellungskonfiguration** Eigenschaft **Upgrade**.

    Diese benutzerdefinierte Konfiguration enthält den neue Schritt der Bereitstellung des Upgrades.

3. Öffnen Sie das Kontextmenü für die **Liste Employees** Projektelement, und wählen Sie dann **Eigenschaften** oder **öffnen**.

    Die Eigenschaften-Editor/Designer wird geöffnet.

4. Auf der **Ansichten** Registerkarte die **-e-Mail** Spalte, und wählen Sie dann die **<** Taste, um diese Spalte aus der **ausgewählte Spalten**Liste der **verfügbaren Spalten** Liste.

    Diese Aktion werden diese Felder in der Standardansicht der **Mitarbeiter** Liste auf der SharePoint-Website.

5. Starten Sie das Debuggen durch Auswählen der **F5** -Taste oder wählen Sie auf der Menüleiste die Optionen **Debuggen** > **Debuggen starten**.

6. Überprüfen Sie, ob die Codeausführung in der anderen Instanz von Visual Studio an dem Haltepunkt unterbrochen wird, den Sie zuvor in der `CanExecute`-Methode festgelegt haben.

7. Wählen Sie die **F5** Taste erneut oder wählen Sie auf der Menüleiste die Option **Debuggen** > **Weiter**.

8. Stellen Sie sicher, dass der Code für den Haltepunkt unterbrochen wird, die Sie zuvor im Festlegen der `Execute` Methode.

9. Wählen Sie die **F5** Taste, oder wählen Sie auf der Menüleiste **Debuggen** > **Weiter** ein letztes Mal.

     Der Webbrowser wird die SharePoint-Website geöffnet.

10. In der **listet** Abschnitt wählen Sie im Schnellstartbereich die **Mitarbeiter** aus, und klicken Sie dann überprüfen Sie die folgenden Details:

    - Das Element, das Sie manuell hinzugefügt haben, zuvor (für Andy einrichtungs-Manager) ist weiterhin in der Liste.

    - Die **Telefon (geschäftlich)** und **e-Mail-Adresse** Spalten nicht in dieser Ansicht der Liste angezeigt werden.

      Die **Upgrade** Bereitstellungskonfiguration wird geändert, die vorhandene **Mitarbeiter** Listeninstanz auf dem SharePoint-Website. Bei Verwendung der **Standard** Bereitstellungskonfiguration statt der **aktualisieren** Konfiguration Umgebungskonflikts auftreten würde. Visual Studio würde den Konflikt lösen, indem Sie ersetzen die **Mitarbeiter** Liste aus, und das Element, für den einrichtungs-Manager, Andy gelöscht werden.

## <a name="clean-up-the-development-computer"></a>Bereinigung auf dem Entwicklungscomputer
 Klicken Sie nach dem Testen des Upgradebereitstellungsschritt entfernen Sie die Listeninstanz und die Listendefinition aus SharePoint-Website, und entfernen Sie die Bereitstellung-Schritt-Erweiterung von Visual Studio.

#### <a name="to-remove-the-list-instance-from-the-sharepoint-site"></a>So entfernen Sie die Listeninstanz aus der SharePoint-Website

1. Öffnen Sie die **Mitarbeiter** Liste auf der SharePoint-Website, wenn die Liste nicht bereits geöffnet ist.

2. Wählen Sie im Menüband auf der SharePoint-Website, die **Listentools** Registerkarte, und wählen Sie dann die **Liste** Registerkarte.

3. In der **Einstellungen** Gruppe der **Listeneinstellungen** Element.

4. Klicken Sie unter **Berechtigungen und Verwaltung**, wählen Sie die **diese Liste löschen** Befehl, wählen Sie **OK** zu bestätigen, dass Sie verwenden möchten, senden Sie die Liste in den Papierkorb verschoben, und schließen Sie das Web Browser.

#### <a name="to-remove-the-list-definition-from-the-sharepoint-site"></a>So entfernen Sie die Listendefinition aus der SharePoint-Website

1. Wählen Sie in der experimentellen Instanz von Visual Studio auf der Menüleiste **erstellen** > **zurückziehen**.

     Visual Studio wird zurückgezogen, die Listendefinition aus SharePoint-Website.

#### <a name="to-uninstall-the-extension"></a>So deinstallieren Sie die Erweiterung

1. Wählen Sie in der experimentellen Instanz von Visual Studio auf der Menüleiste **Tools** > **Erweiterungen und Updates**.

     Das Dialogfeld **Erweiterungen und Updates** wird geöffnet.

2. Wählen Sie in der Liste der Erweiterungen, **Bereitstellungsschritt für SharePoint-Projekte aktualisieren**, und wählen Sie dann die **Deinstallieren** Befehl.

3. Wählen Sie im angezeigten Dialogfeld **Ja** zu bestätigen, dass Sie verwenden möchten, deinstallieren Sie die Erweiterung aus, und wählen Sie dann **jetzt neu starten** um die Deinstallation abzuschließen.

4. Schließen Sie beide Instanzen von Visual Studio (die experimentelle Instanz und die Instanz von Visual Studio, in dem die UpgradeDeploymentStep-Projektmappe geöffnet ist).

## <a name="see-also"></a>Siehe auch
- [Erweitern von SharePoint-Packen und-bereitstellen](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
