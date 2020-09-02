---
title: 'Vorgehensweise: Bildlauf nach oben oder unten im Arbeitsspeicher | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, paging up or down in memory
- memory, paging up or down
- Disassembly window, viewing memory space
- Memory window, paging up or down in memory
ms.assetid: 50b30a68-66f6-43f8-a48b-59ce12c95471
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cc05772e6376dbe151d5ca71b9ee221e61a7be88
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157858"
---
# <a name="how-to-page-up-or-down-in-memory"></a>Vorgehensweise: Bildlauf nach oben oder unten im Arbeitsspeicher
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Beim Anzeigen des Speicherinhalts im Fenster **Arbeitsspeicher** oder im Fenster **Disassemblierung** können Sie mithilfe der vertikalen Scrollleiste im Speicher nach oben oder unten navigieren.  
  
### <a name="to-page-up-or-down-in-memory"></a>So führen Sie im Speicher einen Bildlauf nach oben oder nach unten durch  
  
1. Für einen Bildlauf nach unten (Navigieren zu einer höheren Speicheradresse) klicken Sie auf die vertikale Bildlaufleiste unter dem Bildlauffeld.  
  
2. Für einen Bildlauf nach oben (Navigieren zu einer niedrigeren Speicheradresse) klicken Sie auf die vertikale Scrollleiste über dem Bildlauffeld.  
  
   Beachten Sie auch, dass das Verhalten der vertikalen Bildlaufleiste nicht dem Standardverhalten entspricht. Der Adressbereich eines modernen Computers ist äußerst groß, und eine Suche kann leicht fehlschlagen, wenn Sie das Bildlauffeld der Bildlaufleiste an eine zufällige Position ziehen. Aus diesem Grunde verhält sich das Bildlauffeld, als wäre es beidseitig mit einer Zugfeder verbunden, und verbleibt stets in der Mitte der Bildlaufleiste. In Anwendungen, die in systemeigenem Code geschrieben sind, können Sie einen Bildlauf nach oben oder unten durchführen; die Durchführung eines freien Bildlaufs ist jedoch nicht möglich.  
  
   In verwalteten Anwendungen ist die Disassembly auf eine Funktion begrenzt, und Sie können einen normalen Bildlauf durchführen.  
  
   Beachten Sie, dass die höheren Adressen am unteren Rand des Fensters angezeigt werden. Wenn Sie eine höhere Adresse anzeigen möchten, müssen Sie nach unten navigieren, nicht nach oben.  
  
#### <a name="to-move-up-or-down-one-instruction"></a>So wechseln Sie um eine Anweisung nach oben oder unten  
  
- Klicken Sie auf den Pfeil am oberen oder unteren Ende der vertikalen Scrollleiste.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Arbeitsspeicher Fenster](../debugger/memory-windows.md)   
 [Gewusst wie: Verwenden des disassemblierfensters](../debugger/how-to-use-the-disassembly-window.md)   
 [Anzeigen von Daten im Debugger](../debugger/viewing-data-in-the-debugger.md)
