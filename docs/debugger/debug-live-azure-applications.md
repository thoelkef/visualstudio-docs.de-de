---
title: "Debuggen von apps für live ASP.NET Azure - Visual Studio | Microsoft Docs"
ms.date: 12/06/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugger
ms.assetid: adb22512-4d4d-40e5-9564-1af421b7087e
caps.latest.revision: "1"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- aspnet
- azure
ms.openlocfilehash: 5317c06dc5ff6515627e562d576785c2ff25a98a
ms.sourcegitcommit: 5d43e9590e2246084670b79269cc9d99124bb3df
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/19/2018
---
# <a name="debug-live-aspnet-azure-apps-using-the-snapshot-debugger"></a>Debuggen von live ASP.NET Azure-apps, die mit dem Momentaufnahme-Debugger

Der Debugger Momentaufnahme nimmt eine Momentaufnahme Ihrer Anwendungen in Produktion, bei der Ausführung von Code, der Sie interessiert sind. Legen Sie Andockpunkte und Protokollpunkte in Ihrem Code fest, um den Debugger anzuweisen, eine Momentaufnahme zu erstellen. Der Debugger zeigt Fehler ohne Auswirkungen auf den Datenverkehr Ihrer Produktionsanwendung an. Der Momentaufnahmedebugger kann Sie dabei unterstützen, die Zeit zum Beheben von Fehlern, die in Produktionsumgebungen auftreten, erheblich zu reduzieren.

Snappoints und Logpoints ähneln Haltepunkte. Im Gegensatz zu Haltepunkten Snappoints nicht angehalten, die Anwendung bei Treffer. In der Regel wird die Erstellung einer Momentaufnahme für eine Snappoint 10 bis 20 Millisekunden. 

Die Momentaufnahmensammlung ist für folgende Web-Apps verfügbar, die in Azure App Service ausgeführt werden:

- ASP.NET-Apps, die in .NET Framework 4.6.1 oder höher ausgeführt werden.
- ASP.NET Core-Apps, die in .NET Core 2.0 oder höher unter Windows ausgeführt werden.

Darüber hinaus wird der Momentaufnahme-Debugger nur für Visual Studio 2017 Enterprise Version 15.5 oder höher und Basic "oder" höher App Service-Plänen verfügbar. 

## <a name="start-the-snapshot-debugger"></a>Starten Sie den Momentaufnahme-Debugger

1. Installieren Sie [Visual Studio 2017 Enterprise Version 15.5](https://www.visualstudio.com/downloads/) oder höher. Wenn Sie von einer vorherigen Installation von Visual Studio 2017 aktualisieren, führen Sie den Installer für Visual Studio, und überprüfen Sie die Snapshot-Debugger-Komponente in der arbeitsauslastung für ASP.NET und Entwicklung.

2. Öffnen Sie das Projekt, Momentaufnahme debuggen möchten. 

    > [!IMPORTANT] 
    > In der Reihenfolge nach Momentaufnahme Debuggen, müssen Sie öffnen die **dieselbe Version des Quellcodes** , die in Ihren Azure App Service veröffentlicht wird. 

3. In der Cloud-Explorer (Wählen Sie **Ansicht > Cloud Explorer**) mit der rechten Maustaste auf die Azure App Service, die für das Projekt bereitgestellt wird, und wählen **Snapshot-Debugger anfügen** um den Momentaufnahme-Debugger starten.

   ![Starten des Debuggers Momentaufnahme](../debugger/media/snapshot-launch.png "Starten des Debuggers Momentaufnahme")

    Die zum ersten Mal auswählen **Snapshot-Debugger anfügen**, Sie werden aufgefordert, den Momentaufnahme-Debugger websiteerweiterung für Ihren Azure App Service zu installieren. Diese Installation erfordert einen Neustart des Ihren Azure App Service. 

   Visual Studio ist jetzt im Debugmodus Momentaufnahme.

    > [!NOTE]
    > Die websiteerweiterung Application Insights unterstützt auch die Momentaufnahme zu debuggen. Wenn Sie eine Fehlermeldung "websiteerweiterung veraltet" auftreten, finden Sie unter [Problembehandlung, Tipps und bekannte Probleme für das Debuggen von Momentaufnahme](../debugger/debug-live-azure-apps-troubleshooting.md) zum Aktualisieren von Details.

   ![Momentaufnahme Debugmodus](../debugger/media/snapshot-message.png "Momentaufnahme Debugmodus")

   Die **Module** Fenster erfahren Sie, wenn alle Module geladen haben, für die Azure App Service (Wählen Sie **Debuggen / Windows / Module** zum Öffnen des Fensters).

   ![Überprüfen Sie das Fenster "Module"](../debugger/media/snapshot-modules.png "überprüfen Sie das Fenster "Module"")

## <a name="set-a-snappoint"></a>Legen Sie eine snappoint

1. Klicken Sie im linken Bundsteg neben einer Codezeile, die Sie einem Snappoint festzulegende interessiert sind, im Code-Editor. Stellen Sie sicher, dass es sich um Code handelt, die Sie kennen ausgeführt wird.

   ![Legen Sie eine Snappoint](../debugger/media/snapshot-set-snappoint.png "eine Snappoint festlegen")

2. Klicken Sie auf **Sammlung starten** um die Snappoint zu aktivieren.  

   ![Aktivieren Sie die Snappoint](../debugger/media/snapshot-start-collection.png "der Snappoint aktivieren")

    > [!TIP]
    > Sie können nicht schrittweise, wenn Sie eine Momentaufnahme anzeigen, aber Sie können mehrere Snappoints platzieren, im Code, um die Ausführung auf anderen Codezeilen folgen. Wenn Sie mehrere Snappoints in Ihrem Code verfügen, wird sichergestellt, dass der Momentaufnahme-Debugger die entsprechenden aus der gleichen Sitzung für die Endbenutzer sind auch wenn mehrere Benutzer, die Ihre app vorhanden sind.

## <a name="take-a-snapshot"></a>Erstellen Sie eine Momentaufnahme

Wenn ein Snappoint aktiviert ist, wird der eine Momentaufnahme erfasst werden immer ausgeführt wird, dass Sie die Codezeile, in denen die Snappoint platziert wird. Diese Ausführung kann von einer echten Anforderung auf dem Server verursacht werden. Um Ihre Snappoint auf Treffer zu erzwingen, können Sie auch zur Browseransicht, der Ihre Website, und ergreifen Sie alle Aktionen, die dazu führen, dass Ihre Snappoint auf Treffer zu überprüfenden erforderliche wechseln.

## <a name="inspect-snapshot-data"></a>Überprüfen von momentaufnahmedaten

1. Wenn die Snappoint erreicht wird, wird eine Momentaufnahme im Fenster "Diagnosetools" angezeigt. Wählen Sie **Debuggen / Windows / Diagnosetools anzeigen** zum Öffnen des Fensters.

   ![Öffnen Sie eine Snappoint](../debugger/media/snapshot-diagsession-window.png "eine Snappoint öffnen")

1. Doppelklicken Sie auf die Snappoint, um die Momentaufnahme im Code-Editor zu öffnen.

   ![Überprüfen Sie die momentaufnahmedaten](../debugger/media/snapshot-inspect-data.png "momentaufnahmedaten überprüfen")

   In dieser Ansicht können Sie Variablen verwenden Sie zum Anzeigen von DataTips zeigen die **"lokal"**, **Überwachungen**, und **Aufrufliste** Windows und auch Auswerten von Ausdrücken.

    Die Website selbst ist immer noch live und Endbenutzer sind nicht betroffen. Nur eine Momentaufnahme ist pro Snappoint standardmäßig erfasst: nach dem Erfassen einer Momentaufnahme der Snappoint deaktiviert. Wenn Sie eine andere Momentaufnahme auf die Snappoint aufzeichnen möchten, können Sie die Snappoint wieder aktivieren, indem Sie auf **Sammlung aktualisieren**.

Sie können auch weitere Snappoints der app hinzufügen und aktivieren Sie diese mithilfe der **Sammlung aktualisieren** Schaltfläche.

**Benötigen Sie Hilfe?** Finden Sie unter der [Problembehandlung und bekannte Probleme](../debugger/debug-live-azure-apps-troubleshooting.md) und [– häufig gestellte Fragen zum Debuggen von Momentaufnahme](../debugger/debug-live-azure-apps-faq.md) Seiten.

## <a name="set-a-conditional-snappoint"></a>Legen Sie eine bedingte snappoint

Ist es schwierig, die einen bestimmten Status in der app erneut erstellen, erwägen Sie, ob die Verwendung einer bedingten Snappoint helfen kann. Bedingte Snappoints können Sie vermeiden, bis die app wechselt in den gewünschten Zustand, eine Momentaufnahme erstellen, z. B. wenn eine Variable einen bestimmten Wert hat Sie sich interessieren. Sie können Bedingungen, die mithilfe von Ausdrücken, filtern, festlegen oder Trefferanzahlen.

#### <a name="to-create-a-conditional-snappoint"></a>So erstellen eine bedingte snappoint

1. Mit der rechten Maustaste ein Snappoint-Symbol (leeres Ball), und wählen Sie **Einstellungen**.

   ![Wählen Sie die Einstellungen](../debugger/media/snapshot-snappoint-settings.png "Einstellungen auswählen")

1. Geben Sie im Fenster für die Einstellungen von Snappoint einen Ausdruck ein.

   ![Geben Sie einen Ausdruck](../debugger/media/snapshot-snappoint-conditions.png "Geben Sie einen Ausdruck")

   In der vorherigen Abbildung wird die Momentaufnahme nur für die Snappoint erstellt beim `visitor.FirstName == "Dan"`.

## <a name="set-a-logpoint"></a>Legen Sie eine logpoint

Zusätzlich zum Erstellen einer Momentaufnahme aus, wenn eine Snappoint erreicht wird, können Sie auch eine Snappoint um eine Meldung Protokollieren konfigurieren (d. h. eine Logpoint erstellen). Sie können Logpoints festlegen, ohne die app erneut bereitstellen. Logpoints praktisch ausgeführt werden und verursacht keine Auswirkungen oder Nebeneffekte der laufenden Anwendung.

#### <a name="to-create-a-logpoint"></a>So erstellen eine logpoint

1. Mit der rechten Maustaste ein Snappoint-Symbol (die blaue Sechseck), und wählen Sie **Einstellungen**.

1. Wählen Sie im Fenster Snappoint **Aktionen**.

    ![Erstellen Sie eine Logpoint](../debugger/media/snapshot-logpoint.png "eine Logpoint erstellen")

1. Im Feld "Nachricht" können Sie die neue protokollmeldung eingeben, die protokolliert werden soll. Sie können auch Variablen in Ihrer protokollmeldung auswerten, indem sie in geschweiften Klammern platziert werden.

    Falls gewünscht **senden an das Fenster "Ausgabe"**, wenn die Logpoint die Meldung im Fenster "Diagnosetools" angezeigt erreicht wird,.

    ![Logpoint Daten in das Fenster ".diagsession"](../debugger/media/snapshot-logpoint-output.png "Logpoint-Daten in das Fenster ".diagsession"")

    Falls gewünscht **-Anwendungsprotokoll gesendet**, wenn die Logpoint erreicht wird, die Meldung wird an einer beliebigen Stelle angezeigt, Sie, dass Nachrichten vom sehen können `System.Diagnostics.Trace` (oder `ILogger` in .NET Core), wie z. B. [App Insights](/azure/application-insights/app-insights-asp-net-trace-logs).

## <a name="next-steps"></a>Nächste Schritte

- Gewusst wie: Überprüfen von Variablen beim Anzeigen einer Momentaufnahme finden Sie unter [Debugger Feature Tour](../debugger/debugger-feature-tour.md).
- Anzeigen der [– häufig gestellte Fragen zum Debuggen von Momentaufnahme](../debugger/debug-live-azure-apps-faq.md).
- Ansicht [Problembehandlung, Tipps und bekannte Probleme für das Debuggen von Momentaufnahme](../debugger/debug-live-azure-apps-troubleshooting.md).
- Wenn Sie möchten anzeigen von Momentaufnahmen im Application Insights, wenn Ihre app auf eine Ausnahme trifft, können Sie dies tun. Weitere Informationen finden Sie unter [Momentaufnahmen auf Ausnahmen in .NET apps Debuggen](/azure/application-insights/app-insights-snapshot-debugger). Application Insights unterstützt zusätzlich zu den Azure App Service Service Fabric-apps.
