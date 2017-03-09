---
title: "Gewusst wie: Verwenden der WPF-Strukturschnellansicht | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Debuggen, WPF"
  - "WPF, Debuggen"
ms.assetid: 2a1bf1cd-90f9-4d06-9fb4-1bfc925afef3
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Verwenden der WPF-Strukturschnellansicht
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können die WPF\-Strukturschnellansicht verwenden, um die visuelle Struktur eines WPF\-Objekts zu untersuchen und die WPF\-Abhängigkeitseigenschaften für die Objekte anzuzeigen, die in dieser Struktur enthalten sind.  Weitere Informationen zu visuellen Strukturen finden Sie unter [Strukturen in WPF](../Topic/Trees%20in%20WPF.md).  Weitere Informationen zu Abhängigkeitseigenschaften finden Sie unter [Übersicht über Abhängigkeitseigenschaften](../Topic/Dependency%20Properties%20Overview.md).  
  
 Wenn Sie die WPF\-Strukturschnellansicht öffnen, sehen Sie zwei Bereiche: **Visuelle Struktur** auf der rechten Seite und **Eigenschaften von** *Name***:***Type* auf der rechten Seite.  Wenn Sie im Bereich **Visuelle Struktur** ein Objekt auswählen, wird der Bereich **Eigenschaften von** *Name***:***Type* automatisch aktualisiert, und die Eigenschaften des ausgewählten Objekts werden angezeigt.  
  
### So öffnen Sie die WPF\-Strukturschnellansicht  
  
1.  Klicken Sie in einem DataTip, in einem **Überwachungsfenster**, im Fenster **Auto** oder im Fenster **Lokal** neben dem Namen des WPF\-Objekts auf den Pfeil neben dem Lupensymbol.  
  
     Eine Liste von Schnellansichten wird angezeigt.  
  
2.  Klicken Sie auf **WPF\-Strukturschnellansicht**.  
  
### So durchsuchen Sie die visuelle Struktur  
  
-   Geben Sie im Bereich **Visuelle Struktur** im Feld **Suchen** die Zeichenfolge ein, die Sie suchen möchten.  
  
     Die WPF\-Strukturschnellansicht zeigt sofort das erste Objekt in der visuellen Struktur an, das zur Zeichenfolge passt, die Sie eingegeben haben.  Geben Sie mehr Zeichen ein, um eine genauere Übereinstimmung zu erzielen.  
  
    -   Klicken Sie auf **Weiter**, um zur nächsten Übereinstimmung innerhalb der visuellen Struktur zu wechseln.  
  
    -   Klicken Sie auf **Zurück**, um zurück zur vorherigen Übereinstimmung zu wechseln.  
  
    -   Klicken Sie auf **Löschen**, um die Suchkriterien zu löschen.  
  
### So durchsuchen Sie die Eigenschaftenliste  
  
-   Geben Sie im Bereich **Eigenschaften von** *Name***:***Type* die Zeichenfolge, die Sie suchen möchten, im Feld **Filter** ein.  
  
     Die WPF\-Strukturschnellansicht zeigt sofort die Eigenschaften an, die zur eingegebenen Zeichenfolge passen, und in der Liste werden nur die Eigenschaften angezeigt, die zur eingegebenen Zeichenfolge passen.  Geben Sie mehr Zeichen ein, um eine genauere Übereinstimmung zu erzielen.  
  
    -   Klicken Sie auf **Löschen**, um die Suchkriterien zu löschen.  
  
### So schließen Sie die Schnellansicht  
  
-   Klicken Sie rechts oben im Dialogfeld auf das Symbol **Schließen**.  
  
## Siehe auch  
 [Gewusst wie: Verwenden einer Schnellansicht](../misc/how-to-use-a-visualizer.md)   
 [Schnellansichten](../debugger/create-custom-visualizers-of-data.md)   
 [Strukturen in WPF](../Topic/Trees%20in%20WPF.md)   
 [Übersicht über Abhängigkeitseigenschaften](../Topic/Dependency%20Properties%20Overview.md)