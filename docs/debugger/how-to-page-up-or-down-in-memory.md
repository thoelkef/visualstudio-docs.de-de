---
title: 'Vorgehensweise: Seite nach oben oder unten im Arbeitsspeicher | Microsoft-Dokumentation'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b554a197afe2deef3619551af2d45d4a80708afe
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56715361"
---
# <a name="how-to-page-up-or-down-in-memory"></a>Gewusst wie: Bildlauf nach oben oder unten im Arbeitsspeicher

Beim Anzeigen des Speicherinhalts im Fenster **Arbeitsspeicher** oder im Fenster **Disassemblierung** können Sie mithilfe der vertikalen Scrollleiste im Speicher nach oben oder unten navigieren.

### <a name="to-page-up-or-down-in-memory"></a>So führen Sie im Speicher einen Bildlauf nach oben oder nach unten durch

1. Für einen Bildlauf nach unten (Navigieren zu einer höheren Speicheradresse) klicken Sie auf die vertikale Bildlaufleiste unter dem Bildlauffeld.

2. Für einen Bildlauf nach oben (Navigieren zu einer niedrigeren Speicheradresse) klicken Sie auf die vertikale Scrollleiste über dem Bildlauffeld.

   Beachten Sie auch, dass das Verhalten der vertikalen Bildlaufleiste nicht dem Standardverhalten entspricht. Der Adressbereich eines modernen Computers ist äußerst groß, und eine Suche kann leicht fehlschlagen, wenn Sie das Bildlauffeld der Bildlaufleiste an eine zufällige Position ziehen. Aus diesem Grunde verhält sich das Bildlauffeld, als wäre es beidseitig mit einer Zugfeder verbunden, und verbleibt stets in der Mitte der Bildlaufleiste. In Anwendungen, die in systemeigenem Code geschrieben sind, können Sie einen Bildlauf nach oben oder unten durchführen; die Durchführung eines freien Bildlaufs ist jedoch nicht möglich.

   In verwalteten Anwendungen ist die Disassembly auf eine Funktion begrenzt, und Sie können einen normalen Bildlauf durchführen.

   Beachten Sie, dass die höheren Adressen am unteren Rand des Fensters angezeigt werden. Wenn Sie eine höhere Adresse anzeigen möchten, müssen Sie nach unten navigieren, nicht nach oben.

#### <a name="to-move-up-or-down-one-instruction"></a>So wechseln Sie um eine Anweisung nach oben oder unten

-   Klicken Sie auf den Pfeil am oberen oder unteren Ende der vertikalen Scrollleiste.

## <a name="see-also"></a>Siehe auch
- [Fenster "Arbeitsspeicher"](../debugger/memory-windows.md)
- [Gewusst wie: Verwenden des Disassembierungsfensters](../debugger/how-to-use-the-disassembly-window.md)
- [Anzeigen von Daten im Debugger](../debugger/viewing-data-in-the-debugger.md)