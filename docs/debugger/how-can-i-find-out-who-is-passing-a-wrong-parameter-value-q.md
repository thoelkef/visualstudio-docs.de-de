---
title: Wie wird festgestellt, woher der falsche Parameterwert stammt? | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.parameters
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], parameters
- parameters [debugger]
- passing parameters, troubleshooting wrong values
- functions [debugger], detecting wrong parameter values
- parameter values, troubleshooting
ms.assetid: 1f1ae455-0e25-4e9d-b33f-53908f5bd6ce
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 77c4953840c879a14406003f0bafffe98908cd95
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-can-i-find-out-who-is-passing-a-wrong-parameter-value"></a>Wie wird festgestellt, woher der falsche Parameterwert stammt?
## <a name="problem-description"></a>Problembeschreibung  
 An eine Funktion wird der falsche Parameterwert übergeben. Diese Funktion wird von mehreren Stellen aus aufgerufen. Wie kann festgestellt werden, woher der falsche Wert stammt?  
  
## <a name="solution"></a>Lösung  
  
#### <a name="to-resolve-this-problem"></a>So beheben Sie dieses Problem  
  
1.  Legen Sie am Anfang der Funktion einen Positionshaltepunkt fest.  
  
2.  Mit der rechten Maustaste des Breakpoints, und wählen Sie **Bedingung**.  
  
3.  In der **Haltepunktbedingung** (Dialogfeld), klicken Sie auf die **Bedingung** Kontrollkästchen. Finden Sie unter [Erweiterte Haltepunkte](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression).  
  
4.  Geben Sie einen Ausdruck, z. B. `Var==3`, in das Textfeld ein, wobei `Var` der Name des Parameters ist, der den falschen Wert enthält, und `3` der übergebene falsche Wert.  
  
5.  Wählen Sie die **ist "true"** Optionsfeld aus, und klicken Sie auf die **OK** Schaltfläche.  
  
6.  Führen Sie nun das Programm erneut aus. Der Haltepunkt bewirkt, dass das Programm am Funktionsanfang anhält, sobald `Var` den Wert `3` hat.  
  
7.  Im Fenster Aufrufliste sehen Sie die aufrufende Funktion und können zu ihrem Quellcode navigieren. Weitere Informationen finden Sie unter [Vorgehensweise: Verwenden Sie das Fenster "Aufrufliste"](../debugger/how-to-use-the-call-stack-window.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von systemeigenem Code häufig gestellte Fragen](../debugger/debugging-native-code-faqs.md)   
 [Haltepunkte](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583)   
 [Debuggen von nativem Code](../debugger/debugging-native-code.md)