---
title: Eigenschaftenfenster | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 959bd36995ca4086bf64020816b00aee6f777fbe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662075"
---
# <a name="properties-window"></a>Eigenschaftenfenster
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In diesem Fenster können Sie die Eigenschaften und Ereignisse zur Entwurfszeit für die ausgewählten Objekte in Editoren und Designern anzeigen und ändern. Außerdem können Sie im **Eigenschaftenfenster** die Eigenschaften von Dateien, Projekten oder Projektmappen anzeigen und bearbeiten. Das Fenster **Eigenschaften** finden Sie im Menü **Anzeigen**. Sie können es auch öffnen, indem Sie F4 drücken oder **Eigenschaften** im Fenster **Schnellstart** eingeben.

 Je nach den Erfordernissen der einzelnen Eigenschaften werden im **Eigenschaftenfenster** verschiedene Arten von Bearbeitungsfeldern angezeigt. Diese Bearbeitungsfelder bestehen beispielsweise aus Eingabefeldern, Dropdownlisten und Links zu benutzerdefinierten Editor-Dialogfeldern. In Grau angezeigte Eigenschaften sind schreibgeschützt.

## <a name="uielement-list"></a>UIElement-Liste
 Objektname listet die aktuell ausgewählten Objekte auf. Es werden nur die Objekte aus dem aktiven Editor oder Designer angezeigt. Wenn Sie mehrere Objekte auswählen, werden nur die Eigenschaften aufgeführt, über die alle ausgewählten Objekte verfügen.

 Kategorisiert listet alle Eigenschaften und Eigenschaftswerte für das ausgewählte Objekt nach Kategorie auf. Sie können eine Kategorie reduzieren, um die Anzahl der angezeigten Eigenschaften zu verringern. Wenn Sie eine Kategorie reduzieren oder erweitern, wird ein Pluszeichen (+) bzw. ein Minuszeichen (-) auf der linken Seite des Kategorienamens angezeigt. Kategorien sind in alphabetischer Reihenfolge aufgelistet.

 Alphabetisch sortiert alle Entwurfszeit Eigenschaften und Ereignisse für ausgewählte Objekte. Zum Bearbeiten einer nicht abgeblendeten Eigenschaft klicken Sie auf die Zelle rechts neben der Eigenschaft und nehmen die Änderungen vor.

 Eigenschaften Seiten zeigt das Dialogfeld **Eigenschaften Seiten** oder **Projekt-Designer** für das ausgewählte Element an. Unter **Eigenschaftenseiten** wird entweder eine Teilmenge, dieselbe Menge oder eine Obermenge der im Eigenschaftenfenster verfügbaren Eigenschaften angezeigt. Über diese Schaltfläche werden die Eigenschaften angezeigt und bearbeitet, die sich auf die aktive Konfiguration des Projekts beziehen.

 Eigenschaften zeigt die Eigenschaften für ein Objekt an. Viele Objekte verfügen außerdem über Ereignisse, die im**Eigenschaftenfenster** angezeigt werden können.

 Sortieren Sie nach Eigenschaften Quell Gruppen Eigenschaften nach Quelle, z. b. Vererbung, angewendete Stile und Bindungen. Nur verfügbar, wenn XAML-Dateien im Designer bearbeitet werden.

 Ereignisse zeigt die Ereignisse für ein Objekt an.

> [!NOTE]
> Dieses Symbolleisten-Steuerelement des **Eigenschaftenfensters** ist nur dann verfügbar, wenn im Kontext eines [!INCLUDE[csprcs](../../includes/csprcs-md.md)]-Projekts ein Designer für Formulare oder Steuerelemente aktiviert ist. Wenn Sie XAML-Dateien bearbeiten, werden Ereignisse auf einer separaten Registerkarte des Eigenschaftenfensters angezeigt.

 Nachrichten listet alle Windows-Meldungen auf. Ermöglicht das Hinzufügen oder Löschen bestimmter Handlerfunktionen für die Nachrichten, die für die ausgewählte Klasse gelten.

> [!NOTE]
> Dieses Symbolleisten-Steuerelement des **Eigenschaftenfensters** ist nur dann verfügbar, wenn im Kontext eines [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)]-Projekts die **Klassenansicht** das aktive Fenster ist.

 Über schreibungen listet alle virtuellen Funktionen für die ausgewählte Klasse auf und ermöglicht das Hinzufügen oder Löschen über schreibender Funktionen.

> [!NOTE]
> Dieses Symbolleisten-Steuerelement des **Eigenschaftenfensters** ist nur dann verfügbar, wenn im Kontext eines [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)]-Projekts die **Klassenansicht** das aktive Fenster ist.

 Der Beschreibungs Bereich zeigt den Eigenschaftentyp und eine kurze Beschreibung der Eigenschaft an. Mithilfe des Befehls "Beschreibung" im Kontextmenü können Sie die Beschreibung der Eigenschaft ein- und ausblenden.

> [!NOTE]
> Dieses Symbolleisten-Steuerelement für das **Eigenschaftenfenster** ist nicht verfügbar, wenn XAML-Dateien im Designer bearbeitet werden.

 Die Miniaturansicht zeigt eine visuelle Darstellung des aktuell ausgewählten Elements an, wenn XAML-Dateien im Designer bearbeitet werden.

 Search stellt eine Suchfunktion für Eigenschaften und Ereignisse bereit, wenn XAML-Dateien im Designer bearbeitet werden. Das Suchfeld reagiert auf die Suche nach Wortteilen. Die Suchergebnisse werden bei der Eingabe aktualisiert.

## <a name="see-also"></a>Weitere Informationen
 [Projekteigenschaften Referenz](../../ide/reference/project-properties-reference.md) [Anpassen von Fensterlayouts](../../ide/customizing-window-layouts-in-visual-studio.md)
