---
title: 'Vorgehensweise: Verwenden Sie die WPF-Strukturschnellansicht | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0a478eae1e576ba2556d48f6527f6c9e2dab4ef6
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "42902162"
---
# <a name="how-to-use-the-wpf-tree-visualizer"></a>Gewusst wie: Verwenden des WPF Tree Visualizer (WPF-Strukturschnellansicht)
Sie können den WPF Tree visualizer (WPF-Strukturschnellansicht) verwenden, um die visuelle Struktur eines WPF-Objekts zu untersuchen und die WPF-Abhängigkeitseigenschaften für die Objekte anzuzeigen, die in dieser Struktur enthalten sind. Weitere Informationen zu visuellen Strukturen finden Sie unter [Strukturen in WPF](/dotnet/framework/wpf/advanced/trees-in-wpf). Weitere Informationen zu Abhängigkeitseigenschaften finden Sie unter [Übersicht über Abhängigkeitseigenschaften](/dotnet/framework/wpf/advanced/dependency-properties-overview).  
  
 Wenn Sie die WPF-Strukturschnellansicht öffnen, sehen Sie zwei Bereiche: den **visuelle Struktur** auf der linken Seite und die **Eigenschaften** _Namen_**:**  _Typ_ im rechten Bereich. Wählen Sie ein Objekt in der **visuelle Struktur** Bereich und die **Eigenschaften** _Namen_**:**_Typ_ Bereich automatisch aktualisiert, um die Eigenschaften für dieses Objekt anzuzeigen.  
  
### <a name="to-open-the-wpf-tree-visualizer"></a>So öffnen Sie den WPF Tree visualizer (WPF-Strukturschnellansicht)  
  
1.  In einem DataTip **Watch** Fenster **"Auto"** Fenster oder **"lokal"** Fenster neben dem Namen des WPF-Objekt, klicken Sie auf den Pfeil neben dem Lupensymbol.  
  
     Eine Liste von Schnellansichten wird angezeigt.  
  
2.  Klicken Sie auf **WPF-Strukturschnellansicht**.  
  
### <a name="to-search-the-visual-tree"></a>So durchsuchen Sie die visuelle Struktur  
  
-   In der **visuelle Struktur** Bereich, geben Sie die Zeichenfolge, die Sie suchen möchten die **Suche** Feld.  
  
     Der WPF Tree visualizer (WPF-Strukturschnellansicht) zeigt sofort das erste Objekt in der visuellen Struktur an, das zur Zeichenfolge passt, die Sie eingegeben haben. Geben Sie mehr Zeichen ein, um eine genauere Übereinstimmung zu erzielen.  
  
    -   Klicken Sie zum Wechseln zum nächsten Übereinstimmung innerhalb der visuellen Struktur auf **Weiter**.  
  
    -   Um zurück zur vorherigen Übereinstimmung zu wechseln, klicken Sie auf **Prev**.  
  
    -   Um die Suchkriterien zu löschen, klicken Sie auf **löschen**.  
  
### <a name="to-search-the-properties-list"></a>So durchsuchen Sie die Eigenschaftenliste  
  
-   In der **Eigenschaften** _Namen_**:**_Typ_ Bereich, geben Sie die Zeichenfolge, die Sie suchen möchten die **Filtern**Feld.  
  
     Der WPF Tree visualizer (WPF-Strukturschnellansicht) zeigt sofort die Eigenschaften an, die zur eingegebenen Zeichenfolge passen, und in der Liste werden nur die Eigenschaften angezeigt, die zur eingegebenen Zeichenfolge passen. Geben Sie mehr Zeichen ein, um eine genauere Übereinstimmung zu erzielen.  
  
    -   Um die Suchkriterien zu löschen, klicken Sie auf **löschen**.  
  
### <a name="to-close-the-visualizer"></a>So schließen Sie die Schnellansicht  
  
-   Klicken Sie auf die **schließen** Symbol in der oberen rechten Ecke des Dialogfelds.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen benutzerdefinierter Schnellansichten](../debugger/create-custom-visualizers-of-data.md)   
 [Strukturen in WPF](/dotnet/framework/wpf/advanced/trees-in-wpf)   
 [Übersicht über Abhängigkeitseigenschaften](/dotnet/framework/wpf/advanced/dependency-properties-overview)
