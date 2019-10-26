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
ms.openlocfilehash: dc0d5ce27c3241b89a1baaf540cab4f1f56d24b5
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2019
ms.locfileid: "72911595"
---
# <a name="troubleshooting-and-known-issues-for-snapshot-debugging-in-visual-studio"></a>Problembehandlung und bekannte Probleme beim Debuggen von Momentaufnahmen in Visual Studio

Wenn das Problem durch die in diesem Artikel beschriebenen Schritte nicht behoben werden kann, suchen Sie in der [Entwickler Community](https://developercommunity.visualstudio.com/spaces/8/index.html) nach dem Problem, oder melden Sie ein neues Problem, indem Sie **Hilfe** > **Feedback senden** > **ein Problem** in Visual Studio melden auswählen.

## <a name="issue-attach-snapshot-debugger-encounters-an-http-status-code-error"></a>Problem: beim Anfügen Momentaufnahmedebugger wird ein HTTP-Statuscode Fehler feststellen.

Wenn beim Anfügen der folgende Fehler im Fenster **Ausgabe** angezeigt wird, ist möglicherweise ein bekanntes Problem aufgeführt, das im folgenden aufgeführt ist. Testen Sie die vorgeschlagenen Lösungen, und wenn das Problem weiterhin besteht, wenden Sie sich an den vorangehenden Alias.

`[TIMESTAMP] Error --- Unable to Start Snapshot Debugger - Attach Snapshot Debugger failed: System.Net.WebException: The remote server returned an error: (###) XXXXXX`

### <a name="401-unauthorized"></a>(401) nicht autorisiert

Dieser Fehler zeigt an, dass der von Visual Studio an Azure ausgegebene Rest-Befehl ungültige Anmelde Informationen verwendet. Dieser Fehler kann durch einen bekannten Fehler mit dem Azure Active Directory Easy OAuth-Modul verursacht werden.

Führen Sie diese Schritte aus:

* Stellen Sie sicher, dass Ihr Visual Studio-Personalisierungs Konto über Berechtigungen für das Azure-Abonnement und die Ressource verfügt, an die Sie anhängen. Eine schnelle Möglichkeit, dies zu ermitteln, besteht darin, zu überprüfen, ob die Ressource im Dialogfeld über **Debuggen** > **Anfügen Momentaufnahmedebugger...**  > **Azure-Ressource** > **vorhandene auswählen**oder in Cloud-Explorer verfügbar ist.
* Wenn dieser Fehler weiterhin auftritt, verwenden Sie einen der Feedback Kanäle, die am Anfang dieses Artikels beschrieben werden.

### <a name="403-forbidden"></a>(403) verboten

Dieser Fehler weist darauf hin, dass die Berechtigung verweigert wird. Dies kann durch viele verschiedene Probleme verursacht werden.

Führen Sie diese Schritte aus:

* Stellen Sie sicher, dass Ihr Visual Studio-Konto über ein gültiges Azure-Abonnement mit den erforderlichen rollenbasierten Access Control Berechtigungen (RBAC) für die Ressource verfügt. Überprüfen Sie bei Appservice, ob Sie über die Berechtigungen zum [Abfragen](/rest/api/appservice/appserviceplans/get) des App Service Plans verfügen, der Ihre APP gehostet.
* Überprüfen Sie, ob der Zeitstempel des Client Computers korrekt und aktuell ist. Server mit Zeitstempel, die nach mehr als 15 Minuten nach dem Anforderungs Zeitstempel liegen, führen in der Regel zu diesem Fehler.
* Wenn dieser Fehler weiterhin auftritt, verwenden Sie einen der Feedback Kanäle, die am Anfang dieses Artikels beschrieben werden.

### <a name="404-not-found"></a>(404) nicht gefunden.

Dieser Fehler weist darauf hin, dass die Website auf dem Server nicht gefunden werden konnte.

Führen Sie diese Schritte aus:

* Vergewissern Sie sich, dass Sie eine Website bereitgestellt haben und auf der APP Service Ressource ausgeführt werden, an die Sie anfügen.
* Überprüfen Sie, ob die Website unter https://\<Resource\>verfügbar ist. azurewebsites.net
* Stellen Sie sicher, dass Ihre benutzerdefinierte Webanwendung, die ordnungsgemäß ausgeführt wird, beim Zugriff auf https://\<Resource\>nicht den Statuscode 404 zurückgibt. azurewebsites.net
* Wenn dieser Fehler weiterhin auftritt, verwenden Sie einen der Feedback Kanäle, die am Anfang dieses Artikels beschrieben werden.

### <a name="406-not-acceptable"></a>(406) nicht zulässig

Dieser Fehler zeigt an, dass der Server nicht auf den Typ reagieren kann, der im Accept-Header der Anforderung festgelegt ist.

Führen Sie diese Schritte aus:

* Vergewissern Sie sich, dass Ihre Website unter https://\<Resource\>verfügbar ist. azurewebsites.net
* Vergewissern Sie sich, dass Ihre Site nicht zu neuen Instanzen migriert wurde. Momentaufnahmedebugger verwendet das Konzept von "arverloität" für das Routing von Anforderungen an bestimmte Instanzen, die diesen Fehler zeitweise verursachen können.
* Wenn dieser Fehler weiterhin auftritt, verwenden Sie einen der Feedback Kanäle, die am Anfang dieses Artikels beschrieben werden.

### <a name="409-conflict"></a>(409) Konflikt

Dieser Fehler gibt an, dass die Anforderung mit dem aktuellen Server Zustand in Konflikt steht.

Dies ist ein bekanntes Problem, das auftritt, wenn ein Benutzer versucht, Momentaufnahmedebugger mit einem Appservice anzufügen, der applicationinsights aktiviert hat. Applicationinsights legt die AppSettings mit einer anderen Schreibweise fest als Visual Studio, wodurch dieses Problem verursacht wird.

::: moniker range=">= vs-2019"
Wir haben dies in Visual Studio 2019 gelöst.
::: moniker-end

Führen Sie diese Schritte aus:

::: moniker range="vs-2017"

* Überprüfen Sie in der Azure-Portal, dass die AppSettings für snapshotdebugger (SNAPSHOTDEBUGGER_EXTENSION_VERSION) und instrumentierungsengine (INSTRUMENTATIONENGINE_EXTENSION_VERSION) in Großbuchstaben vorliegen. Falls nicht, aktualisieren Sie die Einstellungen manuell, wodurch ein Neustart des Standorts erzwungen wird.
::: moniker-end
* Wenn dieser Fehler weiterhin auftritt, verwenden Sie einen der Feedback Kanäle, die am Anfang dieses Artikels beschrieben werden.

### <a name="500-internal-server-error"></a>(500) interner Server Fehler.

Dieser Fehler zeigt an, dass der Standort vollständig herunter ist oder der Server die Anforderung nicht verarbeiten kann. Momentaufnahmedebugger nur Funktionen für das Ausführen von Anwendungen. [Application Insights Momentaufnahmedebugger](/azure/azure-monitor/app/snapshot-debugger) bietet snapshotts für Ausnahmen und ist möglicherweise das beste Tool für Ihre Anforderungen.

### <a name="502-bad-gateway"></a>(502) ungültiges Gateway

Dieser Fehler weist auf ein serverseitiges Netzwerkproblem hin und kann temporär sein.

Führen Sie diese Schritte aus:

* Warten Sie einige Minuten, bevor Sie den Momentaufnahmedebugger erneut anfügen.
* Wenn dieser Fehler weiterhin auftritt, verwenden Sie einen der Feedback Kanäle, die am Anfang dieses Artikels beschrieben werden.

## <a name="issue-snappoint-does-not-turn-on"></a>Problem: Andockpunkt wird nicht aktiviert

Wenn Sie anstelle des regulären andympointsymbols ein Warnsymbol mit dem snapspunkt ![-Warnsymbol](../debugger/media/snapshot-troubleshooting-snappoint-warning-icon.png "Symbol "snapspunkt-Warnung"") angezeigt wird, ist der andandandandandchen nicht aktiviert.

![Andandandandandandandandandon](../debugger/media/snapshot-troubleshooting-dont-turn-on.png "Andandandandandandandandandon")

Führen Sie diese Schritte aus:

1. Stellen Sie sicher, dass Sie über dieselbe Version des Quellcodes verfügen, die zum Erstellen und Bereitstellen der APP verwendet wurde. Stellen Sie sicher, dass Sie die richtigen Symbole für die Bereitstellung laden. Zeigen Sie dazu das **Module**-Fenster beim Debuggen von Momentaufnahmen an, und überprüfen Sie, ob die Symboldatei-Spalte eine PDB-Datei enthält, die für das Modul geladen wird, das Sie debuggen. Der Momentaufnahmedebugger versucht, automatisch Symbole für die Bereitstellung herunterzuladen und zu verwenden.

## <a name="issue-symbols-do-not-load-when-i-open-a-snapshot"></a>Problem: Symbole werden nicht geladen, wenn ich eine Momentaufnahme öffne

Wenn das folgende Fenster angezeigt wird, wurden die Symbole nicht geladen.

![Symbole werden nicht geladen.](../debugger/media/snapshot-troubleshooting-symbols-wont-load.png "Symbole werden nicht geladen.")

Führen Sie diese Schritte aus:

- Klicken Sie auf den **Symboleinstellungen ändern**- Link auf dieser Seite. Fügen Sie in den **Debuggen > Symbol**-Einstellungen ein Symbolcacheverzeichnis hinzu. Starten Sie das Debuggen von Momentaufnahmen neu, nachdem der Symbolpfad festgelegt wurde.

   Die in Ihrem Projekt verfügbaren Symbole oder PDB-Dateien müssen mit Ihrer App Service-Bereitstellung übereinstimmen. Die meisten Bereitstellungen (Bereitstellung über Visual Studio, CI/CD mit Azure-Pipelines oder Kudu usw.) veröffentlichen Ihre Symboldateien für Ihren App Service. Die Einstellung des Symbolcacheverzeichnisses ermöglicht Visual Studio, diese Symbole zu verwenden.

   ![Symbol Einstellungen](../debugger/media/snapshot-troubleshooting-symbol-settings.png "Symbol Einstellungen")

- Wenn Ihre Organisation einen Symbolserver verwendet oder Symbole in einem anderen Pfad löscht, verwenden Sie alternativ die Symboleinstellungen, um die richtigen Symbole für die Bereitstellung zu laden.

## <a name="issue-i-cannot-see-the-attach-snapshot-debugger-option-in-the-cloud-explorer"></a>Problem: Die Option „Momentaufnahmedebugger anfügen“ wird im Cloud-Explorer nicht angezeigt

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

## <a name="issue-i-only-see-throttled-snapshots-in-the-diagnostic-tools"></a>Problem: Ich sehe nur gedrosselte Momentaufnahmen in den Diagnosetools

![Gedrosselt andsnapspunkt](../debugger/media/snapshot-troubleshooting-throttled-snapshots.png "Gedrosselt andsnapspunkt")

Führen Sie diese Schritte aus:

- Momentaufnahmen beanspruchen wenig Arbeitsspeicher, nutzen aber festgelegten virtuellen Speicher. Wenn der Momentaufnahmedebugger eine hohe Arbeitsspeicherauslastung Ihres Servers erkennt, erstellt er keine Momentaufnahmen. Sie können bereits erfasste Momentaufnahmen löschen, indem Sie die Momentaufnahmedebugger-Sitzung beenden und es erneut versuchen.

::: moniker range=">= vs-2019"
## <a name="issue-snapshot-debugging-with-multiple-versions-of-the-visual-studio-gives-me-errors"></a>Problem: Beim Debuggen von Momentaufnahmen mit mehreren Versionen von Visual Studio erhalte ich Fehlermeldungen

Visual Studio 2019 erfordert eine neuere Version der Erweiterung der Momentaufnahmedebugger Site auf Ihrem Azure App Service.  Diese Version ist nicht mit der älteren Version der von Visual Studio 2017 verwendeten Momentaufnahmedebugger Site Erweiterung kompatibel.  Sie erhalten die folgende Fehlermeldung, wenn Sie versuchen, die Momentaufnahmedebugger in Visual Studio 2019 an eine Azure App Service anzufügen, die zuvor vom Momentaufnahmedebugger in Visual Studio 2017 deentschlbelt wurde:

![Nicht kompatible Momentaufnahmedebugger Website Erweiterung Visual Studio 2019](../debugger/media/snapshot-troubleshooting-incompatible-vs2019.png "Nicht kompatible Momentaufnahmedebugger Website Erweiterung Visual Studio 2019")

Wenn Sie im Gegensatz dazu Visual Studio 2017 verwenden, um die Momentaufnahmedebugger an eine Azure App Service anzufügen, die zuvor vom Momentaufnahmedebugger in Visual Studio 2019 deentschlbelt wurde, erhalten Sie die folgende Fehlermeldung:

![Nicht kompatible Momentaufnahmedebugger Website Erweiterung Visual Studio 2017](../debugger/media/snapshot-troubleshooting-incompatible-vs2017.png "Nicht kompatible Momentaufnahmedebugger Website Erweiterung Visual Studio 2017")

Um dieses Problem zu lösen, löschen Sie die folgenden App-Einstellungen im Azure-Portal, und fügen Sie den Momentaufnahmedebugger erneut an:

- INSTRUMENTATIONENGINE_EXTENSION_VERSION
- SNAPSHOTDEBUGGER_EXTENSION_VERSION
::: moniker-end

## <a name="issue-i-am-having-problems-snapshot-debugging-and-i-need-to-enable-more-logging"></a>Problem: Das Debuggen von Momentaufnahmen bereitet mir Probleme, und ich muss weitere Protokollierung aktivieren

### <a name="enable-agent-logs"></a>Aktivieren von Agent-Protokollen

Zum Aktivieren und Deaktivieren der Agent-Protokollierung öffnen Sie Visual Studio, und navigieren Sie zu *Extras > Optionen > Momentaufnahmedebugger > Agent-Protokollierung aktivieren*. Beachten Sie: Wenn *Alte Agent-Protokolle beim Sitzungsstart löschen* auch aktiviert ist, löscht jedes erfolgreiche Anfügen in Visual Studio vorherige Agent-Protokolle.

Agent-Protokolle können sich an folgenden Speicherorten befinden:

- App Services:
  - Navigieren Sie zur Kudu-Website Ihres App Service (d.h. yourappservice.**scm**.azurewebsites.net), und navigieren Sie zur Debugging-Konsole.
  - Agent-Protokolle werden im folgenden Verzeichnis gespeichert: „D:\home\LogFiles\SiteExtensions\DiagnosticsAgentLogs\“
- VM/VMSS:
  - Melden Sie sich bei Ihrem virtuellen Computer an; Agent-Protokolle werden wie folgt gespeichert: „C:\WindowsAzure\Logs\Plugins\Microsoft.Azure.Diagnostics.IaaSDiagnostics\<Version>\SnapshotDebuggerAgent_*.txt“
- AKS
  - Navigieren Sie zum folgenden Verzeichnis: „/tmp/diag/AgentLogs/*“

### <a name="enable-profilerinstrumentation-logs"></a>Aktivieren von Profiler/Instrumentierungsprotokollen

Instrumentierungsprotokolle finden Sie an den folgenden Speicherorten:

- App Services:
  - Die Fehler Protokollierung wird automatisch an d:\home\logfiles\eventlog.XML gesendet, Ereignisse werden mit `<Provider Name="Instrumentation Engine" />` oder "Produktions Breakpoints" gekennzeichnet.
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

- [Debuggen in Visual Studio](../debugger/index.yml)
- [Debuggen von Live ASP.net-apps mithilfe der Momentaufnahmedebugger](../debugger/debug-live-azure-applications.md)
- [Live Debuggen ASP.net Azure Virtual machines\vm Scale Sets Using the Momentaufnahmedebugger](../debugger/debug-live-azure-virtual-machines.md)
- [Live Debuggen ASP.net Azure Kubernetes mithilfe der Momentaufnahmedebugger](../debugger/debug-live-azure-kubernetes.md)
- [Häufig gestellte Fragen zum Debuggen von Momentaufnahmen](../debugger/debug-live-azure-apps-faq.md)
