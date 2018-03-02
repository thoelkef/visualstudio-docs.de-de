---
title: "Fehler: Auswerten der Funktion &#39; Function &#39; Timeout und benötigt, um auf unsichere Weise abgebrochen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vs.debug.error.unsafe_func_eval_abort
ms.technology: vs-ide-debug
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 4d0d03efbb844c29195eca7c13303a850c168e0f
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/28/2018
---
# <a name="error-evaluating-the-function-39function39-timed-out-and-needed-to-be-aborted-in-an-unsafe-way"></a>Fehler: Auswerten der Funktion &#39; Function &#39; Timeout und benötigt, um auf unsichere Weise abgebrochen

Vollständiger Text der Fehlermeldung: Auswerten der Funktion 'Funktion' Timeout und erforderlich, um auf unsichere Weise abgebrochen werden. Dies kann den Zielprozess beschädigt. 

Überprüfen Sie den Status von .NET-Objekten zu vereinfachen, wird der Debugger automatisch einen debuggten Prozess zum Ausführen zusätzlichen Codes (in der Regel Eigenschaft Abrufmethoden und ToString Funktionen) erzwungen. In den meisten Szenarien alle diese Funktionen schnell abgeschlossen und Debuggen deutlich vereinfacht. Der Debugger nicht jedoch die Anwendung in einem Sandkasten ausgeführt werden. Daher kann eine Abruf- oder ToString-Methode, die in einer systemeigenen Funktion aufruft, die hängt zu lange Timeouts führen, die möglicherweise nicht wiederhergestellt werden. Wenn Sie diese Fehlermeldung auftritt, ist dies aufgetreten.
 
Eine häufige Ursache für dieses Problem ist, dass wenn der Debugger wertet eine Eigenschaft aus, nur den Thread wird überprüft, um ausführen können. Daher erfolgt wartet die Eigenschaft für andere Threads in der gedebuggten Anwendung ausführen und diese auf eine Weise wartet, die der .NET Common Language Runtime zu unterbrechen, können nicht, dieses Problem.
 
## <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler
 
Es gibt drei mögliche Lösungen für dieses Problem.
 
### <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>Lösung #1: Verhindern Sie, dass des Debuggers Aufrufen der Getter-Eigenschaft oder der ToString-Methode
 
Die Fehlermeldung informiert Sie den Namen der Funktion, die der Debugger versucht hat, aufrufen. Wenn Sie diese Funktion ändern können, können Sie verhindern, dass den Debugger die Getter für eine Eigenschaft oder der ToString-Methode aufrufen. Führen Sie eine der folgenden:
 
* Ändern Sie die Methode, um einen anderen Typ von Code zusätzlich einen Eigenschaften-Getter oder ToString-Methode und das Problem ist natürlich.
    - oder - 
* (Für ToString) DebuggerDisplay-Attribut für den Typ definieren und Sie können den Debugger etwas anderes als ToString auswerten.
    - oder - 
* (Für einen Eigenschaften-Getter) Versetzen der `[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]` Attribut für die Eigenschaft. Dies ist hilfreich, wenn Sie eine Methode besitzen, die eine Eigenschaft aus Kompatibilitätsgründen API bleiben muss, aber es sollte eigentlich eine Methode sein.
 
### <a name="solution-2-have-the-target-code-ask-the-debugger-to-abort-the-evaluation"></a>Lösung #2: Haben Sie den Zielcode, bitten Sie den Debugger zum Abbrechen der Auswertung
 
Die Fehlermeldung informiert Sie den Namen der Funktion, die der Debugger versucht hat, aufrufen. Wenn der Getter für eine Eigenschaft oder der ToString-Methode in einigen Fällen nicht ordnungsgemäß ausgeführt werden, besonders in Situationen, in denen das Problem ist, benötigt der Code einem anderen Thread zum Ausführen von Code, und klicken Sie dann die Implementierung-Funktion aufrufen kann `System.Diagnostics.Debugger.NotifyOfCrossThreadDependency` , bitten Sie den Debugger an die Funktion abgebrochen Evaluation. Mit dieser Lösung ist weiterhin möglich, diese Funktionen explizit ausgewertet, aber das Standardverhalten besteht, dass der Aufruf NotifyOfCrossThreadDependency erfolgt die Ausführung beendet.
 
### <a name="solution-3-disable-all-implicit-evaluation"></a>Lösung #3: Deaktivieren Sie alle implizite Auswertung
 
Wenn die vorherigen Lösungen das Problem nicht beheben, wechseln Sie zu *Tools* > *Optionen*, und deaktivieren Sie die Einstellung *Debuggen*  >   *Allgemeine* > *eigenschaftenauswertung und andere implizite Funktionsaufrufe*. Dadurch wird die auswertungen für die meisten impliziten Funktionen deaktiviert und sollte das Problem zu beheben.



  
