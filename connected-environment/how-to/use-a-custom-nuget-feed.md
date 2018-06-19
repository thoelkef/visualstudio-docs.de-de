---
title: 'Gewusst wie: Verwenden eines benutzerdefinierten NuGet-Feeds in einer Connected Environment-Instanz | Microsoft-Dokumentation'
author: ghogen
ms.author: ghogen
ms.date: 03/27/2018
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Verwenden Sie einen benutzerdefinierten NuGet-Feed, um auf NuGet-Pakete in einer Connected Environment-Instanz zuzugreifen und diese zu verwenden.
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, containers
manager: douge
ms.openlocfilehash: 71fcf1c3cfb37d783de13514f6a048c3b3711a53
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2018
ms.locfileid: "32031220"
---
#  <a name="use-a-custom-nuget-feed-in-a-connected-environment"></a>Gewusst wie: Verwenden eines benutzerdefinierten NuGet-Feeds in einer Connected Environment-Instanz

Ein NuGet-Feed ist eine einfache Möglichkeit, Paketquellen in einem Projekt einzuschließen. Connected Environment muss auf diesen Feed zugreifen können, damit Abhängigkeiten ordnungsgemäß im Docker-Container installiert werden können.

So richten Sie einen NuGet-Feed ein
1. Fügen Sie einen [Paketverweis](https://docs.microsoft.com/en-us/nuget/consume-packages/package-references-in-project-files) in die Datei `*.csproj` unter dem Knoten `PackageReference` ein.

   ```xml
   <ItemGroup>
       <!-- ... -->
       <PackageReference Include="Contoso.Utility.UsefulStuff" Version="3.6.0" />
       <!-- ... -->
   </ItemGroup>
   ```

2. Erstellen Sie eine Datei namens [NuGet.Config](https://docs.microsoft.com/en-us/nuget/reference/nuget-config-file) im Projektordner.
     * Verwenden Sie den Abschnitt `packageSources`, um auf den Speicherort Ihres NuGet-Feeds zu verweisen. Wichtig: Der NuGet-Feed muss öffentlich zugänglich sein.
     * Verwenden Sie den Abschnitt `packageSourceCredentials`, um Anmeldeinformationen wie Benutzernamen und Kennwort zu konfigurieren. 

   ```xml
   <packageSources>
       <add key="Contoso" value="https://contoso.com/packages/" />
   </packageSources>

   <packageSourceCredentials>
       <Contoso>
           <add key="Username" value="user@contoso.com" />
           <add key="ClearTextPassword" value="33f!!lloppa" />
       </Contoso>
   </packageSourceCredentials>
   ```

3. Wenn Sie die Quellcodeverwaltung verwenden, gehen Sie wie folgt vor:
    - Verweisen Sie auf `NuGet.Config` in Ihrer Datei `.gitignore`, um zu verhindern, dass Sie versehentlich Anmeldeinformationen in Ihrem Quellrepository committen.
    - Öffnen Sie die Datei `vsce.yaml` in Ihrem Projekt, und suchen Sie den Abschnitt `build`. Fügen Sie den folgenden Ausschnitt ein, um sicherzustellen, dass die Datei `NuGet.Config` mit Azure synchronisiert wird, sodass diese beim Prozess zur Erstellung von Containerimages verwendet wird. (Standardmäßig synchronisiert Connected Environment keine Dateien, die den Regeln `.gitignore` und `.dockerignore` entsprechen.)

        ```yaml
        build:
        useGitIgnore: true
        ignore:
        - “!NuGet.Config”
        ```


## <a name="next-steps"></a>Nächste Schritte

Wenn Sie die oben genannten Schritte abgeschlossen haben und das nächste Mal `vsce up` ausführen (oder in VSCode oder Visual Studio auf `F5` klicken), synchronisiert Connected Environment die Datei `NuGet.Config` mit Azure, die dann von `dotnet restore` zur Installation von Paketabhängigkeiten im Container verwendet wird.

