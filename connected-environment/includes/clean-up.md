---
ms.topic: include
ms.openlocfilehash: 94e82185b05900101f91e4b368bb30d2aaceac03
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2018
---
## <a name="clean-up"></a>Bereinigen
Verwenden Sie den Befehl `vsce env rm` zum vollständigen Löschen einer Connected Environment-Umgebung in Azure, einschließlich aller Dienste, die darin ausgeführt werden. Beachten Sie, dass dieser Vorgang nicht rückgängig gemacht werden kann.

Im folgenden Beispiel wird Connected Environment in Ihrem aktiven Azure-Abonnement aufgelistet, und die Umgebung „myenv“ in der Ressourcengruppe „myenv-rg“ wird gelöscht.

```cmd
vsce env list
vsce env rm --name myenv --resource-group myenv-rg
```

