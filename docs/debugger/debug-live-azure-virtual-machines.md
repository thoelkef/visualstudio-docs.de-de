---
title: Debug live ASP.NET Azure virtuellen Computern und skalierungsgruppen
description: Erfahren Sie, wie Sie Andockpunkte festlegen und Momentaufnahmen mit dem Momentaufnahmedebugger anzeigen.
ms.custom: ''
ms.date: 02/06/2019
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: poppastring
ms.author: madownie
manager: andster
monikerRange: '>= vs-2019'
ms.workload:
- aspnet
- azure
ms.openlocfilehash: 38cf8b5c2af174b026c507fc5c668f826707adf3
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/28/2019
ms.locfileid: "66263360"
---
# <a name="debug-live-aspnet-apps-on-azure-virtual-machines-and-azure-virtual-machine-scale-sets-using-the-snapshot-debugger"></a>Debuggen von aktiven ASP.NET-Apps auf Azure-VMs und Azure-VMSS mit dem Momentaufnahmedebugger

Der Momentaufnahmedebugger erstellt eine Momentaufnahme Ihrer Apps, die sich in der Produktion befinden, wenn Code ausgeführt wird, der für Sie relevant ist. Legen Sie Andockpunkte und Protokollpunkte in Ihrem Code fest, um den Debugger anzuweisen, eine Momentaufnahme zu erstellen. Der Debugger zeigt Fehler ohne Auswirkungen auf den Datenverkehr Ihrer Produktionsanwendung an. Der Momentaufnahmedebugger kann Sie dabei unterstützen, die Zeit zum Beheben von Fehlern, die in Produktionsumgebungen auftreten, erheblich zu reduzieren.

Andockpunkte und Protokollpunkte ähneln Haltepunkten, aber im Gegensatz zu Haltepunkten halten Andockpunkte die Anwendung nicht an, wenn sie erreicht werden. In der Regel dauert das Erfassen einer Momentaufnahme an einem Andockpunkt 10 bis 20 Millisekunden.

In diesem Tutorial werden Sie Folgendes durchführen:

> [!div class="checklist"]
> * Starten des Momentaufnahmedebuggers
> * Festlegen eines Andockpunkts und Anzeigen einer Momentaufnahme
> * Festlegen eines Protokollpunkts

## <a name="prerequisites"></a>Vorraussetzungen

* Momentaufnahmedebugger für mit Azure Virtual Machines (VMs) und Azure Virtual Machine Scale Sets ist nur verfügbar für Visual Studio 2019 Enterprise oder höher mit der **Azure-entwicklungsworkload**. (Auf der Registerkarte **Einzelne Komponenten** finden Sie ihn unter **Debuggen und Testen** > **Momentaufnahmedebugger**.)

    Wenn sie noch nicht installiert ist, installieren Sie [Visual Studio 2019 Enterprise](https://visualstudio.microsoft.com/vs/).

* Erfassung von Momentaufnahmen ist für die folgenden Azure virtuelle Machines\Virtual Machine Scale Sets-Web-apps zur Verfügung:
  * ASP.NET-Apps, die in .NET Framework 4.6.1 oder höher ausgeführt werden.
  * ASP.NET Core-Apps, die in .NET Core 2.0 oder höher unter Windows ausgeführt werden.

## <a name="open-your-project-and-start-the-snapshot-debugger"></a>Öffnen Ihres Projekts und Starten des Momentaufnahmedebuggers

1. Öffnen Sie das Projekt, das Sie mit einer Momentaufnahme debuggen möchten.

    > [!IMPORTANT]
    > Momentaufnahme Debuggen, müssen Sie öffnen die *dieselbe Version des Quellcodes* dar, mit dem Azure virtuelle Machine\Virtual Machine Scale Sets-Dienst veröffentlicht wird.

1. Wählen Sie **Debuggen > Momentaufnahmedebugger anfügen** aus. Wählen Sie die Azure virtuelle Machine\Virtual VM-Skalierungsgruppe für Ihre Web-app bereitgestellt wird und ein Azure Storage-Konto, und klicken Sie dann auf **Anfügen**.

      ![Starten des Momentaufnahmedebuggers im Menü „Debuggen“](../debugger/media/snapshot-debug-menu-attach.png)

      ![Auswählen der Azure-Ressource](../debugger/media/snapshot-select-azure-resource-vm.png) 

    > [!IMPORTANT]
    > Wenn Sie **Momentaufnahmedebugger anfügen** zum ersten Mal für Ihren virtuellen Computer auswählen, wird IIS automatisch neu gestartet.
    > Die zum ersten Mal auswählen **Momentaufnahmedebugger Anfügen** für Ihre VM-Skalierungsgruppen, erfordert das manuelle Upgrade für jede Instanz von der Virtual Machine Scale Sets.

    Die Metadaten für die **Module** werden anfänglich nicht aktiviert; navigieren Sie zur Web-App, und die Schaltfläche **Sammlung starten** wird aktiv. Visual Studio ist jetzt im Modus des Debuggens von Momentaufnahmen.

   ![Modus des Debuggens von Momentaufnahmen](../debugger/media/snapshot-message.png)

    > [!NOTE]
    > Die Application Insights-Websiteerweiterung unterstützt auch das Debuggen von Momentaufnahmen. Wenn Sie eine „Websiteerweiterung veraltet“-Fehlermeldung erhalten, finden Sie unter [Problembehandlung und bekannte Probleme beim Debuggen von Momentaufnahmen in Visual Studio](../debugger/debug-live-azure-apps-troubleshooting.md) weitere Informationen zum Aktualisieren.
    > VM-skalierungsgruppen ist der Benutzer erforderlich, um die Instanzen in ihrer Virtual Machine Scale Sets manuell zu aktualisieren, nachdem Sie den Momentaufnahmedebugger anzufügen, zum ersten Mal.

   Die **Module** Fenster erfahren Sie, wenn alle Module für die Azure virtuelle Machine\Virtual VM-Skalierungsgruppe geladen wurden (Wählen Sie **Debuggen > Windows > Module** zum Öffnen des Fensters).

   ![Überprüfen des Fensters „Module“](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint"></a>Festlegen eines Andockpunkts

1. Klicken Sie im Code-Editor neben einer Codezeile, die Sie interessiert, auf den linken Bundsteg, um einen Andockpunkt festzulegen. Stellen Sie sicher, dass es sich um Code handelt, von dem Sie wissen, dass er ausgeführt wird.

   ![Festlegen eines Andockpunkts](../debugger/media/snapshot-set-snappoint.png)

1. Klicken Sie auf **Sammlung starten**, um den Andockpunkt zu aktivieren.

   ![Aktivieren des Andockpunkts](../debugger/media/snapshot-start-collection.png)

    > [!TIP]
    > Sie können nicht schrittweise vorgehen, wenn Sie eine Momentaufnahme anzeigen, aber Sie können mehrere Andockpunkte im Code platzieren, um die Ausführung auf verschiedenen Codezeilen zu verfolgen. Wenn Ihr Code mehrere Andockpunkte enthält, stellt der Momentaufnahmedebugger sicher, dass die zugehörigen Momentaufnahmen aus der gleichen Endbenutzersitzung stammen. Der Momentaufnahmedebugger leistet dies auch dann, wenn viele Benutzer Ihre App aufrufen.

## <a name="take-a-snapshot"></a>Momentaufnahme erstellen

Wenn ein Andockpunkt aktiviert ist, erfasst er eine Momentaufnahme, wenn die Codezeile ausgeführt wird, in der er platziert ist. Diese Ausführung kann von einer echten Anforderung auf dem Server verursacht werden. Damit Ihr Andockpunkt erreicht wird, wechseln Sie zur Browseransicht Ihrer Website, und führen Sie Aktionen durch, die sicher dazu führen, dass Ihr Andockpunkt erreicht wird.

## <a name="inspect-snapshot-data"></a>Überprüfen von Momentaufnahmedaten

1. Wenn der Andockpunkt erreicht wird, wird eine Momentaufnahme im Fenster „Diagnosetools“ angezeigt. Um dieses Fenster zu öffnen, wählen Sie **Debuggen > Fenster > Diagnosetools anzeigen** aus.

   ![Öffnen eines Andockpunkts](../debugger/media/snapshot-diagsession-window.png)

1. Doppelklicken Sie auf den Andockpunkt, um die Momentaufnahme im Code-Editor zu öffnen.

   ![Überprüfen von Momentaufnahmedaten](../debugger/media/snapshot-inspect-data.png)

   In dieser Ansicht können Sie den Cursor über Variablen platzieren, um DataTips anzuzeigen, die Fenster **Lokal**, **Überwachungen** und **Aufrufliste** verwenden und auch Ausdrücke auswerten.

    Die Website selbst ist noch aktiv, und Endbenutzer sind nicht betroffen. Standardmäßig wird pro Andockpunkt nur eine einzige Momentaufnahme erfasst: Nachdem eine Momentaufnahme erfasst wurde, wird der Andockpunkt deaktiviert. Wenn Sie eine andere Momentaufnahme an dem Andockpunkt erfassen möchten, können Sie den Andockpunkt durch Klicken auf **Sammlung aktualisieren** wieder aktivieren.

Sie können Ihrer App auch weitere Andockpunkte hinzufügen und sie mit der Schaltfläche **Sammlung aktualisieren** aktivieren.

**Benötigen Sie Hilfe?** Lesen Sie die Seiten [Problembehandlung und bekannte Probleme beim Debuggen von Momentaufnahmen in Visual Studio](../debugger/debug-live-azure-apps-troubleshooting.md) und [Häufig gestellte Fragen zum Debuggen von Momentaufnahmen in Visual Studio](../debugger/debug-live-azure-apps-faq.md).

## <a name="set-a-conditional-snappoint"></a>Festlegen eines bedingten Andockpunkts

Wenn es schwierig ist, einen bestimmten Status in Ihrer App neu herzustellen, überlegen Sie, ob die Verwendung eines bedingten Andockpunkts hilfreich sein kann. Bedingte Andockpunkte helfen Ihnen, zu vermeiden, eine Momentaufnahme zu erstellen, bevor die App in einen gewünschten Status wechselt, wenn z.B. eine Variable einen bestimmten Wert aufweist, den Sie untersuchen möchten. Sie können Bedingungen mithilfe von Ausdrücken, Filtern oder Trefferanzahl festlegen.

#### <a name="to-create-a-conditional-snappoint"></a>So erstellen Sie einen bedingten Andockpunkt

1. Klicken Sie mit der rechten Maustaste auf ein Andockpunktsymbol (die hohle Kugel), und wählen Sie **Einstellungen** aus.

   ![Einstellung auswählen](../debugger/media/snapshot-snappoint-settings.png)

1. Geben Sie im Fenster für Andockpunkteinstellungen einen Ausdruck ein.

   ![Eingeben eines Ausdrucks](../debugger/media/snapshot-snappoint-conditions.png)

   In der vorherigen Abbildung wird die Momentaufnahme nur dann für den Andockpunkt erstellt, wenn `visitor.FirstName == "Dan"`.

## <a name="set-a-logpoint"></a>Festlegen eines Protokollpunkts

Zusätzlich zum Erstellen einer Momentaufnahme, wenn ein Andockpunkt erreicht wird, können Sie auch einen Andockpunkt zum Protokollieren einer Meldung konfigurieren (d.h. einen Protokollpunkt erstellen). Sie können Protokollpunkte festlegen, ohne Ihre App erneut bereitstellen zu müssen. Protokollpunkte werden virtuell ausgeführt und verursachen weder direkte Auswirkungen auf Ihre ausgeführte Anwendung noch Nebeneffekte.

#### <a name="to-create-a-logpoint"></a>So erstellen Sie einen Protokollpunkt

1. Klicken Sie mit der rechten Maustaste auf ein Andockpunktsymbol (das blaue Sechseck), und wählen Sie **Einstellungen** aus.

1. Wählen Sie im Fenster für Andockpunkteinstellungen **Aktionen** aus.

    ![Erstellen eines Protokollpunkts](../debugger/media/snapshot-logpoint.png)

1. Im Feld **Meldung** können Sie die neue Protokollmeldung eingeben, die Sie protokollieren möchten. Sie können auch Variablen in der Protokollmeldung auswerten, indem Sie sie in geschweiften Klammern platzieren.

    Wenn Sie **An Ausgabefenster senden** auswählen, wenn der Protokollpunkt erreicht wird, wird die Meldung im Fenster „Diagnosetools“ angezeigt.

    ![Protokollpunktdaten im Fenster „Diagnosetools“](../debugger/media/snapshot-logpoint-output.png)

    Wenn Sie **An Anwendungsprotokoll senden** auswählen, wenn der Protokollpunkt erreicht wird, wird die Meldung an einer beliebigen Stelle angezeigt, wo Meldungen von `System.Diagnostics.Trace` (oder `ILogger` in .NET Core) angezeigt werden können, wie z.B. [App Insights](/azure/application-insights/app-insights-asp-net-trace-logs).

## <a name="next-steps"></a>Nächste Schritte

In diesem Tutorial haben Sie gelernt, den Momentaufnahmedebugger für Azure-VMs und Azure-VMSSs zu verwenden. Vielleicht wünschen Sie weitere Informationen zu diesem Feature.

> [!div class="nextstepaction"]
> [Häufig gestellte Fragen zum Debuggen von Momentaufnahmen](../debugger/debug-live-azure-apps-faq.md)
