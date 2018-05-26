
1. Schließen Sie und öffnen Sie die IIS-Verwaltungskonsole, um aktualisierte Konfigurationsoptionen auf der Benutzeroberfläche anzuzeigen.

1. In IIS, mit der Maustaste die **Default Web Site**, wählen Sie **bereitstellen** > **konfigurieren bereitstellen Webveröffentlichung**.

    ![Konfigurieren von Web Deploy-Konfiguration](../../deployment/media/tutorial-configure-web-deploy-publishing.png)

1. In der **konfigurieren bereitstellen Webveröffentlichung** Dialogfeld sehen Sie die Einstellungen.

1. Klicken Sie auf **Setup**.

    In der **Ergebnisse** Bereich die Ausgabe zeigt an, die Zugriffsrechte erteilt werden der angegebene Benutzer ist, und dass eine Datei mit einem *publishsettings* -Erweiterung generiert wurde, an dem Speicherort, der im Dialogfeld angezeigt Box.

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

    Abhängig von Ihrer Windows Server und IIS-Konfiguration finden Sie unter verschiedenen Werten in der XML-Datei. Nachfolgend sind einige Details zu den Werten, die Sie sehen:

    * Die *msdeploy.axd* Datei verwiesen wird, dem `publishUrl` -Attribut ist eine dynamisch generierte HTTP-Handler-Datei für Web Deploy. (Für Testzwecke wird `http://myhostname:8172` im Allgemeinen funktioniert ebenfalls.)
    * Die `publishUrl` Port 8172, dies die Standardgröße für Web Deploy ist festgelegt ist.
    * Die `destinationAppUrl` Port 80, dies die Standardgröße für IIS ist festgelegt ist.
    * Wenn Sie keine Verbindung mit dem Remotehost in Visual Studio unter Verwendung des Hostnamens (in späteren Schritten) möglich sind, testen Sie die IP-Adresse anstelle der Hostname.

    > [!NOTE]
    > Wenn Sie auf einer Azure-VM unter IIS veröffentlichen, müssen Sie den Web Deploy- und IIS-Ports in der Netzwerk-Sicherheitsgruppe öffnen. Ausführliche Informationen finden Sie unter [installieren und Ausführen von IIS](/azure/virtual-machines/windows/quick-create-portal#open-port-80-for-web-traffic).

1. Kopieren Sie diese Datei auf dem Computer, auf dem Sie Visual Studio ausgeführt werden.
