
1. Klicken Sie auf dem Computer, auf dem das ASP.NET-Projekt in Visual Studio geöffnet ist, erst mit der rechten Maustaste auf das Projekt im Projektmappen-Explorer und anschließend mit der linken auf **Veröffentlichen**.

1. Wenn Sie bereits Veröffentlichungsprofile konfiguriert haben, wird der Bereich **Veröffentlichen** angezeigt. Klicken Sie auf **Neues Profil erstellen**.

1. Klicken Sie im Dialogfeld **Pick a publish target** (Veröffentlichungsziel auswählen) auf **Profil importieren**.

    ![„Veröffentlichen“ auswählen](../../deployment/media/tutorial-publish-tool-import-profile.png)

1. Navigieren Sie zum Speicherort der Datei mit Veröffentlichungseinstellungen, die Sie bereits erstellt haben.

1. Navigieren Sie im Dialogfeld **Datei mit Veröffentlichungseinstellungen** zu dem Profil, das Sie bereits erstellt haben, wählen Sie es aus, und klicken Sie auf **Öffnen**.

    Dann beginnt Visual Studio mit dem Bereitstellungsprozess, und im Ausgabefenster werden der Fortschritt und die Ergebnisse angezeigt.

    Wenn bei der Bereitstellung Fehler entstehen sollten, klicken Sie auf **Einstellungen**, um die Einstellungen zu bearbeiten. Ändern Sie die Einstellungen, und klicken Sie auf **Überprüfen**, um die neuen Einstellungen zu testen. Wenn der Hostname nicht gefunden wird, geben Sie stattdessen die IP-Adresse in die Felder **Server** und **Ziel-URL** ein.

    ![Bearbeiten von Einstellungen im Tool zum Veröffentlichen](../../deployment/media/tutorial-configure-publish-settings-in-tool.png)
