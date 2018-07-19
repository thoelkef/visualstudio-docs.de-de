---
title: Wie kann festgestellt werden, bei welchem Aufruf ein Fehler aufgetreten ist, wenn eine Funktion sehr häufig aufgerufen wird? | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.functions
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- conditional breakpoints
- errors [debugger], function calls
- breakpoints, troubleshooting
- errors [debugger], finding which function call failed
- failures
- location breakpoint call failures
- errors [Visual Studio], function calls
- hit counts
- function calls, failure
- functions [debugger]
- Skip Count
ms.assetid: 66cfac86-f5be-4d3a-9329-d44cd74bc586
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bdae654dacf7c5965d51cc39f7970bd0347b9dcf
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2018
ms.locfileid: "37056234"
---
# <a name="when-calling-a-function-hundreds-of-times-how-do-i-know-which-call-failed"></a>Wie kann festgestellt werden, bei welchem Aufruf ein Fehler aufgetreten ist, wenn eine Funktion sehr häufig aufgerufen wird?
## <a name="problem-description"></a>Problembeschreibung  
 Das Programm schlägt bei einem Aufruf einer bestimmten Funktion mit dem Namen `CnvtV` fehl. Zuvor hat das Programm die Funktion jedoch mehrere Hundert Male aufgerufen. Wenn ein Positionshaltepunkt für `CnvtV` festgelegt wird, hält das Programm bei jedem Aufruf der Funktion an, was nicht beabsichtigt ist. Da nicht bekannt ist, welche Bedingungen den fehlschlagenden Aufruf verursachen, kann kein bedingter Haltepunkt festgelegt werden. Welche Möglichkeiten gibt es?  
  
## <a name="solution"></a>Lösung  
 Sie können einen Haltepunkt festlegen, für die Funktion der **Trefferanzahl** Feld auf einen Wert, der so hoch, dass es nie erreicht wird. In diesem Fall, weil Sie glauben, die Funktion dass `CnvtV` wird aufgerufen, ein paar Hundert Male, Sie können festlegen, **Trefferanzahl** zu 1.000 oder mehr. Führen Sie dann das Programm aus, und warten Sie, bis der Aufruf fehlschlägt. Sobald dies der Fall ist, öffnen Sie das Fenster "Haltepunkte" und überprüfen die Haltepunktliste. Der für `CnvtV` festgelegte Haltepunkt wird, gefolgt von der Trefferanzahl und der Anzahl der noch verbleibenden Iterationen, angezeigt:  
  
```cpp
CnvtV(int) (no condition) when hit count is equal to 1000 (currently 101)  
```  
  
 Jetzt wissen Sie, dass die Funktion bei Aufruf Nr. 101 fehlgeschlagen ist. Wenn Sie nun den Haltepunkt auf eine Trefferanzahl von 101 zurücksetzen und das Programm erneut ausführen, hält es an dem `CnvtV`-Aufruf an, der zuvor den Fehler verursacht hat.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von nativem Code häufig gestellte Fragen](../debugger/debugging-native-code-faqs.md)   
 [Festlegen von Haltepunkten](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583)   
 [Debuggen von nativem Code](../debugger/debugging-native-code.md)
