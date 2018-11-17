---
title: Fortlaufende Integration in Azure DevOps-Dienste mit Azure-ressourcengruppenprojekten | Microsoft-Dokumentation
description: Beschreibt, wie fortlaufende Integration in Azure DevOps-Dienste mit Azure-Ressourcengruppen-Bereitstellungsprojekte in Visual Studio einrichten.
author: mlearned
manager: douge
ms.assetid: b81c172a-be87-4adc-861e-d20b94be9e38
ms.service: azure-resource-manager
ms.topic: article
ms.workload: azure-vs
ms.date: 08/01/2016
ms.author: mlearned
ms.openlocfilehash: b20a43181ad4d36377e61434b880b491543a6c47
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51791604"
---
# <a name="continuous-integration-in-azure-devops-services-using-azure-resource-group-deployment-projects"></a>Fortlaufende Integration in Azure DevOps-Dienste, die mit der Azure-Ressourcengruppen-Bereitstellungsprojekten
Zum Bereitstellen einer Azure-Vorlage führen Sie Aufgaben in verschiedenen Phasen: erstellen, testen, nach Azure kopieren (auch als "Staging" bezeichnet), und die Vorlage bereitstellen. Es gibt zwei Möglichkeiten zum Bereitstellen von Vorlagen für Azure DevOps-Dienste. Beide Methoden bieten die gleichen Ergebnisse, also wählen dasjenige, das am besten in Ihren Workflow passt.

1. Fügen Sie einen einzigen Schritt zu Ihrer erstellungspipeline, der das PowerShell-Skript ausgeführt wird, das im Azure-Ressourcengruppen-Bereitstellungsprojekt (Deploy-azureresourcegroup. ps1) enthalten ist. Das Skript werden Artefakte kopiert, und klicken Sie dann die Vorlage bereitgestellt.
2. Fügen Sie, dass mehrere Azure DevOps-Dienste, jeweils eine stagingaufgabe ausgeführt Buildschritte hinzu.

In diesem Artikel werden beide Optionen veranschaulicht. Die erste Option hat den Vorteil der Verwendung des Skripts, die von Entwicklern in Visual Studio und Bereitstellung Konsistenz im gesamten Lebenszyklus verwendet. Die zweite Option bietet eine praktische Alternative zum integrierten Skript. Beide Verfahren wird davon ausgegangen, dass Sie bereits ein Visual Studio-Bereitstellungsprojekt in Azure DevOps-Services eingecheckt haben.

## <a name="copy-artifacts-to-azure"></a>Kopieren von Artefakten nach Azure
Unabhängig vom Szenario, gilt Wenn Sie über Artefakte verfügen, die für die vorlagenbereitstellung benötigt werden müssen Sie Azure Resource Manager Zugriff darauf gewähren. Diese Artefakte können folgende Dateien umfassen:

* Geschachtelte Vorlagen
* Konfigurationsskripts und DSC-Skripts
* Anwendungsbinärdateien

### <a name="nested-templates-and-configuration-scripts"></a>Geschachtelte Vorlagen und Konfigurationsskripts
Bei Verwendung von Visual Studio bereitgestellten Vorlagen (oder mit Visual Studio-Codeausschnitten erstellte), das PowerShell-Skript nicht nur die Artefakte bereitgestellt, die sie auch den URI für die Ressourcen für unterschiedliche Bereitstellungen parametrisiert. Das Skript dann kopiert die Elemente in einem sicheren Container in Azure, ein SaS-Token für diesen Container erstellt und übergibt dann diese Informationen an die vorlagenbereitstellung. Finden Sie unter [Erstellen einer vorlagenbereitstellung](https://msdn.microsoft.com/library/azure/dn790564.aspx) Weitere Informationen zu geschachtelten Vorlagen.  Bei Verwendung von Aufgaben in Azure DevOps-Dienste müssen die entsprechenden Aufgaben für die vorlagenbereitstellung auswählen und übergeben bei Bedarf Parameterwerte aus dem stagingschritt an die vorlagenbereitstellung.

## <a name="set-up-continuous-deployment-in-azure-pipelines"></a>Einrichten von continuous Deployment in Azure-Pipelines festgelegt
Um das PowerShell-Skript in Azure-Pipelines aufzurufen, müssen Sie Ihrer erstellungspipeline aktualisieren. Kurz gesagt, sind die Schritte aus: 

1. Bearbeiten Sie die Buildpipeline.
2. Richten Sie Azure-Autorisierung in Azure-Pipelines.
3. Fügen Sie einen, der das PowerShell-Skript im Azure-Ressourcengruppen-Bereitstellungsprojekt verweist auf Azure PowerShell-Buildschritt hinzu.
4. Legen Sie den Wert, der die *- ArtifactsStagingDirectory* Parameter, um die Arbeit mit eines Projekts in Azure-Pipelines.

### <a name="detailed-walkthrough-for-option-1"></a>Ausführliche exemplarische Vorgehensweise für Option 1
Die folgenden Verfahren führen Sie durch die erforderlichen Schritte zum Konfigurieren von continuous Deployment in Azure DevOps-Dienste, die mit einer einzelnen Aufgabe, die das PowerShell-Skript in Ihrem Projekt ausgeführt wird. 

1. Bearbeiten Sie Ihrer erstellungspipeline Azure DevOps-Dienste, und fügen Sie ein Azure PowerShell-Buildschritt hinzu. Wählen Sie die erstellungspipeline, unter der **Pipelines erstellen** Kategorie und wählen Sie dann die **bearbeiten** Link.
   
   ![Buildpipeline bearbeiten][0]
2. Fügen Sie einen neuen **Azure PowerShell** Buildschritt an die erstellungspipeline, und wählen Sie dann die **Buildschritt hinzufügen...** Schaltfläche.
   
   ![Buildschritt hinzufügen][1]
3. Wählen Sie die **Bereitstellungstask** Kategorie der **Azure PowerShell** Aufgabe aus, und wählen Sie dann die **hinzufügen** Schaltfläche.
   
   ![Hinzufügen von Aufgaben][2]
4. Wählen Sie die **Azure PowerShell** Buildschritt, und geben Sie dann die Werte.
   
   1. Wenn Sie bereits einen Azure-Dienstendpunkt Azure DevOps-Dienste hinzugefügt haben, wählen Sie das Abonnement in der **Azure-Abonnement** im Dropdown Listenfeld und klicken Sie dann direkt mit dem nächsten Abschnitt. 
      
      Wenn Sie einen Azure-Dienstendpunkt in Azure DevOps-Dienste nicht haben, müssen Sie eine hinzufügen. In diesem Unterabschnitt führt Sie durch den Prozess. Wenn Ihr Azure-Konto ein Microsoft-Konto (z.B. Hotmail) verwendet, müssen Sie die folgenden Schritte aus, um eine Authentifizierung des Dienstprinzipals erhalten ausführen.

   2. Wählen Sie die **verwalten** link die **Azure-Abonnement** im Dropdown Listenfeld.
      
      ![Azure-Abonnements verwalten][3]
   3. Wählen Sie **Azure** in die **neuer Dienstendpunkt** im Dropdown Listenfeld.
      
      ![Neuer Dienstendpunkt][4]
   4. In der **Azure-Abonnement hinzufügen** wählen Sie im Dialogfeld die **Dienstprinzipal** Option.
      
      ![Option "Dienstprinzipal"][5]
   5. Hinzufügen von Ihrem Azure-Abonnement-Informationen zu den **Azure-Abonnement hinzufügen** Dialogfeld. Sie müssen Folgendes angeben:
      
      * Abonnement-Id
      * Abonnementname
      * Dienstprinzipal-Id
      * Dienstprinzipalschlüssel
      * Mandanten-Id
   6. Fügen Sie einen Namen Ihrer Wahl die **Abonnement** Namenfeld. Dieser Wert wird später in der **Azure-Abonnement** Dropdown-Liste in Azure DevOps-Dienste. 

   7. Wenn Sie Ihre Azure-Abonnement-ID nicht kennen, können einen der folgenden Befehle Sie zum Abrufen.
      
      Verwenden Sie für PowerShell-Skripts:
      
      `Get-AzureRmSubscription`
      
      Verwenden Sie für Azure-Befehlszeilenschnittstelle:
      
      `azure account show`
   8. Um einen Dienstprinzipal-ID, Dienstprinzipalschlüssel und Mandanten-ID, führen Sie die Prozedur im [Erstellen einer Active Directory-Anwendung und eines dienstprinzipals mithilfe des Portals](/azure/azure-resource-manager/resource-group-create-service-principal-portal) oder [Authentifizieren eines dienstprinzipals mit Azure Ressourcen-Manager](/azure/azure-resource-manager/resource-group-authenticate-service-principal).
   9. Fügen Sie die Dienstprinzipal-ID, Dienstprinzipalschlüssel und Mandanten-ID-Werte, die **Azure-Abonnement hinzufügen** Dialogfeld ein, und wählen Sie dann die **OK** Schaltfläche.
      
      Sie verfügen jetzt über einen gültigen Dienstprinzipal zu verwenden, um das PowerShell-Skript auszuführen.
5. Bearbeiten Sie die Buildpipeline, und wählen Sie die **Azure PowerShell** Buildschritt. Wählen Sie das Abonnement in der **Azure-Abonnement** im Dropdown Listenfeld. (Wenn das Abonnement nicht angezeigt wird, wählen Sie die **aktualisieren** Schaltfläche neben dem **verwalten** Link.) 
   
   ![Konfigurieren der Azure PowerShell-Buildaufgabe][8]
6. Geben Sie einen Pfad zum Deploy-azureresourcegroup. ps1-PowerShell-Skript. Wählen Sie hierzu die Schaltfläche mit den Auslassungspunkten (...) neben der **Skriptpfad** navigieren Sie zum Deploy-azureresourcegroup. ps1-PowerShell-Skript in die **Skripts** Ordner des Projekts, wählen Sie ihn, und klicken Sie dann Wählen Sie die **OK** Schaltfläche.    
   
   ![Wählen Sie Pfad zum Skript][9]
7. Nachdem Sie das Skript auswählen, aktualisieren Sie den Pfad zum Skript, damit es über "Build.stagingdirectory" ausgeführt wird (dasselbe Verzeichnis, *ArtifactsLocation* auf festgelegt ist). Sie erreichen dies durch das Hinzufügen von "$(Build.StagingDirectory)/"an den Anfang der Skriptpfad.
   
    ![Pfad zum Skript bearbeiten][10]
8. In der **Skriptargumente** Geben Sie die folgenden Parameter (in einer einzigen Zeile). Wenn Sie das Skript im Visual Studio ausführen, können Sie sehen, wie Visual Studio verwendet die Parameter in der **Ausgabe** Fenster. Sie können dies als Ausgangspunkt verwenden, für das Festlegen der Parameterwerte im Buildschritt verwenden.
   
   | Parameter | Beschreibung |
   | --- | --- |
   | -ResourceGroupLocation |Der GeoLocation-Wert, in dem die Ressourcengruppe, z. B. befindet **Eastus** oder **"USA, Osten"**. (Fügen Sie einfache Anführungszeichen, wenn ein Leerzeichen im Namen ist.) Finden Sie unter [Azure-Regionen](https://azure.microsoft.com/regions/) für Weitere Informationen. |
   | -ResourceGroupName |Der Name der Ressourcengruppe für diese Bereitstellung verwendet werden soll. |
   | -UploadArtifacts |Dieser Parameter, wenn vorhanden, gibt an, die Elemente, die aus dem lokalen System in Azure hochgeladen werden müssen. Sie müssen nur diese Option festgelegt werden soll, wenn die vorlagenbereitstellung zusätzliche Artefakte erforderlich sind, die zum Bereitstellen der mithilfe des PowerShell-Skripts (z. B. Konfigurationsskripts oder geschachtelte Vorlagen) werden sollen. |
   | -"Storageaccountname" |Der Name des Speicherkontos, das zum Bereitstellen von Artefakten für diese Bereitstellung verwendet werden soll. Dieser Parameter wird nur verwendet, wenn Sie staging-Artefakte für die Bereitstellung sind. Wenn dieser Parameter angegeben wird, wird ein neues Speicherkonto erstellt, wenn das Skript nicht während einer vorherigen Bereitstellung erstellt wurde. Wenn der Parameter angegeben wird, muss das Speicherkonto bereits vorhanden sein. |
   | -StorageAccountResourceGroupName |Der Name der Ressourcengruppe mit dem Storage-Konto verknüpft ist. Dieser Parameter ist erforderlich, nur dann, wenn Sie einen Wert für den Parameter "storageaccountname" angeben. |
   | -TemplateFile |Der Pfad zur Vorlagendatei im Azure-Ressourcengruppen-Bereitstellungsprojekt. Zur Steigerung der Flexibilität verwenden Sie einen Pfad für diesen Parameter, der relativ zum Speicherort des PowerShell-Skripts anstelle eines absoluten Pfads ist. |
   | -TemplateParametersFile |Der Pfad zur Parameterdatei im Azure-Ressourcengruppen-Bereitstellungsprojekt. Zur Steigerung der Flexibilität verwenden Sie einen Pfad für diesen Parameter, der relativ zum Speicherort des PowerShell-Skripts anstelle eines absoluten Pfads ist. |
   | -ArtifactStagingDirectory |Mit diesem Parameter können die PowerShell-Skript den Ordner mitteilen, von wo die Binärdateien des Projekts kopiert werden sollen. Dieser Wert überschreibt den Standardwert, der vom PowerShell-Skript verwendet. Für Azure DevOps-Dienste verwenden möchten, legen Sie den Wert auf: - ArtifactStagingDirectory $(Build.StagingDirectory) |
   
   Hier ist ein Beispiel für Skript-Argumente (Zeilenumbruch zur besseren Lesbarkeit):
   
   ```    
   -ResourceGroupName 'MyGroup' -ResourceGroupLocation 'eastus' -TemplateFile '..\templates\azuredeploy.json' 
   -TemplateParametersFile '..\templates\azuredeploy.parameters.json' -UploadArtifacts -StorageAccountName 'mystorageacct' 
   –StorageAccountResourceGroupName 'Default-Storage-EastUS' -ArtifactStagingDirectory '$(Build.StagingDirectory)'    
   ```
   
   Wenn Sie fertig sind, die **Skriptargumente** Feld entspricht in etwa die folgende Liste:
   
   ![Skriptargumente][11]
9. Nachdem Sie alle erforderlichen Komponenten auf den Azure PowerShell-Buildschritt hinzugefügt haben, wählen Sie die **Warteschlange** erstellen-Schaltfläche, um das Projekt zu erstellen. Die **erstellen** Bildschirm zeigt die Ausgabe des PowerShell-Skripts.

### <a name="detailed-walkthrough-for-option-2"></a>Ausführliche exemplarische Vorgehensweise für Option 2
Die folgenden Verfahren führen Sie durch die erforderlichen Schritte zum continuous Deployment in Azure DevOps-Dienste, die mit den integrierten Tasks zu konfigurieren.

1. Bearbeiten Sie Ihrer erstellungspipeline Azure DevOps-Dienste, um zwei neue Buildschritte hinzufügen. Wählen Sie die erstellungspipeline, unter der **Builddefinitionen** Kategorie und wählen Sie dann die **bearbeiten** Link.
   
   ![Builddefinition bearbeiten][12]
2. Fügen Sie die neuen bildschritte der Build-Pipeline mithilfe der **Buildschritt hinzufügen...** Schaltfläche.
   
   ![Buildschritt hinzufügen][13]
3. Wählen Sie die **bereitstellen** Aufgabenkategorie der **Azure-Dateikopiervorgang** Aufgabe aus, und wählen Sie dann die **hinzufügen** Schaltfläche.
   
   ![Azure File Copy-Aufgabe hinzufügen][14]
4. Wählen Sie die **Bereitstellung einer Azure-Ressourcengruppe** Aufgabe aus, und wählen Sie dann die **hinzufügen** Schaltfläche und dann **schließen** der **Aufgabenkatalog**.
   
   ![Hinzufügen von Azure-Ressourcengruppen-Bereitstellungsaufgabe][15]
5. Wählen Sie die **Azure-Dateikopiervorgang** Aufgabe aus, und geben Sie die Werte.
   
   Wenn Sie bereits einen Azure-Dienstendpunkt Azure DevOps-Dienste hinzugefügt haben, wählen Sie das Abonnement in der **Azure-Abonnement** im Dropdown Listenfeld. Wenn Sie nicht über ein Abonnement verfügen, finden Sie unter [Option 1](#detailed-walkthrough-for-option-1) Anweisungen zum Einrichten einer Datenbank in Azure DevOps-Dienste.
   
   * Quelle: Geben Sie **$(Build.StagingDirectory)**
   * Azure-Verbindungstyp: Wählen Sie **Azure Resource Manager**
   * Azure RM-Abonnement: Wählen Sie das Abonnement für das Speicherkonto zu verwenden, in der **Azure-Abonnement** im Dropdown Listenfeld. Wenn das Abonnement nicht angezeigt wird, wählen Sie die **aktualisieren** Schaltfläche neben dem **verwalten** Link.
   * Zieltyp: wählen **Azure-Blob**
   * RM-Speicherkonto: Wählen Sie das Speicherkonto, das Sie möchten zum Kopieren von Artefakten verwenden
   * Containername: Geben Sie den Namen des Containers für das Staging; verwenden möchten Es kann ein beliebiger gültiger Containername sein, sondern eine speziell für diese Buildpipeline
   
   Für die Ausgabewerte:
   
   * Speichercontainer-URI: Geben Sie **ArtifactsLocation**
   * Storage-Container-SAS-Token - Geben Sie **ArtifactsLocationSasToken**
   
   ![Konfigurieren von Azure File Copy-Aufgabe][16]
6. Wählen Sie die **Bereitstellung einer Azure-Ressourcengruppe** Buildschritt, und geben Sie dann die Werte.
   
   * Azure-Verbindungstyp: Wählen Sie **Azure Resource Manager**
   * Azure RM-Abonnement: Wählen Sie das Abonnement für die Bereitstellung in der **Azure-Abonnement** im Dropdown Listenfeld. Dies wird in der Regel dasselbe Abonnement wie im vorherigen Schritt sein.
   * Aktion - Option **erstellen oder Ressourcengruppe aktualisieren**
   * Ressourcengruppe: Wählen Sie eine Ressourcengruppe aus, oder geben Sie den Namen einer neuen Ressourcengruppe für die Bereitstellung
   * Speicherort: Wählen Sie den Speicherort für die Ressourcengruppe
   * Vorlage – Geben Sie den Pfad und Namen der bereitzustellenden Vorlage voranstellen **$(Build.StagingDirectory)**, z. B.: **$(Build.StagingDirectory/DSC-CI/azuredeploy.json)**
   * Vorlagenparameter: Geben Sie den Pfad und Namen der Parameter zu verwendende voranstellen **$(Build.StagingDirectory)**, z. B.: **$(Build.StagingDirectory/DSC-CI/azuredeploy.parameters.json)**
   * Vorlagenparameter überschreiben: Geben Sie ein oder kopieren, und fügen Sie den folgenden Code:
     
     ```    
     -_artifactsLocation $(artifactsLocation) -_artifactsLocationSasToken (ConvertTo-SecureString -String "$(artifactsLocationSasToken)" -AsPlainText -Force)
     ```
     ![Konfigurieren von Azure-Ressourcengruppen-Bereitstellungsaufgabe][17]
7. Nachdem Sie alle erforderlichen Elemente hinzugefügt haben, speichern Sie die Buildpipeline, und wählen Sie **neuen Build in Warteschlange** oben.

## <a name="next-steps"></a>Nächste Schritte
Lesen [Übersicht über Azure Resource Manager](/azure-resource-manager/resource-group-overview.md) Weitere Informationen zum Azure Resource Manager und Azure-Ressourcengruppen.

[0]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough1.png
[1]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough2.png
[2]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough3.png
[3]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough4.png
[4]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough5.png
[5]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough6.png
[8]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough9.png
[9]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough10.png
[10]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough11b.png
[11]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough12.png
[12]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough13.png
[13]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough14.png
[14]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough15.png
[15]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough16.png
[16]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough17.png
[17]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough18.png
