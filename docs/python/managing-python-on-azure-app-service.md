---
title: Verwalten von Python auf Azure App Service | Microsoft-Dokumentation
ms.custom: 
ms.date: 7/12/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e56b5d55-6e6b-48af-af40-5172c768cabc
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: c00adbbabf0d3b82acb17f4a269dfc693246bc69
ms.openlocfilehash: 56fccdd5e103cf29c8ea4a93ab80de7187275642
ms.contentlocale: de-de
ms.lasthandoff: 08/01/2017

---

# <a name="managing-python-on-azure-app-service"></a>Verwalten von Python auf Azure App Service

[Azure App Service](https://azure.microsoft.com/services/app-service/) ist ein Platform-as-a-Service-Angebot für Webanwendungen, egal, ob es sich um über einen Webbrowser zugreifbare Websites, um von Ihren eigenen Clients verwendete REST-APIs, oder um ereignisgesteuerte Verarbeitung handelt. App Service unterstützt die Verwendung von Python zur Implementierung von Anwendungen vollständig.

Die Python-Unterstützung auf Azure App Service wird als ein Satz von Websiteerweiterungen zur Verfügung gestellt, von denen jede eine bestimmte Version der Python-Laufzeit enthält. Die neueste Version von Python 3 wird empfohlen, aber Sie können bei Bedarf natürlich eine ältere Version auswählen. In diesem Thema wird erläutert, wie Sie eine Websiteerweiterung und alle gewünschten Pakete installieren und konfigurieren.

> [!Note]
> Die hier beschriebenen Prozesse unterliegen Veränderungen und vor allem Verbesserungen. Änderungen werden auf dem [Python Engineering at Microsoft-Blog](https://blogs.msdn.microsoft.com/pythonengineering/) angekündigt.

## <a name="choosing-a-python-version-through-the-azure-portal"></a>Auswählen einer Python-Version über das Azure-Portal

Wenn Ihre Website bereits auf Azure App Service bereitgestellt und ausgeführt wird, navigieren Sie zu Ihrem App Service-Blatt, scrollen Sie zu dem Abschnitt **Entwicklungstools**, und wählen Sie dann **Extensions > Add** (Erweiterungen > Hinzufügen). Scrollen Sie durch die Liste, um die spezifischen Erweiterungen für die gewünschte Version von Python zu finden. (Leider lässt sich die Liste nicht sortieren, weshalb die verschiedenen Versionen häufig über die Liste verteilt sind):

![Azure-Portal mit Python-Erweiterungen](media/python-on-azure-extensions.png)

## <a name="choosing-a-python-version-through-the-azure-resource-manager"></a>Auswählen einer Python-Version über den Azure Resource Manager

Wenn Sie Ihre Website mit einer Azure Resource Manager-Vorlage bereitstellen, fügen Sie die Websiteerweiterung als Ressource hinzu. Die Erweiterung wird als geschachtelte Ressource Ihrer Website mit dem Typ `siteextensions` und dem Namen aus [siteextensions.net](https://www.siteextensions.net/packages?q=Tags%3A%22python%22) angezeigt.

Nach dem Hinzufügen eines Verweises auf `python361x64` (Python 3.6.1 x 64), kann Ihre Vorlage wie folgt aussehen:

```json
  "resources": [
    {
      "apiVersion": "2015-08-01",
      "name": "[parameters('siteName')]",
      "type": "Microsoft.Web/sites",
      ...
      "resources": [
        {
          "apiVersion": "2015-08-01",
          "name": "python361x64",
          "type": "siteextensions",
          "properties": { },
          "dependsOn": [
            "[resourceId('Microsoft.Web/sites', parameters('siteName'))]"
          ]
        },
      ...
```

## <a name="configuring-your-site"></a>Konfigurieren Ihrer Website

Nach der Installation der Websiteerweiterung (entweder über das Portal oder eine Azure Resource Manager-Vorlage), wird der Python-Installationspfad in etwa wie `d:\home\python361x64\python.exe` aussehen. Um den jeweiligen Pfad anzuzeigen, wählen Sie die Erweiterung in der für Ihren App Service angezeigten Liste, um deren Beschreibungsseite zu öffnen, die folgenden Pfad enthält:

![Liste der Erweiterung in Azure App Service](media/python-on-azure-extension-list.png)

![Details der Erweiterungen in Azure App Service](media/python-on-azure-extension-detail.png)

Der nächste Schritt besteht darin, die Python-Installation auf der `web.config`-Datei der Website sowohl für die FastCGI- als auch die HTTP-Plattform-Anforderungshandler zu referenzieren.

### <a name="using-the-fastcgi-handler"></a>Verwendung des FastCGI-Handlers

FastCGI ist eine Schnittstelle, die auf der Anforderungsebene funktioniert. IIS empfängt eingehende Verbindungen und leitet jede Anforderung an eine WSGI-Anwendung an einen oder mehrere persistente Python-Prozesse weiter. Das [wfastcgi-Paket](https://pypi.io/project/wfastcgi) ist bereits installiert und mit jeder Python-Websiteerweiterung konfiguriert, sodass Sie es leicht aktivieren können, indem Sie den folgenden Code in `web.config` einschließen:

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <appSettings>
    <add key="PYTHONPATH" value="D:\home\site\wwwroot"/>
    <add key="WSGI_HANDLER" value="app.wsgi_app"/>
    <add key="WSGI_LOG" value="D:\home\LogFiles\wfastcgi.log"/>
  </appSettings>
  <system.webServer>
    <handlers>
      <add name="PythonHandler" path="*" verb="*" modules="FastCgiModule" scriptProcessor="D:\home\Python361x64\python.exe|D:\home\Python361x64\wfastcgi.py" resourceType="Unspecified" requireAccess="Script"/>
    </handlers>
  </system.webServer>
</configuration>
```

Die `<appSettings>` sind für Ihre Anwendung als Umgebungsvariablen verfügbar:
- Der Wert für `PYTHONPATH` kann frei erweitert werden, muss jedoch den Stamm Ihrer Website enthalten.
- `WSGI_HANDLER` muss auf eine durch Ihre Website importierbare WSGI-Anwendung verweisen.
- `WSGI_LOG` ist optional, wird jedoch zum Debuggen Ihrer Website empfohlen. 

Stellen Sie unter `<handlers>` sicher, dass das `scriptProcessor`-Attribut im `<add>`-Element die richtigen Pfade für Ihre bestimmte Installation enthält. Der Pfad wird auf dem Blatt „Details“ der Erweiterung erneut angezeigt.

### <a name="using-the-http-platform-handler"></a>Verwendung des HTTP-Plattform-Handlers

Das HTTP-Plattformmodul übergibt die Socketverbindungen direkt an einen eigenständigen Python-Prozess. Diese Weitergabe ermöglicht es Ihnen, einen beliebigen Webserver auszuführen, benötigt aber ein Startskript, das auf einem lokalen Webserver ausgeführt wird. Geben Sie das Skript in dem `<httpPlatform>`-Element an, in dem das `processPath`-Attribut auf Python, und das `arguments`-Attribut auf Ihr Skript und alle Argumente, die Sie bereitstellen möchten, verweist:

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.webServer>
    <handlers>
      <add name="PythonHandler" path="*" verb="*" modules="httpPlatformHandler" resourceType="Unspecified"/>
    </handlers>
    <httpPlatform processPath="D:\home\Python361x64\python.exe"
                  arguments="D:\home\site\wwwroot\runserver.py --port %HTTP_PLATFORM_PORT%"
                  stdoutLogEnabled="true"
                  stdoutLogFile="D:\home\LogFiles\python.log"
                  startupTimeLimit="60"
                  processesPerApplication="16">
      <environmentVariables>
        <environmentVariable name="SERVER_PORT" value="%HTTP_PLATFORM_PORT%" />
      </environmentVariables>
    </httpPlatform>
  </system.webServer>
</configuration>
```

Der Pfad zu `python.exe` in Ihrer Konfiguration ist natürlich für die Version spezifisch, die Sie installiert haben.

Die Umgebungsvariable `HTTP_PLATFORM_PORT`, die im Code angezeigt wird, enthält den Port, auf den Ihr lokaler Server nach Verbindungen von "localhost" lauschen soll. In diesem Beispiel wird auch gezeigt, wie Sie gegebenenfalls eine andere Umgebungsvariable erstellen, in diesem Fall `SERVER_PORT`.

## <a name="installing-packages"></a>Installieren von Paketen

Da Ihre Anwendung wahrscheinlich von einer Vielzahl von Paketen abhängig ist, müssen Sie sicherstellen, dass diese Pakete in Ihrer Python-Umgebung auf App Service mit einer der drei folgenden Methoden installiert werden:

- Die Azure App Service-Konsole auf dem Azure-Portal
- Die Kudu-REST-API
- Das Kopieren jeder Bibliothek in den Quellcode der Anwendung

### <a name="kudu-console"></a>Kudu-Konsole

Die [Kudu-Konsole](https://github.com/projectkudu/kudu/wiki/Kudu-console) ermöglicht Ihnen den direkten Befehlszeilenzugriff mit erhöhten Rechten auf den App Services-Server und dessen Dateisystem. Abgesehen davon, dass es sich um ein wertvolles Debugging-Tool handelt, können sie sie auch für CLI-basierte Konfigurationen verwenden.

Greifen Sie von Ihrem App Service-Blatt aus auf Kudu zu, indem Sie **Entwicklungstools > Erweiterte Tools**, und dann **Go** (Los) auswählen, um zu einer URL zu navigieren, die mit Ihrer Basis-App Service-URL bis auf das eingefügte `.scm` identisch ist. Wenn Ihre Basis-URL `https://vspython-test.azurewebsites.net/` ist, dann ist Kudu auf `https://vspython-test.scm.azurewebsites.net/`:

![Die Kudu-Konsole für Azure App Service](media/python-on-azure-console01.png)

Wählen Sie **Debug-Konsole > CMD** aus, um die Konsole zu öffnen, in der Sie zu Ihrer Python-Installation navigieren können und sehen, welche Bibliotheken bereits vorhanden sind.

Um ein einzelnes Paket zu installieren:

1. Navigieren Sie zum Ordner der Python-Installation, in dem Sie das Paket installieren möchten, wie z.B. `d:\home\python361x64`.
1. Verwenden Sie `python.exe -m pip install <package_name>`, um ein Paket zu installieren.

![Beispiel für die Installation von matplotlib über die Kudu-Konsole für Azure App Service](media/python-on-azure-console02.png)

Um Pakete aus Ihrer `requirements.txt` zu installieren (empfohlen):

1. Navigieren Sie zum Ordner der Python-Installation, in dem Sie das Paket installieren möchten, wie z.B. `d:\home\python361x64`.
1. Verwenden Sie `python.exe -m pip install --upgrade -r d:\home\site\wwwroot\requirements.txt`, um ein Paket zu installieren.

Die Verwendung requirements.txt wird empfohlen, da es damit einfach ist, ihren genauen Paketsatz sowohl lokal als auch auf dem Server zu reproduzieren.

> [!Note]
> Es gibt keinen C-Compiler auf Ihrem Webserver, daher müssen Sie das Rad für alle Pakete mit nativen Erweiterungsmodulen installieren. Viele gängige Pakete stellen ihre eigenen Räder zur Verfügung. Sollte dies nicht der Fall sein, verwenden Sie `pip wheel <package_name>` auf dem lokalen Entwicklungscomputer und laden Sie das Rad auf Ihre Website hoch. Ein Beispiel finden Sie unter [Verwalten von erforderlichen Paketen](python-environments.md#managing-required-packages)

### <a name="kudu-rest-api"></a>Kudu-REST-API

Anstatt die Kudu-Konsole über das Azure-Portal zu verwenden, können Sie Befehle auch Remote über die Kudu-REST-API ausführen, indem Sie den Befehl auf `https://yoursite.scm.azurewebsites.net/api/command` posten. Posten Sie beispielsweise zum Installieren des `matplotlib`-Pakets den folgenden JSON auf `/api/command`:

```json
{
    "command": 'python.exe -m pip install matplotlib',
    "dir": '\home\python361x64'
}
```

Informationen zu Befehlen und Authentifizierung finden Sie in der [Kudu-Dokumentation](https://github.com/projectkudu/kudu/wiki/REST-API). Sie können auch die Anmeldeinformationen mithilfe der [`az webapp deployment list-publishing-profiles command`](https://docs.microsoft.com/cli/azure/webapp/deployment#list-publishing-profiles) aus der Azure-CLI anzeigen. Eine Hilfsbibliothek zum Bereitstellen von Kudu-Befehlen ist auch [auf GitHub verfügbar](https://github.com/lmazuel/azure-webapp-publish/blob/master/azure_webapp_publish/kudu.py#L42).


### <a name="copying-libraries-into-app-source-code"></a>Kopieren von Bibliotheken in den Anwendungsquellcode

Anstelle die Pakete direkt auf dem Server zu installieren, können Sie auch Bibliotheken in Ihren eigenen Quellcode kopieren und diese bereitstellen, als wären sie Teil Ihrer Anwendung. Je nachdem, wie viele Abhängigkeiten Sie haben und wie oft Sie diese aktualisieren, kann diese Methode möglicherweise die einfachste Möglichkeit darstellen, eine funktionierende Bereitstellung zum Laufen zu bringen.

Der Nachteil ist, dass diese Bibliotheken genau mit der Version von Python auf dem Server übereinstimmen müssen, andernfalls werden nach der Bereitstellung ungewöhnliche Fehler angezeigt. Da die Versionen von Python in den App Service-Websiteerweiterungen jedoch genau identisch mit denen sind, die auf "Python.org" freigegeben wurden, können Sie problemlos eine kompatible Version für die lokale Entwicklung erhalten.

### <a name="avoiding-virtual-environments"></a>Vermeiden virtueller Umgebungen

Obwohl das lokale Arbeiten in einer virtuellen Umgebung Ihnen dabei helfen kann, die von Ihrer Website benötigten Abhängigkeiten vollständig zu verstehen, wird das Verwenden von virtuellen Umgebungen in App Service nicht empfohlen. Installieren Sie stattdessen Bibliotheken in Ihrem Python-Hauptordner und stellen Sie diese mit Ihrer Anwendung bereit, um zu vermeiden, dass in Konflikt stehenden Abhängigkeiten entstehen.

