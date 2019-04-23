---
title: Zeit Travel Debuggen live ASP.NET virtuellen Azure-Computern
description: Informationen Sie zum Aufzeichnen und Wiedergeben von live ASP.NET-Apps auf Azure Virtual Machines mit dem Momentaufnahmedebugger.
ms.custom: ''
ms.date: 04/11/2019
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
ms.openlocfilehash: d392e19bb51cd981cc833535556eb083e8e5ba07
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2019
ms.locfileid: "59672505"
---
# <a name="record-and-replay-live-aspnet-apps-on-azure-virtual-machines-using-the-snapshot-debugger"></a>Aufzeichnen und Wiedergeben von live ASP.NET-Apps auf Azure Virtual Machines mit dem Momentaufnahmedebugger

Die Vorschau Zeit Travel Debuggen (TTD) in Visual Studio Enterprise bietet die Möglichkeit, zeichnen eine Web-app, die auf einer Azure-Computer (VM) ausgeführt, und klicken Sie dann genau Nachbilden und den Ausführungspfad. TTD integriert sich in unsere Snapshot-Debugger bietet und ermöglicht Ihnen das Zurückspulen und Wiedergeben von jeder Zeile des Codes jedoch oft Sie möchten, helfen Sie isoliert und identifiziert Probleme, die nur in produktionsumgebungen auftreten können.

Erfassen eine Aufzeichnung TTD wird die Anwendung nicht angehalten, jedoch wird Aufzeichnung wesentlich höheren Leistungsaufwand beim Hinzufügen, um den ausgeführten Prozess, der basierend auf Faktoren, die die Process-Größe und die Anzahl der aktiven Threads enthalten verlangsamt.

Dieses Feature ist in der Vorschau für die Version von Visual Studio-2019 mit einer wechseln Sie live-Lizenz.

In diesem Tutorial werden Sie Folgendes durchführen:

> [!div class="checklist"]
> * Starten Sie den Snapshot-Debugger mit Time-Debuggen Travel aktiviert
> * Legen Sie einen andockpunkt und erfassen eine Zeitreise Aufzeichnung
> * Starten Sie Debuggen eine "Zeitreise" Aufzeichnung

## <a name="prerequisites"></a>Vorraussetzungen

* Time-Debuggen Travel für Azure Virtual Machines (VMs) ist nur verfügbar für Visual Studio 2019 Enterprise oder höher mit der **Azure-entwicklungsworkload**. (Auf der Registerkarte **Einzelne Komponenten** finden Sie ihn unter **Debuggen und Testen** > **Momentaufnahmedebugger**.)

    Wenn sie noch nicht installiert ist, installieren Sie [Visual Studio 2019 Enterprise](https://visualstudio.microsoft.com/vs/).

* Time-Debuggen Travel steht für die folgenden Azure-VM-Web-apps zur Verfügung:
  * ASP.NET-Anwendungen (AMD64) auf .NET Framework 4.8 oder höher ausgeführt wird.

## <a name="open-your-project-and-start-the-snapshot-debugger-with-time-travel-debugging-enabled"></a>Öffnen Sie das Projekt, und starten Sie den Snapshot-Debugger mit Time-Debuggen Travel aktiviert

1. Öffnen Sie das Projekt, das eine Aufzeichnung Zeitreise gesammelt werden sollen.

    > [!IMPORTANT]
    > Um TTD starten zu können, müssen Sie zum Öffnen der *dieselbe Version des Quellcodes* dar, mit dem Azure-VM-Dienst veröffentlicht wird.

1. Wählen Sie **Debuggen > Momentaufnahmedebugger anfügen** aus. Wählen Sie die Azure-VM, die für Ihre Web-app bereitgestellt wird und ein Azure Storage-Konto. Wählen Sie die **aktivieren die Time-Debuggen Travel** preview (Option), und klicken Sie dann auf **Anfügen**.

      ![Auswählen der Azure-Ressource](../debugger/media/time-travel-debugging-select-azure-resource-vm.png)

    > [!IMPORTANT]
    > Wenn Sie **Momentaufnahmedebugger anfügen** zum ersten Mal für Ihren virtuellen Computer auswählen, wird IIS automatisch neu gestartet.

    Die Metadaten für die **Module** werden anfänglich nicht aktiviert; navigieren Sie zur Web-App, und die Schaltfläche **Sammlung starten** wird aktiv. Visual Studio ist jetzt im Modus des Debuggens von Momentaufnahmen.

   ![Modus des Debuggens von Momentaufnahmen](../debugger/media/snapshot-message.png)

    > [!NOTE]
    > Die Application Insights-Websiteerweiterung unterstützt auch das Debuggen von Momentaufnahmen. Wenn Sie eine „Websiteerweiterung veraltet“-Fehlermeldung erhalten, finden Sie unter [Problembehandlung und bekannte Probleme beim Debuggen von Momentaufnahmen in Visual Studio](../debugger/debug-live-azure-apps-troubleshooting.md) weitere Informationen zum Aktualisieren.

   Die **Module** Fenster erfahren Sie, wenn alle Module für die Azure-VM geladen wurden (Wählen Sie **Debuggen > Windows > Module** zum Öffnen des Fensters).

   ![Überprüfen des Fensters „Module“](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint-and-collect-a-time-travel-recording"></a>Legen Sie einen andockpunkt und erfassen eine Zeitreise Aufzeichnung

1. Klicken Sie im Code-Editor im linken Bundsteg in einer Methode, die Sie interessieren, um einen andockpunkt festgelegt. Stellen Sie sicher, dass es sich um Code handelt, von dem Sie wissen, dass er ausgeführt wird.

   ![Festlegen eines Andockpunkts](../debugger/media/time-travel-debugging-set-snappoint-settings.png)

1. Mit der rechten Maustaste in des Symbol "andockpunkt" (der Ball), und wählen Sie **Aktionen**. Klicken Sie in das Fenster "Momentaufnahme" auf die **Aktion** Kontrollkästchen. Klicken Sie dann auf die **erfassen Sie eine Zeit Travel Ablaufverfolgung am Ende dieser Methode** Kontrollkästchen.

   ![Erfassen Sie eine Zeit Travel Ablaufverfolgung am Ende der Methode](../debugger/media/time-travel-debugging-set-snappoint-action.png)

1. Klicken Sie auf **Sammlung starten**, um den Andockpunkt zu aktivieren.

   ![Aktivieren des Andockpunkts](../debugger/media/snapshot-start-collection.png)

## <a name="take-a-snapshot"></a>Momentaufnahme erstellen

Wenn ein Andockpunkt aktiviert ist, erfasst er eine Momentaufnahme, wenn die Codezeile ausgeführt wird, in der er platziert ist. Diese Ausführung kann von einer echten Anforderung auf dem Server verursacht werden. Damit Ihr Andockpunkt erreicht wird, wechseln Sie zur Browseransicht Ihrer Website, und führen Sie Aktionen durch, die sicher dazu führen, dass Ihr Andockpunkt erreicht wird.

## <a name="start-debugging-a-time-travel-recording"></a>Starten Sie Debuggen eine "Zeitreise" Aufzeichnung

1. Wenn der Andockpunkt erreicht wird, wird eine Momentaufnahme im Fenster „Diagnosetools“ angezeigt. Um dieses Fenster zu öffnen, wählen Sie **Debuggen > Fenster > Diagnosetools anzeigen** aus.

   ![Öffnen eines Andockpunkts](../debugger/media/snapshot-diagsession-window.png)

1. Klicken Sie auf die Momentaufnahme anzeigen-Link, um die Zeitreise Aufzeichnung im Code-Editor zu öffnen.
  
   Sie können jede Codezeile, die von der TTD aufgezeichnet werden, mithilfe von Ausführen der **Weiter** und **Reverse weiterhin** Schaltflächen. Darüber hinaus die Debug-Symbolleiste kann nicht verwendet werden **nächste Anweisung anzeigen**, **Einzelschritt**, **Prozedurschritt**, **Ausführen bis Rücksprung**,  **Schritt wieder**, **wieder Prozedurschritt**, **Schritt zurückgehen**.

   ![Debugging starten](../debugger/media/time-travel-debugging-step-commands.png)

   Sie können auch die **"lokal"**, **Überwachungen**, und **Aufrufliste** Windows und auch Auswerten von Ausdrücken.

   ![Überprüfen von Momentaufnahmedaten](../debugger/media/time-travel-debugging-start-debugging.png)

    Die Website selbst noch aktiv ist, und Endbenutzer sind nicht von allen nachfolgenden Aktivitäten von TTD betroffen sind. Standardmäßig wird pro Andockpunkt nur eine einzige Momentaufnahme erfasst: Nachdem eine Momentaufnahme erfasst wurde, wird der Andockpunkt deaktiviert. Wenn Sie eine andere Momentaufnahme an dem Andockpunkt erfassen möchten, können Sie den Andockpunkt durch Klicken auf **Sammlung aktualisieren** wieder aktivieren.

**Benötigen Sie Hilfe?** Lesen Sie die Seiten [Problembehandlung und bekannte Probleme beim Debuggen von Momentaufnahmen in Visual Studio](../debugger/debug-live-azure-apps-troubleshooting.md) und [Häufig gestellte Fragen zum Debuggen von Momentaufnahmen in Visual Studio](../debugger/debug-live-azure-apps-faq.md).

## <a name="set-a-conditional-snappoint"></a>Festlegen eines bedingten Andockpunkts

Wenn es schwierig ist, einen bestimmten Status in Ihrer App neu herzustellen, überlegen Sie, ob die Verwendung eines bedingten Andockpunkts hilfreich sein kann. Bedingte andockpunkte helfen Ihnen das Sammeln von eine Zeitreise aufgezeichnet, bis die app wechselt in einen gewünschten Status, z. B. wenn eine Variable einen bestimmten Wert aufweist, den Sie untersuchen möchten. [Sie können die Bedingungen, die mithilfe von Ausdrücken, filtern, festlegen oder Trefferanzahlen](../debugger/debug-live-azure-apps-troubleshooting.md).

## <a name="next-steps"></a>Nächste Schritte

In diesem Tutorial haben Sie gelernt, wie eine Aufzeichnung Zeitreise für Azure Virtual Machines sammeln wird. Sie sollten, lesen Weitere Informationen zu Momentaufnahme-Debugger.

> [!div class="nextstepaction"]
> [Häufig gestellte Fragen zum Debuggen von Momentaufnahmen](../debugger/debug-live-azure-apps-faq.md)