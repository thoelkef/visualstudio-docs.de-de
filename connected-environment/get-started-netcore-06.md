---
title: 'Erstellen einer .NET Core-Entwicklungsumgebung mit Containern unter Verwendung von Kubernetes in der Cloud, Schritt 6: Informationen zur Entwicklung im Team | Microsoft-Dokumentation'
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: Schnelle Kubernetes-Entwicklung mit Containern und Microservices in Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, Container
manager: ghogen
ms.openlocfilehash: 80e02e6ce1299278ba1abf530f38cb10b9f36c51
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2018
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
