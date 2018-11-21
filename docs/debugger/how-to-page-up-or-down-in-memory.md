---
title: 'Vorgehensweise: Seite nach oben oder unten im Arbeitsspeicher | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, paging up or down in memory
- memory, paging up or down
- Disassembly window, viewing memory space
- Memory window, paging up or down in memory
ms.assetid: 50b30a68-66f6-43f8-a48b-59ce12c95471
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7f981dafc6c014080960f2a0652420a00ea6ac6f
ms.sourcegitcommit: a7de99f36e9ead7ea9e9bac23c88d05ddfc38b00
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52257124"
---
# <a name="how-to-page-up-or-down-in-memory"></a>Gewusst wie: Bildlauf nach oben oder unten im Arbeitsspeicher

Bei der Anzeige der Speicherinhalt in einem **Arbeitsspeicher** Fenster oder der **Disassembly** Fenster können Sie die vertikale Bildlaufleiste um nach oben oder unten im Arbeitsspeicher zu verschieben.  
  
### <a name="to-page-up-or-down-in-memory"></a>So führen Sie im Speicher einen Bildlauf nach oben oder nach unten durch  
  
1. Für einen Bildlauf nach unten (Navigieren zu einer höheren Speicheradresse) klicken Sie auf die vertikale Scrollleiste unter dem Bildlauffeld.  
  
2. Für einen Bildlauf nach oben (Navigieren zu einer niedrigeren Speicheradresse) klicken Sie auf der vertikalen Bildlaufleiste über dem Bildlauffeld.  
  
   Beachten Sie auch, dass das Verhalten der vertikalen Bildlaufleiste nicht dem Standardverhalten entspricht. Der Adressbereich eines modernen Computers ist äußerst groß, und eine Suche kann leicht fehlschlagen, wenn Sie das Bildlauffeld der Bildlaufleiste an eine zufällige Position ziehen. Aus diesem Grunde verhält sich das Bildlauffeld, als wäre es beidseitig mit einer Zugfeder verbunden, und verbleibt stets in der Mitte der Bildlaufleiste. In Anwendungen, die in systemeigenem Code geschrieben sind, können Sie einen Bildlauf nach oben oder unten durchführen; die Durchführung eines freien Bildlaufs ist jedoch nicht möglich.  
  
   In verwalteten Anwendungen ist die Disassembly auf eine Funktion begrenzt, und Sie können einen normalen Bildlauf durchführen.  
  
   Beachten Sie, dass die höheren Adressen am unteren Rand des Fensters angezeigt werden. Wenn Sie eine höhere Adresse anzeigen möchten, müssen Sie nach unten navigieren, nicht nach oben.  
  
#### <a name="to-move-up-or-down-one-instruction"></a>So wechseln Sie um eine Anweisung nach oben oder unten  
  
-   Klicken Sie auf den Pfeil am oberen oder unteren Ende der vertikalen Scrollleiste.  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeitsspeicher-Windows](../debugger/memory-windows.md)   
 [Vorgehensweise: Verwenden des Disassembierungsfensters](../debugger/how-to-use-the-disassembly-window.md)   
 [Anzeigen von Daten im Debugger](../debugger/viewing-data-in-the-debugger.md)