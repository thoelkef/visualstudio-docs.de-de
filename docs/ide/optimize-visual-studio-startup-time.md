---
title: Verbessern der Uptime
ms.date: 11/15/2017
ms.topic: conceptual
helpviewer_keywords:
- startup time [Visual Studio]
- optimizing performance [Visual Studio]
- speed up start time [Visual Studio]
ms.assetid: d1508121-8499-4084-8eb5-fa89fa7b17d3
author: gewarren
ms.author: gewarren
manager: jillfra
f1_keywords:
- vs.performancecenter
ms.workload:
- multiple
ms.openlocfilehash: 22dcbcbf9a3506e3cd6c962b1f31ada24d5234e5
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/15/2019
ms.locfileid: "56315871"
---
# <a name="optimize-visual-studio-startup-time"></a>Verbessern der Startzeit von Visual Studio

Visual Studio wurde dafür entworfen, so schnell und effizient wie möglich zu starten. Das Laden bestimmter Visual Studio-Erweiterungen und -Toolfenster kann die Startzeit jedoch nachteilig beeinflussen. Sie können das Verhalten langsamer Erweiterungen und Toolfenster im Dialogfeld **Visual Studio-Leistung verwalten** steuern. Allgemeine Tipps zum Verbessern der Leistung finden Sie unter [Tipps und Tricks zur Leistungssteigerung für Visual Studio](../ide/visual-studio-performance-tips-and-tricks.md).

## <a name="startup-behavior"></a>Startverhalten

Visual Studio 2017 lädt Erweiterungen mithilfe eines _bedarfsgesteuerten_ Ansatzes, um verlängerte Startzeiten zu vermeiden. Dieses Verhalten bedeutet, dass Erweiterungen nicht sofort nach dem Start von Visual Studio, sondern nach Bedarf geöffnet werden. Da Toolfenster, die in einer früheren Visual Studio-Sitzung offen gelassen wurden, die Startzeit verlängern können, öffnet Visual Studio Toolfenster auf intelligentere Weise, um Auswirkungen auf die Startzeit zu vermeiden.

Wenn Visual Studio einen langsamen Start erkennt, wird eine Popupmeldung angezeigt, die Sie auf die Erweiterung oder das Toolfenster hinweist, die bzw. das für die Verzögerung verantwortlich ist. Die Meldung enthält einen Link zum Dialogfeld **Visual Studio-Leistung verwalten**. Sie können auf dieses Dialogfeld ebenfalls zugreifen, indem Sie in der Menüleiste auf **Hilfe** > **Visual Studio-Leistung verwalten** klicken.

![„Visual Studio-Leistung verwalten“ – ein Popup, das meldet, dass eine Erweiterung Visual Studio verlangsamt](../ide/media/vside_perfdialog_popup.png)

Im Dialogfeld werden die Erweiterungen und Toolfenster aufgelistet, die sich auf die Startleistung auswirken. Sie können die Einstellungen für Erweiterungen und Toolfenster ändern, um die Leistung beim Start zu verbessern.

## <a name="a-nameextensions-to-change-extension-settings-to-improve-startup-solution-load-and-typing-performance"></a><a name="extensions" />Ändern der Erweiterungseinstellungen zum Verbessern der Leistung des Startens, des Ladens von Projekten und der Eingabe

1. Öffnen Sie das Dialogfeld **Visual Studio-Leistung verwalten**, indem Sie in der Menüleiste auf **Hilfe** > **Visual Studio-Leistung verwalten** klicken.

    Wenn eine Erweiterung den Start von Visual Studio, das Laden von Projektmappen oder die Eingabe verlangsamt, wird diese Erweiterung im Dialogfeld **Visual Studio-Leistung verwalten** unter **Erweiterungen** > **Start** (bzw. unter **Laden der Projektmappe** oder **Eingabe**) angezeigt.

    ![„Visual Studio-Leistung verwalten“ – Ansicht der Erweiterungen](../ide/media/vside_perfdialog_extensions.png)

2. Wählen Sie die Erweiterung aus, die Sie deaktivieren möchten, und klicken Sie dann auf die Schaltfläche **Deaktivieren**.

Sie können die Erweiterung jederzeit über den **Erweiterungs-Manager** oder das Dialogfeld **Visual Studio-Leistung verwalten** für zukünftige Sitzungen wieder aktivieren.

## <a name="a-nametool-windows-to-change-tool-window-settings-to-improve-startup-time"></a><a name="tool-windows" />Ändern der Einstellungen für Toolfenster zum Verbessern der Startzeit

1. Öffnen Sie das Dialogfeld **Visual Studio-Leistung verwalten**, indem Sie in der Menüleiste auf **Hilfe** > **Visual Studio-Leistung verwalten** klicken.

    Wenn ein Toolfenster die Startzeit von Visual Studio verlangsamt, wird dieses im Dialogfeld **Visual Studio-Leistung verwalten** unter **Toolfenster** > **Start** angezeigt.

2. Wählen Sie das Toolfenster aus, dessen Verhalten Sie ändern möchten.

3. Wählen Sie eine der folgenden drei Optionen aus:

   - **Standardverfahren verwenden:** Das Standardverhalten für das Toolfenster. Wenn diese Option ausgewählt ist, wird die Startleistung nicht verbessert.

   - **Fenster beim Start nicht anzeigen:** Das angegebene Toolfenster ist beim Öffnen von Visual Studio immer geschlossen, auch dann, wenn Sie es in einer früheren Sitzung offen gelassen hatten. Sie können das Toolfenster bei Bedarf über das entsprechende Menü öffnen.

   - **Fenster beim Start automatisch ausblenden:** Wenn ein Toolfenster in einer früheren Sitzung offen gelassen wurde, bewirkt diese Option, dass die Gruppe des Toolfensters beim Start zugeklappt ist, um die Initialisierung des Toolfensters zu verhindern. Diese Option wird empfohlen, wenn Sie ein Toolfenster häufig verwenden. Das Toolfenster ist trotzdem verfügbar, wirkt sich aber nicht mehr negativ auf die Startzeit von Visual Studio aus.

     ![„Visual Studio-Leistung verwalten“ – Ansicht des Toolfensters](../ide/media/vside_perfdialog_toolwindows.png)

> [!NOTE]
> In einigen Visual Studio-Versionen vor Version 2017 war ein Feature namens **Lightweight-Ladevorgang für Projektmappen** integriert. Diese Funktion ist in Visual Studio 2017 Version 15.5 und höher nicht mehr enthalten. In Visual Studio Version 2017 Version 15.5 und höher laden große Projektmappen, die verwalteten Code enthalten, auch ohne den Lightweight-Ladevorgang für Projektmappen viel schneller als zuvor.

## <a name="see-also"></a>Siehe auch

- [Optimieren der Leistung von Visual Studio](../ide/optimize-visual-studio-performance.md)
- [Tipps und Tricks zur Leistungssteigerung für Visual Studio](../ide/visual-studio-performance-tips-and-tricks.md)
- [Blog zu Visual Studio: Schnelleres Laden von Projektmappen mit Visual Studio 2017 (Version 15.6)](https://devblogs.microsoft.com/visualstudio/load-solutions-faster-with-visual-studio-2017-version-15-6/)