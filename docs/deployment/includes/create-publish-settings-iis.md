
1. Schließen Sie und öffnen Sie die IIS-Verwaltungskonsole, um die aktualisierte Konfiguration-Optionen in der Benutzeroberfläche anzuzeigen.

2. In IIS, mit der Maustaste der **Default Web Site**, wählen Sie **bereitstellen** > **konfigurieren bereitstellen Webveröffentlichung**.

    ![Konfigurieren von Web Deploy-Konfiguration](../../deployment/media/tutorial-configure-web-deploy-publishing.png)

3. In der **konfigurieren bereitstellen Webveröffentlichung** Dialogfeld sehen Sie die Einstellungen.

4. Klicken Sie auf **Setup**.

    In der **Ergebnisse** Bereich erhalten die Ausgabe zeigt an, die Zugriffsrechte in den angegebenen Benutzer und diese eine Datei mit einem *.publishsettings* Dateierweiterung generiert wurde, an dem Speicherort, der im Dialogfeld angezeigt Box.

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

    Abhängig von Ihrer Windows Server und IIS-Konfiguration sehen Sie andere Werte in der XML-Datei. Hier sind einige Details zu den Werten, die Sie sehen:

   * Die *msdeploy.axd* Dateiverweis auf die `publishUrl` -Attribut ist eine dynamisch generierte HTTP-Handler-Datei für Web Deploy. (Zu Testzwecken `http://myhostname:8172` in der Regel kann auch verwendet werden.)
   * Die `publishUrl` Port 8172, dies die Standardgröße für Web Deploy ist festgelegt ist.
   * Die `destinationAppUrl` Port 80, die Standardeinstellung für IIS festgelegt ist.
   * Wenn Sie keine Verbindung mit dem Remotehost in Visual Studio mit den Namen des Hosts (in späteren Schritten) sind, testen Sie die IP-Adresse anstelle des Namens des Hosts.

     > [!NOTE]
     > Wenn Sie auf einer Azure-VM unter IIS veröffentlichen, müssen Sie den Web Deploy- und IIS-Ports in der Netzwerk-Sicherheitsgruppe öffnen. Ausführliche Informationen finden Sie unter [installieren und Ausführen von IIS](/azure/virtual-machines/windows/quick-create-portal#open-port-80-for-web-traffic).

5. Kopieren Sie diese Datei auf dem Computer, in denen Sie Visual Studio ausgeführt werden.
