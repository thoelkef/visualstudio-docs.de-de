
1. Klicken Sie auf dem Computer, in dem Sie das ASP.NET-Projekt in Visual Studio geöffnet haben, mit der rechten Maustaste in des Projekts im Projektmappen-Explorer, und wählen **veröffentlichen**.

1. Wenn Sie Veröffentlichungsprofile, zuvor konfiguriert haben die **veröffentlichen** angezeigt. Klicken Sie auf **neues Profil erstellen**.

1. In der **Veröffentlichungsziel** Dialogfeld klicken Sie auf **Profil importieren**.

    ![Wählen Sie veröffentlichen](../../deployment/media/tutorial-publish-tool-import-profile.png)

1. Navigieren Sie zum Speicherort der Datei mit den veröffentlichungseinstellungen, den Sie im vorherigen Abschnitt erstellt haben.

1. In der **importieren die Datei mit Veröffentlichungseinstellungen** Dialogfeld, navigieren Sie zu wählen Sie das Profil, das Sie im vorherigen Abschnitt erstellt haben, und klicken Sie auf **öffnen**.

    Visual Studio startet den Bereitstellungsprozess und das Fenster "Ausgabe" zeigt Status und die Ergebnisse.

    Wenn Sie eine Bereitstellung Fehler auftreten, klicken Sie auf **Einstellungen** um Einstellungen zu bearbeiten. Ändern Sie die Einstellungen, und klicken Sie auf **überprüfen** zum Testen der neuer Einstellungen. Wenn der Hostname nicht gefunden wird, wiederholen Sie die IP-Adresse nicht des Hostnamens in der **Server** und **Ziel-URL** Felder.

    ![Bearbeiten von Einstellungen in das Tool "Veröffentlichen"](../../deployment/media/tutorial-configure-publish-settings-in-tool.png)
