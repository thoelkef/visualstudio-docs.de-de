---
title: Problembehandlung beim Debuggen der Momentaufnahme | Microsoft-Dokumentation
ms.custom: seodec18
ms.date: 11/07/2017
ms.technology: vs-ide-debug
ms.topic: troubleshooting
helpviewer_keywords:
- debugger
ms.assetid: 511a0697-c68a-4988-9e29-8d0166ca044a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 82d8a310b86d5dc3c776243293a91f176025f897
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2018
ms.locfileid: "53059826"
---
# <a name="troubleshooting-and-known-issues-for-snapshot-debugging-in-visual-studio"></a>Problembehandlung und bekannte Probleme beim Debuggen von Momentaufnahmen in Visual Studio

Wenn Sie die Schritte in diesem Artikel Ihr Problem nicht beheben, wenden Sie sich an snaphelp@microsoft.com.

## <a name="issue-snappoint-does-not-turn-on"></a>Problem: Andockpunkt ist nicht aktiviert

Wenn Sie ein Warnsymbol ![Andockpunkt Symbol "Warnung"](../debugger/media/snapshot-troubleshooting-snappoint-warning-icon.png "Andockpunkt Symbol \"Warnung\"") mit Ihrem andockpunkt anstelle der regulären andockpunkt-Symbol, klicken Sie dann die andockpunkt ist nicht aktiviert.

![Andockpunkt nicht einschalten](../debugger/media/snapshot-troubleshooting-dont-turn-on.png "Andockpunkt ist nicht aktiviert")

Führen Sie diese Schritte aus:

1. Stellen Sie sicher, dass Sie die gleiche Version des Quellcodes verfügen, die zum Erstellen und Bereitstellen Ihrer app.isua1 verwendet wurde. Stellen Sie sicher, dass Sie die richtigen Symbole für die Bereitstellung geladen werden. Zeigen Sie dazu die **Module** Fenster beim, Debuggen von Momentaufnahmen, und überprüfen Sie die Symboldatei-Spalte enthält eine PDB-Datei, die für das Modul, das Sie Debuggen geladen. Der Snapshot Debugger versucht, automatisch herunterladen und verwenden die Symbole für die Bereitstellung.

## <a name="issue-symbols-do-not-load-when-i-open-a-snapshot"></a>Problem: Symbole werden nicht geladen werden, wenn ich eine Momentaufnahme öffnen

Wenn Sie folgende Fenster angezeigt wird, wurde die Symbole nicht geladen.

![Laden Sie Symbole nicht](../debugger/media/snapshot-troubleshooting-symbols-wont-load.png "Symbole werden nicht geladen werden.")

Führen Sie diese Schritte aus:

- Klicken Sie auf die **Symboleinstellungen ändern...** auf dieser Seite verknüpfen. In der **Debuggen > Symbol** Einstellungen, fügen Sie ein Symbolcacheverzeichnis hinzu. Starten Sie neu, Debuggen von Momentaufnahmen, nachdem der Symbolpfad festgelegt wurde.

   Die Symbole oder die PDB-Dateien, die in Ihrem Projekt verfügbar ist, müssen Ihre App Service-Bereitstellung übereinstimmen. Die meisten Bereitstellungen (Bereitstellung über Visual Studio, CI/CD mit Azure-Pipelines oder Kudu, usw.) werden Ihre Symboldateien zusammen zu Ihrer App Service veröffentlichen. Das Symbolcacheverzeichnis festlegen, kann Visual Studio diese Symbole verwenden.

   ![Symboleinstellungen](../debugger/media/snapshot-troubleshooting-symbol-settings.png "Symboleinstellungen")

- Alternativ verwenden Sie Ihre Organisation verwendet einen Symbolserver oder löscht Symbole in einen anderen Pfad, den symboleinstellungen Laden Sie die richtigen Symbole für die Bereitstellung.

## <a name="issue-i-cannot-see-the-attach-snapshot-debugger-option-in-the-cloud-explorer"></a>Problem: Die Option "Snapshot Debugger anfügen" in der Cloud-Explorer nicht angezeigt werden.

Führen Sie diese Schritte aus:

- Stellen Sie sicher, dass die Snapshot-Debugger-Komponente installiert ist. Öffnen Sie Visual Studio-Installer aus, und überprüfen Sie die **Momentaufnahmedebugger** -Komponente in der Azure-Workload.
- Stellen Sie sicher, dass Ihre app unterstützt wird. Derzeit nur ASP.NET (4.6.1+) und ASP.NET Core (2.0 und höher)-apps, die in Azure App Service bereitgestellt werden unterstützt.

## <a name="issue-i-only-see-throttled-snapshots-in-the-diagnostic-tools"></a>Problem: Ich sehen nur eingeschränkt Momentaufnahmen in den Diagnosetools

![Gedrosselte andockpunkt](../debugger/media/snapshot-troubleshooting-throttled-snapshots.png "gedrosselt andockpunkt")

Führen Sie diese Schritte aus:

- Momentaufnahmen wenig Speicher beanspruchen, aber eine kapazitätsverbraucher besitzen. Wenn die Snapshot-Debugger, dass Ihr Server unter hoher arbeitsspeicherauslastung ist erkennt, dauert es nicht Momentaufnahmen. Sie können bereits erfasste Momentaufnahmen löschen, indem die Momentaufnahmedebugger-Sitzung zu beenden, und versuchen Sie es erneut.

## <a name="known-issues"></a>Bekannte Probleme

- Debuggen von Momentaufnahmen mit mehreren Visual Studio-Clients für den gleichen App Service wird derzeit nicht unterstützt.
- Roslyn-IL-Optimierungen sind nicht vollständig in ASP.NET Core-Projekten unterstützt. Für einige ASP.NET Core-Projekte ist es möglicherweise nicht möglich, finden einige Variablen, oder verwenden einige Variablen in bedingten Anweisungen. 
- Bestimmte Variablen, wie z. B. *$FUNCTION* oder *$CALLER*, kann nicht ausgewertet werden, in bedingten Anweisungen oder protokollpunkte für ASP.NET Core-Projekte.
- Debuggen von Momentaufnahmen funktioniert nicht auf App-Dienste, die [lokale Zwischenspeicherung](/azure/app-service/app-service-local-cache) aktiviert.
- API-Apps Debuggen von Momentaufnahmen wird derzeit nicht unterstützt.

## <a name="site-extension-upgrade"></a>Erweiterung der Standortaktualisierung

Momentaufnahme Debuggen und Application Insights basieren auf einer ICorProfiler, die in der Website-Prozess geladen wird und bewirkt, dass Probleme durch Sperren von Dateien während des Upgrades. Dieser Prozess aus, um sicherzustellen, dass es gibt keine Ausfallzeiten auf Ihren Produktionsstandort empfohlen.

- Erstellen Sie eine [Bereitstellungsslot](/azure/app-service/web-sites-staged-publishing) in Ihrer App Service und Bereitstellen des Standorts im Slot.
- Wechseln Sie im Slot mit der Produktion von Cloud-Explorer in Visual Studio oder über das Azure-Portal.
- Beenden Sie den Slot-Standort. Dies dauert ein paar Sekunden, aus der Website w3wp.exe-Prozess aus allen Instanzen zu beenden.
- Die Slot-websiteerweiterung von Kudu-Website oder das Azure-Portal aktualisieren (*Blatt "App Service" > Entwicklungstools > Erweiterungen > Update*).
- Starten Sie die Slot-Website. Es wird empfohlen, besuchen Sie die Website zum Aufwärmen es noch mal.
- Wechseln Sie im Slot mit der Produktion.

## <a name="see-also"></a>Siehe auch

[Debuggen in Visual Studio](../debugger/index.md)  
[Debug live ASP.NET-Apps, die mit dem Momentaufnahmedebugger](../debugger/debug-live-azure-applications.md)  
[Häufig gestellte Fragen zum Debuggen von Momentaufnahmen](../debugger/debug-live-azure-apps-faq.md)  
