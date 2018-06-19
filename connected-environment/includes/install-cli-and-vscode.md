---
ms.topic: include
ms.openlocfilehash: 78de57178350d4317896c41a455efbeeb553c58d
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2018
ms.locfileid: "32031154"
---
## <a name="install-the-connected-environment-cli"></a>Installieren der CLI für Connected Environment
Connected Environment erfordert eine minimale Einrichtung auf lokalen Computern. Der Großteil der Konfigurierung Ihrer Entwicklungsumgebung wird in der Cloud gespeichert und kann für andere Benutzer freigegeben werden.

### <a name="install-on-mac"></a>Installieren unter Mac
Herunterladen und Installieren der CLI für Connected Environment:
```cmd
curl -L https://aka.ms/get-vsce-mac | bash
```

### <a name="install-on-windows"></a>Installieren unter Windows
1. Laden Sie den [Installer für die CLI für Connected Environment](https://aka.ms/get-vsce-windows) herunter, und führen Sie ihn aus. 

### <a name="install-on-linux"></a>Installation unter Linux
Bald verfügbar...

## <a name="get-kubernetes-debugging-for-vs-code"></a>Kubernetes-Debugging für Visual Studio Code
Sie können die CLI für Connected Environment zwar als eigenständiges Tool verwenden, aber es gibt umfangreiche Features wie Kubernetes-Debugging für .NET Core- und Node.js-Entwickler, die Visual Studio Code verwenden.

1. Wenn Sie noch nicht darüber verfügen, installieren Sie [Visual Studio Code](https://code.visualstudio.com/Download).
1. Laden Sie die [Erweiterung für Visual Studio Connected Environment](https://aka.ms/get-vsce-code) herunter.
1. Installieren der Erweiterung: 

```cmd
code --install-extension path-to-downloaded-extension/vsce-0.1.1.vsix
```
