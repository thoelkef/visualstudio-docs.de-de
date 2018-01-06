---
title: Verlaufsbezogenes Debugging | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7cc5ddf2-2f7c-4f83-b7ca-58e92e9bfdd2
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 0107109cfa5b15b8db0c84b304e8e1daae5dfbfa
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="historical-debugging"></a>Verlaufsbezogenes debugging
Das verlaufsbezogene Debuggen ist ein Debug-Modus, der von den durch IntelliTrace erfassten Informationen abhängig ist. Dadurch können Sie die Ausführung Ihrer Anwendung rückwärts und vorwärts durchlaufen und ihren Status überprüfen.  
  
 Sie können IntelliTrace in der Visual Studio Enterprise Edition verwenden(jedoch nicht in der Professional oder Community Edition).  
  
## <a name="why-use-historical-debugging"></a>Verwenden Sie Warum verlaufsbezogenes debugging?  
 Das Festlegen von Haltepunkten zum Auffinden von Fehlern ist eher eine unsichere Angelegenheit. Sie legen einen Haltepunkt in der Nähe der Stelle im Code fest, an der Sie einen Fehler vermuten, führen dann die Anwendung im Debugger aus, hoffen, dass der Haltepunkt erreicht wird, und dass die Stelle, an der die Ausführung unterbrochen wurde, die Ursache des Fehlers aufdeckt. Wenn dies nicht der Fall ist, versuchen, einen Haltepunkt an anderer Stelle im Code festlegen, und führen den Debugger, die Testschritte fortlaufend ausgeführt, bis Sie das Problem gefunden haben.  
  
 ![Festlegen eines Haltepunkts](../debugger/media/breakpointprocesa.png "BreakpointProcesa")  
  
 Sie können mit IntelliTrace und dem verlaufsbezogenen debugging in Ihrer Anwendung durchgehen und überprüfen dessen Status (Aufruflisten- und lokale Variablen), ohne Haltepunkte festzulegen, Debuggen neu starten und Testschritte zu wiederholen. Dadurch sparen Sie viel Zeit, besonders wenn der Fehler sich tief in einem Testszenario verbirgt, das azum Ausführen viel Zeit erfordert.  
  
## <a name="how-do-i-start-using-historical-debugging"></a>Wie beginne ich mit dem verlaufsbezogenen Debuggen?  
 IntelliTrace ist standardmäßig aktiviert. Sie müssen lediglich lediglich entscheiden, welche Ereignisse und Funktionsaufrufe für Sie von Interesse sind, und gibt an, ob Sie Momentaufnahmen Ihrer vollständigem Anwendungszustand anzeigen möchten. Weitere Informationen zum definieren, was Sie suchen möchten, finden Sie unter [IntelliTrace-Features](../debugger/intellitrace-features.md).  

 - Momentaufnahmen mit verlaufsbezogenem debugging finden Sie unter [Anzeigen von Momentaufnahmen mithilfe von IntelliTrace-Schritt-zurück](../debugger/how-to-use-intellitrace-step-back.md)
 - Wie Variablen überprüfen, und Navigieren im Code finden Sie unter [überprüfen Sie Ihre app mit verlaufsbezogenem debugging](../debugger/historical-debugging-inspect-app.md)
 - Weitere Informationen zum Debuggen mit IntelliTrace-Ereignissen finden Sie unter [Exemplarische Vorgehensweise: Verwenden von IntelliTrace](../debugger/walkthrough-using-intellitrace.md).