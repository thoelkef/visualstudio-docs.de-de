---
title: Verlaufsbezogenes Debugging | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7cc5ddf2-2f7c-4f83-b7ca-58e92e9bfdd2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: edf0bc2b233a44893e9a526e172fa75043ebaa42
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56689264"
---
# <a name="historical-debugging-c-visual-basic-c"></a>Verlaufsbezogenes debugging (C#, Visual Basic, C++)

Das verlaufsbezogene Debuggen ist ein Debug-Modus, der von den durch IntelliTrace erfassten Informationen abhängig ist. Dadurch können Sie die Ausführung Ihrer Anwendung rückwärts und vorwärts durchlaufen und ihren Status überprüfen.

 Sie können IntelliTrace in der Visual Studio Enterprise Edition verwenden(jedoch nicht in der Professional oder Community Edition).

## <a name="why-use-historical-debugging"></a>Warum verlaufsbezogenes Debuggen?

 Das Festlegen von Haltepunkten zum Auffinden von Fehlern ist eher eine unsichere Angelegenheit. Sie legen einen Haltepunkt in der Nähe der Stelle im Code fest, an der Sie einen Fehler vermuten, führen dann die Anwendung im Debugger aus, hoffen, dass der Haltepunkt erreicht wird, und dass die Stelle, an der die Ausführung unterbrochen wurde, die Ursache des Fehlers aufdeckt. Wenn dies nicht der Fall ist, müssen Sie versuchen, einen Haltepunkt an anderer Stelle im Code festzulegen und den Debugger erneut auszuführen. Diese Testschritte müssen Sie so oft wiederholen, bis Sie das Problem gefunden haben.

 ![Festlegen eines Haltepunkts](../debugger/media/breakpointprocesa.png "BreakpointProcesa")

 Mit IntelliTrace und dem verlaufsbezogenen Debugging können Sie Ihre Anwendung durchgehen und den Status überprüfen (Aufrufliste und lokale Variablen), ohne Haltepunkte festzulegen, den Debugvorgang neu zu starten und die Testschritte zu wiederholen. Dadurch sparen Sie viel Zeit, besonders wenn der Fehler sich tief in einem Testszenario verbirgt, das azum Ausführen viel Zeit erfordert.

## <a name="how-do-i-start-using-historical-debugging"></a>Wie beginne ich mit dem verlaufsbezogenen Debuggen?

 IntelliTrace ist standardmäßig aktiviert. Sie müssen lediglich lediglich entscheiden, welche Ereignisse und Funktionsaufrufe für Sie von Interesse sind, und gibt an, ob Sie Momentaufnahmen des Zustands vollständige Anwendung anzeigen möchten. Weitere Informationen zum Definieren von Elementen, die Sie suchen möchten, finden Sie unter [IntelliTrace-Funktionen](../debugger/intellitrace-features.md). Unterstützung von Funktionen variiert je nach Sprache und die app Typ.

 - Zum Anzeigen von Momentaufnahmen mit verlaufsbezogenen Debuggen finden Sie unter [überprüfen Sie die vorherigen app-Status, die mit IntelliTrace](../debugger/view-historical-application-state.md)
 - So untersuchen Sie Variablen, und Navigieren im Code finden Sie unter [untersuchen Ihrer app mit verlaufsbezogenem debugging](../debugger/historical-debugging-inspect-app.md)
 - Weitere Informationen zum Debuggen mit IntelliTrace-Ereignissen finden Sie unter [Exemplarische Vorgehensweise: Verwenden von IntelliTrace](../debugger/walkthrough-using-intellitrace.md).