---
title: Azure-Remotedebuggen mit Python
description: Konfigurieren eines Azure App Services zum Verwenden von Visual Studio für das Remotedebuggen einer Python-Anwendung.
ms.date: 06/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 1e3e70675901128ed6b8d118e54dc10ddee152a5
ms.sourcegitcommit: 96a6d1f16d06ca28d309d05b6e9fbd52f628cdbc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2018
ms.locfileid: "40008618"
---
# <a name="remotely-debug-python-code-on-azure"></a>Remotedebuggen von Python-Code in Azure

[Die Python-Unterstützung in Visual Studio](installing-python-support-in-visual-studio.md) umfasst die Möglichkeit, Python-Code, der in Azure App Service ausgeführt wird, remote zu debuggen. Anders als beim einfachen Remotedebuggen kann in diesem Szenario nicht direkt über TCP auf den Zielcomputer zugegriffen werden. Daher stellt Visual Studio einen Proxy bereit, der das Debuggerprotokoll über HTTP verfügbar macht. Projekte, die mithilfe der Webvorlage erstellt wurden, konfigurieren diesen Proxy automatisch in der generierten Datei *web.debug.config*. Das Remotedebuggen wird auch aktiviert, wenn Sie eine **Debugkonfiguration** Ihres Projekts veröffentlichen, wie unter [Veröffentlichen in Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md) beschrieben.

Da beim Azure-Remotedebuggen Websockets verwendet werden, müssen Sockets für Ihre App Service-Instanz über das [Azure-Portal](https://portal.azure.com) aktiviert werden. Wechseln Sie hierfür zu **Einstellungen** > **Anwendungseinstellungen**, und legen Sie **Allgemeine Einstellungen** > **Websockets** auf **Ein** fest. Klicken Sie anschließend auf **Speichern**, um die Änderung zu übernehmen. (Beachten Sie, dass die Optionen für das **Debuggen** nicht für das Debuggen von Python gelten.)

![Aktivieren von Websockets im Azure-Portal](media/azure-remote-debugging-enable-web-sockets.png)

## <a name="attach-with-server-explorer"></a>Anfügen mit Server-Explorer

Sobald Ihr Projekt ordnungsgemäß bereitgestellt wurde und Websockets aktiviert wurden, können Sie das Projekt über den **Server-Explorer** in Visual Studio (**Ansicht** > **Server-Explorer**) an die App Service-Instanz anfügen. Suchen Sie unter **Azure** > **App Service** in der entsprechenden Ressourcengruppe nach Ihrer Website, klicken Sie mit der rechten Maustaste darauf, und wählen Sie **Debugger anfügen (Python)** aus. (Der Befehl **Debugger anfügen** ist auf in IIS ausgeführte .NET-Anwendungen ausgelegt und nur dann hilfreich, wenn Sie neben Ihrer Python-App auch .NET-Code hosten.)

Visual Studio leitet Sie möglicherweise zu einer Reihe von Anweisungen zum direkten Anfügen weiter. Dies wird im Verlauf dieses Artikels unter [Anfügen ohne Server-Explorer](#attach-without-server-explorer) beschrieben. Wenn der Befehl **Debugger anhängen (Python)** nicht angezeigt wird oder beim Anfügen an Ihre Website ein Fehler in Visual Studio auftritt, finden Sie weitere Informationen unter [Problembehandlung für das Remotedebuggen für Python und Azure](debugging-remote-python-code-on-azure-troubleshooting.md).

Wenn das Anfügen erfolgreich ist, wechselt Visual Studio zu einer Debuggeransicht. Die Symbolleiste zeigt den Prozess an, der gerade debuggt wird, z.B. `wss://`-URI:

![Debuggen einer Azure App Service-Website](media/azure-remote-debugging-attached.png)

Nach dem Anfügen entspricht der Debugvorgang größtenteils dem regulären Remotedebuggen. Allerdings gibt es einige Einschränkungen. Für den IIS-Webserver, der eingehende Anforderungen verarbeitet und über FastCGI an Python-Code delegiert, besteht ein Timeout für die Anforderungsverarbeitung. Der Standardwert ist 90 Sekunden. Wenn die Anforderungsverarbeitung länger dauert (z.B. weil der Prozess an einem Haltepunkt angehalten wurde), beendet IIS den Prozess, wodurch auch die Debugsitzung beendet wird. 

## <a name="attach-without-server-explorer"></a>Anfügen ohne Server-Explorer

Wenn der Debugger direkt an App Service angefügt werden soll, folgen Sie den Anweisungen auf der Infoseite zum Websocketproxy, die Visual Studio unter *\<site_url>/ptvsd* auf Ihrer Website bereitstellt (Beispiel: *ptvsdemo.azurewebsites.net/ptvsd*). Auf dieser Seite können Sie auch überprüfen, ob der Proxy richtig konfiguriert ist:

![Azure-Remotedebuggen – Informationsseite zum Proxy](media/azure-remote-debugging-proxy-info-page.png)

Erstellen Sie gemäß den Anweisungen mithilfe des Geheimnisses aus *web.debug.config* eine URL, die bei jeder Veröffentlichung Ihres Projekts erneut generiert wird. Diese Datei ist im **Projektmappen-Explorer** standardmäßig ausgeblendet und nicht im Projekt enthalten. Sie müssen daher alle Dateien anzeigen oder die Datei in einem separaten Editor öffnen. Wenn Sie die Datei geöffnet haben, betrachten Sie den Wert der appSettings-Einstellung `WSGI_PTVSD_SECRET`:

![Ermitteln des Debuggerendpunkts in einer Azure App Service-Instanz](media/azure-remote-debugging-secret.png)

Die nun benötigte URL weist die Form `wss://<secret>@<site_name>.azurewebsites.net/ptvsd` auf, und Sie müssen die Werte &lt;secret&gt; und &lt;site_name&gt; in der Zeichenfolge durch Ihre eigenen Werte ersetzen.

Wählen Sie zum Anfügen des Debuggers **Debuggen** > **An den Prozess anhängen** aus, wählen sie in der Dropdownliste **Transport** die Option **Python-Remotedebuggen** aus, geben Sie die URL in das Textfeld **Qualifizierer** ein, und drücken Sie die **EINGABETASTE**. Wenn Visual Studio eine Verbindung mit App Service herstellen kann, wird in der Liste ein einzelner Python-Prozess angezeigt. Wählen Sie den Prozess aus, und klicken Sie auf **Anfügen**, um das Debuggen zu starten:

![Verwenden des Dialogfelds „An den Prozess anhängen“ zum Anfügen an eine Azure-Website](media/azure-remote-debugging-manual-attach.png)
