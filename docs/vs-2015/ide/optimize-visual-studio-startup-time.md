---
title: Optimieren der Startzeit von Visual Studio | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- startup time [Visual Studio]
- optimizing startup time [Visual Studio]
- speed up start time [Visual Studio]
ms.assetid: d1508121-8499-4084-8eb5-fa89fa7b17d3
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c2c31a67ac019435c5131a1ab33600d26c76f32d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47512827"
---
# <a name="optimize-visual-studio-startup-time"></a>Optimieren der Startzeit von Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Im Idealfall sollte Visual Studio immer so schnell wie möglich starten. Allerdings können sich Visual Studio-Erweiterungen und geöffnete Toolfenster negativ auf die Startzeit auswirken, da sie beim Start automatisch geladen werden. Im Fenster **Visual Studio-Leistung verwalten** können Sie nicht nur sehen, welche Erweiterungen und Funktionen sich auf die Visual Studio-Startzeit auswirken, sondern auch ihr Ladeverhalten festlegen, damit Sie mehr Kontrolle darüber haben, wie schnell Visual Studio gestartet wird.

## <a name="control-startup-behavior"></a>Steuern des Startverhaltens

Um verlängerte Startzeiten zu vermeiden, vermeidet Visual Studio "15" Laden von Erweiterungen beim Start mit einem Ansatz auf Bedarf geladen. Das bedeutet, dass Erweiterungen nicht sofort nach dem Start von Visual Studio, sondern erst später asynchron auf Bedarfsbasis geöffnet werden. Da Toolfenster, die in einer früheren Visual Studio-Sitzung offen gelassen wurden, die Startzeit verlängern können, öffnet Visual Studio Toolfenster auf intelligentere Weise, um Auswirkungen auf die Startzeit zu vermeiden.

Wenn Visual Studio einen langsamen Start erkennt, wird eine Popupmeldung angezeigt, die Sie auf die Erweiterung oder das Toolfenster hinweist, die bzw. das für die Verzögerung verantwortlich ist. Die Meldung enthält darüber hinaus eine Verknüpfung zum Dialogfeld **Visual Studio-Leistung verwalten**, in dem die Erweiterungen und Toolfenster aufgelistet sind, die sich auf die Leistung beim Start auswirken. In diesem Dialogfeld können Sie die Einstellungen für Erweiterungen und Toolfenster ändern, um die Leistung beim Start zu verbessern.

![Visual Studio-Leistung verwalten – Popup](../ide/media/vside-perfdialog-popup.PNG "Visual Studio-Leistung verwalten – Popup")

Das Dialogfeld **Visual Studio-Leistung verwalten** weist zwei Kategorien auf: **Erweiterungen** und **Toolfenster**.

### <a name="control-extensions"></a>Steuern von Erweiterungen
Wenn eine Erweiterung den Start von Visual Studio verlangsamt, wird die Erweiterung im Dialogfeld **Visual Studio-Leistung verwalten** angezeigt, wenn Sie einen der Erweiterungstypen auswählen. Wenn der Einfluss auf die Startzeit (der im Abschnitt **Auswirkungen** aufgelistet ist) inakzeptabel hoch ist, können Sie sich entscheiden, die Erweiterung beim Start immer zu deaktivieren, indem Sie die Schaltfläche **Deaktivieren** auswählen. Sie können die Erweiterung mithilfe des Erweiterungs-Managers oder des Dialogfelds „Visual Studio-Leistung verwalten“ für zukünftige Sitzungen wieder aktivieren.

![Visual Studio-Leistung verwalten – Erweiterungen](../ide/media/vside-perfdialog-extensions.PNG "Visual Studio-Leistung verwalten – Erweiterungen")

Über den Start von Erweiterungen beim Starten hinaus können Sie auch Erweiterungen deaktivieren, die beim Laden von Projektmappen oder bei Benutzereingaben geladen werden. Wählen Sie einfach das Szenario aus, um eine Liste der zugeordneten Erweiterungen anzuzeigen.

### <a name="control-tool-windows"></a>Steuern von Toolfenstern
Wenn der Start von Visual Studio durch ein Toolfenster verlangsamt wird, haben Sie die Wahl, ob Sie dessen Standardverhalten beibehalten (was keine Vorteile bei der Startgeschwindigkeit bringt) oder das Verhalten durch Auswahl einer von zwei Verhaltensweisen außer Kraft setzen:

- **Fenster beim Start nicht anzeigen:** Wenn Sie diese Option aktivieren, ist das angegebene Toolfenster beim Öffnen von Visual Studio immer geschlossen, auch, wenn Sie es in einer früheren Sitzung offen gelassen hatten. Sie können das Toolfenster über das Menü öffnen.
- **Fenster beim Start automatisch ausblenden:** Wenn ein Toolfenster in einer früheren Sitzung offen gelassen wurde, bewirkt die Aktivierung dieser Option, dass die Gruppe des Toolfensters beim Start eingeklappt ist, um die Initialisierung des Toolfensters zu verhindern. Dies ist eine gute Wahl, wenn Sie ein Toolfenster häufig verwenden, da das Toolfenster trotzdem verfügbar ist, sich aber nicht mehr negativ auf die Startzeit von Visual Studio auswirkt.

![Visual Studio-Leistung verwalten – Toolfenster](../ide/media/vside-perfdialog-toolwindows.PNG "Visual Studio-Leistung verwalten – Toolfenster")

Wenn Sie Ihre Meinung zu einem späteren Zeitpunkt ändern, können Sie jede dieser Optionen im Dialogfeld **Visual Studio-Leistung verwalten** zurücksetzen. Um das Dialogfeld **Visual Studio-Leistung verwalten** zu öffnen, wählen Sie **Hilfe**, **Visual Studio-Leistung verwalten** aus.


