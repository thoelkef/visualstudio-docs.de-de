---
title: 'Gewusst wie: Verwenden der WPF-Struktur Schnellansicht | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- WPF, debugging
- debugging, WPF
ms.assetid: 2a1bf1cd-90f9-4d06-9fb4-1bfc925afef3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0adcca4acd5fc72d301d707ccdd831c86ef3e48f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72731920"
---
# <a name="how-to-use-the-wpf-tree-visualizer"></a>Gewusst wie: Verwenden des WPF Tree Visualizer (WPF-Strukturschnellansicht)
Sie können den WPF Tree visualizer (WPF-Strukturschnellansicht) verwenden, um die visuelle Struktur eines WPF-Objekts zu untersuchen und die WPF-Abhängigkeitseigenschaften für die Objekte anzuzeigen, die in dieser Struktur enthalten sind. Weitere Informationen zu visuellen Bäumen finden Sie Unterstrukturen [in WPF](/dotnet/framework/wpf/advanced/trees-in-wpf). Weitere Informationen zu Abhängigkeits Eigenschaften finden Sie unter [Übersicht über Abhängigkeits Eigenschaften](/dotnet/framework/wpf/advanced/dependency-properties-overview).

 Wenn Sie die WPF-Struktur Schnellansicht öffnen, werden zwei Bereiche angezeigt: die **visuelle** Struktur auf der linken Seite und die **Eigenschaften von** _Name_ **:** _Typbereich_ auf der rechten Seite. Wählen Sie im **visuellen** Strukturbereich ein beliebiges Objekt aus, und die **Eigenschaften des** _Bereichs Name_ **:** _Typ_ werden automatisch aktualisiert, um die Eigenschaften für dieses Objekt anzuzeigen.

### <a name="to-open-the-wpf-tree-visualizer"></a>So öffnen Sie die WPF-Strukturschnellansicht

1. Klicken Sie in einem DataTip, in einem **Überwachungsfenster**, im Fenster **Auto** oder im Fenster **Lokal** neben dem Namen des WPF-Objekts auf den Pfeil neben dem Lupensymbol.

     Eine Liste von Schnellansichten wird angezeigt.

2. Klicken Sie auf **WPF Tree Visualizer** (WPF-Strukturschnellansicht).

### <a name="to-search-the-visual-tree"></a>So durchsuchen Sie die visuelle Struktur

- Geben Sie im Bereich **Visuelle Struktur** im Feld **Suchen** die Zeichenfolge ein, die Sie suchen möchten.

  Der WPF Tree visualizer (WPF-Strukturschnellansicht) zeigt sofort das erste Objekt in der visuellen Struktur an, das zur Zeichenfolge passt, die Sie eingegeben haben. Geben Sie mehr Zeichen ein, um eine genauere Übereinstimmung zu erzielen.

  - Klicken Sie auf **Weiter**, um zur nächsten Übereinstimmung innerhalb der visuellen Struktur zu wechseln.

  - Klicken Sie auf **Zurück**, um zurück zur vorherigen Übereinstimmung zu wechseln.

  - Klicken Sie auf **Löschen**, um die Suchkriterien zu löschen.

### <a name="to-search-the-properties-list"></a>So durchsuchen Sie die Eigenschaftenliste

- Geben Sie im Bereich **Eigenschaften von** _Name_ **:** _Typ_ im Feld **Filter** die Zeichenfolge ein, nach der Sie suchen möchten.

  Die WPF-Strukturschnellansicht zeigt sofort die Eigenschaften an, die zur eingegebenen Zeichenfolge passen, und in der Liste werden nur die Eigenschaften angezeigt, die zur eingegebenen Zeichenfolge passen. Geben Sie mehr Zeichen ein, um eine genauere Übereinstimmung zu erzielen.

  - Klicken Sie auf **Löschen**, um die Suchkriterien zu löschen.

### <a name="to-close-the-visualizer"></a>So schließen Sie die Schnellansicht

- Klicken Sie rechts oben im Dialogfeld auf das Symbol **Schließen**.

## <a name="see-also"></a>Siehe auch
- [Erstellen benutzerdefinierter Schnellansichten](../debugger/create-custom-visualizers-of-data.md)
- [Strukturen in WPF](/dotnet/framework/wpf/advanced/trees-in-wpf)
- [Übersicht über Abhängigkeitseigenschaften](/dotnet/framework/wpf/advanced/dependency-properties-overview)
