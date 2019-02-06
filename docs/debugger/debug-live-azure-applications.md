---
title: Debuggen von ASP.NET Azure-live-apps
description: Erfahren Sie, wie Sie legen Sie andockpunkte und Anzeigen von Momentaufnahmen mit dem Momentaufnahmedebugger.
ms.custom: mvc
ms.date: 03/16/2018
ms.topic: conceptual
helpviewer_keywords:
- debugger
ms.assetid: adb22512-4d4d-40e5-9564-1af421b7087e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
- azure
ms.openlocfilehash: f0936078039c4c1071f0214b61702a7f57f794ec
ms.sourcegitcommit: 0f7411c1a47d996907a028e920b73b53c2098c9f
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/04/2019
ms.locfileid: "55690191"
---
# <a name="debug-live-aspnet-azure-apps-using-the-snapshot-debugger"></a>Debug live ASP.NET-Azure-apps, die mit dem Momentaufnahmedebugger

Der Momentaufnahmedebugger erstellt eine Momentaufnahme Ihrer Apps in der Produktion aus, bei der Ausführung von Code, der Sie interessiert sind. Legen Sie Andockpunkte und Protokollpunkte in Ihrem Code fest, um den Debugger anzuweisen, eine Momentaufnahme zu erstellen. Der Debugger zeigt Fehler ohne Auswirkungen auf den Datenverkehr Ihrer Produktionsanwendung an. Der Momentaufnahmedebugger kann Sie dabei unterstützen, die Zeit zum Beheben von Fehlern, die in Produktionsumgebungen auftreten, erheblich zu reduzieren.

Andockpunkte und protokollpunkte ähneln Haltepunkte, aber im Gegensatz zu Haltepunkten, andockpunkte nicht die Anwendung anhalten, wenn Sie getroffen. Erfassen eine Momentaufnahme auf einen andockpunkt dauert normalerweise 10 bis 20 Millisekunden.

In diesem Tutorial werden Sie Folgendes durchführen:

> [!div class="checklist"]
> * Starten Sie den Snapshot-Debugger
> * Legen Sie einen andockpunkt und zeigen eine Momentaufnahme an
> * Legen Sie eine protokollpunkt

## <a name="prerequisites"></a>Erforderliche Komponenten

* Momentaufnahmedebugger ist nur verfügbar für Visual Studio 2017 Enterprise-Version 15.5 oder höher mit der **Azure-entwicklungsworkload**. (Unter der **Einzelkomponenten** Registerkarte finden Sie unter **Debuggen und testen** > **momentaufnahmedebugger**.)

    Wenn sie noch nicht installiert ist, installieren Sie [Visual Studio 2017 Enterprise-Version 15.5](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) oder höher. Wenn Sie von einer früheren Visual Studio 2017-Installation aktualisieren, führen Sie den Visual Studio-Installer, und überprüfen Sie die Snapshot-Debugger-Komponente in der **ASP.NET und Web-entwicklungsworkload**.

* Azure App Service-Plan Basic oder höher.

* Die Momentaufnahmensammlung ist für folgende Web-Apps verfügbar, die in Azure App Service ausgeführt werden:

    * ASP.NET-Apps, die in .NET Framework 4.6.1 oder höher ausgeführt werden.
    * ASP.NET Core-Apps, die in .NET Core 2.0 oder höher unter Windows ausgeführt werden.

## <a name="open-your-project-and-start-the-snapshot-debugger"></a>Öffnen Sie das Projekt, und starten Sie den Snapshot-Debugger

1. Öffnen Sie das Projekt, für die Momentaufnahme debuggen möchten.

    > [!IMPORTANT]
    > Momentaufnahme Debuggen, müssen Sie öffnen die **dieselbe Version des Quellcodes** , die in Azure App Service veröffentlicht wird.

1. In der Cloud-Explorer (**Ansicht > Cloud-Explorer**) mit der rechten Maustaste auf das Projekt, um bereitgestellt wird Azure App Service, und wählen Sie **Momentaufnahmedebugger Anfügen**.

   ![Starten Sie den Snapshot-debugger](../debugger/media/snapshot-launch.png)

    Die zum ersten Mal auswählen **Momentaufnahmedebugger Anfügen**, Sie werden aufgefordert, um die websiteerweiterung des Momentaufnahmedebuggers in Azure App Service zu installieren. Diese Installation erfordert einen Neustart des Azure App Service.

   Visual Studio ist jetzt im Debugmodus Momentaufnahme.

    > [!NOTE]
    > Die Application Insights-websiteerweiterung unterstützt auch das Debuggen von Momentaufnahmen. Wenn Sie eine Fehlermeldung "websiteerweiterung veraltet" auftreten, finden Sie unter [zur Problembehandlung, Tipps und bekannte Probleme beim Debuggen von Momentaufnahmen](../debugger/debug-live-azure-apps-troubleshooting.md) zum Aktualisieren von Informationen.

   ![Momentaufnahme-debugging-Modus](../debugger/media/snapshot-message.png)

   Die **Module** Fenster erfahren Sie, wenn alle Module für Azure App Service geladen wurden (Wählen Sie **Debuggen / Windows / Module** zum Öffnen des Fensters).

   ![Überprüfen Sie das Fenster "Module"](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint"></a>Legen Sie einen andockpunkt

1. Klicken Sie im linken Bundsteg neben einer Codezeile, die Sie interessieren, um einen andockpunkt festgelegt, im Code-Editor. Stellen Sie sicher, dass es sich um Code handelt, die Sie kennen ausgeführt wird.

   ![Legen Sie einen andockpunkt](../debugger/media/snapshot-set-snappoint.png)

2. Klicken Sie auf **Sammlung starten** um die andockpunkt zu aktivieren.

   ![Aktivieren Sie die andockpunkt](../debugger/media/snapshot-start-collection.png)

    > [!TIP]
    > Sie können nicht schrittweise, wenn Sie eine Momentaufnahme anzeigen, aber Sie können mehrere andockpunkte platzieren, im Code, um die Ausführung auf verschiedene Codezeilen folgen. Wenn Sie mehrere andockpunkte in Ihrem Code verfügen, wird der Snapshot Debugger sichergestellt, dass die zugehörigen Momentaufnahmen aus der gleichen endbenutzersitzung. Der Momentaufnahmedebugger wird auch wenn viele Benutzer, die Ihrer app vorhanden sind.

## <a name="take-a-snapshot"></a>Momentaufnahme erstellen

Wenn Sie ein andockpunkt aktiviert ist, wird es eine Momentaufnahme erfasst wird, wenn die Codezeile aus der Platzierung der andockpunkt ausgeführt wird. Diese Ausführung kann von einer echten Anforderung auf dem Server verursacht werden. Erforderlich, um Ihre andockpunkt erreicht, wechseln zu der Browseransicht Ihrer Website und keine Aktionen zu erzwingen, dass dazu führen, dass Ihre andockpunkt erreicht wird.

## <a name="inspect-snapshot-data"></a>Überprüfen von momentaufnahmedaten

1. Wenn die andockpunkt erreicht wird, wird eine Momentaufnahme im Fenster "Diagnosetools" angezeigt. Wählen Sie zum Öffnen dieses Fensters **Debuggen / Windows / Diagnosetools anzeigen**.

   ![Öffnen Sie einen andockpunkt](../debugger/media/snapshot-diagsession-window.png)

1. Doppelklicken Sie auf der andockpunkt, um die Momentaufnahme im Code-Editor zu öffnen.

   ![Überprüfen von momentaufnahmedaten](../debugger/media/snapshot-inspect-data.png)

   In dieser Ansicht können Sie auf Variablen verwenden Sie zum Anzeigen von DataTips zeigen die **"lokal"**, **Überwachungen**, und **Aufrufliste** Windows und auch Auswerten von Ausdrücken.

    Die Website selbst noch aktiv ist, und Endbenutzer sind nicht betroffen. Nur eine Momentaufnahme ist pro andockpunkt standardmäßig erfasst: Nachdem eine Momentaufnahme erfasst wurde der andockpunkt deaktiviert. Wenn Sie eine andere Momentaufnahme an die andockpunkt erfassen möchten, können Sie die andockpunkt wieder aktivieren, indem Sie auf **Upgradesammlung**.

Sie können auch weitere andockpunkte Ihrer app hinzufügen und aktivieren sie mit der **Upgradesammlung** Schaltfläche.

**Benötigen Sie Hilfe?** Finden Sie unter den [Problembehandlung und bekannte Probleme](../debugger/debug-live-azure-apps-troubleshooting.md) und [– häufig gestellte Fragen zum Debuggen von Momentaufnahmen](../debugger/debug-live-azure-apps-faq.md) Seiten.

## <a name="set-a-conditional-snappoint"></a>Legen Sie einen bedingten andockpunkt

Ist es schwierig, einen bestimmten Status in Ihrer app neu zu erstellen, berücksichtigen Sie, ob die Verwendung von einem bedingten andockpunkt kann ein. Bedingte andockpunkte-Hilfe, die Sie vermeiden, Erstellen einer Momentaufnahme, bis die app wechselt in einen gewünschten Status, z. B. wenn eine Variable einen bestimmten Wert aufweist, den Sie untersuchen möchten. Sie können Bedingungen, die mithilfe von Ausdrücken, filtern, festlegen oder Trefferanzahlen.

#### <a name="to-create-a-conditional-snappoint"></a>Erstellen Sie einen bedingten andockpunkt

1. Mit der rechten Maustaste ein andockpunkt-Symbol (der Ball), und wählen Sie **Einstellungen**.

   ![Einstellung auswählen](../debugger/media/snapshot-snappoint-settings.png)

1. Geben Sie im Fenster andockpunkt einen Ausdruck ein.

   ![Geben Sie einen Ausdruck](../debugger/media/snapshot-snappoint-conditions.png)

   In der vorherigen Abbildung wird die Momentaufnahme nur für die andockpunkt erstellt bei `visitor.FirstName == "Dan"`.

## <a name="set-a-logpoint"></a>Legen Sie eine protokollpunkt

Zusätzlich zum Erstellen einer Momentaufnahme aus, wenn Sie einen andockpunkt erreicht ist, können Sie auch einen andockpunkt zum Protokollieren einer Meldung konfigurieren (d. h. eine protokollpunkt erstellen). Sie können die protokollpunkte festlegen, ohne dass Ihre app erneut bereitstellen. Protokollpunkte praktisch ausgeführt und dazu führen, dass keine Auswirkungen oder Nebeneffekte der ausgeführten Anwendung.

#### <a name="to-create-a-logpoint"></a>Erstellen Sie eine protokollpunkt

1. Mit der rechten Maustaste ein andockpunkt-Symbol (die blaue Sechseck), und wählen Sie **Einstellungen**.

1. Wählen Sie im Fenster andockpunkt **Aktionen**.

    ![Erstellen Sie eine protokollpunkt](../debugger/media/snapshot-logpoint.png)

1. In das Nachrichtenfeld können Sie die neue Nachricht eingeben, die Sie protokollieren möchten. Sie können auch Variablen in der protokollmeldung auswerten, indem Sie sie in geschweiften Klammern platzieren.

    Auf Wunsch **an Ausgabefenster senden**, wenn die protokollpunkt die Meldung im Fenster "Diagnosetools" angezeigt erreicht wird,.

    ![Protokollpunkt Daten im Fenster diagsession](../debugger/media/snapshot-logpoint-output.png)

    Auf Wunsch **an Anwendungsprotokoll senden**, wenn die protokollpunkt erreicht wird, die Meldung angezeigt, dass Sie Meldungen anzuzeigen, können an einer beliebigen Stelle wird `System.Diagnostics.Trace` (oder `ILogger` in .NET Core), wie z. B. [App Insights](/azure/application-insights/app-insights-asp-net-trace-logs).

## <a name="next-steps"></a>Nächste Schritte

In diesem Tutorial haben Sie gelernt, wie der Snapshot-Debugger verwendet wird. Sie sollten, lesen Weitere Informationen zu diesem Feature.

> [!div class="nextstepaction"]
> [Häufig gestellte Fragen zum Debuggen von Momentaufnahmen](../debugger/debug-live-azure-apps-faq.md)
