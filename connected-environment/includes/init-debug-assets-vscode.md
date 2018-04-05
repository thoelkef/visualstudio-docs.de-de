## <a name="initialize-debug-assets-with-the-vs-code-extension"></a>Initialisieren von Debugobjekten mit der Visual Studio Code-Erweiterung
Zunächst müssen Sie Ihr Codeprojekt konfigurieren, sodass Visual Studio Code mit der Entwicklungsumgebung in Azure kommuniziert. Die Visual Studio Code-Erweiterung für Connected Environment bietet einen Hilfsbefehl zum Einrichten der Debugkonfiguration. 

Öffnen Sie die **Befehlspalette** (über das Menü **Ansicht > Befehlspalette**), und verwenden Sie die automatische Vervollständigung, um den folgenden Befehl einzugeben und zu verwenden: `Connected Environment: Create configuration files for connected development`. 

Dadurch wird im Ordner `.vscode` die Debugkonfiguration für Connected Environment hinzugefügt.

![](../media/vsce-command-palette.png)

> [!Note]
> **WICHTIG**: Aufgrund eines Fehlers müssen Sie Visual Studio Code schließen und erneut öffnen, bevor Sie fortfahren.