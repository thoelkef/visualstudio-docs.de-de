---
title: Azure-Remotedebuggen mit Python in Visual Studio | Microsoft-Dokumentation
ms.custom: 
ms.date: 07/12/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d68fdc53-65a1-423c-8964-9815dbb3387e
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 1ce80ecdc38075b048c8ae0a7f5773de965355f5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="remotely-debugging-python-code-on-azure"></a>Remotedebuggen von Python-Code in Azure

[Die Python-Unterstützung in Visual Studio](installation.md) umfasst die Möglichkeit, Python-Code, der in Azure App Service ausgeführt wird, remote zu debuggen. Anders als beim einfachen Remotedebuggen kann in diesem Szenario nicht direkt über TCP auf den Zielcomputer zugegriffen werden. Daher stellt Visual Studio einen Proxy bereit, der das Debuggerprotokoll über HTTP verfügbar macht. Projekte, die mithilfe der Webvorlage erstellt wurden, konfigurieren diesen Proxy automatisch in der generierten `web.debug.config`-Datei. Das Remotedebuggen wird auch aktiviert, wenn Sie eine Debugkonfiguration Ihres Projekts veröffentlichen, wie unter [Veröffentlichen in Azure App Service](template-web.md#publishing-to-azure-app-service) beschrieben.

Da das Azure-Remotedebuggen Websockets verwendet, müssen Sockets für Ihre App Service-Instanz aktiviert werden. Wechseln Sie zum [Azure-Portal](https://portal.azure.com), wählen Sie **Einstellungen > Anwendungseinstellungen** aus, und legen Sie **Allgemeine Einstellungen > Websockets** auf **Ein** fest. Wählen Sie anschließend **Speichern** aus, um die Änderung zu übernehmen. (Beachten Sie, dass die Optionen für das **Debuggen** nicht für das Debuggen von Python gelten.)

![Aktivieren von Websockets im Azure-Portal](media/azure-remote-debugging-enable-web-sockets.png)

Sobald Ihr Projekt ordnungsgemäß bereitgestellt wurde und Websockets aktiviert wurden, können Sie das Projekt über den **Server-Explorer** in Visual Studio (**Ansicht > Server-Explorer**) an die App Service-Instanz anfügen. Suchen Sie unter **Azure > App Service** in der entsprechenden Ressourcengruppe nach Ihrer Website, klicken Sie mit der rechten Maustaste, und wählen Sie **Debugger anfügen (Python)**. (Der Befehl **Debugger anfügen** ist auf in IIS ausgeführte .NET-Anwendungen ausgelegt und nur dann hilfreich, wenn Sie neben Ihrer Python-App auch .NET-Code hosten.)

Visual Studio leitet Sie möglicherweise zu einer Reihe von Anweisungen zum direkten Anfügen weiter, wie weiter unten in diesem Artikel unter [Anfügen ohne Server-Explorer](#attaching-without-server-explorer) beschrieben. Wenn der Befehl **Debugger anfügen (Python)** nicht angezeigt wird oder beim Anfügen an Ihre Website ein Fehler in Visual Studio auftritt, finden Sie Informationen zur Fehlerbehebung unter [Problembehandlung für das Azure-Remotedebuggen](debugging-azure-remote-troubleshooting.md).

Wenn das Anfügen erfolgreich ist, wechselt Visual Studio zu einer Debuggeransicht. Die Symbolleiste zeigt den Prozess an, der gerade debuggt wird, z.B. `wss://`-URI:

![Debuggen einer Azure App Service-Website](media/azure-remote-debugging-attached.png)

Nach dem Anfügen entspricht der Debugvorgang größtenteils dem regulären Remotedebuggen. Allerdings gibt es einige Einschränkungen. Für den IIS-Webserver, der eingehende Anforderungen verarbeitet und über FastCGI an Python-Code delegiert, besteht ein Timeout für die Anforderungsverarbeitung. Der Standardwert ist 90 Sekunden. Wenn die Anforderungsverarbeitung länger dauert (z.B. weil der Prozess an einem Haltepunkt angehalten wurde), beendet IIS den Prozess, wodurch auch die Debugsitzung beendet wird. 

## <a name="attaching-without-server-explorer"></a>Anfügen ohne Server-Explorer

Um den Debugger direkt an App Service anzufügen, folgen Sie den Anweisungen auf der Infoseite zum Websocketproxy, die Visual Studio unter `<site_url>/ptvsd` auf Ihrer Website bereitstellt (Beispiel: `ptvsdemo.azurewebsites.net/ptvsd`). Auf dieser Seite können Sie auch überprüfen, ob der Proxy richtig konfiguriert ist:

![Azure-Remotedebuggen – Informationsseite zum Proxy](media/azure-remote-debugging-proxy-info-page.png)

Erstellen Sie gemäß den Anweisungen mithilfe des Geheimnisses aus `web.debug.config` eine URL, die bei jeder Veröffentlichung Ihres Projekts erneut generiert wird. Diese Datei ist im Projektmappen-Explorer standardmäßig ausgeblendet und nicht im Projekt enthalten. Sie müssen daher alle Dateien anzeigen oder die Datei in einem separaten Editor öffnen. Wenn Sie die Datei geöffnet haben, betrachten Sie den Wert der appSettings-Einstellung `WSGI_PTVSD_SECRET`:

![Ermitteln des Debuggerendpunkts in einer Azure App Service-Instanz](media/azure-remote-debugging-secret.png)

Die nun benötigte URL weist die Form `wss://<secret>@<site_name>.azurewebsites.net/ptvsd` auf, und Sie müssen die Werte &lt;secret&gt; und &lt;site_name&gt; in der Zeichenfolge durch Ihre eigenen Werte ersetzen.

Um den Debugger anzufügen, wählen Sie **Debuggen > An den Prozess anhängen** aus, wählen Sie in der Dropdownliste **Transport** die Option **Python-Remotedebuggen** aus, geben Sie die URL in das Textfeld **Qualifizierer** ein, und drücken Sie die EINGABETASTE. Wenn Visual Studio eine Verbindung mit App Service herstellen kann, wird in der Liste ein einzelner Python-Prozess angezeigt. Wählen Sie den Prozess aus, und klicken Sie auf **Anfügen**, um das Debuggen zu starten:

![Verwenden des Dialogfelds „An den Prozess anhängen“ zum Anfügen an eine Azure-Website](media/azure-remote-debugging-manual-attach.png)
