---
title: "Gewusst wie: Bildlauf nach oben oder unten im Arbeitsspeicher | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Debugger, Paging im Arbeitsspeicher"
  - "Arbeitsspeicher, Paging"
  - "Disassemblierung (Fenster), Anzeigen von Speicherplatz im Arbeitsspeicher"
  - "Speicherfenster, Paging im Arbeitsspeicher"
ms.assetid: 50b30a68-66f6-43f8-a48b-59ce12c95471
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# Gewusst wie: Bildlauf nach oben oder unten im Arbeitsspeicher
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Beim Anzeigen des Speicherinhalts im Fenster **Arbeitsspeicher** oder im Fenster **Disassembly** können Sie mithilfe der vertikalen Bildlaufleiste im Speicher nach oben oder unten navigieren.  
  
### So führen Sie im Speicher einen Bildlauf nach oben oder nach unten durch  
  
1.  Für einen Bildlauf nach unten \(Navigieren zu einer höheren Speicheradresse\) klicken Sie auf die vertikale Bildlaufleiste unter dem Bildlauffeld.  
  
2.  Für einen Bildlauf nach oben \(Navigieren zu einer niedrigeren Speicheradresse\) klicken Sie auf der vertikalen Bildlaufleiste über dem Bildlauffeld.  
  
 Beachten Sie auch, dass das Verhalten der vertikalen Bildlaufleiste nicht dem Standardverhalten entspricht.  Der Adressbereich eines modernen Computers ist äußerst groß, und eine Suche kann leicht fehlschlagen, wenn Sie das Bildlauffeld der Bildlaufleiste an eine zufällige Position ziehen.  Aus diesem Grunde verhält sich das Bildlauffeld, als wäre es beidseitig mit einer Zugfeder verbunden, und verbleibt stets in der Mitte der Bildlaufleiste.  In Anwendungen, die in systemeigenem Code geschrieben sind, können Sie einen Bildlauf nach oben oder unten durchführen; die Durchführung eines freien Bildlaufs ist jedoch nicht möglich.  
  
 In verwalteten Anwendungen ist die Disassembly auf eine Funktion begrenzt, und Sie können einen normalen Bildlauf durchführen.  
  
 Beachten Sie, dass die höheren Adressen am unteren Rand des Fensters angezeigt werden.  Wenn Sie eine höhere Adresse anzeigen möchten, müssen Sie nach unten navigieren, nicht nach oben.  
  
#### So wechseln Sie um eine Anweisung nach oben oder unten  
  
-   Klicken Sie auf den Pfeil am oberen oder unteren Ende der vertikalen Bildlaufleiste.  
  
## Siehe auch  
 [Fenster "Arbeitsspeicher"](../debugger/memory-windows.md)   
 [Gewusst wie: Verwenden des Fensters Disassembly](../debugger/how-to-use-the-disassembly-window.md)   
 [Anzeigen von Daten im Debugger](../debugger/viewing-data-in-the-debugger.md)