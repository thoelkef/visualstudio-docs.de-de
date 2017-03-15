---
title: Optimieren der Startzeit von Visual Studio | Microsoft-Dokumentation
ms.custom: 
ms.date: 01/09/2016
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
translationtype: Human Translation
ms.sourcegitcommit: ba88bad0753653dcde8a4d28b4dd1c71522d6506
ms.openlocfilehash: 435197f1536dc9006691c0f2e58fafd0fcf27718
ms.lasthandoff: 02/22/2017

---
# <a name="optimize-visual-studio-startup-time"></a>Optimieren der Startzeit von Visual Studio
Im Idealfall sollte Visual Studio immer so schnell wie möglich starten. Allerdings können sich Visual Studio-Erweiterungen und geöffnete Toolfenster negativ auf die Startzeit auswirken, da sie beim Start automatisch geladen werden. Im Fenster **Visual Studio-Leistung verwalten** können Sie nicht nur sehen, welche Erweiterungen und Funktionen sich auf die Visual Studio-Startzeit auswirken, sondern auch ihr Ladeverhalten festlegen, damit Sie mehr Kontrolle darüber haben, wie schnell Visual Studio gestartet wird.

## <a name="control-startup-behavior"></a>Steuern des Startverhaltens

Um das Verlängern der Startzeit zu verhindern, vermeidet Visual Studio 2017 RC das Laden von Erweiterungen beim Start mithilfe von Ladevorgängen bei Bedarf. Das bedeutet, dass Erweiterungen nicht sofort nach dem Start von Visual Studio, sondern erst später asynchron auf Bedarfsbasis geöffnet werden. Da Toolfenster, die in einer früheren Visual Studio-Sitzung offen gelassen wurden, die Startzeit verlängern können, öffnet Visual Studio Toolfenster auf intelligentere Weise, um Auswirkungen auf die Startzeit zu vermeiden.

Wenn Visual Studio einen langsamen Start erkennt, wird eine Popupmeldung angezeigt, die Sie auf die Erweiterung oder das Toolfenster hinweist, die bzw. das für die Verzögerung verantwortlich ist. Die Meldung enthält darüber hinaus eine Verknüpfung zum Dialogfeld **Visual Studio-Leistung verwalten**, in dem die Erweiterungen und Toolfenster aufgelistet sind, die sich auf die Leistung beim Start auswirken. In diesem Dialogfeld können Sie die Einstellungen für Erweiterungen und Toolfenster ändern, um die Leistung beim Start zu verbessern.

![Visual Studio-Leistung verwalten – Popup](../ide/media/vside_perfdialog_popup.PNG "Visual Studio-Leistung verwalten – Popup")

Das Dialogfeld **Visual Studio-Leistung verwalten** weist zwei Kategorien auf: **Erweiterungen** und **Toolfenster**.

### <a name="control-extensions"></a>Steuern von Erweiterungen
Wenn eine Erweiterung den Start von Visual Studio verlangsamt, wird die Erweiterung im Dialogfeld **Visual Studio-Leistung verwalten** angezeigt, wenn Sie einen der Erweiterungstypen auswählen. Wenn der Einfluss auf die Startzeit (der im Abschnitt **Auswirkungen** aufgelistet ist) inakzeptabel hoch ist, können Sie sich entscheiden, die Erweiterung beim Start immer zu deaktivieren, indem Sie die Schaltfläche **Deaktivieren** auswählen. Sie können die Erweiterung mithilfe des Erweiterungs-Managers oder des Dialogfelds „Visual Studio-Leistung verwalten“ für zukünftige Sitzungen wieder aktivieren.

![Visual Studio-Leistung verwalten – Erweiterungen](../ide/media/vside_perfdialog_extensions.PNG "Visual Studio-Leistung verwalten – Erweiterungen")

Über den Start von Erweiterungen beim Starten hinaus können Sie auch Erweiterungen deaktivieren, die beim Laden von Projektmappen oder bei Benutzereingaben geladen werden. Wählen Sie einfach das Szenario aus, um eine Liste der zugeordneten Erweiterungen anzuzeigen.

### <a name="control-tool-windows"></a>Steuern von Toolfenstern
Wenn der Start von Visual Studio durch ein Toolfenster verlangsamt wird, haben Sie die Wahl, ob Sie dessen Standardverhalten beibehalten (was keine Vorteile bei der Startgeschwindigkeit bringt) oder das Verhalten durch Auswahl einer von zwei Verhaltensweisen außer Kraft setzen:

- **Fenster beim Start nicht anzeigen:** Wenn Sie diese Option aktivieren, ist das angegebene Toolfenster beim Öffnen von Visual Studio immer geschlossen, auch, wenn Sie es in einer früheren Sitzung offen gelassen hatten. Sie können das Toolfenster über das Menü öffnen.
- **Fenster beim Start automatisch ausblenden:** Wenn ein Toolfenster in einer früheren Sitzung offen gelassen wurde, bewirkt die Aktivierung dieser Option, dass die Gruppe des Toolfensters beim Start eingeklappt ist, um die Initialisierung des Toolfensters zu verhindern. Dies ist eine gute Wahl, wenn Sie ein Toolfenster häufig verwenden, da das Toolfenster trotzdem verfügbar ist, sich aber nicht mehr negativ auf die Startzeit von Visual Studio auswirkt.

![Visual Studio-Leistung verwalten – Toolfenster](../ide/media/vside_perfdialog_toolwindows.PNG "Visual Studio-Leistung verwalten – Toolfenster")

Wenn Sie Ihre Meinung zu einem späteren Zeitpunkt ändern, können Sie jede dieser Optionen im Dialogfeld **Visual Studio-Leistung verwalten** zurücksetzen. Um das Dialogfeld **Visual Studio-Leistung verwalten** zu öffnen, wählen Sie **Hilfe**, **Visual Studio-Leistung verwalten** aus.

## <a name="speed-up-solution-load"></a>Beschleunigen des Ladens von Projektmappen

Mit Visual Studio 2017 RC wird eine neue Funktion mit der Bezeichnung **Lightweight-Ladevorgang für Projektmappen** eingeführt, mit der sich die erforderliche Zeit und der benötigte Arbeitsspeicher beim Laden von Projektmappen in der IDE verringern lassen. Wenn Sie mit einer großen Projektmappe arbeiten, die viele C#-, VB- oder C++-Projekte enthält, werden Sie wahrscheinlich eine deutlich verbesserte Leistung feststellen, wenn Sie den Lightweight-Ladevorgang für Projektmappen aktivieren.

Da einige IDE-Funktionen bei aktiviertem Lightweight-Ladevorgang für Projektmappen nicht vollständig verfügbar sind, ist die Funktion standardmäßig deaktiviert. Die folgenden Abschnitte geben Ihnen Hilfestellung bei der Entscheidung, ob Sie diese Funktion aktivieren sollen.

### <a name="enable-lightweight-solution-load"></a>Aktivieren des Lightweight-Ladevorgangs für Projektmappen

Sie können den Lightweight-Ladevorgang für Projektmappen für die gesamte IDE oder für einzelne Projektmappen aktivieren. Um den Lightweight-Ladevorgang für Projektmappen für die gesamte IDE zu aktivieren, wechseln Sie zu **Tools**, **Optionen**, und navigieren Sie dann zum Abschnitt **Projekte und Projektmappen**.

![Dialogfeld „Extras“ | „Optionen“](../ide/media/VSIDE_LightweightSolutionLoad.png)

Um den Lightweight-Ladevorgang für Projektmappen für eine einzelne Projektmappe zu aktivieren, wählen Sie im Projektmappen-Explorer den Projektmappenknoten der obersten Ebene aus.  Wählen Sie im Fenster „Eigenschaften“ einen der folgenden Werte für die Eigenschaft **Lightweight-Ladevorgang** aus.

- **Aktiviert:** Der Lightweight-Ladevorgang für Projektmappen ist für diese Projektmappe unabhängig von der IDE-weiten Einstellung aktiviert.
- **Deaktiviert:** Der Lightweight-Ladevorgang für Projektmappen ist für diese Lösung unabhängig von der IDE-weiten Einstellung deaktiviert.
- **Standard:** Das Lightweight-Ladeverhalten für Projektmappen entspricht der IDE-weiten Einstellung.

![Projektmappen-Explorer](../ide/media/VSIDE_LSL Solution Setting.png)

Wenn Sie die Einstellung für den Lightweight-Ladevorgang für Projektmappen ändern, wirkt sich die Änderung beim nächsten Laden der Projektmappe aus. Sie brauchen die IDE nicht neu zu starten.

### <a name="automatically-enable-lightweight-solution-load"></a>Automatisches Aktivieren des Lightweight-Ladevorgangs für Projektmappen

Wenn Sie eine umfangreiche Projektmappe in Visual Studio 2017 RC öffnen, sehen Sie möglicherweise eine Popupnachricht, die das Aktivieren des Lightweight-Ladevorgangs für Projektmappen anbietet. Die Nachricht wird nur für Projektmappen angezeigt, die viele C#-, VB- oder C++-Projekte enthalten. Wenn Sie den Befehl **Aktivieren** auswählen, wird der Lightweight-Ladevorgang für Projektmappen nur für die betreffende Projektmappe aktiviert. Die IDE-weite Einstellung wird nicht geändert.

![Popupfenster](../ide/media/VSIDE_LSL Popup.png)

Sie können den Lightweight-Ladevorgang für Projektmappen später im Fenster „Eigenschaften“ der Projektmappe deaktivieren.

### <a name="lightweight-solution-load-limitations"></a>Einschränkungen beim Lightweight-Ladevorgang für Projektmappen
Die meisten Funktionen der IDE stehen bei aktiviertem Lightweight-Ladevorgang für Projektmappen in vollem Umfang zur Verfügung. Allerdings sind möglicherweise einige IDE-Funktionen und Erweiterungen von Drittanbietern nicht vollständig kompatibel.  Die folgenden Features funktionieren bekanntermaßen nicht, wenn der Lightweight-Ladevorgang für Projektmappen aktiviert ist:

#### <a name="third-party-extensions"></a>Drittanbietererweiterungen
Einige Erweiterungen verhalten sich womöglich nicht wie erwartet, wenn das Laden einer Lightweight-Lösung aktiviert ist.

#### <a name="edit-and-continue"></a>Bearbeiten und Fortfahren
Bearbeiten und Fortfahren funktioniert nicht in Projekten, die beim Beginnen des Debuggens nicht geladen sind. Die in einem solchen Projekt enthaltenen Dateien sind schreibgeschützt, und es wird ein Fehler angezeigt, dass das Projekt nicht geladen wurde, wenn die Bearbeitung versucht wird.

#### <a name="f-support"></a>F#-Support
Wenn das Laden einer Lightweight-Lösung aktiviert ist, werden F#-Projekte möglicherweise nicht ordnungsgemäß erstellt und Symbole sind in „GoTo“ möglicherweise nicht uneingeschränkt verfügbar.

