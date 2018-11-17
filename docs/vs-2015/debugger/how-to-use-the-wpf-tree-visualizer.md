---
title: 'Vorgehensweise: Verwenden Sie die WPF-Strukturschnellansicht | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- WPF, debugging
- debugging, WPF
ms.assetid: 2a1bf1cd-90f9-4d06-9fb4-1bfc925afef3
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 69ce98efe7429b011915f14b267cf5346528a93d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51752107"
---
# <a name="how-to-use-the-wpf-tree-visualizer"></a>Gewusst wie: Verwenden des WPF Tree Visualizer (WPF-Strukturschnellansicht)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können den WPF Tree visualizer (WPF-Strukturschnellansicht) verwenden, um die visuelle Struktur eines WPF-Objekts zu untersuchen und die WPF-Abhängigkeitseigenschaften für die Objekte anzuzeigen, die in dieser Struktur enthalten sind. Weitere Informationen zu visuellen Strukturen finden Sie unter [Strukturen in WPF](http://msdn.microsoft.com/library/e83f25e5-d66b-4fc7-92d2-50130c9a6649). Weitere Informationen zu Abhängigkeitseigenschaften finden Sie unter [Übersicht über Abhängigkeitseigenschaften](http://msdn.microsoft.com/library/d119d00c-3afb-48d6-87a0-c4da4f83dee5).  
  
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
  
-   In der **Eigenschaften** _Name_**:**_Typ_ Bereich der in gesucht werden soll, geben Sie die Zeichenfolge der **filtern**Feld.  
  
     Der WPF Tree visualizer (WPF-Strukturschnellansicht) zeigt sofort die Eigenschaften an, die zur eingegebenen Zeichenfolge passen, und in der Liste werden nur die Eigenschaften angezeigt, die zur eingegebenen Zeichenfolge passen. Geben Sie mehr Zeichen ein, um eine genauere Übereinstimmung zu erzielen.  
  
    -   Um die Suchkriterien zu löschen, klicken Sie auf **löschen**.  
  
### <a name="to-close-the-visualizer"></a>So schließen Sie die Schnellansicht  
  
-   Klicken Sie auf die **schließen** Symbol in der oberen rechten Ecke des Dialogfelds.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Verwenden einer Schnellansicht](../misc/how-to-use-a-visualizer.md)   
 [Erstellen benutzerdefinierter Schnellansichten](../debugger/create-custom-visualizers-of-data.md)   
 [Strukturen in WPF](http://msdn.microsoft.com/library/e83f25e5-d66b-4fc7-92d2-50130c9a6649)   
 [Übersicht über Abhängigkeitseigenschaften](http://msdn.microsoft.com/library/d119d00c-3afb-48d6-87a0-c4da4f83dee5)



