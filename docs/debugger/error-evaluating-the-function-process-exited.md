---
title: 'Fehler: Der Zielprozess wurde beim Auswerten der Funktion &#39;Funktion&#39; | Microsoft Docs'
ms.custom: ''
ms.date: 4/06/2018
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.process_exit_func_eval_abort
ms.technology: vs-ide-debug
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 620ff03ef364c21e20151547effe8bfbf5935fe7
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
---
# <a name="error-the-target-process-exited-while-evaluating-the-function-39function39"></a>Fehler: Der Zielprozess wurde beim Auswerten der Funktion &#39;Funktion&#39;

Vollständiger Text der Fehlermeldung: der Zielprozess beim Auswerten der Funktion 'Funktion' wurde beendet. Finden Sie im Ausgabefenster der Zielprozess Exitcode.

Zum Überprüfen des Status von Objekten .NET zu vereinfachen, wird der Debugger automatisch einen debuggten Prozess zum Ausführen zusätzlichen Codes erzwingen (i. d. r. Eigenschaft Abrufmethoden und `ToString` Funktionen). In den meisten Szenarien werden diese Funktionen erfolgreich abgeschlossen oder lösen Ausnahmen, die vom Debugger abgefangen werden können. Es gibt jedoch einige Situationen, in denen Ausnahmen abgefangen werden können, da sie Kernel Grenzen plattformübergreifende, benötigen Benutzer meldungsweiterleitung oder nicht behebbar sind. Als ein Ergebnis, einen Getter für eine Eigenschaft oder der ToString-Methode, die Code ausführt, beendet, entweder explizit den Prozess (z. B. ruft `ExitProcess()`) oder löst eine nicht behandelte Ausnahme, die abgefangen werden kann (z. B. `StackOverflowException`) wird beendet die debuggten Prozess und Ende der Debugsitzung. Wenn Sie diese Fehlermeldung auftritt, ist dies aufgetreten.
 
Eine häufige Ursache für dieses Problem ist, dass beim wertet der Debugger einer Eigenschaft, die sich selbst aufruft, dies zu einer Stapelüberlaufausnahme führen kann. Die Stapelüberlaufausnahme kann nicht wiederhergestellt werden, und der Zielprozess wird beendet.
 
## <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler
 
Es gibt zwei mögliche Lösungen für dieses Problem.
 
### <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>Lösung #1: Verhindern Sie, dass des Debuggers Aufrufen der Getter-Eigenschaft oder der ToString-Methode 

Die Fehlermeldung informiert Sie den Namen der Funktion, die der Debugger versucht hat, aufrufen. Mit dem Namen der Funktion können Sie versuchen, diese Funktion erneut auswerten der **Direktfenster** Fenster aus, um die Auswertung zu debuggen. Debuggen ist möglich, bei der Auswertung von der **Direktfenster** Fenster daran, dass im Gegensatz zu impliziten auswertungen aus der **"Auto" / "lokal" / Überwachen** Windows, unterbricht der Debugger bei Ausnahmefehlern.

Wenn Sie diese Funktion ändern können, können Sie verhindern den Debugger den Eigenschaftengetter aufrufen oder `ToString` Methode. Führen Sie eine der folgenden:
 
* Ändern Sie die Methode, um einen anderen Typ von Code zusätzlich einen Eigenschaften-Getter oder ToString-Methode und das Problem ist natürlich.
    - oder - 
* (Für `ToString`) definieren eine `DebuggerDisplay` Attribut auf den Typ, und Sie können den Debugger etwas anders als ausgewertet haben `ToString`.
    - oder - 
* (Für einen Eigenschaften-Getter) Versetzen der `[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]` Attribut für die Eigenschaft. Dies ist hilfreich, wenn Sie eine Methode verfügen, die eine Eigenschaft API aus Kompatibilitätsgründen weiterhin auf, aber es sollte eigentlich eine Methode sein.

Wenn Sie diese Methode nicht ändern, können Sie möglicherweise den Zielprozess an eine alternative Anweisung unterbrochen, und wiederholen die Auswertung.
 
### <a name="solution-2-disable-all-implicit-evaluation"></a>Lösung #2: Deaktivieren Sie alle implizite Auswertung
 
Wenn die vorherigen Lösungen das Problem nicht beheben, wechseln Sie zu **Tools** > **Optionen**, und deaktivieren Sie die Einstellung **Debuggen**  >   **Allgemeine** > **eigenschaftenauswertung und andere implizite Funktionsaufrufe**. Dadurch wird die auswertungen für die meisten impliziten Funktionen deaktiviert und sollte das Problem zu beheben.



  
