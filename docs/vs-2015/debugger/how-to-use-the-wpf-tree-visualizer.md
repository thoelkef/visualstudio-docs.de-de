---
title: 'Vorgehensweise: Verwenden der WPF-Strukturschnellansicht | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 381dc45351ae03e615afbdd31239869e3dba8e4e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "67825433"
---
# <a name="how-to-use-the-wpf-tree-visualizer"></a>Vorgehensweise: Verwenden der WPF-Strukturschnellansicht
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können den WPF Tree visualizer (WPF-Strukturschnellansicht) verwenden, um die visuelle Struktur eines WPF-Objekts zu untersuchen und die WPF-Abhängigkeitseigenschaften für die Objekte anzuzeigen, die in dieser Struktur enthalten sind. Weitere Informationen zu visuellen Strukturen finden Sie unter [Strukturen in WPF](https://msdn.microsoft.com/library/e83f25e5-d66b-4fc7-92d2-50130c9a6649). Weitere Informationen zu Abhängigkeitseigenschaften finden Sie unter [Übersicht über Abhängigkeitseigenschaften](https://msdn.microsoft.com/library/d119d00c-3afb-48d6-87a0-c4da4f83dee5).  
  
 Wenn Sie die WPF-Strukturschnellansicht öffnen, werden zwei Bereiche angezeigt: **Visuelle Struktur** auf der linken und **Eigenschaften von** _Name_ **:** _Typ_ auf der rechten Seite. Wenn Sie im Bereich **Visuelle Struktur** auf ein Objekt klicken, wird der Bereich **Eigenschaften von** _Name_ **:** _Typ_ automatisch aktualisiert, und die Eigenschaften des ausgewählten Objekts werden angezeigt.  
  
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
  
- Geben Sie im Bereich **Eigenschaften von** _Name_**:**_Typ_ im Feld **Filter** die Zeichenfolge ein, nach der Sie suchen möchten.  
  
  Die WPF-Strukturschnellansicht zeigt sofort die Eigenschaften an, die zur eingegebenen Zeichenfolge passen, und in der Liste werden nur die Eigenschaften angezeigt, die zur eingegebenen Zeichenfolge passen. Geben Sie mehr Zeichen ein, um eine genauere Übereinstimmung zu erzielen.  

  - Klicken Sie auf **Löschen**, um die Suchkriterien zu löschen.  
  
### <a name="to-close-the-visualizer"></a>So schließen Sie die Schnellansicht  
  
- Klicken Sie rechts oben im Dialogfeld auf das Symbol **Schließen**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gewusst wie: Verwenden einer Schnellansicht](../misc/how-to-use-a-visualizer.md)   
 [Erstellen von benutzerdefinierten Visualisierungen](../debugger/create-custom-visualizers-of-data.md)   
 [Strukturen in WPF](https://msdn.microsoft.com/library/e83f25e5-d66b-4fc7-92d2-50130c9a6649)   
 [Übersicht über Abhängigkeitseigenschaften](https://msdn.microsoft.com/library/d119d00c-3afb-48d6-87a0-c4da4f83dee5)
