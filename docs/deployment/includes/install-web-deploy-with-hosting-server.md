Web Deploy 3.6 für Hosting-Server bietet zusätzliche Konfigurationsschritte-Funktionen, die die Erstellung der Datei mit den veröffentlichungseinstellungen aus der Benutzeroberfläche zu ermöglichen.

1. Wenn Sie Web bereitstellen 3.6 bereits unter Windows Server installiert haben, deinstallieren Sie ihn mit **Systemsteuerung** > **Programme** > **Deinstallationsprogramm**.

1. Installieren Sie dann Web bereitstellen 3.6 für Hosting-Server unter Windows Server.

    Verwenden Sie zum Installieren von Web Deploy für Server hostet die [Webplattform-Installer (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). (Wählen Sie den Webplattform-Installer Link von IIS finden **IIS** im linken Bereich des Server-Managers. Mit der rechten Maustaste in des Servers, und wählen Sie **(Internet Information Services, IIS) Manager**.)

    In den Webplattform-Installer, finden Sie **Web Deploy für Hosting Servern** in der Registerkarte "Anwendungen".

1. Wenn Sie nicht bereits installiert haben **IIS-Verwaltungsskripts und-Tools**, installieren Sie es jetzt.

    Wechseln Sie zu **Serverrollen auswählen** > **Webserver (IIS)** > **Verwaltungstools**, und wählen Sie dann die **IIS-Verwaltungsskripts und Tools** Rolle, klicken Sie auf **Weiter**, und installieren Sie die Rolle.

    ![IIS-Verwaltungsskripts und-Tools installieren](../../deployment/media/tutorial-iis-management-scripts-and-tools.png)

    Die Skripts und Tools sind erforderlich, um die Generierung von der Datei mit veröffentlichungseinstellungen zu aktivieren.

1. (Optional) Vergewissern Sie sich, Web Deploy durch Öffnen des ordnungsgemäß ausgeführt wird **Systemsteuerung > System und Sicherheit > Verwaltung > Dienste** und stellen Sie sicher, dass **Webbereitstellungs-Agent-Dienst** ausgeführt wird (die Name des Diensts unterscheidet sich in älteren Versionen).

    Wenn der Agent-Dienst nicht ausgeführt wird, starten Sie ihn aus. Wenn es nicht vorhanden ist, wechseln Sie zu **Systemsteuerung > Programme > Programm deinstallieren**, suchen **Microsoft Web Deploy <version>** . Wählen Sie auf **ändern** die Installation und stellen Sie sicher, dass Sie auswählen, **wird auf der lokalen Festplatte installiert werden** für die Web Deploy-Komponenten. Führen Sie die Installationsschritte ändern.