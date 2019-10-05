---
ms.openlocfilehash: 69f4f4c2b55670d510652b44a203b9f0eafcc53a
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68143537"
---

1. Schließen Sie die IIS-Verwaltungskonsole, und öffnen Sie sie anschließend erneut. Dann werden die aktualisierten Konfigurationsoptionen auf der Benutzeroberfläche angezeigt.

2. Klicken Sie in IIS erst mit der rechten Maustaste auf **Standardwebsite** und anschließend mit der linken auf **Bereitstellen** > **Configure Web Deploy Publishing** (Web Deploy-Veröffentlichung konfigurieren).

    ![Web Deploy-Veröffentlichung konfigurieren](../../deployment/media/tutorial-configure-web-deploy-publishing.png)

3. Überprüfen Sie die Einstellungen im Dialogfeld **Configure Web Deploy Publishing** (Web Deploy-Veröffentlichung konfigurieren).

4. Klicken Sie auf **Einrichten**.

    Im Bereich **Ergebnisse** sehen Sie, dass dem angegebenen Benutzer Zugriffsrechte gewährt wurden und eine Datei mit der Erweiterung *.publishsettings* erstellt und an dem im Dialogfeld angegebenen Ort gespeichert wurde.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <publishData>
      <publishProfile
        publishUrl="https://myhostname:8172/msdeploy.axd"
        msdeploySite="Default Web Site"
        destinationAppUrl="http://myhostname:80/"
        mySQLDBConnectionString=""
        SQLServerDBConnectionString=""
        profileName="Default Settings"
        publishMethod="MSDeploy"
        userName="myhostname\myusername" />
    </publishData>
    ```

    Je nach Windows Server- und IIS-Konfiguration werden in der XML-Datei unterschiedliche Werte angezeigt. Nachfolgend erhalten Sie Informationen zu den angezeigten Werten:

   * Bei der *msdeploy.axd*-Datei, auf die im `publishUrl`-Attribut verwiesen wird, handelt es sich um eine HTTP-Handlerdatei für Web Deploy. (Zu Testzwecken können Sie auch `http://myhostname:8172` verwenden.)
   * Der `publishUrl`-Port ist auf Port 8172 festgelegt. Dabei handelt es sich um die Standardeinstellung für Web Deploy.
   * Der `destinationAppUrl`-Port ist auf Port 80 festgelegt. Dabei handelt es sich um die Standardeinstellung für IIS.
   * Wenn Sie über den Hostnamen (später beschrieben) keine Verbindung mit dem Remotehost in Visual Studio herstellen können, nehmen Sie stattdessen die IP-Adresse.

     > [!NOTE]
     > Wenn Sie in IIS veröffentlichen, die auf einer Azure-VM ausgeführt werden, müssen Sie Web Deploy und die IIS-Ports in der Netzwerksicherheitsgruppe öffnen. Ausführlichere Informationen dazu finden Sie unter [Installieren und Ausführen von IIS](/azure/virtual-machines/windows/quick-create-portal#install-web-server).

5. Kopieren Sie diese Datei auf den Computer, auf dem Visual Studio ausgeführt wird.
