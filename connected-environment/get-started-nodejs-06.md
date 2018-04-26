---
title: 'Erstellen einer Node.js-Entwicklungsumgebung mit Containern unter Verwendung von Kubernetes in der Cloud, Schritt 6: Informationen zur Entwicklung im Team | Microsoft-Dokumentation'
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Schnelle Kubernetes-Entwicklung mit Containern und Microservices in Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, Container
manager: douge
ms.openlocfilehash: 6a17dfc3eeebccf1508ea3f69aecb53d067de7af
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="get-started-on-connected-environment-with-nodejs"></a>Erste Schritte in Connected Environment mit Node.js

Vorheriger Schritt: [Aufrufen eines Diensts, der in einem separaten Container ausgeführt wird](get-started-nodejs-05.md)

[!INCLUDE[](includes/team-development-1.md)]

So sieht das in der Praxis aus:
1. Navigieren Sie zum Visual Studio Code-Fenster für `mywebapi`, und bearbeiten Sie den Code des Standard-GET-Handlers `/` zum Beispiel wie folgt:

```javascript
app.get('/', function (req, res) {
    res.send('mywebapi now says something new');
});
```

[!INCLUDE[](includes/team-development-2.md)]

> [!div class="nextstepaction"]
> [Nächste](get-started-nodejs-07.md)

