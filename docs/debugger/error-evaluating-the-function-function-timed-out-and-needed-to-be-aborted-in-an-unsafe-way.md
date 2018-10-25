---
title: 'Fehler: Die Funktion auswerten &#39;Funktion&#39; Timeout und musste auf unsichere Weise abgebrochen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.unsafe_func_eval_abort
ms.technology: vs-ide-debug
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1f36e56b2870d5f099a3b8ed95265fe7e2d688ff
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49934443"
---
# <a name="error-evaluating-the-function-39function39-timed-out-and-needed-to-be-aborted-in-an-unsafe-way"></a>Fehler: Die Funktion auswerten &#39;Funktion&#39; Timeout und musste auf unsichere Weise abgebrochen werden

Vollständiger Nachrichtentext: Timeout beim Auswerten der Funktion 'Funktion', und musste auf unsichere Weise abgebrochen werden. Dies kann den Zielprozess beschädigt. 

Zum Überprüfen des Status von Objekten für .NET zu vereinfachen, wird der Debugger automatisch den gedebuggten Prozess zum Ausführen von zusätzlichen Codes (in der Regel die Eigenschaft Getter-Methoden und Funktionen mit ToString) erzwungen. In den meisten Szenarien alle diese Funktionen schnell ausführen und Debuggen deutlich vereinfacht. Der Debugger nicht jedoch die Anwendung in einer Sandbox ausgeführt wird. Daher kann eine Abruf- oder die ToString-Methode, die eine native Funktion aufruft, das hängt zu lange Timeouts führen, die nicht wiederhergestellt werden kann. Wenn Sie diese Fehlermeldung auftritt, ist dies aufgetreten.
 
Ein häufiger Grund für dieses Problem ist, dass wenn der Debugger eine Eigenschaft ausgewertet wird, nur den Thread wird überprüft, um Sie ausführen können. Also wird ob die Eigenschaft in der debuggten Anwendung Ausführung anderer Threads warten ist und wenn es auf eine Weise, die die .NET Runtime unterbrechen, können nicht im Wartezustand befindet, dieses Problem auftreten.
 
## <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler
 
Es gibt drei mögliche Lösungen für dieses Problem.
 
### <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>Lösung #1: Verhindern Sie, dass des Debuggers beim Aufrufen der Getter-Eigenschaft oder die ToString-Methode
 
Die Fehlermeldung informiert Sie den Namen der Funktion, die der Debugger versucht hat, aufgerufen. Wenn Sie diese Funktion ändern können, können Sie verhindern, dass den Debugger die Getter für eine Eigenschaft oder die ToString-Methode aufrufen. Versuchen Sie Folgendes:
 
* Ändern Sie die Methode in eine andere Art von Code als einen Eigenschaften-Getter oder ToString-Methode und das Problem werden verschwinden.
    - oder - 
* (Für ToString) Einem DebuggerDisplay-Attribut für den Typ definieren und Sie können den Debugger, einen anderen Wert als ToString ausgewertet.
    - oder - 
* (Für einen Eigenschaften-Getter) Platzieren der `[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]` Attribut für die Eigenschaft. Dies ist hilfreich, wenn Sie eine Methode verwenden, die eine Eigenschaft aus Gründen der Kompatibilität von API-bleiben muss, aber es sollte eigentlich eine Methode sein.
 
### <a name="solution-2-have-the-target-code-ask-the-debugger-to-abort-the-evaluation"></a>Lösung #2: Haben Sie den Zielcode, bitten Sie den Debugger an die Auswertung Abbrechen
 
Die Fehlermeldung informiert Sie den Namen der Funktion, die der Debugger versucht hat, aufgerufen. Wenn der Eigenschaftengetter oder eine ToString-Methode in einigen Fällen nicht ordnungsgemäß ausgeführt werden, insbesondere in Situationen, in denen das Problem, das Code einem anderen Thread zum Ausführen von Code benötigt, und die implementierungsfunktion aufrufen kann `System.Diagnostics.Debugger.NotifyOfCrossThreadDependency` , bitten Sie den Debugger an die Funktion abgebrochen nützlich. Mit dieser Lösung ist es weiterhin möglich, diese Funktionen bewerten, aber das Standardverhalten ist, dass die Ausführung hält bei der NotifyOfCrossThreadDependency des Anrufs gewählt.
 
### <a name="solution-3-disable-all-implicit-evaluation"></a>Lösung #3: Deaktivieren Sie alle implizite Auswertung
 
Wenn die vorherigen Lösungen das Problem nicht beheben, wechseln Sie zu *Tools* > *Optionen*, und deaktivieren Sie die Einstellung *Debuggen*  >   *Allgemeine* > *eigenschaftenauswertung und andere implizite Funktionsaufrufe*. Dadurch werden die meisten Evaluierungsversionen von impliziten Funktionen deaktiviert und sollte das Problem zu beheben.



  
