---
title: Konfigurieren der Rollen für Azure-Clouddienst mit Visual Studio | Microsoft-Dokumentation
description: Informationen Sie zum Einrichten und Konfigurieren von Rollen für Azure Cloud Services mithilfe von Visual Studio.
author: ghogen
manager: douge
assetId: d397ef87-64e5-401a-aad5-7f83f1022e16
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: ce2259debb55c4792c2998f0e67df69dbc8cb7f9
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002089"
---
# <a name="configure-azure-cloud-service-roles-with-visual-studio"></a>Konfigurieren von Azure-Clouddienstrollen mit Visual Studio
Azure Cloud Services kann eine oder mehrere Worker- oder Webrollen aufweisen. Für jede Rolle müssen Sie definieren, wie diese Rolle eingerichtet ist, und auch konfigurieren, wie die Rolle ausgeführt wird. Weitere Informationen zu Rollen in Clouddiensten finden Sie unter dem Video [Einführung in Azure Cloud Services](https://channel9.msdn.com/Series/Windows-Azure-Cloud-Services-Tutorials/Introduction-to-Windows-Azure-Cloud-Services). 

Die Informationen für den Cloud-Dienst wird in den folgenden Dateien gespeichert:

- **"Servicedefinition.csdef"** -die dienstdefinitionsdatei definiert die Laufzeiteinstellungen für Ihre Cloud-Dienst, die u. a. welche Rollen erforderlich sind, Endpunkte und Größe des virtuellen Computers. Keine der in gespeicherten Daten `ServiceDefinition.csdef` kann geändert werden, wenn die Rolle ausgeführt wird.
- **"ServiceConfiguration.cscfg"** : die Dienstkonfigurationsdatei konfiguriert, wie viele Instanzen einer Rolle ausgeführt werden, und die Werte der Einstellungen für eine Rolle definiert. Die Daten im `ServiceConfiguration.cscfg` kann geändert werden, während der Ausführung der Rolle.

Um unterschiedliche Werte für die Einstellungen zu speichern, die steuern, wie eine Rolle ausgeführt wird, können Sie mehrere Dienstkonfigurationen definieren. Sie können eine andere Dienstkonfiguration für jede bereitstellungsumgebung verwenden. Beispielsweise können Sie festlegen, Ihre Speicherkonto-Verbindungszeichenfolge auf den lokalen Azure-Speicheremulator in einer lokalen Dienstkonfiguration verwendet, und erstellen eine andere Dienstkonfiguration zum Azure-Speicher in der Cloud verwendet werden sollen.

Beim Erstellen von Azure-Clouddienst in Visual Studio werden automatisch zwei Dienstkonfigurationen erstellt und Ihr Azure-Projekt hinzugefügt:

- `ServiceConfiguration.Cloud.cscfg`
- `ServiceConfiguration.Local.cscfg`

## <a name="configure-an-azure-cloud-service"></a>Konfigurieren Sie einen Azure-Cloud-Dienst
Sie können Azure-Clouddienst vom Projektmappen-Explorer in Visual Studio konfigurieren, wie in den folgenden Schritten gezeigt:

1. Erstellen Sie oder öffnen Sie ein Azure-Cloud-Service-Projekt in Visual Studio.

1. In **Projektmappen-Explorer**, mit der rechten Maustaste in des Projekts und wählen Sie im Kontextmenü des **Eigenschaften**.
   
    ![Projektkontextmenü des Projektmappen-Explorer](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-project-context-menu.png)

1. Wählen Sie in der Eigenschaftenseite des Projekts die **Entwicklung** Registerkarte. 

    ![Projekt-Eigenschaftenseite – Registerkarte "Entwicklung"](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-development-tab.png)

1. In der **Dienstkonfiguration** Liste, wählen Sie den Namen der Dienstkonfiguration aus, die Sie bearbeiten möchten. (Wenn Sie Änderungen an allen Dienstkonfigurationen für diese Rolle vornehmen möchten, wählen Sie **alle Konfigurationen**.)
   
    > [!IMPORTANT]
    > Wenn Sie eine bestimmte Dienstkonfiguration auswählen, werden einige Eigenschaften deaktiviert, da sie nur für alle Konfigurationen festgelegt werden können. Um diese Eigenschaften zu bearbeiten, Sie müssen auswählen, **alle Konfigurationen**.
    > 
    > 
   
    ![Dienstkonfigurationsliste für einen Azure-Cloud-Dienst](./media/vs-azure-tools-configure-roles-for-cloud-service/cloud-service-service-configuration-property.png)

## <a name="change-the-number-of-role-instances"></a>Die Anzahl der Rolleninstanzen ändern
Um die Leistung des Cloud-Diensts zu verbessern, können Sie die Anzahl der Instanzen einer Rolle ändern, die basierend auf der Anzahl von Benutzern oder der erwarteten Auslastung für eine bestimmte Rolle ausgeführt werden. Ein separater virtueller Computer wird für jede Instanz einer Rolle erstellt, wenn es sich bei der Cloud-Dienst in Azure ausgeführt wird. Dies wirkt sich auf die Abrechnung für die Bereitstellung dieses Clouddiensts aus. Weitere Informationen zur Abrechnung finden Sie unter [erläuterungen zur Rechnung für Microsoft Azure](/azure/billing/billing-understand-your-bill).

1. Erstellen Sie oder öffnen Sie ein Azure-Cloud-Service-Projekt in Visual Studio.

1. In **Projektmappen-Explorer**, erweitern Sie den Projektknoten. Unter den **Rollen** Knoten mit der rechten Maustaste in der Rolle, die Sie verwenden möchten, aktualisieren, und wählen Sie im Kontextmenü der **Eigenschaften**.

    ![Projektmappen-Explorer-Azure-rollenkontextmenü im](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Wählen Sie die **Konfiguration** Registerkarte.

    ![Registerkarte "Konfiguration"](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page.png)

1. In der **Dienstkonfiguration** wählen Sie die Dienstkonfiguration, die Sie aktualisieren möchten.
   
    ![Dienstkonfigurationsliste](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page-select-configuration.png)

1. In der **Instanzanzahl** Text Geben Sie die Anzahl der Instanzen, die Sie für diese Rolle starten möchten. Jede Instanz wird auf einem separaten virtuellen Computer ausgeführt, wenn Sie den Cloud-Dienst in Azure veröffentlichen.

    ![Aktualisieren die Anzahl der Instanzen](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page-instance-count.png)

1. In der Visual Studio-Symbolleiste wählen **speichern**.

## <a name="manage-connection-strings-for-storage-accounts"></a>Verwalten von Verbindungszeichenfolgen für Speicherkonten
Sie können das Hinzufügen, entfernen oder Ändern von Verbindungszeichenfolgen für Ihre Dienstkonfigurationen. Beispielsweise möchten Sie eine lokale Verbindungszeichenfolge für eine lokale Dienstkonfiguration mit dem Wert des `UseDevelopmentStorage=true`. Möglicherweise möchten Sie auch eine clouddienstkonfiguration konfigurieren, die ein Speicherkonto in Azure verwendet.

> [!WARNING]
> Wenn Sie die Azure Storage-Konto-Schlüsselinformationen für eine Verbindungszeichenfolge für Speicherkonto eingeben, wird diese Informationen lokal in der Dienstkonfigurationsdatei gespeichert. Diese Informationen ist jedoch derzeit nicht als verschlüsselter Text gespeichert.
> 
> 

Durch die verschiedene Werte für die einzelnen Dienstkonfigurationen verwenden, müssen Sie nicht verschiedene Verbindungszeichenfolgen im Clouddienst verwenden oder Ihren Code ändern, wenn Sie Ihren Cloud-Dienst in Azure veröffentlichen. Können Sie den gleichen Namen für die Verbindungszeichenfolge in Ihrem Code, und der Wert unterscheidet sich basierend auf der Dienstkonfiguration, die Sie auswählen, wenn Sie einen Clouddienst erstellen oder veröffentlichen.

1. Erstellen Sie oder öffnen Sie ein Azure-Cloud-Service-Projekt in Visual Studio.

1. In **Projektmappen-Explorer**, erweitern Sie den Projektknoten. Unter den **Rollen** Knoten mit der rechten Maustaste in der Rolle, die Sie verwenden möchten, aktualisieren, und wählen Sie im Kontextmenü der **Eigenschaften**.

    ![Projektmappen-Explorer-Azure-rollenkontextmenü im](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Wählen Sie die **Einstellungen** Registerkarte.

    ![Registerkarte "Einstellungen"](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab.png)

1. In der **Dienstkonfiguration** wählen Sie die Dienstkonfiguration, die Sie aktualisieren möchten.

    ![Dienstkonfiguration](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-select-configuration.png)

1. Wählen Sie zum Hinzufügen einer Verbindungszeichenfolge **Einstellung hinzufügen**.

    ![Verbindungszeichenfolge hinzufügen](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting.png)

1. Nachdem die neue Einstellung zur Liste hinzugefügt wurde, aktualisieren Sie die Zeile in der Liste mit den erforderlichen Informationen ein.

    ![Neue Verbindungszeichenfolge](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting-new-setting.png)

    - **Namen** -Geben Sie den Namen, die Sie für die Verbindungszeichenfolge verwenden möchten.
    - **Typ** : wählen **Verbindungszeichenfolge** aus der Dropdown-Liste.
    - **Wert** -Sie können entweder eingeben die Verbindungszeichenfolge direkt in der **Wert** Zelle aus, oder wählen Sie die Auslassungspunkte (...) in der Sie arbeiten die **Verbindungszeichenfolge für Speicherkonto** Dialogfeld.  

1. In der **Verbindungszeichenfolge für Speicherkonto** Dialogfeld eine Option für **Herstellen einer Verbindung mit**. Befolgen Sie dann die Anweisungen für die ausgewählte Option:

    - **Microsoft Azure-Speicheremulator** – Wenn Sie diese Option auswählen, sind die verbleibenden Einstellungen im Dialogfeld deaktiviert, da sie nur für Azure gelten. Klicken Sie auf **OK**.
    - **Ihr Abonnement** : Bei Auswahl dieser Option verwenden Sie die Dropdownliste, um entweder auszuwählen, und melden Sie sich bei einem Microsoft-Konto oder Microsoft-Konto hinzufügen. Wählen Sie ein Azure-Abonnement und Storage-Konto an. Klicken Sie auf **OK**.
    - **Manuell eingegebene Anmeldeinformationen** -Geben Sie den Namen des Speicherkontos und den primären oder sekundären Schlüssel. Wählen Sie eine Option für **Verbindung** (HTTPS wird empfohlen, für die meisten Szenarien.) Klicken Sie auf **OK**.

1. Um eine Verbindungszeichenfolge zu löschen, wählen Sie die Verbindungszeichenfolge, und wählen Sie dann **Einstellung entfernen**.

1. In der Visual Studio-Symbolleiste wählen **speichern**.

## <a name="programmatically-access-a-connection-string"></a>Programmgesteuerten Zugriff auf eine Verbindungszeichenfolge

Die folgenden Schritte zeigen, wie Sie programmgesteuerten Zugriff auf eine Verbindungszeichenfolge mithilfe C#.

1. Fügen Sie die folgenden using-Direktiven ein C# Datei, in denen die Einstellung zu verwenden soll werden:

    ```csharp
    using Microsoft.WindowsAzure;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.ServiceRuntime;
    ```

1. Der folgende Code zeigt ein Beispiel für eine Verbindungszeichenfolge den Zugriff auf. Ersetzen Sie die &lt;ConnectionStringName >-Platzhalter durch den entsprechenden Wert. 

    ```csharp
    // Setup the connection to Azure Storage
    var storageAccount = CloudStorageAccount.Parse(RoleEnvironment.GetConfigurationSettingValue("<ConnectionStringName>"));
    ```

## <a name="add-custom-settings-to-use-in-your-azure-cloud-service"></a>Hinzufügen von benutzerdefinierten Einstellungen für die Verwendung in Ihrem Azure-Cloud-Dienst
Benutzerdefinierte Einstellungen in der Dienstkonfigurationsdatei können Sie einen Namen und Wert für eine Zeichenfolge für eine bestimmte Dienstkonfiguration hinzufügen. Möglicherweise möchten diese Einstellung verwenden, um ein Feature in Ihren Cloud-Dienst zu konfigurieren, indem Sie den Wert der Einstellung lesen und diesen Wert zum Steuern der Logik in Ihrem Code. Sie können diese dienstkonfigurationswerte ohne erneute Erstellung des Dienstpakets oder während der Ausführung Ihres Clouddiensts ändern. Ihr Code kann Benachrichtigungen bzgl. Änderungen einer Einstellung suchen. Finden Sie unter [RoleEnvironment.Changing-Ereignis](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleenvironment.changing.aspx).

Sie können das Hinzufügen, entfernen oder Ändern von benutzerdefinierten Einstellungen für Ihre Dienstkonfigurationen. Möglicherweise möchten Sie verschiedene Werte für diese Zeichenfolgen für verschiedene Dienstkonfigurationen.

Durch die verschiedene Werte für die einzelnen Dienstkonfigurationen verwenden, müssen Sie nicht verschiedene Zeichenfolgen in Ihren Cloud-Dienst verwenden oder Ihren Code ändern, wenn Sie Ihren Cloud-Dienst in Azure veröffentlichen. Können Sie den gleichen Namen für die Zeichenfolge in Ihrem Code, und der Wert unterscheidet sich basierend auf der Dienstkonfiguration, die Sie auswählen, wenn Sie einen Clouddienst erstellen oder veröffentlichen.

1. Erstellen Sie oder öffnen Sie ein Azure-Cloud-Service-Projekt in Visual Studio.

1. In **Projektmappen-Explorer**, erweitern Sie den Projektknoten. Unter den **Rollen** Knoten mit der rechten Maustaste in der Rolle, die Sie verwenden möchten, aktualisieren, und wählen Sie im Kontextmenü der **Eigenschaften**.

    ![Projektmappen-Explorer-Azure-rollenkontextmenü im](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Wählen Sie die **Einstellungen** Registerkarte.

    ![Registerkarte "Einstellungen"](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab.png)

1. In der **Dienstkonfiguration** wählen Sie die Dienstkonfiguration, die Sie aktualisieren möchten.

    ![Dienstkonfigurationsliste](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-select-configuration.png)

1. Wählen Sie zum Hinzufügen einer benutzerdefinierten Einstellung **Einstellung hinzufügen**.

    ![Benutzerdefinierte Einstellung hinzufügen](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting.png)

1. Nachdem die neue Einstellung zur Liste hinzugefügt wurde, aktualisieren Sie die Zeile in der Liste mit den erforderlichen Informationen ein.

    ![Neue benutzerdefinierte Einstellung](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting-new-setting.png)

    - **Namen** -Geben Sie den Namen der Einstellung.
    - **Typ** : wählen **Zeichenfolge** aus der Dropdown-Liste.
    - **Wert** -Geben Sie den Wert der Einstellung. Sie können entweder den Wert direkt eingeben der **Wert** Zelle aus, oder wählen Sie die Auslassungspunkte (...) den Wert eingeben, aus der **Zeichenfolge bearbeiten** Dialogfeld.  

1. Um eine benutzerdefinierte Einstellung zu löschen, wählen Sie die Einstellung aus, und wählen Sie dann **Einstellung entfernen**.

1. In der Visual Studio-Symbolleiste wählen **speichern**.

## <a name="programmatically-access-a-custom-settings-value"></a>Programmgesteuerten Zugriff auf eine benutzerdefinierte Einstellung Wert
 
Die folgenden Schritte zeigen, wie Sie eine benutzerdefinierte Einstellung mit programmgesteuerten Zugriff auf C#.

1. Fügen Sie die folgenden using-Direktiven ein C# Datei, in denen die Einstellung zu verwenden soll werden:

    ```csharp
    using Microsoft.WindowsAzure;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.ServiceRuntime;
    ```

1. Der folgende Code zeigt ein Beispiel für eine benutzerdefinierte Einstellung den Zugriff auf. Ersetzen Sie die &lt;SettingName >-Platzhalter durch den entsprechenden Wert. 
    
    ```csharp
    var settingValue = RoleEnvironment.GetConfigurationSettingValue("<SettingName>");
    ```

## <a name="manage-local-storage-for-each-role-instance"></a>Verwalten Sie lokalen Speicher für jede Rolleninstanz
Sie können lokalen Dateisystemspeicher für jede Instanz einer Rolle hinzufügen. Die Daten, die von anderen Instanzen der Rolle für die die Daten gespeichert sind oder von anderen Rollen, Speicher kann nicht zugegriffen werden gespeichert.  

1. Erstellen Sie oder öffnen Sie ein Azure-Cloud-Service-Projekt in Visual Studio.

1. In **Projektmappen-Explorer**, erweitern Sie den Projektknoten. Unter den **Rollen** Knoten mit der rechten Maustaste in der Rolle, die Sie verwenden möchten, aktualisieren, und wählen Sie im Kontextmenü der **Eigenschaften**.

    ![Projektmappen-Explorer-Azure-rollenkontextmenü im](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Wählen Sie die **lokalen Speicher** Registerkarte.

    ![Registerkarte "Lokaler Speicher"](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab.png)

1. In der **Dienstkonfiguration** sicher, dass **alle Konfigurationen** ausgewählt ist, wie die Einstellungen des lokalen Speichers für alle Dienstkonfigurationen. Jeder andere Wert führt alle Eingabefelder auf der Seite deaktiviert werden. 

    ![Dienstkonfigurationsliste](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-service-configuration.png)

1. Um einen lokalen Speichereintrag hinzuzufügen, wählen Sie **lokalen Speicher hinzufügen**.

    ![Lokalen Speicher hinzufügen](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-add-local-storage.png)

1. Sobald die neue lokale Speichereintrag zur Liste hinzugefügt wurde, aktualisieren Sie die Zeile in der Liste mit den erforderlichen Informationen ein.

    ![Neuer lokaler Speichereintrag](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-new-local-storage.png)

    - **Namen** -Geben Sie den Namen, die Sie für den neuen lokalen Speicher verwenden möchten.
    - **Größe (MB)** -Geben Sie die Größe in MB, die Sie für den neuen lokalen Speicher benötigen.
    - **Bei Wiederverwendung der Rolle Bereinigen** -wählen Sie diese Option, um die Daten in den neuen lokalen Speicher entfernt werden soll, wenn der virtuelle Computer für die Rolle wiederverwendet wird.

1. Um einen lokalen Speichereintrag zu löschen, wählen Sie den Eintrag, und wählen Sie dann **lokalen Speicher entfernen**.

1. In der Visual Studio-Symbolleiste wählen **speichern**.

## <a name="programmatically-accessing-local-storage"></a>Programmgesteuerter Zugriff auf lokalen Speicher

Dieser Abschnitt veranschaulicht die Verwendung des lokalen Speichers programmgesteuerten Zugriff auf C# durch das Schreiben einer testtextdatei `MyLocalStorageTest.txt`.  

### <a name="write-a-text-file-to-local-storage"></a>Schreiben einer Textdatei in den lokalen Speicher

Der folgende Code zeigt ein Beispiel, wie Sie eine Textdatei in den lokalen Speicher zu schreiben. Ersetzen Sie die &lt;Namedeslokalenspeichers >-Platzhalter durch den entsprechenden Wert. 

    ```csharp
    // Retrieve an object that points to the local storage resource
    LocalResource localResource = RoleEnvironment.GetLocalResource("<LocalStorageName>");
    
    //Define the file name and path
    string[] paths = { localResource.RootPath, "MyLocalStorageTest.txt" };
    String filePath = Path.Combine(paths);
    
    using (FileStream writeStream = File.Create(filePath))
    {
        Byte[] textToWrite = new UTF8Encoding(true).GetBytes("Testing Web role storage");
        writeStream.Write(textToWrite, 0, textToWrite.Length);
    }

    ```

### <a name="find-a-file-written-to-local-storage"></a>Suchen nach einer Datei, die in den lokalen Speicher geschrieben

Um die durch den Code im vorherigen Abschnitt erstellte Datei anzuzeigen, gehen Sie folgendermaßen vor:
    
1.  In der Windows-Infobereich mit der rechten Maustaste in des Azure-Symbols, und wählen Sie im Kontextmenü des **Serveremulator-Benutzeroberfläche anzeigen**. 

    ![Azure-Serveremulator anzeigen](./media/vs-azure-tools-configure-roles-for-cloud-service/show-compute-emulator.png)

1. Wählen Sie die Webrolle.

    ![Azure-Serveremulator](./media/vs-azure-tools-configure-roles-for-cloud-service/compute-emulator.png)

1. Auf der **Microsoft Azure-Serveremulator** , wählen Sie im Menü **Tools** > **lokalen Speicher öffnen**.

    ![Menüelement für lokalen Speicher öffnen](./media/vs-azure-tools-configure-roles-for-cloud-service/compute-emulator-open-local-store-menu.png)

1. Wenn Sie das Windows-Explorer-Fenster geöffnet wird, geben Sie "MyLocalStorageTest.txt" in der **Suche** Textfeld, und wählen **Geben Sie** mit der Suche begonnen. 

## <a name="next-steps"></a>Nächste Schritte
Erfahren Sie mehr über Azure-Projekte in Visual Studio [Konfigurieren eines Azure-Projekts](vs-azure-tools-configuring-an-azure-project.md). Erfahren Sie mehr über das Schema des Cloud-Diensts lesen [Schemareferenz](https://msdn.microsoft.com/library/azure/dd179398).

