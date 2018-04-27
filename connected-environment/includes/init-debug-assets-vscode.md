---
ms.topic: include
ms.openlocfilehash: dbf7482acb02c6347c9c0d0765ef962cfb43a050
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2018
---
## <a name="initialize-debug-assets-with-the-vs-code-extension"></a>Initialisieren von Debugobjekten mit der Visual Studio Code-Erweiterung
Zunächst müssen Sie Ihr Codeprojekt konfigurieren, sodass Visual Studio Code mit der Entwicklungsumgebung in Azure kommuniziert. Die Visual Studio Code-Erweiterung für Connected Environment bietet einen Hilfsbefehl zum Einrichten der Debugkonfiguration. 

Öffnen Sie die **Befehlspalette** (über das Menü **Ansicht > Befehlspalette**), und verwenden Sie die automatische Vervollständigung, um den folgenden Befehl einzugeben und zu verwenden: `Connected Environment: Create configuration files for connected development`. 

Dadurch wird im Ordner `.vscode` die Debugkonfiguration für Connected Environment hinzugefügt.

![](../media/vsce-command-palette.png)

> [!Note]
> **WICHTIG**: Aufgrund eines Fehlers müssen Sie Visual Studio Code schließen und erneut öffnen, bevor Sie fortfahren.