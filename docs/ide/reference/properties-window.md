---
title: Eigenschaftenfenster
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- properties [Visual Studio], Properties Window
- handler functions, Properties window
- handlers, Properties window
- Windows messages
- properties [Visual Studio], setting at design time
- properties [Visual Studio], editing
- Property Browser
- Windows messages, adding message handlers
- Properties window, overrides
- virtual functions, Properties window
- Properties window
ms.assetid: e6e0fa4f-75c4-4a52-af15-281cd61876ca
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4701f5ea882ab2fbb75f11bc3cc6d85fc92b4b8e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655695"
---
# <a name="properties-window"></a>Eigenschaftenfenster

In diesem Fenster können Sie die Eigenschaften und Ereignisse zur Entwurfszeit für die ausgewählten Objekte in Editoren und Designern anzeigen und ändern. Außerdem können Sie im **Eigenschaftenfenster** die Eigenschaften von Dateien, Projekten oder Projektmappen anzeigen und bearbeiten. Das Fenster **Eigenschaften** finden Sie im Menü **Anzeigen**. Sie können es auch öffnen, indem Sie **F4** drücken oder im Suchfeld **Eigenschaften** eingeben.

Je nach den Erfordernissen der einzelnen Eigenschaften werden im **Eigenschaftenfenster** verschiedene Arten von Bearbeitungsfeldern angezeigt. Diese Bearbeitungsfelder bestehen beispielsweise aus Eingabefeldern, Dropdownlisten und Links zu benutzerdefinierten Editor-Dialogfeldern. In Grau angezeigte Eigenschaften sind schreibgeschützt.

## <a name="uielement-list"></a>UIElement-Liste

Objektname\
Listet die momentan ausgewählten Objekte auf. Es werden nur die Objekte im aktiven Editor bzw. Designer angezeigt. Wenn Sie mehrere Objekte auswählen, werden nur die Eigenschaften aufgeführt, über die alle ausgewählten Objekte verfügen.

Nach Kategorien\
Listet alle Eigenschaften und Eigenschaftswerte für das ausgewählte Objekt nach Kategorie sortiert auf. Kategorien können reduziert werden, um die Anzahl von sichtbaren Eigenschaften zu verringern. Wenn Sie eine Kategorie erweitern oder reduzieren, wird links neben dem Kategorienamen ein Pluszeichen (+) oder ein Minuszeichen (-) angezeigt. Die Kategorien werden in alphabetischer Reihenfolge aufgeführt.

Alphabetisch\
Sortiert alle Entwurfszeit-Eigenschaften und -Ereignisse ausgewählter Objekte in alphabetischer Reihenfolge. Zum Bearbeiten einer nicht abgeblendeten Eigenschaft klicken Sie auf die Zelle rechts neben der Eigenschaft und nehmen die Änderungen vor.

Eigenschaftenseiten\
Zeigt das Dialogfeld **Eigenschaftenseiten** oder **Projekt-Designer** für das ausgewählte Element an. Unter **Eigenschaftenseiten** wird entweder eine Teilmenge, dieselbe Menge oder eine Obermenge der im Eigenschaftenfenster verfügbaren Eigenschaften angezeigt. Über diese Schaltfläche werden die Eigenschaften angezeigt und bearbeitet, die sich auf die aktive Konfiguration des Projekts beziehen.

Eigenschaften\
Zeigt die Eigenschaften eines Objekts an. Viele Objekte verfügen außerdem über Ereignisse, die im**Eigenschaftenfenster** angezeigt werden können.

Nach Eigenschaftsquelle sortieren\
Gruppiert Eigenschaften nach Quelle, z. B. Vererbung, geltende Formate und Bindungen. Nur verfügbar, wenn XAML-Dateien im Designer bearbeitet werden.

Ereignisse\
Zeigt die Ereignisse eines Objekts an.

> [!NOTE]
> Dieses Symbolleisten-Steuerelement des **Eigenschaftenfensters** ist nur dann verfügbar, wenn im Kontext eines [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]-Projekts ein Designer für Formulare oder Steuerelemente aktiviert ist. Wenn Sie XAML-Dateien bearbeiten, werden Ereignisse auf einer separaten Registerkarte des Eigenschaftenfensters angezeigt.

Meldungen\
Führt alle Windows-Meldungen auf. Ermöglicht das Hinzufügen oder Löschen bestimmter Handlerfunktionen für die Nachrichten, die für die ausgewählte Klasse gelten.

> [!NOTE]
> Dieses Symbolleisten-Steuerelement des **Eigenschaftenfensters** ist nur dann verfügbar, wenn im Kontext eines [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]-Projekts die **Klassenansicht** das aktive Fenster ist.

Überschreibungen\
Führt alle virtuellen Funktionen für die ausgewählte Klasse auf und ermöglicht das Hinzufügen oder Löschen überschreibender Funktionen.

> [!NOTE]
> Dieses Symbolleisten-Steuerelement des **Eigenschaftenfensters** ist nur dann verfügbar, wenn im Kontext eines [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]-Projekts die **Klassenansicht** das aktive Fenster ist.

Beschreibungsbereich\
Zeigt den Eigenschaftentyp und eine Kurzbeschreibung der Eigenschaft an. Mithilfe des Befehls "Beschreibung" im Kontextmenü können Sie die Beschreibung der Eigenschaft ein- und ausblenden.

> [!NOTE]
> Dieses Symbolleisten-Steuerelement für das **Eigenschaftenfenster** ist nicht verfügbar, wenn XAML-Dateien im Designer bearbeitet werden.

Miniaturansicht\
Zeigt beim Bearbeiten von XAML-Dateien im Designer eine visuelle Darstellung des gerade ausgewählten Elements an.

Suchen\
Stellt eine Suchfunktion für Eigenschaften und Ereignisse bereit, wenn XAML-Dateien im Designer bearbeitet werden. Das Suchfeld reagiert auf die Suche nach Wortteilen. Die Suchergebnisse werden bei der Eingabe aktualisiert.

## <a name="see-also"></a>Siehe auch

- [Projekteigenschaftenverweise](../../ide/reference/project-properties-reference.md)
- [Anpassen von Fensterlayouts](../../ide/customizing-window-layouts-in-visual-studio.md)