---
title: Debug live ASP.NET Azure Kubernetes-Dienste
description: Erfahren Sie, wie Sie legen Sie andockpunkte und Anzeigen von Momentaufnahmen mit dem Momentaufnahmedebugger.
ms.custom: ''
ms.date: 02/11/2019
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: poppastring
ms.author: madownie
manager: andster
monikerRange: vs-2019
ms.workload:
- aspnet
- azure
ms.openlocfilehash: 437c9a6d75df3c063a53bda0549c22fd0cbc0876
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56627947"
---
# <a name="debug-live-aspnet-azure-kubernetes-services-using-the-snapshot-debugger"></a>Debug live ASP.NET Azure Kubernetes-Dienste mit dem Momentaufnahmedebugger

Der Momentaufnahmedebugger erstellt eine Momentaufnahme Ihrer Apps in der Produktion aus, bei der Ausführung von Code, der Sie interessiert sind. Legen Sie Andockpunkte und Protokollpunkte in Ihrem Code fest, um den Debugger anzuweisen, eine Momentaufnahme zu erstellen. Der Debugger zeigt Fehler ohne Auswirkungen auf den Datenverkehr Ihrer Produktionsanwendung an. Der Momentaufnahmedebugger kann Sie dabei unterstützen, die Zeit zum Beheben von Fehlern, die in Produktionsumgebungen auftreten, erheblich zu reduzieren.

Andockpunkte und protokollpunkte ähneln Haltepunkte, aber im Gegensatz zu Haltepunkten, andockpunkte nicht die Anwendung anhalten, wenn Sie getroffen. Erfassen eine Momentaufnahme auf einen andockpunkt dauert normalerweise 10 bis 20 Millisekunden.

In diesem Tutorial werden Sie Folgendes durchführen:

> [!div class="checklist"]
> * Starten Sie den Snapshot-Debugger
> * Legen Sie einen andockpunkt und zeigen eine Momentaufnahme an
> * Legen Sie eine protokollpunkt

## <a name="prerequisites"></a>Erforderliche Komponenten

* Snapshot-Debugger für die Azure-Kubernetes-Dienste nur für die Vorschau für Visual Studio 2019 Enterprise oder höher mit der **Azure-entwicklungsworkload**. (Unter der **Einzelkomponenten** Registerkarte finden Sie unter **Debuggen und testen** > **momentaufnahmedebugger**.)

    Wenn sie noch nicht installiert ist, installieren Sie [Visual Studio 2019 Enterprise Preview](https://visualstudio.microsoft.com/vs/preview/).

* Erfassung von Momentaufnahmen ist für die folgenden Web-apps in Azure Kubernetes-Dienste verfügbar:
  * ASP.NET Core-Anwendungen, die auf .NET Core 2.2 oder höher auf Debian 9 ausgeführt wird.
  * ASP.NET Core-Anwendungen, die auf .NET Core 2.2 oder höher auf Alpine 3.8 ausgeführt.
  * ASP.NET Core-Anwendungen, die auf .NET Core 2.2 oder höher auf Ubuntu 18.04 ausgeführt.

    > [!NOTE]
    > Können Sie die Unterstützung für den Momentaufnahmedebugger in AKS zu aktivieren, wir bereitgestellt haben, eine [Repository mit einem Satz von dockerfile-Dateien, die veranschaulichen, das Setup auf Docker-Images](https://github.com/Microsoft/vssnapshotdebugger-docker).

## <a name="open-your-project-and-start-the-snapshot-debugger"></a>Öffnen Sie das Projekt, und starten Sie den Snapshot-Debugger

1. Öffnen Sie das Projekt, für die Momentaufnahme debuggen möchten.

    > [!IMPORTANT]
    > Momentaufnahme Debuggen, müssen Sie öffnen die *dieselbe Version des Quellcodes* dar, mit dem Azure-Kubernetes-Dienst veröffentlicht wird.

1. Fügen Sie die Snapshot-Debugger. Sie können eine der Methoden verwenden:

    * Wählen Sie **Debuggen > Momentaufnahmedebugger anfügen...** . Wählen Sie die AKS-Ressource für Ihre Web-app bereitgestellt wird und ein Azure Storage-Konto, und klicken Sie dann auf **Anfügen**.

      ![Starten Sie den Snapshot-Debugger im Menü Debuggen](../debugger/media/snapshot-debug-menu-attach.png)

    * Klicken Sie mit der rechten Maustaste auf Ihr Projekt, und wählen Sie **veröffentlichen**, und klicken Sie dann auf die Veröffentlichung auf **Momentaufnahmedebugger Anfügen**. Wählen Sie die AKS-Ressource für Ihre Web-app bereitgestellt wird und ein Azure Storage-Konto, und klicken Sie dann auf **Anfügen**.
    ![Starten Sie den Snapshot-Debugger von der Seite "Veröffentlichen"](../debugger/media/snapshot-publish-attach.png)

    * In der Debug-Ziel Dropdown-Menü die Option **Momentaufnahmedebugger**, Treffer **F5** wenn nötig auswählen, die AKS-Ressource für Ihre Web-app bereitgestellt wird und ein Azure Storage-Konto und klicken Sie dann auf  **Fügen Sie**.
    ![Starten Sie den Snapshot-Debugger im F5 Dropdown-Menü](../debugger/media/snapshot-F5-dropdown-attach.png)

    * Mit dem Cloud-Explorer (**Ansicht > Cloud-Explorer**) mit der rechten Maustaste auf die AKS-Ressource für Ihre Web-app bereitgestellt wird und ein Azure Storage-Konto, und klicken Sie dann auf **Momentaufnahmedebugger Anfügen**.

      ![Starten Sie den Snapshot-Debugger aus der Cloud-Explorer](../debugger/media/snapshot-launch.png)

    > [!NOTE]
    > Die Application Insights-websiteerweiterung unterstützt auch das Debuggen von Momentaufnahmen. Wenn Sie eine Fehlermeldung "websiteerweiterung veraltet" auftreten, finden Sie unter [zur Problembehandlung, Tipps und bekannte Probleme beim Debuggen von Momentaufnahmen](../debugger/debug-live-azure-apps-troubleshooting.md) zum Aktualisieren von Informationen.

   ![Momentaufnahme-debugging-Modus](../debugger/media/snapshot-message.png)

   Die **Module** Fenster erfahren Sie, wenn alle Module für Azure App Service geladen wurden (Wählen Sie **Debuggen > Windows > Module** zum Öffnen des Fensters).

   ![Überprüfen Sie das Fenster "Module"](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint"></a>Legen Sie einen andockpunkt

1. Klicken Sie im linken Bundsteg neben einer Codezeile, die Sie interessieren, um einen andockpunkt festgelegt, im Code-Editor. Stellen Sie sicher, dass es sich um Code handelt, die Sie kennen ausgeführt wird.

   ![Legen Sie einen andockpunkt](../debugger/media/snapshot-set-snappoint.png)

1. Klicken Sie auf **Sammlung starten** um die andockpunkt zu aktivieren.

   ![Aktivieren Sie die andockpunkt](../debugger/media/snapshot-start-collection.png)

    > [!TIP]
    > Sie können nicht schrittweise, wenn Sie eine Momentaufnahme anzeigen, aber Sie können mehrere andockpunkte platzieren, im Code, um die Ausführung auf verschiedene Codezeilen folgen. Wenn Sie mehrere andockpunkte in Ihrem Code verfügen, wird der Snapshot Debugger sichergestellt, dass die zugehörigen Momentaufnahmen aus der gleichen endbenutzersitzung. Der Momentaufnahmedebugger wird auch wenn viele Benutzer, die Ihrer app vorhanden sind.

## <a name="take-a-snapshot"></a>Momentaufnahme erstellen

Wenn Sie ein andockpunkt aktiviert ist, wird es eine Momentaufnahme erfasst wird, wenn die Codezeile aus der Platzierung der andockpunkt ausgeführt wird. Diese Ausführung kann von einer echten Anforderung auf dem Server verursacht werden. Erforderlich, um Ihre andockpunkt erreicht, wechseln zu der Browseransicht Ihrer Website und keine Aktionen zu erzwingen, dass dazu führen, dass Ihre andockpunkt erreicht wird.

## <a name="inspect-snapshot-data"></a>Überprüfen von momentaufnahmedaten

1. Wenn die andockpunkt erreicht wird, wird eine Momentaufnahme im Fenster "Diagnosetools" angezeigt. Wählen Sie zum Öffnen dieses Fensters **Debuggen > Windows > Diagnosetools anzeigen**.

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

1. In der **Nachricht** Feld können Sie die neue protokollmeldung, die Sie protokollieren möchten eingeben. Sie können auch Variablen in der protokollmeldung auswerten, indem Sie sie in geschweiften Klammern platzieren.

    Auf Wunsch **an Ausgabefenster senden**, wenn die protokollpunkt die Meldung im Fenster "Diagnosetools" angezeigt erreicht wird,.

    ![Protokollpunkt Daten im Fenster diagsession](../debugger/media/snapshot-logpoint-output.png)

    Auf Wunsch **an Anwendungsprotokoll senden**, wenn die protokollpunkt erreicht wird, die Meldung angezeigt, dass Sie Meldungen anzuzeigen, können an einer beliebigen Stelle wird `System.Diagnostics.Trace` (oder `ILogger` in .NET Core), wie z. B. [App Insights](/azure/application-insights/app-insights-asp-net-trace-logs).

## <a name="next-steps"></a>Nächste Schritte

In diesem Tutorial haben Sie erfahren, wie den Momentaufnahmedebugger für Azure-Kubernetes verwendet wird. Sie sollten, lesen Weitere Informationen zu diesem Feature.

> [!div class="nextstepaction"]
> [Häufig gestellte Fragen zum Debuggen von Momentaufnahmen](../debugger/debug-live-azure-apps-faq.md)