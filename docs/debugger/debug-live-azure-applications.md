---
title: "Debuggen von apps für live ASP.NET Azure - Visual Studio | Microsoft Docs"
ms.description: Learn how to set snappoints and view snapshots with the Snapshot Debugger
ms.custom: mvc
ms.date: 03/16/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugger
ms.assetid: adb22512-4d4d-40e5-9564-1af421b7087e
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- aspnet
- azure
ms.openlocfilehash: d313dea17700d4e64d3156ee72ee15521111329b
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2018
---
# <a name="debug-live-aspnet-azure-apps-using-the-snapshot-debugger"></a>Debuggen von live ASP.NET Azure-apps, die mit dem Momentaufnahme-Debugger

Der Debugger Momentaufnahme nimmt eine Momentaufnahme Ihrer Anwendungen in Produktion, bei der Ausführung von Code, der Sie interessiert sind. Legen Sie Andockpunkte und Protokollpunkte in Ihrem Code fest, um den Debugger anzuweisen, eine Momentaufnahme zu erstellen. Der Debugger zeigt Fehler ohne Auswirkungen auf den Datenverkehr Ihrer Produktionsanwendung an. Der Momentaufnahmedebugger kann Sie dabei unterstützen, die Zeit zum Beheben von Fehlern, die in Produktionsumgebungen auftreten, erheblich zu reduzieren.

Snappoints und Logpoints sind Haltepunkte ähnlich, aber im Gegensatz zu Haltepunkten anhalten Snappoints nicht die Anwendung bei Treffer. In der Regel wird die Erstellung einer Momentaufnahme für eine Snappoint 10 bis 20 Millisekunden. 

Die Momentaufnahmensammlung ist für folgende Web-Apps verfügbar, die in Azure App Service ausgeführt werden:

- ASP.NET-Apps, die in .NET Framework 4.6.1 oder höher ausgeführt werden.
- ASP.NET Core-Apps, die in .NET Core 2.0 oder höher unter Windows ausgeführt werden.

Darüber hinaus wird der Momentaufnahme-Debugger nur für Visual Studio 2017 Enterprise Version 15.5 oder höher und Basic "oder" höher App Service-Plänen verfügbar. 

In diesem Lernprogramm führen Sie folgende Aktionen ausführen:

> [!div class="checklist"]
> * Starten Sie den Momentaufnahme-Debugger
> * Festlegen Sie einer Snappoint und zeigen Sie eine Momentaufnahme an.
> * Legen Sie eine logpoint

## <a name="start-the-snapshot-debugger"></a>Starten Sie den Momentaufnahme-Debugger

1. Installieren Sie [Visual Studio 2017 Enterprise Version 15.5](https://www.visualstudio.com/downloads/) oder höher. Wenn Sie von einer vorherigen Installation von Visual Studio 2017 aktualisieren, führen Sie den Installer für Visual Studio, und überprüfen Sie die Snapshot-Debugger-Komponente in der arbeitsauslastung für ASP.NET und Entwicklung.

2. Öffnen Sie das Projekt, Momentaufnahme debuggen möchten. 

    > [!IMPORTANT] 
    > Momentaufnahme Debuggen, müssen Sie öffnen die **dieselbe Version des Quellcodes** , die in Ihren Azure App Service veröffentlicht wird. 

3. In der Cloud-Explorer (**Ansicht > Cloud Explorer**) mit der rechten Maustaste auf die Azure App Service, die für das Projekt bereitgestellt wird, und wählen Sie **Snapshot-Debugger anfügen**.

   ![Starten Sie den Momentaufnahme-debugger](../debugger/media/snapshot-launch.png)

    Die zum ersten Mal auswählen **Snapshot-Debugger anfügen**, Sie werden aufgefordert, die websiteerweiterung Momentaufnahme Debugger auf Ihren Azure App Service zu installieren. Diese Installation erfordert einen Neustart des Ihren Azure App Service. 

   Visual Studio ist jetzt im Debugmodus Momentaufnahme.

    > [!NOTE]
    > Die websiteerweiterung Application Insights unterstützt auch die Momentaufnahme zu debuggen. Wenn Sie eine Fehlermeldung "websiteerweiterung veraltet" auftreten, finden Sie unter [Problembehandlung, Tipps und bekannte Probleme für das Debuggen von Momentaufnahme](../debugger/debug-live-azure-apps-troubleshooting.md) zum Aktualisieren von Details.

   ![Momentaufnahme-Debugmodus](../debugger/media/snapshot-message.png)

   Die **Module** Fenster erfahren Sie, wenn alle Module geladen haben, für die Azure App Service (Wählen Sie **Debuggen / Windows / Module** zum Öffnen des Fensters).

   ![Überprüfen Sie das Fenster "Module"](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint"></a>Legen Sie eine snappoint

1. Klicken Sie im linken Bundsteg neben einer Codezeile, die Sie einem Snappoint festzulegende interessiert sind, im Code-Editor. Stellen Sie sicher, dass es sich um Code handelt, die Sie kennen ausgeführt wird.

   ![Legen Sie eine snappoint](../debugger/media/snapshot-set-snappoint.png)

2. Klicken Sie auf **Sammlung starten** um die Snappoint zu aktivieren.  

   ![Aktivieren Sie die snappoint](../debugger/media/snapshot-start-collection.png)

    > [!TIP]
    > Sie können nicht schrittweise, wenn Sie eine Momentaufnahme anzeigen, aber Sie können mehrere Snappoints platzieren, im Code, um die Ausführung auf anderen Codezeilen folgen. Wenn Sie mehrere Snappoints in Ihrem Code verfügen, wird der Snapshot-Debugger sicher, dass die entsprechenden Momentaufnahmen aus der gleichen Sitzung für die Endbenutzer sind. Der Momentaufnahme-Debugger wird auch wenn viele Benutzer, die Ihre app vorhanden sind.

## <a name="take-a-snapshot"></a>Erstellen Sie eine Momentaufnahme

Wenn ein Snappoint aktiviert ist, wird der eine Momentaufnahme erfasst werden immer ausgeführt, wird die Codezeile, in denen die Snappoint platziert wird. Diese Ausführung kann von einer echten Anforderung auf dem Server verursacht werden. Zum Erzwingen der Snappoint erreicht, wechseln zur Browseransicht, Ihrer Website und keine Aktionen erforderlich, die dazu führen, dass Ihre Snappoint erreicht wird.

## <a name="inspect-snapshot-data"></a>Überprüfen von momentaufnahmedaten

1. Wenn die Snappoint erreicht wird, wird eine Momentaufnahme im Fenster "Diagnosetools" angezeigt. Um dieses Fenster zu öffnen, wählen Sie **Debuggen / Windows / Diagnosetools anzeigen**.

   ![Öffnen Sie eine snappoint](../debugger/media/snapshot-diagsession-window.png)

1. Doppelklicken Sie auf die Snappoint, um die Momentaufnahme im Code-Editor zu öffnen.

   ![Überprüfen von momentaufnahmedaten](../debugger/media/snapshot-inspect-data.png)

   In dieser Ansicht können Sie Variablen verwenden Sie zum Anzeigen von DataTips zeigen die **"lokal"**, **Überwachungen**, und **Aufrufliste** Windows und auch Auswerten von Ausdrücken.

    Die Website selbst noch aktiv ist, und Endbenutzer sind nicht betroffen. Nur eine Momentaufnahme ist pro Snappoint standardmäßig erfasst: nach dem Erfassen einer Momentaufnahme der Snappoint deaktiviert. Wenn Sie eine andere Momentaufnahme auf die Snappoint aufzeichnen möchten, können Sie die Snappoint wieder aktivieren, indem Sie auf **Sammlung aktualisieren**.

Sie können auch weitere Snappoints der app hinzufügen und aktivieren Sie diese mithilfe der **Sammlung aktualisieren** Schaltfläche.

**Benötigen Sie Hilfe?** Finden Sie unter der [Problembehandlung und bekannte Probleme](../debugger/debug-live-azure-apps-troubleshooting.md) und [– häufig gestellte Fragen zum Debuggen von Momentaufnahme](../debugger/debug-live-azure-apps-faq.md) Seiten.

## <a name="set-a-conditional-snappoint"></a>Legen Sie eine bedingte snappoint

Ist es schwierig, die einen bestimmten Status in der app erneut erstellen, erwägen Sie, ob die Verwendung einer bedingten Snappoint helfen kann. Bedingte Snappoints vermeiden Sie eine Momentaufnahme erstellen, bis die app wechselt in den gewünschten Zustand, beispielsweise wenn eine Variable einen bestimmten Wert besitzt, den Sie untersuchen möchten. Sie können Bedingungen, die mithilfe von Ausdrücken, filtern, festlegen oder Trefferanzahlen.

#### <a name="to-create-a-conditional-snappoint"></a>So erstellen eine bedingte snappoint

1. Mit der rechten Maustaste ein Snappoint-Symbol (leeres Ball), und wählen Sie **Einstellungen**.

   ![Wählen Sie die Einstellungen](../debugger/media/snapshot-snappoint-settings.png)

1. Geben Sie im Fenster für die Einstellungen von Snappoint einen Ausdruck ein.

   ![Geben Sie einen Ausdruck](../debugger/media/snapshot-snappoint-conditions.png)

   In der vorherigen Abbildung wird die Momentaufnahme nur für die Snappoint erstellt beim `visitor.FirstName == "Dan"`.

## <a name="set-a-logpoint"></a>Legen Sie eine logpoint

Zusätzlich zum Erstellen einer Momentaufnahme aus, wenn eine Snappoint erreicht wird, können Sie auch eine Snappoint um eine Meldung Protokollieren konfigurieren (d. h. eine Logpoint erstellen). Sie können Logpoints festlegen, ohne die app erneut bereitstellen. Logpoints praktisch ausgeführt werden und verursacht keine Auswirkungen oder Nebeneffekte der laufenden Anwendung.

#### <a name="to-create-a-logpoint"></a>So erstellen eine logpoint

1. Mit der rechten Maustaste ein Snappoint-Symbol (die blaue Sechseck), und wählen Sie **Einstellungen**.

1. Wählen Sie im Fenster Snappoint **Aktionen**.

    ![Erstellen Sie eine logpoint](../debugger/media/snapshot-logpoint.png)

1. Im Feld "Nachricht" können Sie die neue protokollmeldung eingeben, die protokolliert werden soll. Sie können auch Variablen in Ihrer protokollmeldung auswerten, indem sie in geschweiften Klammern platziert werden.

    Falls gewünscht **senden an das Fenster "Ausgabe"**, wenn die Logpoint die Meldung im Fenster "Diagnosetools" angezeigt erreicht wird,.

    ![Logpoint Daten im Fenster diagsession](../debugger/media/snapshot-logpoint-output.png)

    Falls gewünscht **-Anwendungsprotokoll gesendet**, wenn die Logpoint erreicht wird, die Meldung wird an einer beliebigen Stelle angezeigt, Sie, dass Nachrichten vom sehen können `System.Diagnostics.Trace` (oder `ILogger` in .NET Core), wie z. B. [App Insights](/azure/application-insights/app-insights-asp-net-trace-logs).

## <a name="next-steps"></a>Nächste Schritte

In diesem Lernprogramm haben Sie gelernt, wie der Momentaufnahme-Debugger verwendet wird. Sie möchten möglicherweise weitere Informationen zu diesem Feature gelesen.

> [!div class="nextstepaction"]
> [Häufig gestellte Fragen zum Debuggen von Momentaufnahmen](../debugger/debug-live-azure-apps-faq.md)
