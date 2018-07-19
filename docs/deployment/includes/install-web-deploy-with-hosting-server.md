Web Deploy 3.6 für Hostserver bietet zusätzliche Konfiguration, die die Erstellung der Datei mit den veröffentlichungseinstellungen von der Benutzeroberfläche zu ermöglichen.

1. Wenn Sie Web bereitstellen 3.6 unter Windows Server bereits installiert haben, deinstallieren Sie es mit **Systemsteuerung** > **Programme** > **Deinstallationsprogramm**.

1. Als Nächstes installieren Sie Web bereitstellen 3.6 für Hostserver unter Windows Server.

    Verwenden Sie zum Installieren von Web Deploy für den Hostserver der [Webplattform-Installer (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). (Um den Webplattform-Installer-Link aus IIS zu suchen, wählen **IIS** im linken Bereich des Server-Managers. Mit der rechten Maustaste in des Servers, und wählen Sie **(Internet Information Services, IIS) Manager**.)

    In den Webplattform-Installer, finden Sie **Web Deploy für Hostserver** auf der Registerkarte "Anwendungen".

1. Wenn Sie nicht bereits installiert haben **IIS-Verwaltungsskripts und-Tools**, installieren Sie es jetzt.

    Wechseln Sie zu **Serverrollen auswählen** > **Webserver (IIS)** > **Verwaltungstools**, und wählen Sie dann die **IIS-Verwaltungsskripts und Tools** Rolle, klicken Sie auf **Weiter**, und installieren Sie dann auf die Rolle.

    ![Installieren von IIS-Verwaltungsskripts und-Tools](../../deployment/media/tutorial-iis-management-scripts-and-tools.png)

    Die Skripts und Tools sind erforderlich, um das Generieren der Datei mit den veröffentlichungseinstellungen zu ermöglichen.

1. (Optional) Stellen Sie sicher, dass Web Deploy öffnen ordnungsgemäß ausgeführt wird **Systemsteuerung > System und Sicherheit > Verwaltung > Dienste** und stellen Sie sicher, dass **Webbereitstellungs-Agent-Dienst** ausgeführt wird (die Name des Diensts unterscheidet sich in älteren Versionen).

    Wenn der Agent-Dienst nicht ausgeführt wird, starten Sie ihn aus. Wenn es nicht vorhanden ist, fahren Sie mit **Systemsteuerung > Programme > Programm deinstallieren**, finden Sie **Microsoft Web Deploy <version>** . Wählen Sie auf **Änderung** die Installation und stellen Sie sicher, dass Sie auswählen **auf der lokalen Festplatte installiert werden** für die Web Deploy-Komponenten. Führen Sie die Installationsschritte ändern.