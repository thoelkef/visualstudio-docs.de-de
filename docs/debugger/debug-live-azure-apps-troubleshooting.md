---
title: Problembehandlung beim Debuggen von Momentaufnahmen | Microsoft-Dokumentation
ms.custom: seodec18
ms.date: 11/07/2018
ms.topic: troubleshooting
helpviewer_keywords:
- debugger
ms.assetid: 511a0697-c68a-4988-9e29-8d0166ca044a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7b7916cbd3a7faa633baf53a18686779dc2b386c
ms.sourcegitcommit: 509fc3a324b7748f96a072d0023572f8a645bffc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/02/2019
ms.locfileid: "58857761"
---
# <a name="troubleshooting-and-known-issues-for-snapshot-debugging-in-visual-studio"></a>Problembehandlung und bekannte Probleme beim Debuggen von Momentaufnahmen in Visual Studio

Wenn die in diesem Artikel beschriebenen Schritte Ihr Problem nicht lösen, wenden Sie sich an snaphelp@microsoft.com.

## <a name="issue-snappoint-does-not-turn-on"></a>Problem: Andockpunkt wird nicht aktiviert

Wenn Sie ein Warnsymbol ![Andockpunktwarnsymbol](../debugger/media/snapshot-troubleshooting-snappoint-warning-icon.png "Andockpunktwarnsymbol") anstelle des regulären Andockpunktsymbols bei Ihrem Andockpunkt sehen, dann ist der Andockpunkt nicht aktiviert.

![Andockpunkt wird nicht aktiviert](../debugger/media/snapshot-troubleshooting-dont-turn-on.png "Andockpunkt wird nicht aktiviert")

Führen Sie diese Schritte aus:

1. Stellen Sie sicher, dass Sie über die gleiche Version des Quellcodes verfügen, die zum Erstellen und Bereitstellen Ihrer „app.isua1“ verwendet wurde. Stellen Sie sicher, dass Sie die richtigen Symbole für die Bereitstellung laden. Zeigen Sie dazu das **Module**-Fenster beim Debuggen von Momentaufnahmen an, und überprüfen Sie, ob die Symboldatei-Spalte eine PDB-Datei enthält, die für das Modul geladen wird, das Sie debuggen. Der Momentaufnahmedebugger versucht, automatisch Symbole für die Bereitstellung herunterzuladen und zu verwenden.

## <a name="issue-symbols-do-not-load-when-i-open-a-snapshot"></a>Problem: Symbole werden nicht geladen, wenn ich eine Momentaufnahme öffne

Wenn das folgende Fenster angezeigt wird, wurden die Symbole nicht geladen.

![Symbole werden nicht geladen](../debugger/media/snapshot-troubleshooting-symbols-wont-load.png "Symbole werden nicht geladen")

Führen Sie diese Schritte aus:

- Klicken Sie auf den **Symboleinstellungen ändern**- Link auf dieser Seite. Fügen Sie in den **Debuggen > Symbol**-Einstellungen ein Symbolcacheverzeichnis hinzu. Starten Sie das Debuggen von Momentaufnahmen neu, nachdem der Symbolpfad festgelegt wurde.

   Die in Ihrem Projekt verfügbaren Symbole oder PDB-Dateien müssen mit Ihrer App Service-Bereitstellung übereinstimmen. Die meisten Bereitstellungen (Bereitstellung über Visual Studio, CI/CD mit Azure-Pipelines oder Kudu usw.) veröffentlichen Ihre Symboldateien für Ihren App Service. Die Einstellung des Symbolcacheverzeichnisses ermöglicht Visual Studio, diese Symbole zu verwenden.

   ![Symboleinstellungen](../debugger/media/snapshot-troubleshooting-symbol-settings.png "Symboleinstellungen")

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

![Gedrosselte Momentaufnahme](../debugger/media/snapshot-troubleshooting-throttled-snapshots.png "Gedrosselte Momentaufnahme")

Führen Sie diese Schritte aus:

- Momentaufnahmen beanspruchen wenig Arbeitsspeicher, nutzen aber festgelegten virtuellen Speicher. Wenn der Momentaufnahmedebugger eine hohe Arbeitsspeicherauslastung Ihres Servers erkennt, erstellt er keine Momentaufnahmen. Sie können bereits erfasste Momentaufnahmen löschen, indem Sie die Momentaufnahmedebugger-Sitzung beenden und es erneut versuchen.

## <a name="issue-snapshot-debugging-with-multiple-versions-of-the-visual-studio-gives-me-errors"></a>Problem: Beim Debuggen von Momentaufnahmen mit mehreren Versionen von Visual Studio erhalte ich Fehlermeldungen

VS 2019 erfordert eine neuere Version dieser Momentaufnahmedebugger-Websiteerweiterung in Ihrem Azure App Service.  Diese Version ist nicht kompatibel mit der älteren Version der Momentaufnahmedebugger-Websiteerweiterung, die von Visual Studio 2017 verwendet wird.  Sie erhalten die folgende Fehlermeldung, wenn Sie versuchen, den Momentaufnahmedebugger in Visual Studio 2019 einem App Service anzufügen, der zuvor vom Momentaufnahmedebugger in Visual Studio 2017 gedebugt wurde:

![Inkompatible Momentaufnahmedebugger-Websiteerweiterung VS 2019](../debugger/media/snapshot-troubleshooting-incompatible-vs2019.png "Inkompatible Momentaufnahmedebugger-Websiteerweiterung VS 2019")

Wenn Sie im Gegensatz dazu Visual Studio 2017 verwenden, um den Momentaufnahmedebugger einem Azure App Service anzufügen, der zuvor vom Momentaufnahmedebugger in Visual Studio 2019 gedebugt wurde, erhalten Sie folgende Fehlermeldung:

![Inkompatible Momentaufnahmedebugger-Websiteerweiterung VS 2017](../debugger/media/snapshot-troubleshooting-incompatible-vs2017.png "Inkompatible Momentaufnahmedebugger-Websiteerweiterung VS 2017")

Um dieses Problem zu lösen, löschen Sie die folgenden App-Einstellungen im Azure-Portal, und fügen Sie den Momentaufnahmedebugger erneut an:

- INSTRUMENTATIONENGINE_EXTENSION_VERSION
- SNAPSHOTDEBUGGER_EXTENSION_VERSION

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
  - Fehlerprotokollierung wird automatisch an „D:\Home\LogFiles\eventlog.xml“ gesendet, Ereignisse werden mit <<Provider Name="Instrumentation Engine" //>> oder "Production Breakpoints" markiert
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
- [Debuggen von aktiven ASP.NET-Apps mit dem Momentaufnahmedebugger](../debugger/debug-live-azure-applications.md)
- [Debuggen von aktiven ASP.NET Azure-VMs\-VMSS, die den Momentaufnahmedebugger verwenden](../debugger/debug-live-azure-virtual-machines.md)
- [Debuggen von aktiven ASP.NET Azure Kubernetes Services mit dem Momentaufnahmedebugger](../debugger/debug-live-azure-kubernetes.md)
- [Häufig gestellte Fragen zum Debuggen von Momentaufnahmen](../debugger/debug-live-azure-apps-faq.md)