---
title: Optimieren der Startzeit von Visual Studio | Microsoft-Dokumentation
ms.custom: 
ms.date: 7/20/2017
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
author: kempb
ms.author: kempb
manager: ghogen
f1_keywords:
- vs.performancecenter
ms.translationtype: HT
ms.sourcegitcommit: 3037d92e9de377ab4b306a5a0e164e29fa6659e7
ms.openlocfilehash: 5448253ae93b82a2631e6c48495a31d2724ed0b7
ms.contentlocale: de-de
ms.lasthandoff: 08/07/2017

---

# <a name="optimize-visual-studio-startup-time"></a>Optimieren der Startzeit von Visual Studio
Im Idealfall sollte Visual Studio immer so schnell wie möglich starten. Allerdings können sich Visual Studio-Erweiterungen und geöffnete Toolfenster negativ auf die Startzeit auswirken, da sie beim Start automatisch geladen werden. Im Fenster **Visual Studio-Leistung verwalten** können Sie sehen, welche Erweiterungen und Features sich auf die Startzeit von Visual Studio auswirken, und das Ladeverhalten dieser Erweiterungen und Features steuern.

## <a name="control-startup-behavior"></a>Steuern des Startverhaltens

Um das Verlängern der Startzeit zu verhindern, vermeidet Visual Studio 2017 das Laden von Erweiterungen beim Start mithilfe von Ladevorgängen bei Bedarf. Dieses Verhalten bedeutet, dass Erweiterungen nicht sofort nach dem Start von Visual Studio, sondern erst später und nach Bedarf geöffnet werden. Da Toolfenster, die in einer früheren Visual Studio-Sitzung offen gelassen wurden, die Startzeit verlängern können, öffnet Visual Studio Toolfenster auf intelligentere Weise, um Auswirkungen auf die Startzeit zu vermeiden.

Wenn Visual Studio einen langsamen Start erkennt, wird eine Popupmeldung angezeigt, die Sie auf die Erweiterung oder das Toolfenster hinweist, die bzw. das für die Verzögerung verantwortlich ist. Die Meldung enthält einen Link zum Dialogfeld **Visual Studio-Leistung verwalten**, das auch über den Menübefehl **Hilfe > Visual Studio-Leistung verwalten** geöffnet werden kann.

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

## <a name="speed-up-solution-load"></a>Beschleunigen des Ladens von Projektmappen

Visual Studio 2017 unterstützt die Funktion **Lightweight-Ladevorgang für Projektmappen**, mit der sich die Dauer und die Arbeitsspeichermenge beim Laden von Projektmappen in die IDE verringern lassen. Wenn Sie mit einer umfangreichen Projektmappe arbeiten, die viele C#-, VB- und/oder C++-Projekte enthält, werden Sie mit dem Lightweight-Ladevorgang für Projektmappen wahrscheinlich eine deutlich verbesserte Leistung feststellen.

Da einige IDE-Funktionen bei aktiviertem Lightweight-Ladevorgang für Projektmappen nicht vollständig verfügbar sind, ist die Funktion standardmäßig deaktiviert. Die folgenden Abschnitte geben Ihnen Hilfestellung bei der Entscheidung, ob Sie dieses Feature aktivieren sollten.

### <a name="enable-lightweight-solution-load"></a>Aktivieren des Lightweight-Ladevorgangs für Projektmappen

Sie können den Lightweight-Ladevorgang für Projektmappen für die gesamte IDE oder für einzelne Projektmappen aktivieren.

Um den Lightweight-Ladevorgang für alle Projekte und Projektmappen zu ändern, wechseln Sie zu **Extras > Optionen > Projekte und Projektmappen > Allgemein**, und wählen Sie eine der folgenden drei Ladeoptionen aus:

![Dialogfeld „Extras“ | „Optionen“](../ide/media/VSIDE_LightweightSolutionLoad.png)

- **Visual Studio wählen lassen, was für meine Projektmappe am besten geeignet ist**: Visual Studio analysiert jede Projektmappe beim Öffnen und bestimmt so, ob der Lightweight-Ladevorgang für Projektmappen angewendet wird. 
- **Aktivieren:** Der Lightweight-Ladevorgang für Projektmappen ist für diese Projektmappe unabhängig von der IDE-weiten Einstellung aktiviert.
- **Deaktivieren:** Der Lightweight-Ladevorgang für Projektmappen ist für diese Lösung unabhängig von der IDE-weiten Einstellung deaktiviert.

Um den Lightweight-Ladevorgang für Projektmappen für eine einzelne Projektmappe zu aktivieren, wählen Sie im Projektmappen-Explorer den Projektmappenknoten der obersten Ebene aus. Wählen Sie im Fenster **Eigenschaften** eine der Optionen **Standard**, **Aktiviert** oder **Deaktiviert** für die Eigenschaft **Lightweight-Ladevorgang**.

![Projektmappen-Explorer](../ide/media/VSIDE_LSL Solution Setting.png)

Sie können auch im Projektmappen-Explorer mit der rechten Maustaste auf den Projektmappenknoten der obersten Ebene klicken und eine dieser Optionen wählen: **Lightweight-Ladevorgang für Projektmappen aktivieren** (wenn das Feature derzeit deaktiviert ist) oder **Lightweight-Ladevorgang für Projektmappen deaktivieren** (wenn das Feature derzeit aktiviert ist):

Wenn Sie die Einstellung für den Lightweight-Ladevorgang für Projektmappen ändern, wirkt sich die Änderung beim nächsten Laden der Projektmappe aus. Sie brauchen die IDE nicht neu zu starten.

### <a name="automatically-enable-lightweight-solution-load"></a>Automatisches Aktivieren des Lightweight-Ladevorgangs für Projektmappen

Wenn Sie eine umfangreiche Projektmappe in Visual Studio 2017 öffnen, sehen Sie möglicherweise eine Popupmeldung, die das Aktivieren des Lightweight-Ladevorgangs für Projektmappen anbietet. Die Meldung wird nur für Projektmappen angezeigt, die viele C#-, VB- oder C++-Projekte enthalten. Wenn Sie **Aktivieren** auswählen, wird der Lightweight-Ladevorgang nur für die betreffende Projektmappe aktiviert. Die IDE-weite Einstellung ändert sich nicht.

![Popupfenster](../ide/media/VSIDE_LSL Popup.png)

Sie können den Lightweight-Ladevorgang für Projektmappen später im Fenster **Eigenschaften** der Projektmappe deaktivieren.

### <a name="limitations"></a>Einschränkungen

Die meisten Funktionen der IDE stehen bei aktiviertem Lightweight-Ladevorgang für Projektmappen in vollem Umfang zur Verfügung. Allerdings sind möglicherweise einige IDE-Features und Erweiterungen von Drittanbietern nicht vollständig kompatibel.  Die folgenden Features funktionieren bekanntermaßen nicht, wenn der Lightweight-Ladevorgang für Projektmappen aktiviert ist:

- Einige Erweiterungen von Drittanbietern verhalten sich womöglich nicht wie erwartet, wenn der Ladevorgang für Projektmappen aktiviert ist.
- Bearbeiten und Fortfahren funktioniert nicht in Projekten, die beim Beginnen des Debuggens nicht geladen sind. Die in einem solchen Projekt enthaltenen Dateien sind schreibgeschützt, und beim Versuch einer Bearbeitung wird ein Fehler angezeigt, dass das Projekt nicht geladen wurde.
- Wenn das Laden einer Lightweight-Lösung aktiviert ist, werden F#-Projekte möglicherweise nicht ordnungsgemäß erstellt und Symbole sind in „GoTo“ möglicherweise nicht uneingeschränkt verfügbar.

