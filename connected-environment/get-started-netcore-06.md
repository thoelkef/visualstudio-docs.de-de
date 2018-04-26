---
title: 'Erstellen einer .NET Core-Entwicklungsumgebung mit Containern unter Verwendung von Kubernetes in der Cloud, Schritt 6: Informationen zur Entwicklung im Team | Microsoft-Dokumentation'
author: ghogen
ms.author: ghogen
ms.date: 02/20/2018
ms.topic: tutorial
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Schnelle Kubernetes-Entwicklung mit Containern und Microservices in Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, Container
manager: douge
ms.openlocfilehash: 4da5051b760a12f8fd8837072ada44c8c5a9b239
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="get-started-on-connected-environment-with-net-core"></a>Erste Schritte in Connected Environment mit .NET Core

Vorheriger Schritt: [Aufrufen eines weiteren Containers](get-started-netcore-05.md)

[!INCLUDE[](includes/team-development-1.md)]

So sieht das in der Praxis aus:
1. Navigieren Sie zum Visual Studio Code-Fenster für `mywebapi`, und bearbeiten Sie den Code der Methode `string Get(int id)`, zum Beispiel:

```csharp
[HttpGet("{id}")]
public string Get(int id)
{
    return "mywebapi now says something new";
}
```

[!INCLUDE[](includes/team-development-2.md)]

> [!div class="nextstepaction"]
> [Nächste](get-started-netcore-07.md)
