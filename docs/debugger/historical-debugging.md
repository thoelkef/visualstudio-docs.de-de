---
title: Verlaufsbezogenes Debugging | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7cc5ddf2-2f7c-4f83-b7ca-58e92e9bfdd2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0a622fcb91ad40e7d0777f37ce87e9a2cb950695
ms.sourcegitcommit: a749c287ec7d54148505978e8ca55ccd406b71ee
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/21/2018
ms.locfileid: "46542402"
---
# <a name="historical-debugging"></a>Verlaufsbezogenes Debuggen
Das verlaufsbezogene Debuggen ist ein Debug-Modus, der von den durch IntelliTrace erfassten Informationen abhängig ist. Dadurch können Sie die Ausführung Ihrer Anwendung rückwärts und vorwärts durchlaufen und ihren Status überprüfen.  
  
 Sie können IntelliTrace in der Visual Studio Enterprise Edition verwenden(jedoch nicht in der Professional oder Community Edition).  
  
## <a name="why-use-historical-debugging"></a>Verwenden Sie Warum verlaufsbezogenes debugging?  
 Das Festlegen von Haltepunkten zum Auffinden von Fehlern ist eher eine unsichere Angelegenheit. Sie legen einen Haltepunkt in der Nähe der Stelle im Code fest, an der Sie einen Fehler vermuten, führen dann die Anwendung im Debugger aus, hoffen, dass der Haltepunkt erreicht wird, und dass die Stelle, an der die Ausführung unterbrochen wurde, die Ursache des Fehlers aufdeckt. Wenn dies nicht der Fall ist, müssen Sie versuchen, einen Haltepunkt an anderer Stelle im Code festlegen und Testschritte immer wieder ausführen, bis Sie das Problem ermittelt den Debugger erneut.  
  
 ![Festlegen eines Haltepunkts](../debugger/media/breakpointprocesa.png "BreakpointProcesa")  
  
 Sie können mit IntelliTrace und dem verlaufsbezogenen debugging in Ihrer Anwendung durchgehen, und überprüfen den Zustand (Aufrufliste und lokale Variablen), ohne Haltepunkte festzulegen, Debuggen neu starten und Testschritte zu wiederholen. Dadurch sparen Sie viel Zeit, besonders wenn der Fehler sich tief in einem Testszenario verbirgt, das azum Ausführen viel Zeit erfordert.  
  
## <a name="how-do-i-start-using-historical-debugging"></a>Wie beginne ich mit der verlaufsbezogenen Debugging?  
 IntelliTrace ist standardmäßig aktiviert. Sie müssen lediglich lediglich entscheiden, welche Ereignisse und Funktionsaufrufe für Sie von Interesse sind, und gibt an, ob Sie Momentaufnahmen des Zustands vollständige Anwendung anzeigen möchten. Weitere Informationen zu definieren, was Sie suchen möchten, finden Sie unter [IntelliTrace-Funktionen](../debugger/intellitrace-features.md).  

 - Zum Anzeigen von Momentaufnahmen mit verlaufsbezogenen Debuggen finden Sie unter [überprüfen Sie die vorherigen app-Status, die mit IntelliTrace](../debugger/view-historical-application-state.md)
 - So untersuchen Sie Variablen, und Navigieren im Code finden Sie unter [untersuchen Ihrer app mit verlaufsbezogenem debugging](../debugger/historical-debugging-inspect-app.md)
 - Weitere Informationen zum Debuggen mit IntelliTrace-Ereignissen finden Sie unter [Exemplarische Vorgehensweise: Verwenden von IntelliTrace](../debugger/walkthrough-using-intellitrace.md).