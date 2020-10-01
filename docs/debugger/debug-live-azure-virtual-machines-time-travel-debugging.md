---
title: Zeitreisedebuggen in Echtzeit von ASP.NET auf einer Azure-VM
description: Es wird beschrieben, wie Sie ASP.NET-Live-Apps auf virtuellen Azure-Computern mit dem Momentaufnahmedebugger aufzeichnen und wiedergeben.
ms.custom: SEO-VS-2020
ms.date: 04/11/2019
ms.topic: how-to
helpviewer_keywords:
- debugger
author: poppastring
ms.author: madownie
manager: andster
monikerRange: '>= vs-2019'
ms.workload:
- aspnet
- azure
ms.openlocfilehash: eb0db0bab5295925f71a81645e64fdeb5f2077df
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809569"
---
# <a name="record-and-replay-live-aspnet-apps-on-azure-virtual-machines-using-the-snapshot-debugger"></a>Aufzeichnen und Wiedergeben von ASP.NET-Live-Apps auf virtuellen Azure-Computern mit dem Momentaufnahmedebugger

Die Vorschauversion des „Zeitreisedebuggen“-Tools (Time Travel Debugging, TTD) in Visual Studio Enterprise ermöglicht das Aufzeichnen einer Web-App, die auf einem virtuellen Azure-Computer (VM) ausgeführt wird, und die anschließende präzise Rekonstruierung und Wiedergabe des Ausführungspfads. TTD wird mit dem Momentaufnahmedebugger integriert und ermöglicht Ihnen das wiederholte Zurückspulen und Wiedergeben jeder einzelnen Codezeile. Dies ist hilfreich, um Probleme zu isolieren und zu identifizieren, die unter Umständen nur in Produktionsumgebungen auftreten.

Beim Erfassen einer TTD-Aufzeichnung wird die Anwendung nicht angehalten. Durch die TTD-Aufzeichnung erhöht sich der Aufwand für Ihren ausgeführten Prozess erheblich, und er wird basierend auf Faktoren wie Prozessgröße und Anzahl aktiver Threads verlangsamt.

Dieses Feature befindet sich für das Release von Visual Studio 2019 mit einer Aktivierungslizenz in der Vorschauphase.

In diesem Tutorial werden Sie Folgendes durchführen:

> [!div class="checklist"]
> * Starten des Momentaufnahmedebuggers mit aktiviertem Time Travel Debugging
> * Festlegen eines Andockpunkts und Erfassen der Aufzeichnung einer Zeitreise
> * Starten des Debugvorgangs für die Aufzeichnung einer Zeitreise

## <a name="prerequisites"></a>Voraussetzungen

* Time Travel Debugging für virtuelle Azure-Computer (VM) ist nur für Visual Studio 2019 Enterprise oder höher mit der **Workload „Azure-Entwicklung“** verfügbar. (Auf der Registerkarte **Einzelne Komponenten** finden Sie ihn unter **Debuggen und Testen** > **Momentaufnahmedebugger**.)

    Installieren Sie [Visual Studio 2019 Enterprise](https://visualstudio.microsoft.com/vs/), falls Sie dies noch nicht durchgeführt haben.

* Time Travel Debugging ist für die folgenden Azure-VM-Web-Apps verfügbar:
  * ASP.NET-Anwendungen (AMD64), die unter .NET Framework 4.8 oder höher ausgeführt werden.

## <a name="start-the-snapshot-debugger-with-time-travel-debugging-enabled"></a>Starten des Momentaufnahmedebuggers mit aktiviertem Time Travel Debugging

1. Öffnen Sie das Projekt, für das Sie die Aufzeichnung einer Zeitreise erfassen möchten.

    > [!IMPORTANT]
    > Zum Starten von TTD müssen Sie *dieselbe Version des Quellcodes* öffnen, die für Ihren Azure-VM-Dienst veröffentlicht wird.

1. Wählen Sie **Debuggen > Momentaufnahmedebugger anfügen** aus. Wählen Sie die Azure-VM, auf der Ihre Web-App bereitgestellt wurde, und ein Azure-Speicherkonto aus. Wählen Sie die Vorschauoption **Time Travel Debugging aktivieren** aus, und klicken Sie anschließend auf **Anfügen**.

      ![Auswählen der Azure-Ressource](../debugger/media/time-travel-debugging-select-azure-resource-vm.png)

    > [!IMPORTANT]
    > Wenn Sie **Momentaufnahmedebugger anfügen** zum ersten Mal für Ihren virtuellen Computer auswählen, wird IIS automatisch neu gestartet.

    Die Metadaten für die **Module** sind anfänglich nicht aktiviert. Navigieren Sie zur Web-App. Die Schaltfläche **Sammlung starten** wird aktiviert. Visual Studio ist jetzt im Modus des Debuggens von Momentaufnahmen.

   ![Modus des Debuggens von Momentaufnahmen](../debugger/media/snapshot-message.png)

    > [!NOTE]
    > Die Application Insights-Websiteerweiterung unterstützt auch das Debuggen von Momentaufnahmen. Wenn Sie eine „Websiteerweiterung veraltet“-Fehlermeldung erhalten, finden Sie unter [Problembehandlung und bekannte Probleme beim Debuggen von Momentaufnahmen in Visual Studio](../debugger/debug-live-azure-apps-troubleshooting.md) weitere Informationen zum Aktualisieren.

   Im Fenster **Module** sehen Sie, ob alle Module für die Azure-VM geladen wurden (wählen Sie **Debuggen > Fenster > Module** zum Öffnen des Fensters aus).

   ![Überprüfen des Fensters „Module“](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint-and-collect-a-time-travel-recording"></a>Festlegen eines Andockpunkts und Erfassen der Aufzeichnung einer Zeitreise

1. Klicken Sie im Code-Editor für eine Methode, die Sie interessiert, auf den linken Bundsteg, um einen Andockpunkt festzulegen. Stellen Sie sicher, dass es sich um Code handelt, von dem Sie wissen, dass er ausgeführt wird.

   ![Festlegen eines Andockpunkts](../debugger/media/time-travel-debugging-set-snappoint-settings.png)

1. Klicken Sie mit der rechten Maustaste auf das Andockpunktsymbol (nicht ausgefüllte Kugel), und wählen Sie **Aktionen** aus. Klicken Sie im Fenster **Momentaufnahmeeinstellungen** auf das Kontrollkästchen **Aktion**. Klicken Sie anschließend auf das Kontrollkästchen **Erfassen Sie eine Ablaufverfolgung per Zeitreise bis zum Ende dieser Methode**.

   ![Erfassen Sie eine Ablaufverfolgung per Zeitreise bis zum Ende dieser Methode](../debugger/media/time-travel-debugging-set-snappoint-action.png)

1. Klicken Sie auf **Sammlung starten**, um den Andockpunkt zu aktivieren.

   ![Aktivieren des Andockpunkts](../debugger/media/snapshot-start-collection.png)

## <a name="take-a-snapshot"></a>Momentaufnahme erstellen

Wenn ein Andockpunkt aktiviert ist, erfasst er jeweils eine Momentaufnahme, sobald die dem Andockpunkt zugeordnete Codezeile ausgeführt wird. Diese Ausführung kann durch eine echte Anforderung auf dem Server verursacht werden. Damit Ihr Andockpunkt erreicht wird, wechseln Sie zur Browseransicht Ihrer Website, und führen Sie Aktionen durch, die sicher dazu führen, dass Ihr Andockpunkt erreicht wird.

## <a name="start-debugging-a-time-travel-recording"></a>Starten des Debugvorgangs für die Aufzeichnung einer Zeitreise

1. Wenn der Andockpunkt erreicht wird, wird eine Momentaufnahme im Fenster „Diagnosetools“ angezeigt. Um dieses Fenster zu öffnen, wählen Sie **Debuggen > Fenster > Diagnosetools anzeigen** aus.

   ![Öffnen eines Andockpunkts](../debugger/media/snapshot-diagsession-window.png)

1. Klicken Sie auf den Link „Momentaufnahme anzeigen“, um die Aufzeichnung der Zeitreise im Code-Editor zu öffnen.
  
   Sie können jede Codezeile ausführen, die mit TTD aufgezeichnet wird, indem Sie die Schaltflächen **Weiter** und **In umgekehrter Richtung fortsetzen** verwenden. Sie können in der Symbolleiste **Debuggen** auch die Optionen **Nächste Anweisung anzeigen**, **Hineinspringen**, **Überspringen**, **Herausspringen**, **Einzelschritt zurück**, **Prozedurschritt zurück** und **Rücksprung zurück** verwenden.

   ![Debugging starten](../debugger/media/time-travel-debugging-step-commands.png)

   Sie können auch die Fenster **Lokal**, **Überwachungselemente** und **Aufrufliste** nutzen und Ausdrücke auswerten.

   ![Überprüfen von Momentaufnahmedaten](../debugger/media/time-travel-debugging-start-debugging.png)

    Die Website selbst befindet sich weiterhin im Livezustand, und Endbenutzer werden durch nachfolgende TTD-Aktivitäten nicht beeinträchtigt. Standardmäßig wird pro Andockpunkt nur eine einzige Momentaufnahme erfasst: Nachdem eine Momentaufnahme erfasst wurde, wird der Andockpunkt deaktiviert. Wenn Sie eine andere Momentaufnahme an dem Andockpunkt erfassen möchten, können Sie den Andockpunkt durch Klicken auf **Sammlung aktualisieren** wieder aktivieren.

**Benötigen Sie Hilfe?** Lesen Sie die Seiten [Problembehandlung und bekannte Probleme beim Debuggen von Momentaufnahmen in Visual Studio](../debugger/debug-live-azure-apps-troubleshooting.md) und [Häufig gestellte Fragen zum Debuggen von Momentaufnahmen in Visual Studio](../debugger/debug-live-azure-apps-faq.md).

## <a name="set-a-conditional-snappoint"></a>Festlegen eines bedingten Andockpunkts

Wenn es schwierig ist, einen bestimmten Status in Ihrer App neu herzustellen, überlegen Sie, ob die Verwendung eines bedingten Andockpunkts hilfreich sein kann. Bedingte Andockpunkte helfen Ihnen, die Erfassung der Aufzeichnung einer Zeitreise zu vermeiden, bevor die App in einen gewünschten Status wechselt. Dies kann beispielsweise der Fall sein, wenn eine Variable einen bestimmten Wert aufweist, den Sie untersuchen möchten. [Sie können Bedingungen mithilfe von Ausdrücken, Filtern oder Trefferanzahl festlegen](../debugger/debug-live-azure-apps-troubleshooting.md).

## <a name="next-steps"></a>Nächste Schritte

In diesem Tutorial wurde beschrieben, wie Sie für virtuelle Azure-Computer die Aufzeichnung einer Zeitreise erfassen. Informieren Sie sich weiter über den Momentaufnahmedebugger.

> [!div class="nextstepaction"]
> [Häufig gestellte Fragen zum Debuggen von Momentaufnahmen](../debugger/debug-live-azure-apps-faq.md)