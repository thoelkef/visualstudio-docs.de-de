---
title: Eigenschaftenfenster | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 88ff9388a7d23543a32368e763b5efb7abbdc8cc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47515006"
---
# <a name="properties-window"></a>Eigenschaftenfenster
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Fenster "Eigenschaften"](https://docs.microsoft.com/visualstudio/ide/reference/properties-window).  
  
  
In diesem Fenster können Sie die Eigenschaften und Ereignisse zur Entwurfszeit für die ausgewählten Objekte in Editoren und Designern anzeigen und ändern. Außerdem können Sie im **Eigenschaftenfenster** die Eigenschaften von Dateien, Projekten oder Projektmappen anzeigen und bearbeiten. Das Fenster **Eigenschaften** finden Sie im Menü **Anzeigen**. Sie können es auch öffnen, indem Sie F4 drücken oder **Eigenschaften** im Fenster **Schnellstart** eingeben.  
  
 Je nach den Erfordernissen der einzelnen Eigenschaften werden im **Eigenschaftenfenster** verschiedene Arten von Bearbeitungsfeldern angezeigt. Diese Bearbeitungsfelder bestehen beispielsweise aus Eingabefeldern, Dropdownlisten und Links zu benutzerdefinierten Editor-Dialogfeldern. In Grau angezeigte Eigenschaften sind schreibgeschützt.  
  
## <a name="uielement-list"></a>UIElement-Liste  
 Objektname  
 Listet die momentan ausgewählten Objekte auf. Es werden nur die Objekte im aktiven Editor bzw. Designer angezeigt. Wenn Sie mehrere Objekte auswählen, werden nur die Eigenschaften aufgeführt, über die alle ausgewählten Objekte verfügen.  
  
 Nach Kategorien  
 Listet alle Eigenschaften und Eigenschaftswerte für das ausgewählte Objekt nach Kategorie sortiert auf. Kategorien können reduziert werden, um die Anzahl von sichtbaren Eigenschaften zu verringern. Wenn Sie eine Kategorie erweitern oder reduzieren, wird links neben dem Kategorienamen ein Pluszeichen (+) oder ein Minuszeichen (-) angezeigt. Die Kategorien werden in alphabetischer Reihenfolge aufgeführt.  
  
 Alphabetisch  
 Sortiert alle Entwurfszeit-Eigenschaften und -Ereignisse ausgewählter Objekte in alphabetischer Reihenfolge. Zum Bearbeiten einer nicht abgeblendeten Eigenschaft klicken Sie auf die Zelle rechts neben der Eigenschaft und nehmen die Änderungen vor.  
  
 Eigenschaftenseiten  
 Zeigt das Dialogfeld **Eigenschaftenseiten** oder **Projekt-Designer** für das ausgewählte Element an. Unter **Eigenschaftenseiten** wird entweder eine Teilmenge, dieselbe Menge oder eine Obermenge der im Eigenschaftenfenster verfügbaren Eigenschaften angezeigt. Über diese Schaltfläche werden die Eigenschaften angezeigt und bearbeitet, die sich auf die aktive Konfiguration des Projekts beziehen.  
  
 Eigenschaften  
 Zeigt die Eigenschaften eines Objekts an. Viele Objekte verfügen außerdem über Ereignisse, die im**Eigenschaftenfenster** angezeigt werden können.  
  
 Nach Eigenschaftsquelle sortieren  
 Gruppiert Eigenschaften nach Quelle, z. B. Vererbung, geltende Formate und Bindungen. Nur verfügbar, wenn XAML-Dateien im Designer bearbeitet werden.  
  
 Ereignisse  
 Zeigt die Ereignisse eines Objekts an.  
  
> [!NOTE]
>  Dieses Symbolleisten-Steuerelement des **Eigenschaftenfensters** ist nur dann verfügbar, wenn im Kontext eines [!INCLUDE[csprcs](../../includes/csprcs-md.md)]-Projekts ein Designer für Formulare oder Steuerelemente aktiviert ist. Wenn Sie XAML-Dateien bearbeiten, werden Ereignisse auf einer separaten Registerkarte des Eigenschaftenfensters angezeigt.  
  
 Mitteilungen  
 Führt alle Windows-Meldungen auf. Ermöglicht das Hinzufügen oder Löschen bestimmter Handlerfunktionen für die Nachrichten, die für die ausgewählte Klasse gelten.  
  
> [!NOTE]
>  Dieses Symbolleisten-Steuerelement des **Eigenschaftenfensters** ist nur dann verfügbar, wenn im Kontext eines [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)]-Projekts die **Klassenansicht** das aktive Fenster ist.  
  
 Overrides  
 Führt alle virtuellen Funktionen für die ausgewählte Klasse auf und ermöglicht das Hinzufügen oder Löschen überschreibender Funktionen.  
  
> [!NOTE]
>  Dieses Symbolleisten-Steuerelement des **Eigenschaftenfensters** ist nur dann verfügbar, wenn im Kontext eines [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)]-Projekts die **Klassenansicht** das aktive Fenster ist.  
  
 Beschreibungsbereich  
 Zeigt den Eigenschaftentyp und eine Kurzbeschreibung der Eigenschaft an. Mithilfe des Befehls "Beschreibung" im Kontextmenü können Sie die Beschreibung der Eigenschaft ein- und ausblenden.  
  
> [!NOTE]
>  Dieses Symbolleisten-Steuerelement für das **Eigenschaftenfenster** ist nicht verfügbar, wenn XAML-Dateien im Designer bearbeitet werden.  
  
 Miniaturansicht  
 Zeigt beim Bearbeiten von XAML-Dateien im Designer eine visuelle Darstellung des gerade ausgewählten Elements an.  
  
 Suchen  
 Stellt eine Suchfunktion für Eigenschaften und Ereignisse bereit, wenn XAML-Dateien im Designer bearbeitet werden. Das Suchfeld reagiert auf die Suche nach Wortteilen. Die Suchergebnisse werden bei der Eingabe aktualisiert.  
  
## <a name="see-also"></a>Siehe auch  
 [Projekteigenschaftenverweise](../../ide/reference/project-properties-reference.md)   
 [Anpassen von Fensterlayouts](../../ide/customizing-window-layouts-in-visual-studio.md)



