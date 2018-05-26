
1. Klicken Sie auf dem Computer, die dort stehen Ihnen die ASP.NET-Projekt in Visual Studio öffnen, mit der rechten Maustaste des Projekts im Projektmappen-Explorer, und wählen Sie **veröffentlichen**.

1. Wenn Sie Veröffentlichungsprofile zuvor konfiguriert haben die **veröffentlichen** Bereich wird angezeigt. Klicken Sie auf **neues Profil erstellen**.

1. In der **Veröffentlichungsziel auswählen** (Dialogfeld), klicken Sie auf **Profil importieren**.

    ![Wählen Sie veröffentlichen](../../deployment/media/tutorial-publish-tool-import-profile.png)

1. Navigieren Sie zum Speicherort der Datei mit den veröffentlichungseinstellungen, den Sie im vorherigen Abschnitt erstellt haben.

1. In der **veröffentlichen-Einstellungsdatei importieren** (Dialogfeld), navigieren Sie zu und wählen Sie das Profil, das Sie im vorherigen Abschnitt erstellt haben, und klicken Sie auf **öffnen**.

    Visual Studio startet den Bereitstellungsprozess, und das Ausgabefenster zeigt Status und die Ergebnisse.

    Wenn Sie einer Bereitstellung Fehler angezeigt werden, klicken Sie auf **Einstellungen** Einstellungen bearbeiten. Ändern Sie die Einstellungen, und klicken Sie auf **Validate** So testen Sie die neue Einstellungen. Wenn der Hostname nicht gefunden wird, wiederholen Sie die IP-Adresse anstelle des Hostnamens in der **Server** und **Ziel-URL** Felder.

    ![Bearbeiten von Einstellungen in den Tools zum Veröffentlichen](../../deployment/media/tutorial-configure-publish-settings-in-tool.png)
