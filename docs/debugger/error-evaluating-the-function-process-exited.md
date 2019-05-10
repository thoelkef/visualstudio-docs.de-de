---
title: 'Fehler: Der Zielprozess wurde beendet mit Code &#39;Code&#39; beim Auswerten der Funktion &#39;Funktion&#39; | Microsoft-Dokumentation'
ms.date: 4/06/2018
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.process_exit_during_func_eval
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 75d82b6011a0dfa7f2c388e7d5f39a9ebabcd663
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62850817"
---
# <a name="error-the-target-process-exited-with-code-39code39-while-evaluating-the-function-39function39"></a>Fehler: Der Zielprozess wurde beendet mit Code &#39;Code&#39; beim Auswerten der Funktion &#39;Funktion&#39;

Vollständige Nachrichtentext: Der Zielprozess wurde mit Code 'Code' beim Auswerten der Funktion 'Funktion' beendet.

Zum Überprüfen des Status von Objekten für .NET zu vereinfachen, der Debugger wird automatisch erzwingen, dass den gedebuggten Prozess zum Ausführen von zusätzlichen Codes (in der Regel die Eigenschaft Getter-Methoden und `ToString` Funktionen). In den meisten Szenarien werden diese Funktionen erfolgreich abgeschlossen oder Auslösen von Ausnahmen, die vom Debugger abgefangen werden kann. Es gibt jedoch einige Situationen, in denen Ausnahmen abgefangen werden können, da diese Kernel-Grenzen überschreiten, müssen die Benutzer-meldungsweiterleitung oder nicht behebbar sind. Als ein Ergebnis, einen Eigenschaftengetter oder die ToString-Methode, die Code ausführt, beendet, dass entweder explizit den Prozess (z. B. Aufrufe `ExitProcess()`) oder eine nicht behandelte Ausnahme auslöst, die nicht abgefangen werden kann (z. B. `StackOverflowException`) wird beendet die debuggten Prozess und Ende der Debugsitzung. Wenn Sie diese Fehlermeldung auftritt, ist dies aufgetreten.

Ein häufiger Grund für dieses Problem ist, dass wenn der Debugger eine Eigenschaft, die sich selbst aufruft wertet, dies in einer Stapelüberlauf-Ausnahmen führen kann. Die Stapelüberlaufausnahme kann nicht wiederhergestellt werden, und der Zielprozess wird beendet.

## <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

Es gibt zwei mögliche Lösungen für dieses Problem.

### <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>#1-Lösung: Verhindern Sie, dass des Debuggers beim Aufrufen der Getter-Eigenschaft oder die ToString-Methode 

Die Fehlermeldung informiert Sie den Namen der Funktion, die der Debugger versucht hat, aufgerufen. Mit dem Namen der Funktion können Sie versuchen, erneut auswerten dieser Funktion aus der **direkt** Fenster aus, um die Auswertung zu debuggen. Debuggen ist möglich, bei der Auswertung von der **direkt** Fenster daran, im Gegensatz zu impliziten auswertungen aus der **Auto/lokal/Überwachung** Windows, unterbricht der Debugger bei Ausnahmefehlern.

Wenn Sie diese Funktion ändern können, können Sie verhindern den Debugger den Eigenschaftengetter aufrufen oder `ToString` Methode. Versuchen Sie Folgendes:

* Ändern Sie die Methode in eine andere Art von Code als einen Eigenschaften-Getter oder ToString-Methode und das Problem werden verschwinden.
    - oder - 
* (Für `ToString`) definieren eine `DebuggerDisplay` Attribut für den Typ, und Sie können den Debugger, die etwas anders als ausgewertet haben `ToString`.
    - oder - 
* (Für einen Eigenschaften-Getter) Platzieren der `[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]` Attribut für die Eigenschaft. Dies ist hilfreich, wenn Sie eine Methode, die eine Eigenschaft aus Gründen der Kompatibilität von API-bleiben muss verfügen, aber es sollte eigentlich eine Methode sein.

Wenn Sie diese Methode nicht ändern, können Sie möglicherweise den Zielprozess an eine alternative Anweisung unterbrochen, und wiederholen die Auswertung.

### <a name="solution-2-disable-all-implicit-evaluation"></a>Lösung #2: Deaktivieren Sie alle implizite Auswertung

Wenn die vorherigen Lösungen das Problem nicht beheben, wechseln Sie zu **Tools** > **Optionen**, und deaktivieren Sie die Einstellung **Debuggen**  >   **Allgemeine** > **eigenschaftenauswertung und andere implizite Funktionsaufrufe**. Dadurch werden die meisten Evaluierungsversionen von impliziten Funktionen deaktiviert und sollte das Problem zu beheben.
