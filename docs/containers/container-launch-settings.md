---
title: Visual Studio Starteinstellungen für Containertools
author: ghogen
description: Übersicht über den Buildprozess für Containertools
ms.author: ghogen
ms.date: 08/15/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: e039e862040036f3d96729c3bdf48caafe092136
ms.sourcegitcommit: 3cda0d58c5cf1985122b8977b33a171c7359f324
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/29/2019
ms.locfileid: "71126052"
---
# <a name="container-tools-launch-settings"></a>Starteinstellungen für Containertools

Im Ordner *Eigenschaften* in einem ASP.NET Core-Projekt finden Sie die Datei „launchSettings.json“. Sie enthält Einstellungen, mit denen gesteuert wird, wie Ihre Web-App auf dem Entwicklungscomputer gestartet wird. Ausführliche Informationen dazu, wie diese Datei in der ASP.NET-Entwicklung verwendet wird, finden Sie unter [Verwenden von mehreren Umgebungen in ASP.NET Core](/aspnet/core/fundamentals/environments?view=aspnetcore-2.2). In *launchSettings.json* beziehen sich die Einstellungen im Abschnitt **Docker** darauf, wie Visual Studio containerisierte Apps behandelt.

::: moniker range="vs-2017"
```json
    "Docker": {
      "commandName": "Docker",
      "launchBrowser": true,
      "launchUrl": "{Scheme}://{ServiceHost}:{ServicePort}"
    }
```

::: moniker-end
::: moniker range=">=vs-2019"

```json
    "Docker": {
      "commandName": "Docker",
      "launchBrowser": true,
      "launchUrl": "{Scheme}://{ServiceHost}:{ServicePort}",
      "environmentVariables": {
        "ASPNETCORE_URLS": "https://+:443;http://+:80",
        "ASPNETCORE_HTTPS_PORT": "44360"
      },
      "httpPort": 51803,
      "useSSL": true,
      "sslPort": 44360
    }
```

::: moniker-end

Die Einstellung „commandName“ gibt an, dass dieser Abschnitt für Container Tools gilt. In der folgenden Tabelle sind die Eigenschaften aufgeführt, die in diesem Abschnitt festgelegt werden können:

::: moniker range="vs-2017"
|Einstellungsname|Beispiel|BESCHREIBUNG|
|------------|-------|-------|---------------|
|launchBrowser|Visual Studio 2017|"launchBrowser": true|Gibt an, ob der Browser nach dem erfolgreichen Starten des Projekts gestartet werden soll.|
|launchUrl|Visual Studio 2017|"launchUrl": "\<scheme>://\<serviceHost>:\<servicePort>"|Diese URL wird beim Start des Browsers verwendet.  Für diese Zeichenfolge werden folgende Ersetzungstoken unterstützt:<br>   \<scheme> – Wird entweder durch „http“ oder „https“ ersetzt, je nachdem, ob SSL verwendet wird.<br>   \<serviceHost> – Wird normalerweise durch „localhost“ ersetzt. Wenn Windows-Container unter Windows 10 RS3 oder älter als Ziel verwendet werden, wird sie jedoch durch die IP-Adresse des Containers ersetzt.<br>   \<servicePort> – Wird normalerweise entweder durch sslPort oder httpPort ersetzt, je nachdem, ob SSL verwendet wird.  Wenn Windows-Container unter Windows 10 RS3 oder älter als Ziel verwendet werden, wird sie jedoch durch „443“ oder „80“ ersetzt, je nachdem, ob SSL verwendet wird.|
::: moniker-end
::: moniker range=">=vs-2019"
|Einstellungsname|Beispiel|BESCHREIBUNG|
|------------|-------|-------|---------------|
|commandLineArgs|"commandLineArgs": "--mysetting myvalue"|Diese Befehlszeilenargumente werden verwendet, wenn Sie das Projekt im Container starten.|
|EnvironmentVariables|"environmentVariables": {<br>    "ASPNETCORE_URLS": "https://+:443; http://+:80",<br>    "ASPNETCORE_HTTPS_PORT": "44381"<br>}|Diese Umgebungsvariablenwerte werden beim Starten im Container an den Prozess übermittelt.|
|httpPort|"httpPort": 24051|Dieser Port auf dem Host wird dem Port 80 des Containers zugeordnet, wenn der Container gestartet wird.  Wenn keine Angabe erfolgt, wird der Wert aus dem „iisSettings“-Wert entnommen.|
|launchBrowser|"launchBrowser": true|Gibt an, ob der Browser nach dem erfolgreichen Starten des Projekts gestartet werden soll.|
|launchUrl|"launchUrl": "\<scheme>://\<serviceHost>:\<servicePort>"|Diese URL wird beim Start des Browsers verwendet.  Für diese Zeichenfolge werden folgende Ersetzungstoken unterstützt:<br>   \<scheme> – Wird entweder durch „http“ oder „https“ ersetzt, je nachdem, ob SSL verwendet wird.<br>   \<serviceHost> – Wird normalerweise durch „localhost“ ersetzt. Wenn Windows-Container unter Windows 10 RS3 oder älter als Ziel verwendet werden, wird sie jedoch durch die IP-Adresse des Containers ersetzt.<br>   \<servicePort> – Wird normalerweise entweder durch sslPort oder httpPort ersetzt, je nachdem, ob SSL verwendet wird.  Wenn Windows-Container unter Windows 10 RS3 oder älter als Ziel verwendet werden, wird sie jedoch durch „443“ oder „80“ ersetzt, je nachdem, ob SSL verwendet wird.|
|sslPort|"sslPort": 44381|Dieser Port auf dem Host wird dem Port 443 des Containers zugeordnet, wenn der Container gestartet wird.  Wenn keine Angabe erfolgt, wird der Wert aus dem „iisSettings“-Wert entnommen.|
|useSSL|"useSSL": true|Gibt an, ob beim Starten des Projekts SSL verwendet werden soll.  Wenn useSSL nicht angegeben ist, wird SSL bei sslPort > 0 verwendet.
::: moniker-end

## <a name="next-steps"></a>Nächste Schritte

Konfigurieren Sie Ihr Projekt, indem Sie die [Buildeigenschaften für Containertools](container-msbuild-properties.md) festlegen.

## <a name="see-also"></a>Siehe auch

[Buildeigenschaften von Docker Compose](docker-compose-properties.md)
