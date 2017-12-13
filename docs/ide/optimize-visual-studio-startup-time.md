---
title: Optimieren der Leistung von Visual Studio | Microsoft-Dokumentation
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- startup time [Visual Studio]
- optimizing performance [Visual Studio]
- speed up start time [Visual Studio]
ms.assetid: d1508121-8499-4084-8eb5-fa89fa7b17d3
caps.latest.revision: "4"
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vs.performancecenter
ms.technology: vs-ide-general
ms.openlocfilehash: d1058ca5762db28f0afc678a9d31cc6f0f3be6bc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="optimize-visual-studio-performance"></a>Optimieren der Leistung von Visual Studio
Visual Studio wurde dafür entworfen, so schnell und effizient wie möglich zu starten. Das Laden bestimmter Visual Studio-Erweiterungen und -Toolfenster kann die Startzeit jedoch nachteilig beeinflussen. Sie können das Verhalten langsamer Erweiterungen und Toolfenster im Dialogfeld **Visual Studio-Leistung verwalten** steuern. Allgemeiner Tipps zum Verbessern der Leistung finden Sie unter [Visual Studio Performance Tips and Tricks (Tipps und Tricks zur Leistungssteigerung für Visual Studio)](../ide/visual-studio-performance-tips-and-tricks.md).  

## <a name="startup-behavior"></a>Startverhalten

Visual Studio 2017 lädt Erweiterungen mithilfe eines _bedarfsgesteuerten_ Ansatzes, um verlängerte Startzeiten zu vermeiden. Dieses Verhalten bedeutet, dass Erweiterungen nicht sofort nach dem Start von Visual Studio, sondern nach Bedarf geöffnet werden. Da Toolfenster, die in einer früheren Visual Studio-Sitzung offen gelassen wurden, die Startzeit verlängern können, öffnet Visual Studio Toolfenster auf intelligentere Weise, um Auswirkungen auf die Startzeit zu vermeiden.  

Wenn Visual Studio einen langsamen Start erkennt, wird eine Popupmeldung angezeigt, die Sie auf die Erweiterung oder das Toolfenster hinweist, die bzw. das für die Verzögerung verantwortlich ist. Die Meldung enthält einen Link zum Dialogfeld **Visual Studio-Leistung verwalten**. Sie können auf dieses Dialogfeld ebenfalls zugreifen, indem Sie in der Menüleiste auf **Hilfe** > **Visual Studio-Leistung verwalten** klicken.  

![„Visual Studio-Leistung verwalten“ – ein Popup, das meldet, dass eine Erweiterung Visual Studio verlangsamt](../ide/media/vside_perfdialog_popup.png)

Im Dialogfeld werden die Erweiterungen und Toolfenster aufgelistet, die sich auf die Startleistung auswirken. Sie können die Einstellungen für Erweiterungen und Toolfenster ändern, um die Leistung beim Start zu verbessern.  

## <a name="to-change-extension-settings-to-improve-startup-solution-load-and-typing-performance"></a>Ändern der Erweiterungseinstellungen zum Verbessern der Leistung des Startens, des Ladens von Projekten und der Eingabe

1. Öffnen Sie das Dialogfeld **Visual Studio-Leistung verwalten**, indem Sie in der Menüleiste auf **Hilfe** > **Visual Studio-Leistung verwalten** klicken.  

    Wenn eine Erweiterung den Start von Visual Studio, das Laden von Projektmappen oder die Eingabe verlangsamt, wird diese Erweiterung im Dialogfeld **Visual Studio-Leistung verwalten** unter **Erweiterungen** > **Start** (bzw. unter **Laden der Projektmappe** oder **Eingabe**) angezeigt.  

    ![„Visual Studio-Leistung verwalten“ – Ansicht der Erweiterungen](../ide/media/vside_perfdialog_extensions.png)

2. Wählen Sie die Erweiterung aus, die Sie deaktivieren möchten, und klicken Sie dann auf die Schaltfläche **Deaktivieren**.  

Sie können die Erweiterung jederzeit über den Erweiterungs-Manager oder das Dialogfeld „Visual Studio-Leistung verwalten“ für zukünftige Sitzungen wieder aktivieren.

## <a name="to-change-tool-window-settings-to-improve-startup-time"></a>Ändern der Einstellungen für Toolfenster zum Verbessern der Startzeit

1. Öffnen Sie das Dialogfeld **Visual Studio-Leistung verwalten**, indem Sie in der Menüleiste auf **Hilfe** > **Visual Studio-Leistung verwalten** klicken.  

    Wenn ein Toolfenster die Startzeit von Visual Studio verlangsamt, wird dieses im Dialogfeld **Visual Studio-Leistung verwalten** unter **Toolfenster** > **Start** angezeigt.  

2. Wählen Sie das Toolfenster aus, dessen Verhalten Sie ändern möchten.  

3. Wählen Sie eine der folgenden drei Optionen aus:    

    - **Standardverhalten verwenden:** Das Standardverhalten des Toolfensters. Wenn diese Option ausgewählt ist, wird die Startleistung nicht verbessert.  

    - **Fenster beim Start nicht anzeigen:** Das angegebene Toolfenster ist beim Öffnen von Visual Studio immer geschlossen, auch dann, wenn Sie es in einer früheren Sitzung offen gelassen hatten. Sie können das Toolfenster bei Bedarf über das entsprechende Menü öffnen.  
    
    - **Fenster beim Start automatisch ausblenden:** Wenn ein Toolfenster in einer früheren Sitzung offen gelassen wurde, bewirkt diese Option, dass die Gruppe des Toolfensters beim Start zugeklappt ist, um die Initialisierung des Toolfensters zu verhindern. Diese Option wird empfohlen, wenn Sie ein Toolfenster häufig verwenden. Das Toolfenster ist trotzdem verfügbar, wirkt sich aber nicht mehr negativ auf die Startzeit von Visual Studio aus.  

    ![„Visual Studio-Leistung verwalten“ – Ansicht des Toolfensters](../ide/media/vside_perfdialog_toolwindows.png)

## <a name="speed_up_solution_load"></a>Schnelleres Laden großer Projektmappen in Visual Studio 2017

Mit Visual Studio 2017 wird eine neue Funktion mit der Bezeichnung „Lightweight-Ladevorgang für Projektmappen“ eingeführt, mit der sich die erforderliche Zeit und der benötigte Arbeitsspeicher beim Laden von Projektmappen in der IDE verringern lassen. Wenn Sie mit einer großen Projektmappe arbeiten, die viele C#-, VB- oder C++-Projekte enthält, werden Sie wahrscheinlich eine deutlich verbesserte Leistung feststellen, wenn Sie den Lightweight-Ladevorgang für Projektmappen aktivieren. Ausführliche Informationen zu den Vorteilen, die Ihnen diese Funktion bieten könnte, finden Sie unter [Optimize Solution Loading in Visual Studio](../ide/optimize-solution-loading-in-visual-studio.md) (Optimieren des Ladens von Projektmappen in Visual Studio).

### <a name="enable-or-disable-lightweight-solution-load"></a>Aktivieren oder Deaktivieren der Funktion „Lightweight-Ladevorgang für Projektmappen“

Sie können mit der rechten Maustaste im Projektmappen-Explorer auf den Namen der Projektmappe klicken und **Laden der Lightweight-Lösung aktivieren** wählen. Nach Auswahl der Option müssen Sie die Projektmappe schließen und wieder öffnen, um „Lightweight-Ladevorgang für Projektmappen“ zu aktivieren.

![Projektmappen-Explorer](../ide/media/VSIDE_LSL_Solution_Setting.png)

Wie Sie globale Einstellungen für „Lightweight-Ladevorgang für Projektmappen“ konfigurieren, erfahren Sie unter [Optimize Solution Loading in Visual Studio](../ide/optimize-solution-loading-in-visual-studio.md#global_solution_load_settings) (Optimieren des Ladens von Projektmappen in Visual Studio)

## <a name="see-also"></a>Siehe auch
[Visual Studio Performance Tips and Tricks (Tipps und Tricks zur Leistungssteigerung für Visual Studio)](../ide/visual-studio-performance-tips-and-tricks.md)
