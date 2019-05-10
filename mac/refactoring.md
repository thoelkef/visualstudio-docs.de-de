---
title: Umgestalten von Code (Refactoring)
description: Optimieren von Code mithilfe von Visual Studio für Mac und schnelle Aktionen.
author: conceptdev
ms.author: crdun
ms.date: 03/29/2019
ms.assetid: C7782BF3-016F-4B41-8A81-85FC540A1A8F
ms.custom: video
ms.openlocfilehash: 48e290fddd1c4b7c95ac5e76cb6cf5908247e6f6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62937839"
---
# <a name="refactoring"></a>Umgestaltung

Das Umgestalten von Code ist eine Möglichkeit, vorhandenen Code neu anzuordnen, neu zu strukturieren und zu verdeutlichen, wobei sichergestellt wird, dass das Gesamtverhalten des Codes nicht verändert wird.

Umgestalten erzeugt eine Codebasis mit weniger Fehlern, die für Sie oder andere Entwickler oder Benutzer, die möglicherweise auf den Code verweisen, besser verwendbar, lesbar und verwaltbar ist.

Die Integration in Roslyn, Microsofts Open Source-.NET Compilerplattform, von Visual Studio für Mac ermöglicht mehr Umgestaltungsvorgänge.

## <a name="renaming"></a>Umbenennen

Der Refactoringbefehl *Umbenennen* kann für jeden Codebezeichner (z.B. Klassenname, Eigenschaftenname usw.) verwendet werden, um alle Vorkommen dieses Bezeichners zu finden und zu ändern. Wenn Sie ein Symbol umbenennen möchten, klicken Sie mit der rechten Maustaste darauf, und wählen Sie **Umbenennen…** aus, oder Sie verwenden die Tastenzuordnung **CMD (⌘) + R**:

![Menüelement „Umbenennen“](media/refactoring-renaming1.png)

Dadurch werden das Symbol und sämtliche Verweise darauf hervorgehoben. Wenn Sie beginnen, einen neuen Namen einzugeben, werden automatisch alle Verweise in Ihrem Code geändert. Sie können die Fertigstellung der Umbenennung signalisieren, indem Sie die **EINGABETASTE** drücken:

![Umbenennen und Bezeichner](media/refactoring-renaming2.png)

## <a name="quick-actions"></a>Schnelle Aktionen

Mit schnellen Aktionen können Sie ganz leicht Code mit einer einzelnen Aktion umgestalten, generieren oder anderweitig ändern.

Schnelle Aktionen können für Folgendes verwendet werden:

* Anwenden einer Codefehlerbehebung für eine Verletzung einer Regel des Codeanalysetools
* Unterdrücken einer Verletzung einer Regel des Codeanalysetools
* Anwenden eines Refactorings (z.B. Inlinesetzen einer temporären Variable)
* Generieren von Code (z.B. Einführen einer lokalen Variable)

Schnelle Aktionen können angewendet werden, indem das Glühbirnen- ![Glühbirnensymbol](media/quick-actions-light-bulb-icon.png) oder Schraubendrehersymbol ![Schraubendrehersymbol](media/quick-actions-screwdriver-icon.png) verwendet oder **Option (⌥)**+**EINGABETASTE** gedrückt wird, wenn sich der Cursor auf einer Codezeile befindet, für die eine Aktion verfügbar ist. Es wird eine Glühbirne mit einem roten Warnzeichen ![Glühbirnensymbol](media/quick-actions-error-light-bulb-icon.png) angezeigt, was auf einen Fehler hindeutet, und in Visual Studio ist für diesen Fehler eine Problemlösung verfügbar.

Für jede Sprache können Drittanbieter benutzerdefinierte Diagnosen und Empfehlungen bereitstellen, beispielsweise als Bestandteil eines SDKs. Anhand dieser Regeln leuchten die Visual Studio-Glühbirnen dann auf.

### <a name="quick-action-icons"></a>Symbole für schnelle Aktionen
Das Symbol, das angezeigt wird, wenn eine schnelle Aktion verfügbar ist, erläutert den Typ der verfügbaren Fehlerkorrektur oder des Refactorings. Der *Schraubendreher* ![Schraubendrehersymbol](media/quick-actions-screwdriver-icon.png) gibt nur an, dass Aktionen für die Änderung des Codes verfügbar sind, Sie diese jedoch nicht unbedingt verwenden müssen. Die *gelbe Glühbirne* ![Symbol für gelbe Glühbirne](media/quick-actions-light-bulb-icon.png) zeigt, dass Aktionen verfügbar sind, die Sie *durchführen sollten*, um Ihren Code zu verbessern. Die *Glühbirne mit Warnzeichen* ![Symbol für Glühbirne mit Warnzeichen](media/quick-actions-error-light-bulb-icon.png) zeigt, dass eine Aktion verfügbar ist, die einen Fehler in Ihrem Code beheben kann.

### <a name="to-see-a-light-bulb-or-screwdriver"></a>So zeigen Sie eine Glühbirne oder einen Schraubendreher an

- Wenn eine Fehlerkorrektur verfügbar ist, erscheinen Glühbirnen spontan, wenn Sie mit der Maus auf die Position eines Fehlers zeigen.

   ![Glühbirne mit Mauszeigerbewegung](media/refactoring-lightbulb-hover.png)

- Glühbirnen und Schraubendreher werden im linken Rand des Editors angezeigt, wenn Sie das Caretzeichen in eine Codezeile verschieben, für die eine schnelle Aktion verfügbar ist.

- Drücken Sie **Option (⌥)**+**EINGABETASTE**, wenn sich der Cursor irgendwo auf einer Zeile befindet, damit eine Liste verfügbarer schneller Aktionen und Refactorings anzeigt wird.

![Anzeigen der Kontextelemente](media/refactoring-context-action.png)

Wenn Sie den Mauszeiger über beliebige Kontextaktionen bewegen, wird Ihnen eine Vorschau dessen angezeigt, was zu Ihrem Code hinzugefügt oder daraus entfernt wird.

![Kontextelemente Option + Enter](media/refactoring-image2a.png)

Um diese Optionen zu aktivieren, müssen Sie *Quellanalyse geöffneter Dateien aktivieren* in den Optionen **Visual Studio für Mac > Einstellungen > Texteditor > Quellanalyse** auswählen:

![Aktivieren der Quellanalyse](media/refactoring-options.png)

Es existieren mehr als 100 mögliche Aktionen, die vorgeschlagen werden können. Diese können aktiviert bzw. deaktiviert werden können, indem Sie zu **Visual Studio für Mac > Einstellungen > Quellanalyse > C# > Codeaktionen** navigieren und das Kontrollkästchen neben der Aktion aktivieren bzw. deaktivieren:

![C#-Quellanalyseaktionen](media/refactoring-image3a.png)

### <a name="common-quick-actions"></a>Häufige schnelle Aktionen

Weitere Informationen zu schnellen Aktionen finden Sie im Artikel [Häufige schnelle Aktionen](/visualstudio/ide/common-quick-actions).

## <a name="source-analysis"></a>Quellanalyse

Bei der Quellanalyse wird Ihr Code schnell analysiert, indem potenzielle Fehler und Stilverstöße unterstrichen und automatische Korrekturen als Kontextaktionen bereitgestellt werden.

Sie können alle Ergebnisse der Quellanalyse jeder Datei zu jeder Zeit anzeigen lassen, indem Sie die Scrollleiste an der rechten Seite des Editors anzeigen:

![Quellanalyse – Randleiste](media/refactoring-image4a.png)

Wenn Sie auf den Kreis oben klicken, können Sie jeden einzelnen Vorschlag durchlaufen lassen, wobei die schwerwiegendsten Probleme zuerst angezeigt werden. Wenn Sie auf ein einzelnes Ergebnis oder eine einzelne Zeile zeigen, wird das Problem angezeigt, das durch Kontextaktionen behoben werden kann:

![Quellanalyseelement](media/refactoring-image5.png)

## <a name="related-video"></a>Zugehörige Videos

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Refactoring-Code/player]

## <a name="see-also"></a>Siehe auch

- [Schnellaktionen (Visual Studio unter Windows)](/visualstudio/ide/quick-actions)
- [Umgestalten von Code (Visual Studio unter Windows)](/visualstudio/ide/refactoring-in-visual-studio)