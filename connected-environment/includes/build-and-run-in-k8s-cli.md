---
ms.topic: include
ms.openlocfilehash: b10d15b90f7f413d26adf8037c6f52c711a9ed69
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2018
ms.locfileid: "32030932"
---
## <a name="build-and-run-code-in-kubernetes"></a>Erstellen und Ausführen von Code in Kubernetes
Führen Sie den Code aus. Führen Sie im Terminalfenster den folgenden Befehl aus webfrontend, dem **Stammcodeordner**, aus:

```cmd
vsce up
```

Beobachten Sie die Ausgabe des Befehls, Ihnen werden während der Ausgabe einige Dinge auffallen:
1. Der Quellcode wird mit der Entwicklungsumgebung in Azure synchronisiert.
1. Ein Containerimage wird gemäß der Docker-Objekte in Ihrem Codeordner in Azure erstellt.
1. Es werden Kubernetes-Objekte erstellt, die das Containerimage entsprechend dem Helm-Diagramm in Ihrem Codeordner verwenden.
1. Informationen zu den Endpunkten des Containers werden angezeigt. Im Beispiel wird eine öffentliche HTTPS-URL erwartet.
1. Wenn die bisherigen Schritte erfolgreich ausgeführt werden, sollten Sie die Ausgabe `stdout` (und `stderr`) sehen, während der Container gestartet wird.

> [!Note]
> Wenn der Befehl `up` zum ersten Mal ausgeführt wird, beanspruchen diese Schritte mehr Zeit, nachfolgende Ausführungen sollten jedoch schneller sein.

## <a name="test-the-web-app"></a>Testen der Web-App
Überprüfen Sie die Konsolenausgabe auf Informationen über die öffentliche URL, die durch den Befehl `up` erstellt wurde. Sie wird in dieser Form angegeben: 

`Running at public URL: https://<servicename>-<environmentname>.vsce.io` 

Wenn Sie diese URL in einem Browserfenster öffnen, sollte die Auslastung der Web-App angezeigt werden. Während der Container ausgeführt wird, werden die Ausgaben `stdout` und `stderr` an das Terminalfenster übertragen.
