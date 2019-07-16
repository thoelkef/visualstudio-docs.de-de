---
title: Problembehandlung beim Debuggen von Momentaufnahmen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/24/2019
ms.topic: troubleshooting
helpviewer_keywords:
- debugger
ms.assetid: 511a0697-c68a-4988-9e29-8d0166ca044a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e3c66ba4a5031326ec288d3a5f2f3c4851d17ca6
ms.sourcegitcommit: 74c5360186731de07828764eb32ea1033a8c2275
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2019
ms.locfileid: "67559763"
---
# <a name="troubleshooting-and-known-issues-for-snapshot-debugging-in-visual-studio"></a>Problembehandlung und bekannte Probleme beim Debuggen von Momentaufnahmen in Visual Studio

Die in diesem Artikel beschriebenen Schritte das Problem nicht beheben, suchen Sie nach dem Problem auf [Entwicklercommunity](https://developercommunity.visualstudio.com/spaces/8/index.html) oder ein neues Problem melden, durch Auswahl **Hilfe** > **Feedback senden**   >  **Melden eines Problems** in Visual Studio.

## <a name="issue-attach-snapshot-debugger-encounters-an-http-status-code-error"></a>Problem: Tritt ein HTTP-Status-Code-Fehler auf "Snapshot Debugger anfügen"

Wenn Sie den folgenden Fehler in finden Sie unter den **Ausgabe** Fenster während des Versuchs, fügen Sie es möglicherweise ein bekanntes Problem mit dem unten aufgeführten. Wiederholen Sie die vorgeschlagenen Lösungen aus, und wenn das Problem weiterhin bestehen, wenden Sie sich an der vorherigen alias.

`[TIMESTAMP] Error --- Unable to Start Snapshot Debugger - Attach Snapshot Debugger failed: System.Net.WebException: The remote server returned an error: (###) XXXXXX`

### <a name="401-unauthorized"></a>(401) nicht autorisiert

Dieser Fehler weist darauf hin, dass der REST-Aufruf von Visual Studio für Azure verwendet einen ungültigen Anmeldeinformationen ausgestellt. Ein bekanntes Problem mit dem Azure Active Directory leicht-OAuth-Modul kann diesen Fehler generieren.

Führen Sie diese Schritte aus:

* Stellen Sie sicher, dass es sich bei Ihrem personalisierungskonto Visual Studio verfügt über Berechtigungen für die Azure-Abonnement und Ressourcen, die Sie zum Anfügen. Eine schnelle Möglichkeit, die dadurch bestimmt wird überprüft, ob die Ressource verfügbar ist, klicken Sie im Dialogfeld aus **Debuggen** > **Momentaufnahmedebugger anfügen...**   >  **Azure-Ressource** > **wählen Sie vorhandene**, oder klicken Sie im Cloud-Explorer.
* Wenn dieser Fehler auftritt weiterhin, gehen Sie die Feedbackkanäle, die am Anfang dieses Artikels beschrieben.

### <a name="403-forbidden"></a>(403) Forbidden

Dieser Fehler weist darauf hin, dass die Berechtigung verweigert wird. Dies kann durch viele andere Probleme verursacht werden.

Führen Sie diese Schritte aus:

* Stellen Sie sicher, dass Ihr Visual Studio-Konto ein gültiges Azure-Abonnement mit den erforderlichen Berechtigungen für Role-Based Access Control (RBAC) für die Ressource verfügt. Für App Service, überprüfen Sie, ob Sie berechtigt, [Abfrage](https://docs.microsoft.com/rest/api/appservice/appserviceplans/get) App Service-Plan Hosten Ihrer app.
* Stellen Sie sicher, dass der Zeitstempel des Client-Computer richtig und aktuell ist. Server mit Zeitstempeln aus mehr als 15 Minuten der Zeitstempel der Anforderung in der Regel erstellen, diesen Fehler.
* Wenn dieser Fehler auftritt weiterhin, gehen Sie die Feedbackkanäle, die am Anfang dieses Artikels beschrieben.

### <a name="404-not-found"></a>(404) nicht gefunden.

Dieser Fehler weist darauf hin, dass die Website auf dem Server nicht gefunden werden.

Führen Sie diese Schritte aus:

* Stellen Sie sicher, dass Sie eine Website bereitgestellt, und klicken Sie auf die App Service-Ressource, der Sie zum Anfügen, ausgeführt haben.
* Stellen Sie sicher, dass die Site unter https://\<Ressource\>. azurewebsites.net
* Wenn dieser Fehler auftritt weiterhin, gehen Sie die Feedbackkanäle, die am Anfang dieses Artikels beschrieben.

### <a name="406-not-acceptable"></a>(406) nicht akzeptabel

Dieser Fehler weist darauf hin, dass der Server nicht in den Typ an, legen Sie in der Accept-Header der Anforderung zu reagieren ist.

Führen Sie diese Schritte aus:

* Stellen Sie sicher, dass Ihre Website unter https:// ist\<Ressource\>. azurewebsites.net
* Stellen Sie sicher, dass Ihre Website nicht für neue Instanzen migriert wurden. Snapshot-Debugger verwendet das Konzept der ARRAffinity für das Weiterleiten von Anforderungen an bestimmte Instanzen, die diesen Fehler gelegentlich erzeugen können.
* Wenn dieser Fehler auftritt weiterhin, gehen Sie die Feedbackkanäle, die am Anfang dieses Artikels beschrieben.

### <a name="409-conflict"></a>(409) Konflikt...

Dieser Fehler weist darauf hin, dass die Anforderung mit dem aktuellen Serverstatus in Konflikt steht.

Dies ist ein bekanntes Problem, das auftritt, wenn ein Benutzer versucht, Debugger für Momentaufnahmen für eine App Service anzufügen, die Application Insights aktiviert hat. Application Insights wird die App-Einstellungen mit einem unterschiedlicher Groß-/Kleinschreibung als Visual Studio dieses Problem verursachen.

::: moniker range=">= vs-2019"
Wir haben dies in Visual Studio-2019 behoben.
::: moniker-end

Führen Sie diese Schritte aus:

::: moniker range="vs-2017"

* Überprüfen Sie im Azure-Portal, dass die App-Einstellungen des Momentaufnahmedebuggers (SNAPSHOTDEBUGGER_EXTENSION_VERSION) und InstrumentationEngine (INSTRUMENTATIONENGINE_EXTENSION_VERSION) in Großbuchstaben angegeben werden. Falls nicht, aktualisieren Sie die Einstellungen manuell die Site Neustart erzwungen.
::: moniker-end
* Wenn dieser Fehler auftritt weiterhin, gehen Sie die Feedbackkanäle, die am Anfang dieses Artikels beschrieben.

### <a name="500-internal-server-error"></a>Interner-Serverfehler (500)

Dieser Fehler weist darauf hin, dass der Standort vollständig heruntergefahren oder der Server die Anforderung kann nicht behandelt wird. Snapshot Debugger nur Funktionen zum Ausführen von Anwendungen. [Application Insights-Momentaufnahmedebugger](https://docs.microsoft.com/azure/azure-monitor/app/snapshot-debugger) Erstellen von Snapshots von Ausnahmen und möglicherweise das beste Tool für Ihre Anforderungen.

### <a name="502-bad-gateway"></a>(502) Bad Gateway

Dieser Fehler gibt an, ein Netzwerkproblem serverseitige und kann temporär sein.

Führen Sie diese Schritte aus:

* Warten Sie einige Minuten, bevor Sie erneut den Momentaufnahmedebugger anzufügen.
* Wenn dieser Fehler auftritt weiterhin, gehen Sie die Feedbackkanäle, die am Anfang dieses Artikels beschrieben.

## <a name="issue-snappoint-does-not-turn-on"></a>Problem: Andockpunkt ist nicht aktiviert

Wenn Sie ein Warnsymbol ![Andockpunktwarnsymbol](../debugger/media/snapshot-troubleshooting-snappoint-warning-icon.png "Andockpunktwarnsymbol") anstelle des regulären Andockpunktsymbols bei Ihrem Andockpunkt sehen, dann ist der Andockpunkt nicht aktiviert.

![Andockpunkt wird nicht aktiviert](../debugger/media/snapshot-troubleshooting-dont-turn-on.png "Andockpunkt wird nicht aktiviert")

Führen Sie diese Schritte aus:

1. Stellen Sie sicher, dass Sie die gleiche Version des Quellcodes verfügen, die zum Erstellen und Bereitstellen Ihrer app verwendet wurde. Stellen Sie sicher, dass Sie die richtigen Symbole für die Bereitstellung laden. Zeigen Sie dazu das **Module**-Fenster beim Debuggen von Momentaufnahmen an, und überprüfen Sie, ob die Symboldatei-Spalte eine PDB-Datei enthält, die für das Modul geladen wird, das Sie debuggen. Der Momentaufnahmedebugger versucht, automatisch Symbole für die Bereitstellung herunterzuladen und zu verwenden.

## <a name="issue-symbols-do-not-load-when-i-open-a-snapshot"></a>Problem: Symbole werden nicht geladen werden, wenn ich eine Momentaufnahme öffnen

Wenn das folgende Fenster angezeigt wird, wurden die Symbole nicht geladen.

![Symbole werden nicht geladen](../debugger/media/snapshot-troubleshooting-symbols-wont-load.png "Symbole werden nicht geladen")

Führen Sie diese Schritte aus:

- Klicken Sie auf den **Symboleinstellungen ändern**- Link auf dieser Seite. Fügen Sie in den **Debuggen > Symbol**-Einstellungen ein Symbolcacheverzeichnis hinzu. Starten Sie das Debuggen von Momentaufnahmen neu, nachdem der Symbolpfad festgelegt wurde.

   Die in Ihrem Projekt verfügbaren Symbole oder PDB-Dateien müssen mit Ihrer App Service-Bereitstellung übereinstimmen. Die meisten Bereitstellungen (Bereitstellung über Visual Studio, CI/CD mit Azure-Pipelines oder Kudu usw.) veröffentlichen Ihre Symboldateien für Ihren App Service. Die Einstellung des Symbolcacheverzeichnisses ermöglicht Visual Studio, diese Symbole zu verwenden.

   ![Symboleinstellungen](../debugger/media/snapshot-troubleshooting-symbol-settings.png "Symboleinstellungen")

- Wenn Ihre Organisation einen Symbolserver verwendet oder Symbole in einem anderen Pfad löscht, verwenden Sie alternativ die Symboleinstellungen, um die richtigen Symbole für die Bereitstellung zu laden.

## <a name="issue-i-cannot-see-the-attach-snapshot-debugger-option-in-the-cloud-explorer"></a>Problem: Die Option "Snapshot Debugger anfügen" in der Cloud-Explorer nicht angezeigt werden.

Führen Sie diese Schritte aus:

- Stellen Sie sicher, dass die Momentaufnahmedebugger-Komponente installiert ist. Öffnen Sie den Visual Studio-Installer, und aktivieren Sie die **Momentaufnahmedebugger**-Komponente in der Azure-Workload.
::: moniker range="< vs-2019"
- Stellen Sie sicher, dass Ihre App unterstützt wird. Derzeit werden nur ASP.NET- und ASP.NET Core-Apps (4.6.1+ und 2.0+) unterstützt, die für Azure App Services bereitgestellt werden.
::: moniker-end
::: moniker range=">= vs-2019"
- Stellen Sie sicher, dass Ihre App unterstützt wird:
  - Azure App Services – ASP.NET-Apps, die in .NET Framework 4.6.1 oder höher ausgeführt werden.
  - Azure App Services – ASP.NET Core-Apps, die in .NET Core 2.0 oder höher unter Windows ausgeführt werden.
  - Azure-VMs (und VMSSs) – ASP.NET-Apps, die unter .NET Framework 4.6.1 oder höher ausgeführt werden.
  - Azure-VMs (und VMSSs) – ASP.NET Core-Apps, die in .NET Core 2.0 oder höher unter Windows ausgeführt werden.
  - Azure Kubernetes Services – ASP.NET Core-Apps, die in .NET Core 2.2 oder höher unter Debian 9 ausgeführt werden.
  - Azure Kubernetes Services – ASP.NET Core-Apps, die in .NET Core 2.2 oder höher unter Alpine 3.8 ausgeführt werden.
  - Azure Kubernetes Services – ASP.NET Core-Apps, die in .NET Core 2.2 oder höher unter Ubuntu 18.04 ausgeführt werden.
::: moniker-end

## <a name="issue-i-only-see-throttled-snapshots-in-the-diagnostic-tools"></a>Problem: Ich sehen nur eingeschränkt Momentaufnahmen in den Diagnosetools

![Gedrosselte Momentaufnahme](../debugger/media/snapshot-troubleshooting-throttled-snapshots.png "Gedrosselte Momentaufnahme")

Führen Sie diese Schritte aus:

- Momentaufnahmen beanspruchen wenig Arbeitsspeicher, nutzen aber festgelegten virtuellen Speicher. Wenn der Momentaufnahmedebugger eine hohe Arbeitsspeicherauslastung Ihres Servers erkennt, erstellt er keine Momentaufnahmen. Sie können bereits erfasste Momentaufnahmen löschen, indem Sie die Momentaufnahmedebugger-Sitzung beenden und es erneut versuchen.

::: moniker range=">= vs-2019"
## <a name="issue-snapshot-debugging-with-multiple-versions-of-the-visual-studio-gives-me-errors"></a>Problem: Debuggen von Momentaufnahmen mit mehreren Versionen von Visual Studio erhalte ich Fehler

Visual Studio-2019 erfordert eine neuere Version der Website der Erweiterung des Momentaufnahmedebuggers in Azure App Service.  Diese Version ist nicht kompatibel mit einer älteren Version der Website der Erweiterung des Momentaufnahmedebuggers, die von Visual Studio 2017 verwendet.  Sie erhalten den folgenden Fehler, wenn Sie versuchen, die Snapshot-Debugger in Visual Studio-2019 in einer Azure App Service anzufügen, die zuvor von der Snapshot Debugger in Visual Studio 2017 Debuggen:

![Inkompatible Momentaufnahmedebugger-websiteerweiterung Visual Studio-2019](../debugger/media/snapshot-troubleshooting-incompatible-vs2019.png "inkompatible Momentaufnahmedebugger-websiteerweiterung 2019 für Visual Studio")

Im Gegensatz dazu, wenn Sie Visual Studio 2017 verwenden, um die Snapshot-Debugger mit einem Azure App Service anfügen, sodass die zuvor von der Snapshot Debugger in Visual Studio-2019 Debuggen, den folgenden Fehler erhalten Sie:

![Inkompatible Momentaufnahmedebugger-websiteerweiterung Visual Studio 2017](../debugger/media/snapshot-troubleshooting-incompatible-vs2017.png "inkompatible Momentaufnahmedebugger-websiteerweiterung Visual Studio 2017")

Um dieses Problem zu lösen, löschen Sie die folgenden App-Einstellungen im Azure-Portal, und fügen Sie den Momentaufnahmedebugger erneut an:

- INSTRUMENTATIONENGINE_EXTENSION_VERSION
- SNAPSHOTDEBUGGER_EXTENSION_VERSION
::: moniker-end

## <a name="issue-i-am-having-problems-snapshot-debugging-and-i-need-to-enable-more-logging"></a>Problem: Ich habe Probleme Debuggen von Momentaufnahmen und weitere Protokollierung aktivieren

### <a name="enable-agent-logs"></a>Aktivieren von Agent-Protokollen

Zum Aktivieren und Deaktivieren der Agent-Protokollierung öffnen Sie Visual Studio, und navigieren Sie zu *Extras > Optionen > Momentaufnahmedebugger > Agent-Protokollierung aktivieren*. Beachten Sie: Wenn *Alte Agent-Protokolle beim Sitzungsstart löschen* auch aktiviert ist, löscht jedes erfolgreiche Anfügen in Visual Studio vorherige Agent-Protokolle.

Agent-Protokolle können sich an folgenden Speicherorten befinden:

- App Services:
  - Navigieren Sie zur Kudu-Website Ihres App Service (d.h. yourappservice.**scm**.azurewebsites.net), und navigieren Sie zur Debugging-Konsole.
  - Agentprotokolle werden im folgenden Verzeichnis gespeichert:  D:\home\LogFiles\SiteExtensions\DiagnosticsAgentLogs\
- VM/VMSS:
  - Melden Sie sich mit Ihrem virtuellen Computer, Agent-Protokolle wie folgt gespeichert werden:  C:\WindowsAzure\Logs\Plugins\Microsoft.Azure.Diagnostics.IaaSDiagnostics\<Version>\SnapshotDebuggerAgent_*.txt
- AKS
  - Navigieren Sie zum folgenden Verzeichnis: „/tmp/diag/AgentLogs/*“

### <a name="enable-profilerinstrumentation-logs"></a>Aktivieren von Profiler/Instrumentierungsprotokollen

Instrumentierungsprotokolle finden Sie an den folgenden Speicherorten:

- App Services:
  - Fehlerprotokollierung automatisch an D:\Home\LogFiles\eventlog.xml gesendet, werden Ereignisse mit markiert `<Provider Name="Instrumentation Engine" />` oder "Produktion Haltepunkte"
- VM/VMSS:
  - Melden Sie sich bei Ihrem virtuellen Computer an, und öffnen Sie die Ereignisanzeige.
  - Öffnen Sie die folgende Ansicht: *Windows-Protokolle > Anwendung*.
  - *Aktuelles Protokoll filtern* nach *Ereignisquelle* mit entweder *Produktionshaltepunkten* oder *Instrumentation-Engine*.
- AKS
  - Instrumentation-Engine-Protokollierung unter „/tmp/diag/log.txt“ (legen Sie MicrosoftInstrumentationEngine_FileLogPath in DockerFile-Datei fest)
  - Produktionshaltepunkt-Protokollierung unter „/tmp/diag/shLog.txt“

## <a name="known-issues"></a>Bekannte Probleme

- Debuggen von Momentaufnahmen mit mehreren Visual Studio-Clients für den gleichen App Service wird derzeit nicht unterstützt.
- Roslyn IL-Optimierungen werden in ASP.NET Core-Projekten nicht vollständig unterstützt. Für einige ASP.NET Core-Projekte ist es möglicherweise nicht möglich, einige Variablen anzuzeigen oder einige Variablen in bedingten Anweisungen zu verwenden.
- Bestimmte Variablen, wie z.B. *$FUNCTION* oder *$CALLER*, können in bedingten Anweisungen oder Protokollpunkten für ASP.NET Core-Projekte nicht ausgewertet werden.
- Debuggen von Momentaufnahmen funktioniert nicht in App Services, für die [Lokale Zwischenspeicherung](/azure/app-service/app-service-local-cache) aktiviert ist.
- Debuggen von Momentaufnahmen von API-Apps wird derzeit nicht unterstützt.

## <a name="site-extension-upgrade"></a>Websiteerweiterungsupgrade

Debuggen von Momentaufnahmen und Application Insights hängen von einem ICorProfiler ab, der in den Websiteprozess geladen wird und Probleme durch Sperren von Dateien während des Upgrades verursacht. Wir empfehlen diesen Prozess, um sicherzustellen, dass keine Downtime auf Ihrer Produktionswebsite auftritt.

- Erstellen Sie einen [Bereitstellungsslot](/azure/app-service/web-sites-staged-publishing) in Ihrem App Service, und stellen Sie Ihre Website für den Slot bereit.
- Tauschen Sie den Slot vom Cloud-Explorer in Visual Studio aus oder über das Azure-Portal mit der Produktion aus.
- Beenden Sie die Slot-Website. Es dauert ein paar Sekunden, den w3wp.exe-Prozess der Website in allen Instanzen zu beenden.
- Upgraden Sie die Slot-Websiteerweiterung von der Kudu-Website aus oder über das Azure-Portal (*App Service-Blatt > Entwicklungstools > Erweiterungen > Update*).
- Starten Sie die Slot-Website. Sie sollten die Website besuchen, um sie wieder zu aktivieren.
- Tauschen Sie den Slot mit der Produktion aus.

## <a name="see-also"></a>Siehe auch

- [Debuggen in Visual Studio](../debugger/index.md)
- [Debug live ASP.NET-Apps, die mit dem Momentaufnahmedebugger](../debugger/debug-live-azure-applications.md)
- [Debug live ASP.NET Azure virtuelle Machines\Virtual Computer Skalierungsgruppen mit der Snapshot-Debugger](../debugger/debug-live-azure-virtual-machines.md)
- [Debug live ASP.NET-Azure-Kubernetes, die mit dem Momentaufnahmedebugger](../debugger/debug-live-azure-kubernetes.md)
- [Häufig gestellte Fragen zum Debuggen von Momentaufnahmen](../debugger/debug-live-azure-apps-faq.md)
