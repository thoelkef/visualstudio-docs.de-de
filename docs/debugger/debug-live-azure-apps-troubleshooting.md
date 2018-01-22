---
title: "Problembehandlung und bekannte Probleme für das Debuggen von Momentaufnahme | Microsoft Docs"
ms.date: 11/07/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugger
ms.assetid: 511a0697-c68a-4988-9e29-8d0166ca044a
caps.latest.revision: "1"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7792e22398afd476703407e8ae2159e0f1afd931
ms.sourcegitcommit: 5d43e9590e2246084670b79269cc9d99124bb3df
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/19/2018
---
# <a name="troubleshooting-and-known-issues-for-snapshot-debugging-in-visual-studio"></a>Problembehandlung und bekannte Probleme für die Momentaufnahme Debuggen in Visual Studio

Wenn Sie die Schritte in diesem Thema beschriebenen Ihr Problem nicht beheben, wenden Sie sich an snaphelp@microsoft.com.

## <a name="issue-snappoint-does-not-turn-on"></a>Problem: Snappoint ist nicht aktiviert

Wenn Sie ein Warnsymbol angezeigt ![Snappoint Warnsymbol](../debugger/media/snapshot-troubleshooting-snappoint-warning-icon.png "Snappoint Warnsymbol") mit Ihrem Snappoint anstelle der regulären Snappoint-Symbol, klicken Sie dann die Snappoint ist nicht eingeschaltet.

![Snappoint nicht einschalten](../debugger/media/snapshot-troubleshooting-dont-turn-on.png "Snappoint nicht einschalten")

Gehen Sie wie folgt vor:

1. Stellen Sie sicher, dass Sie die gleiche Version des Quellcodes verfügen, die zum Erstellen und Bereitstellen Ihrer app.isua1 verwendet wurde. Stellen Sie sicher, dass Sie für Ihre Bereitstellung die korrekten Symbole geladen sind. Zeigen Sie dazu an der **Module** Fenster while Debugging Momentaufnahme und überprüfen Sie, ob die Spalte "Symbol" zeigt eine PDB-Datei für das Modul, das Sie Debuggen geladen werden. Beachten Sie, dass der Momentaufnahme-Debugger versucht automatisch herunterzuladen und die Symbole für Ihre Bereitstellung verwenden.

## <a name="issue-symbols-do-not-load-when-i-open-a-snapshot"></a>Problem: Symbole werden nicht geladen werden, wenn ich eine Momentaufnahme öffnen

Wenn folgende Fenster angezeigt wird, wurde die Symbole nicht geladen.

![Laden Sie Symbole nicht](../debugger/media/snapshot-troubleshooting-symbols-wont-load.png "Symbole werden nicht geladen werden.")

Gehen Sie wie folgt vor:

- Klicken Sie auf die **Symboleinstellungen ändern...** Verknüpfen Sie auf dieser Seite. In der **Debuggen > Symbol** Einstellungen, fügen Sie ein Symbolcacheverzeichnis hinzu. Starten Sie die Momentaufnahme zu debuggen, wenn der Symbolpfad festgelegt wurde.

   Die Symbole oder die PDB-Dateien, die in Ihrem Projekt zur Verfügung müssen Ihre App Service-Bereitstellung übereinstimmen. Die meisten Bereitstellungen (Bereitstellung über Visual Studio, CD/CI mit VSTS oder Kudu, usw.) veröffentlicht die Symboldateien zusammen mit Ihrem App Service. Festlegen der Symbolcacheverzeichnis kann Visual Studio diese Symbole verwenden.

   ![Symbol Settings](../debugger/media/snapshot-troubleshooting-symbol-settings.png "Symbol Einstellungen")

- Alternativ können Sie verwenden Sie Ihre Organisation verwendet einen anderen Symbolserver oder löscht Symbole in einen anderen Pfad, die symboleinstellungen So laden Sie die richtigen Symbole für Ihre Bereitstellung.

## <a name="issue-i-cannot-see-the-attach-snapshot-debugger-option-in-the-cloud-explorer"></a>Problem: die Option "Momentaufnahme-Debugger anfügen" in der Cloud-Explorer nicht angezeigt werden.

Gehen Sie wie folgt vor:

- Stellen Sie sicher, dass die Momentaufnahme Debugger-Komponente installiert ist. Öffnen Sie im Visual Studio-Installer, und überprüfen Sie die **Momentaufnahme Debugger** Komponente in der Azure-arbeitsauslastung.
- Stellen Sie sicher, dass Ihre app unterstützt wird. Derzeit nur ASP.NET (4.6.1+) und ASP.NET Core (2.0 und höher)-apps, die für Azure-App-Dienste bereitgestellt werden unterstützt.

## <a name="issue-i-only-see-throttled-snapshots-in-the-diagnostic-tools"></a>Problem: ich sehen nur eingeschränkt Momentaufnahmen in die Diagnosetools

![Throttled Snappoint](../debugger/media/snapshot-troubleshooting-throttled-snapshots.png "Snappoint gedrosselt")

Gehen Sie wie folgt vor:

- Momentaufnahmen haben eine zugesicherte aber sehr wenig Speicher beanspruchen. Wenn der Momentaufnahme-Debugger, dass der Server Arbeitsspeicher stark ausgelastet ist erkennt, dauert es keine Momentaufnahmen. Sie können bereits erfasste Momentaufnahmen löschen, indem Sie die Snapshot-Debugsitzung zu beenden, und es erneut zu versuchen.

## <a name="known-issues"></a>Bekannte Probleme

- Momentaufnahme Debuggen mit mehreren Visual Studio-Clients für den gleichen App-Dienst ist derzeit nicht unterstützt.
- Roslyn-IL-Optimierungen sind nicht vollständig in ASP.NET Core-Projekten unterstützt. Bei einigen Projekten ASP.NET Core ist es möglicherweise nicht möglich, finden einige Variablen oder einige Variablen in bedingten Anweisungen verwenden. 
- Spezielle Variablen, wie z. B. *$FUNCTION* oder *$CALLER*, kann nicht in bedingten Anweisungen oder Logpoints für ASP.NET Core Projekte ausgewertet werden.
- Momentaufnahme-Debuggen funktioniert nicht auf App-Dienste, die über [lokales Cashing](/azure/app-service/app-service-local-cache) eingeschaltet.
- Debuggen-API-Apps Momentaufnahme wird derzeit nicht unterstützt.

## <a name="site-extension-upgrade"></a>Erweiterung der Standortaktualisierung

Momentaufnahme-Debugging und Application Insights richten sich nach einer ICorProfiler lädt in den Site-Prozess und führt dazu, dass Probleme mit der Sperren während des Upgrades. Es wird empfohlen, diesen Vorgang stellen Sie sicher, dass keine Ausfallzeit Ihre Produktionswebsite vorhanden ist.

- Erstellen einer [Bereitstellungsslot](/azure/app-service/web-sites-staged-publishing) in Ihren App Service und Ihre Website in das Einschubfach bereitstellen.
- Tauschen Sie der Slot mit dem Produktions aus, Cloud-Explorer in Visual Studio oder über das Azure-Portal.
- Beenden Sie der Slot Standort. Dies dauert einige Sekunden, um den Standort w3wp.exe-Prozess über alle Instanzen zu beenden.
- Die websiteerweiterung Slot von der Kudu-Website oder der Azure-Verwaltungsportal aktualisieren (*Blatt "App-Dienst" > Entwicklungstools > Extensions > Update*).
- Starten Sie die Slot-Website. Es wird empfohlen, besuchen die Website, um es erneut Aufwärmen.
- Der Slot mit Produktion ausgetauscht werden.

## <a name="see-also"></a>Siehe auch

[Debuggen in Visual Studio](../debugger/index.md)  
[Debuggen von Livedaten ASP.NET-apps, die mit dem Momentaufnahme-Debugger](../debugger/debug-live-azure-applications.md)  
[Häufig gestellte Fragen zum Debuggen von Momentaufnahmen](../debugger/debug-live-azure-apps-faq.md)  
