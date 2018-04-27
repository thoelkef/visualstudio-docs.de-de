---
ms.topic: include
ms.openlocfilehash: 9da28d29dc431f2f6ec92a01c397244147042f12
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2018
---
2. Drücken Sie die Taste F5 (oder geben Sie `vsce up` im Terminalfenster ein), um den Dienst auszuführen. Dadurch wird er automatisch im neu ausgewählten Bereich `scott` ausgeführt. 
1. Dies können Sie überprüfen, indem Sie `vsce list` erneut ausführen. Zuerst wird Ihnen auffallen, dass eine Instanz von `mywebapi` nun im Bereich `scott` ausgeführt wird (die Version, die in `mainline` ausgeführt wird, wird weiterhin ausgeführt, aber nicht aufgelistet). Außerdem wird der Zugriffspunkt-URL für `webfrontend` nun der Text „scott-“ vorangestellt. Diese URL ist für den Bereich `scott` eindeutig und gibt an, dass Anforderungen an die „Scott-URL“ zunächst versuchen, an den Bereich `scott` zu routen und dann auf die Dienste im Bereich `mainline` zurückfallen.

```
Name         Space     Chart              Ports   Updated     Access Points
-----------  --------  -----------------  ------  ----------  -------------
mywebapi     scott     mywebapi-0.1.0     80/TCP  15s ago     http://localhost:61466
webfrontend  mainline  webfrontend-0.1.0  80/TCP  5h ago      https://scott-webfrontend-contosodev.vsce.io
```

![](../media/space-routing.png)

Mithilfe dieser in Connected Environment integrierten Funktion können Sie End-to-End-Tests von Codes in einer freigegebenen Umgebung durchführen, ohne dass jeder Entwickler sämtliche Dienste in seinem Bereich neu erstellen muss. Beachten Sie, dass dieses Routing die Weitergabe von Headern im App-Code erfordert, wie im vorherigen Schritt dieses Leitfadens veranschaulicht.

## <a name="test-code-in-a-space"></a>Testen von Code in einem Bereich
Zum Testen Ihrer neuen Version von `mywebapi` in Verbindung mit `webfrontend` öffnen Sie in Ihrem Browser die öffentliche Zugriffspunkt-URL für webfrontend, und navigieren Sie zur Seite „Info“. Sie sollten sehen, dass Ihre Nachricht angezeigt wird.

Entfernen Sie nun den Teil „scott-“ aus der URL, und aktualisieren Sie den Browser. Daraufhin sollten Sie das alte Verhalten sehen (durch die `mywebapi`-Version, die in `mainline` ausgeführt wird).