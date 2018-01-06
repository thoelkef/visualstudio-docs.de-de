---
title: 'Vorgehensweise: Verwenden von WPF-Strukturschnellansicht | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- WPF, debugging
- debugging, WPF
ms.assetid: 2a1bf1cd-90f9-4d06-9fb4-1bfc925afef3
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 78806b2ace7872db06ff403bcae28bb6eff21cd2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-the-wpf-tree-visualizer"></a>Gewusst wie: Verwenden des WPF Tree Visualizer (WPF-Strukturschnellansicht)
Sie können den WPF Tree visualizer (WPF-Strukturschnellansicht) verwenden, um die visuelle Struktur eines WPF-Objekts zu untersuchen und die WPF-Abhängigkeitseigenschaften für die Objekte anzuzeigen, die in dieser Struktur enthalten sind. Weitere Informationen zu visuellen Strukturen finden Sie unter [Strukturen in WPF](/dotnet/framework/wpf/advanced/trees-in-wpf). Weitere Informationen über Abhängigkeitseigenschaften finden Sie unter [Übersicht über Abhängigkeitseigenschaften](/dotnet/framework/wpf/advanced/dependency-properties-overview).  
  
 Wenn Sie die WPF-Strukturschnellansicht öffnen, sehen Sie zwei Bereiche: den **visuellen Struktur** auf der linken Seite und die **Eigenschaften des** *Namen***:**  *Typ* im rechten Bereich. Wählen Sie ein Objekt in der **visuellen Struktur** Bereich und die **Eigenschaften des** *Name***:***Typ* Bereich automatisch aktualisiert, um die Eigenschaften für dieses Objekt anzuzeigen.  
  
### <a name="to-open-the-wpf-tree-visualizer"></a>So öffnen Sie den WPF Tree visualizer (WPF-Strukturschnellansicht)  
  
1.  In einem DataTip **Überwachen** Fenster **"Auto"** Fenster oder **"lokal"** Fenster neben dem Namen des WPF-Objekt, klicken Sie auf den Pfeil neben dem Lupensymbol.  
  
     Eine Liste von Schnellansichten wird angezeigt.  
  
2.  Klicken Sie auf **WPF-Strukturschnellansicht**.  
  
### <a name="to-search-the-visual-tree"></a>So durchsuchen Sie die visuelle Struktur  
  
-   In der **visuellen Struktur** Bereich, geben Sie die Zeichenfolge, die Sie suchen möchten die **Suche** Feld.  
  
     Der WPF Tree visualizer (WPF-Strukturschnellansicht) zeigt sofort das erste Objekt in der visuellen Struktur an, das zur Zeichenfolge passt, die Sie eingegeben haben. Geben Sie mehr Zeichen ein, um eine genauere Übereinstimmung zu erzielen.  
  
    -   Um zur nächsten Übereinstimmung innerhalb der visuellen Struktur zu wechseln, klicken Sie auf **Weiter**.  
  
    -   Um zurück zur vorherigen Übereinstimmung zu gelangen, klicken Sie auf **Prev**.  
  
    -   Um die Suchkriterien zu löschen, klicken Sie auf **deaktivieren**.  
  
### <a name="to-search-the-properties-list"></a>So durchsuchen Sie die Eigenschaftenliste  
  
-   In der **Eigenschaften des** *Namen***:***Typ* Bereich geben Sie die Zeichenfolge die suchen möchten, in der **Filtern**Feld.  
  
     Der WPF Tree visualizer (WPF-Strukturschnellansicht) zeigt sofort die Eigenschaften an, die zur eingegebenen Zeichenfolge passen, und in der Liste werden nur die Eigenschaften angezeigt, die zur eingegebenen Zeichenfolge passen. Geben Sie mehr Zeichen ein, um eine genauere Übereinstimmung zu erzielen.  
  
    -   Um die Suchkriterien zu löschen, klicken Sie auf **deaktivieren**.  
  
### <a name="to-close-the-visualizer"></a>So schließen Sie die Schnellansicht  
  
-   Klicken Sie auf die **schließen** Symbol in der oberen rechten Ecke des Dialogfelds.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen Sie benutzerdefinierte Schnellansichten](../debugger/create-custom-visualizers-of-data.md)   
 [Strukturen in WPF](/dotnet/framework/wpf/advanced/trees-in-wpf)   
 [Übersicht über Abhängigkeitseigenschaften](/dotnet/framework/wpf/advanced/dependency-properties-overview)