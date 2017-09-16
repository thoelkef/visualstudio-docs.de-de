---
title: Optimieren der Startzeit von Visual Studio | Microsoft-Dokumentation
ms.custom: 
ms.date: 8/31/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- startup time [Visual Studio]
- optimizing startup time [Visual Studio]
- speed up start time [Visual Studio]
ms.assetid: d1508121-8499-4084-8eb5-fa89fa7b17d3
caps.latest.revision: 4
author: mikejo
ms.author: mikejo
manager: ghogen
f1_keywords:
- vs.performancecenter
ms.translationtype: HT
ms.sourcegitcommit: 4306111cd49a5299bfa5d4e5e22b212bc7799fe2
ms.openlocfilehash: 8e419de02104d30344b32e28174bd7de41f91677
ms.contentlocale: de-de
ms.lasthandoff: 09/06/2017

---

# <a name="optimize-visual-studio-startup-time"></a>Optimieren der Startzeit von Visual Studio
Im Idealfall sollte Visual Studio immer so schnell wie möglich starten. Allerdings können sich Visual Studio-Erweiterungen und geöffnete Toolfenster negativ auf die Startzeit auswirken, da sie beim Start automatisch geladen werden. Im Fenster **Visual Studio-Leistung verwalten** können Sie sehen, welche Erweiterungen und Features sich auf die Startzeit von Visual Studio auswirken, und das Ladeverhalten dieser Erweiterungen und Features steuern.

Allgemeiner Tipps zum Verbessern der Leistung finden Sie unter [Visual Studio Performance Tips and Tricks (Tipps und Tricks zur Leistungssteigerung für Visual Studio)](../ide/visual-studio-performance-tips-and-tricks.md).

## <a name="control-startup-behavior"></a>Steuern des Startverhaltens

Um das Verlängern der Startzeit zu verhindern, vermeidet Visual Studio 2017 das Laden von Erweiterungen beim Start mithilfe von Ladevorgängen bei Bedarf. Dieses Verhalten bedeutet, dass Erweiterungen nicht sofort nach dem Start von Visual Studio, sondern erst später und nach Bedarf geöffnet werden. Da Toolfenster, die in einer früheren Visual Studio-Sitzung offen gelassen wurden, die Startzeit verlängern können, öffnet Visual Studio Toolfenster auf intelligentere Weise, um Auswirkungen auf die Startzeit zu vermeiden.

Wenn Visual Studio einen langsamen Start erkennt, wird eine Popupmeldung angezeigt, die Sie auf die Erweiterung oder das Toolfenster hinweist, die bzw. das für die Verzögerung verantwortlich ist. Die Meldung enthält auch einen Link zum Dialogfeld **Visual Studio-Leistung verwalten**. Sie können dieses Fenster auch mit dem Menübefehl **Hilfe > Visual Studio-Leistung verwalten** öffnen.

![„Visual Studio-Leistung verwalten“ – ein Popup, das meldet, dass eine Erweiterung Visual Studio verlangsamt](../ide/media/vside_perfdialog_popup.png)

Im Dialogfeld werden die Erweiterungen und Toolfenster aufgelistet, die sich auf die Startleistung auswirken. In diesem Dialogfeld können Sie die Einstellungen für Erweiterungen und Toolfenster ändern, um die Leistung beim Start zu verbessern.

### <a name="change-extension-settings"></a>Ändern von Erweiterungseinstellungen

Sollte eine Erweiterung den Start von Visual Studio verlangsamen, wird die Erweiterung im Dialogfeld **Visual Studio-Leistung verwalten** angezeigt, wenn Sie einen der Erweiterungstypen auswählen. Das Dialogfeld zeigt, welche Erweiterungen sich auf die Leistung beim Start, beim Laden einer Lösung oder bei der Eingabe in den Editor auswirken.

![„Visual Studio-Leistung verwalten“ – Ansicht der Erweiterungen](../ide/media/vside_perfdialog_extensions.png)

Wenn die Auswirkungen beim Start, beim Laden einer Lösung oder bei der Eingabe nicht akzeptabel sind, deaktivieren Sie die Erweiterung für dieses Szenario, indem Sie auf die Schaltfläche **Deaktivieren** klicken. Sie können die Erweiterung jederzeit über den Erweiterungs-Manager oder das Dialogfeld „Visual Studio-Leistung verwalten“ für zukünftige Sitzungen wieder aktivieren.

### <a name="change-tool-window-settings"></a>Ändern der Einstellungen für Toolfenster

Wenn ein Toolfenster den Start von Visual Studio verlangsamt und Sie diese Auswirkung ändern möchten, können Sie das Verhalten des Fensters überschreiben, indem Sie statt **Standardverhalten verwenden** eine von zwei Optionen auswählen:

- **Fenster beim Start nicht anzeigen:** Das angegebene Toolfenster ist beim Öffnen von Visual Studio immer geschlossen, auch dann, wenn Sie es in einer früheren Sitzung offen gelassen hatten. Sie können das Toolfenster über das entsprechende Menü öffnen.
- **Fenster beim Start automatisch ausblenden:** Wenn ein Toolfenster in einer früheren Sitzung offen gelassen wurde, bewirkt diese Option, dass die Gruppe des Toolfensters beim Start zugeklappt ist, um die Initialisierung des Toolfensters zu verhindern. Diese Option eignet sich gut, wenn Sie ein Toolfenster häufig verwenden, da das Toolfenster trotzdem verfügbar ist, sich aber nicht mehr negativ auf die Startzeit von Visual Studio auswirkt.

![„Visual Studio-Leistung verwalten“ – Ansicht des Toolfensters](../ide/media/vside_perfdialog_toolwindows.png)

Sie können die Einstellung für jedes Toolfenster jederzeit diesem Dialogfeld ändern.

## <a name="speed_up_solution_load"></a>Schnelleres Laden großer Projektmappen in Visual Studio 2017

Mit Visual Studio 2017 wird eine neue Funktion mit der Bezeichnung „Lightweight-Ladevorgang für Projektmappen“ eingeführt, mit der sich die erforderliche Zeit und der benötigte Arbeitsspeicher beim Laden von Projektmappen in der IDE verringern lassen. Wenn Sie mit einer großen Projektmappe arbeiten, die viele C#-, VB- oder C++-Projekte enthält, werden Sie wahrscheinlich eine deutlich verbesserte Leistung feststellen, wenn Sie den Lightweight-Ladevorgang für Projektmappen aktivieren. Ausführliche Informationen zu den Vorteilen, die Ihnen diese Funktion bieten könnte, finden Sie unter [Optimize Solution Loading in Visual Studio](../ide/optimize-solution-loading-in-visual-studio) (Optimieren des Ladens von Projektmappen in Visual Studio).

> [!NOTE]
> Dieser Inhalt gilt für Visual Studio 2017 Update 3.

### <a name="enable-or-disable-lightweight-solution-load"></a>Aktivieren oder Deaktivieren der Funktion „Lightweight-Ladevorgang für Projektmappen“

Sie können mit der rechten Maustaste im Projektmappen-Explorer auf den Namen der Projektmappe klicken und **Laden der Lightweight-Lösung aktivieren** wählen. Nach Auswahl der Option müssen Sie die Projektmappe schließen und wieder öffnen, um „Lightweight-Ladevorgang für Projektmappen“ zu aktivieren.

![Projektmappen-Explorer](../ide/media/VSIDE_LSL_Solution_Setting.png)

Wie Sie globale Einstellungen für „Lightweight-Ladevorgang für Projektmappen“ konfigurieren, erfahren Sie unter [Optimize Solution Loading in Visual Studio](../ide/optimize-solution-loading-in-visual-studio.md#global_solution_load_settings) (Optimieren des Ladens von Projektmappen in Visual Studio)

## <a name="see-also"></a>Siehe auch
[Visual Studio Performance Tips and Tricks (Tipps und Tricks zur Leistungssteigerung für Visual Studio)](../ide/visual-studio-performance-tips-and-tricks.md)

