---
title: Startseite für den Momentaufnahmedebugger
ms.date: 07/14/2018
robots: noindex, nofollow
ms.topic: reference
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cf2aba33089623dc98a90c23166291bb2d6e7123
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62905255"
---
# <a name="getting-started-with-the-snapshot-debugger"></a>Erste Schritte mit dem Momentaufnahmedebugger

Die Snapshot-Debugger von Visual Studio ist jetzt mit Ihrem Dienst verbunden, und Sie können beginnen, das Sammeln von Momentaufnahmen, die beim Debuggen hilfreich sein.

Um die Snapshot-Debugger verwenden, legen Sie einige fangpunkte in Ihrem Code, klicken Sie auf die Schaltfläche, um zu beginnen, Erfassen von Momentaufnahmen, und führen Sie dann Ihr Szenario. Wenn der code führt in der Sie einen andockpunkt festgelegt haben, wird eine Momentaufnahme Ihrer Anwendung erstellt. Öffnen Sie dann die Momentaufnahme, indem Sie darauf klicken, in Visual Studio im Fenster "Diagnosetools". Sie können nun die Momentaufnahme von Ihrem Dienst debuggen, genau wie lokale war. Lesen Sie ausführliche Informationen erhalten Sie auf Weiter.

## <a name="collect-and-view-snapshots"></a>Erfassen und Anzeigen von Momentaufnahmen

Der Momentaufnahmedebugger erfasst Momentaufnahmen Ihrer Anwendung. Momentaufnahmen sind wie Bilder von Ihrem Application zu einem bestimmten Zeitpunkt. Sie mitteilen Visual Studio, wann und wo eine Momentaufnahme erfasst wird, indem Sie einen andockpunkt in Code festlegen. In der andockpunkt legen Sie die Bedingungen, die Sie benötigen, um sicherzustellen, dass Sie eine Momentaufnahme des Problems zu erhalten, die Sie untersuchen.

### <a name="set-a-snappoint"></a>Legen Sie einen Andockpunkt

1. Klicken Sie im linken Bundsteg neben einer Codezeile, die Sie interessieren, um einen andockpunkt festgelegt sind, im Code-Editor. Stellen Sie sicher, dass es sich um Code handelt, die Sie kennen ausgeführt wird.

    ![Festlegen einen andockpunkt im Editor](../media/snapshot-startpage-set-snappoint.png)

    Eine violette Sechseck wird angezeigt, in dem Sie auf der linken Seite klicken.

2. Klicken Sie auf **Sammlung starten**, um den Andockpunkt zu aktivieren.

### <a name="open-a-snapshot"></a>Öffnen Sie eine Momentaufnahme

1. Wenn die andockpunkt erreicht wird, wird eine Momentaufnahme im Fenster "Diagnosetools" auf der rechten Seite angezeigt. Wenn das Fenster geöffnet wird, können Sie es öffnen, indem Sie auswählen **Debuggen** > **Windows** > **Diagnosetools anzeigen**.

    ![Momentaufnahme im Fenster "Diagnosetools"](../media/snapshot-startpage-diagsession-window.png)

2. Doppelklicken Sie auf die Momentaufnahme, um ihn zu öffnen.

### <a name="inspect-snapshot-data"></a>Überprüfen von momentaufnahmedaten

In dieser Ansicht können Sie auf Variablen DataTips anzuzeigen, verwenden Sie die lokalen Variablen, Überwachungselemente, und rufen Sie zeigen, Aufrufliste und auch Auswerten von Ausdrücken.

Die Website selbst ist noch aktiv, und Endbenutzer sind nicht betroffen. Standardmäßig wird nur eine Momentaufnahme pro andockpunkt erfasst. Nachdem eine Momentaufnahme erfasst wurde, wird der andockpunkt, also deaktiviert. Wenn Sie eine andere Momentaufnahme an dem Andockpunkt erfassen möchten, können Sie den Andockpunkt durch Klicken auf **Sammlung aktualisieren** wieder aktivieren.

### <a name="set-a-logpoint"></a>Legen Sie eine Protokollpunkt

1. Mit der rechten Maustaste ein andockpunkt-Symbol (Lila Sechseck), und wählen Sie **Einstellungen**.

2. In der **Andockpunkt Einstellungen** wählen Sie im Fenster **Aktionen**.

    ![Andockpunkt Bedingungen](../media/snapshot-startpage-logpoint.png)

3. In der **Nachricht** Geben Sie eine protokollmeldung, die Sie protokollieren möchten. Sie können auch Variablen in der Protokollmeldung auswerten, indem Sie sie in geschweiften Klammern platzieren.

    Auf Wunsch **an Ausgabefenster senden**, die Meldung im Fenster "Diagnosetools" angezeigt, wenn die protokollpunkt erreicht wird.

    Auf Wunsch **an Anwendungsprotokoll senden**, die Meldung angezeigt, dass Sie Meldungen anzuzeigen, können an einer beliebigen Stelle wird `System.Diagnostics.Trace` (oder `ILogger` in .NET Core), z. B. Application Insights, wenn die protokollpunkt erreicht wird.

## <a name="learn-more"></a>Weitere Informationen

Weitere Informationen zum Debugger für Momentaufnahmen finden Sie auf die [Dokumentationsseite](../debug-live-azure-applications.md). Weitere Informationen finden Sie Informationen zum Festlegen von Bedingungen zu erleichtern, Fehler zu finden.

## <a name="dont-show-me-this-again"></a>Diese Meldung nicht mehr anzeigen

Um nie die Snapshot-Debugger-Startseite erneut anzuzeigen, wenn Sie die Snapshot-Debugger eine Verbindung herstellen, ändern Sie die **"Erste Schritte" die Seite beim sitzungsstart anzeigen** option **Tools**  >   **Optionen** > **Momentaufnahmedebugger**.

![Snapshot Debugger-Tool-Optionsseite](../media/snapshot-startpage-tools-options.png)
