---
title: 'Fehler: Timeout beim Auswerten der Funktion &#39;Funktion&#39;. Der Abbruch musste auf unsichere Weise erfolgen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.topic: reference
f1_keywords:
- vs.debug.error.unsafe_func_eval_abort
ms.assetid: 0a9f70ed-21ad-4a10-8535-b9c5885ad8f4
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a27bf67770eef770fddef0301a804e6c45579539
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "86387121"
---
# <a name="error-evaluating-the-function-39function39-timed-out-and-needed-to-be-aborted-in-an-unsafe-way"></a>Fehler: Timeout beim Auswerten der Funktion &#39;Funktion&#39;. Der Abbruch musste auf unsichere Weise erfolgen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vollständiger Meldungstext: Timeout beim Auswerten der Funktion „Funktion“. Der Abbruch musste auf unsichere Weise erfolgen. Dies hat den Zielprozess ggf. beschädigt. 

Um das Überprüfen des Status von .NET-Objekten zu vereinfachen, zwingt der Debugger den debuggten Prozess automatisch zur Ausführung von zusätzlichem Code (in der Regel Eigenschaftengettermethoden und ToString-Funktionen). In den meisten Szenarien werden diese Funktionen schnell ausgeführt, und sie vereinfachen das Debuggen erheblich. Der Debugger führt die Anwendung jedoch nicht in einem Sandkasten aus. Folglich kann eine Getter-Methode für Eigenschaften oder eine ToString-Methode, die eine native Funktion aufruft, die nicht mehr reagiert, zu langen Timeouts führen, die möglicherweise nicht behebbar sind. Wenn diese Fehlermeldung angezeigt wird, ist dieser Fall eingetreten.
 
Ein häufiger Grund für dieses Problem liegt darin, dass der Debugger beim Auswerten einer Eigenschaft nur die Ausführung des zu überprüfenden Threads zulässt. Wenn die Eigenschaft also darauf wartet, dass andere Threads innerhalb der debuggten Anwendung ausgeführt werden, und wenn Sie darauf wartet, dass die .NET-Runtime nicht unterbrechen kann, tritt dieses Problem auf.
 
## <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler
 
Es gibt drei mögliche Lösungen für dieses Problem.
 
### <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>Lösung 1: Verhindern, dass der Debugger die Eigenschaftengetter- oder ToString-Methode aufruft
 
In der Fehlermeldung wird der Name der Funktion angegeben, die der Debugger aufzurufen versucht hat. Wenn es Ihnen möglich ist, diese Funktion zu ändern, können Sie verhindern, dass der Debugger die Eigenschaftengetter- oder ToString-Methode aufruft. Probieren Sie einen der folgenden Lösungsschritte aus:
 
* Ändern Sie die Methode in einen anderen Codetyp neben einer Eigenschaftengetter- oder ToString-Methode. Dadurch wird das Problem gelöst.
    - oder -
* (Für ToString) Definieren Sie ein DebuggerDisplay-Attribut für den Typ. Dann kann der Debugger etwas anderes als ToString auswerten.
    - oder -
* (Für einen Eigenschaftengetter) Legen Sie das Attribut `[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]` für die Eigenschaft fest. Dies kann sinnvoll sein, wenn Sie über eine Methode verfügen, die aus Gründen der API-Kompatibilität eine Eigenschaft bleiben muss, aber tatsächlich eine Methode sein sollte.
 
### <a name="solution-2-have-the-target-code-ask-the-debugger-to-abort-the-evaluation"></a>Lösung 2: Veranlassen, dass der Zielcode den Debugger zum Abbrechen der Auswertung auffordert
 
In der Fehlermeldung wird der Name der Funktion angegeben, die der Debugger aufzurufen versucht hat. Wenn die Eigenschaftengetter- oder ToString-Methode manchmal nicht ordnungsgemäß ausgeführt wird, insbesondere in Situationen, in denen der Code einen anderen Thread zum Ausführen von Code benötigt, kann die Implementierungsfunktion `System.Diagnostics.Debugger.NotifyOfCrossThreadDependency` aufrufen, um den Debugger zum Abbrechen der Funktionsauswertung aufzufordern. Bei dieser Lösung ist es immer noch möglich, diese Funktionen explizit auszuwerten. Das Standardverhalten besteht jedoch darin, dass die Ausführung beendet wird, wenn der NotifyOfCrossThreadDependency-Aufruf erfolgt.
 
### <a name="solution-3-disable-all-implicit-evaluation"></a>Lösung 3: Deaktivieren aller impliziten Auswertungen
 
Wenn das Problem durch die vorherigen Lösungen nicht behoben werden kann, navigieren Sie zu *Extras* / *Optionen*, und deaktivieren Sie die Einstellung *Debuggen* / *Allgemein* / *Eigenschaftenauswertung und andere implizite Funktionsaufrufe zulassen*. Dadurch werden die meisten impliziten Funktionsauswertungen deaktiviert, und das Problem sollte behoben sein.
