---
title: Hinzufügen von Kommentaren Sperrverhalten | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _Releases_nonreentrant_lock_
- _Lock_kind_mutex_
- _Lock_kind_critical_section_
- _Acquires_lock_
- _Releases_lock_
- _Has_lock_kind_
- _Releases_exclusive_lock_
- _Post_same_lock_
- _Requires_exclusive_lock_held_
- _Requires_shared_lock_held_
- _Lock_kind_semaphore_
- _Requires_lock_held_
- _Acquires_exclusive_lock_
- _Create_lock_level_
- _Acquires_nonreentrant_lock_
- _Releases_shared_lock_
- _Has_lock_level_
- _Lock_kind_spin_lock_
- _Requires_lock_not_held_
- _Acquires_shared_lock_
- _Requires_no_locks_held_
- _Lock_level_order_
- _Lock_kind_event_
ms.assetid: 07769c25-9b97-4ab7-b175-d1c450308d7a
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: 66c4aafb380d50ec0faafce931b8ce73e5138e6f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68157110"
---
# <a name="annotating-locking-behavior"></a>Hinzufügen einer Anmerkung zum Sperrverhalten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Um Fehler bei der Parallelität in einem Multithreadprogramm zu vermeiden, führen Sie eine entsprechende Sperren Disziplin immer, und Verwenden von SAL-Anmerkungen an.  
  
 Fehler bei der Parallelität sind bekanntermaßen schwierig zu reproduzieren, diagnostizieren und zu debuggen, da sie nicht deterministisch sind. Argumentation Thread überlappen ist bestenfalls schwierig und unpraktisch wird, wenn Sie einen Codeabschnitt entwerfen, die mehr als ein paar Threads hat. Aus diesem Grund ist es empfiehlt sich, eine Sperre Disziplin in Ihre Multithreadprogramme zu folgen. Z. B. eine Sperre Reihenfolge obeying, während mehrere Sperren kann Deadlocks zu vermeiden, und die richtige guarding Sperre abrufen, bevor Sie den Zugriff auf eine freigegebene Ressource verhindert, dass Racebedingungen.  
  
 Leider können scheinbar einfache Sperre Regeln überraschend schwierig in der Praxis sein. Eine grundlegende Einschränkung in der heutigen Programmiersprachen und -Compiler ist, dass sie nicht direkt die Spezifikation und die Analyse der parallelitätsanforderungen unterstützen. Programmierer müssen um informellen Codekommentare, die zum Ausdrücken von seiner Wahlabsicht darüber, wie sie Sperren verwenden.  
  
 Parallelität SAL-Anmerkungen werden entwickelt, um Hilfe bei der Angabe von Nebeneffekten, Sperren verantwortlich, Daten genießen, Sperrhierarchie für Reihenfolge und andere Sperren erwartet. Durch implizite Regeln explizites, bieten die Parallelität von SAL-Anmerkungen eine konsistente Möglichkeit für Sie, wie Ihr Code verwendet, Sperre Regeln zu dokumentieren. Concurrency-Anmerkungen verbessern auch die Möglichkeit des Codeanalysetools Racebedingungen, Deadlocks, nicht übereinstimmende Synchronisierungsvorgänge und andere geringfügige Parallelitätsfehler gefunden.  
  
## <a name="general-guidelines"></a>Allgemeine Richtlinien  
 Verwenden von Anmerkungen, können Sie angeben, die Verträge, die von Funktionsdefinitionen zwischen Clients (Aufrufer) und Implementierungen (aufgerufene) impliziert werden, und express Invarianten und andere Eigenschaften des Programms, das kann Verbesserung der Analyse.  
  
 SAL unterstützt viele verschiedene Arten von Sperren primitiven – z. B. kritische Abschnitte, Mutexe, Spinlocks und anderen Ressourcenobjekten. Viele Parallelität Anmerkungen einen Lock-Ausdruck als Parameter in Anspruch nehmen. Gemäß der Konvention ist eine Sperre durch den Pfadausdruck, der das zugrunde liegende Sperrobjekt gekennzeichnet.  
  
 Einige Threads Besitzregeln zu beachten:  
  
- Spinlocks sind ungezählte sperren, die klare Thread den Besitz an.  
  
- Mutexe und kritische Abschnitte werden Sperren gezählt, die klare Thread den Besitz zu haben.  
  
- Semaphoren und Ereignissen werden Sperren gezählt, die keine klare Thread den Besitz aufweisen.  
  
## <a name="locking-annotations"></a>Sperren von Anmerkungen  
 Die folgende Tabelle enthält die Sperren von Anmerkungen.  
  
|Anmerkung|Beschreibung|  
|----------------|-----------------|  
|`_Acquires_exclusive_lock_(expr)`|Kommentiert eine Funktion und gibt an, dass die in POST-Anforderung Zustand der Funktion von einem die exklusive Sperrenanzahl von das Sperrobjekt erhöht sich mit dem Namen von `expr`.|  
|`_Acquires_lock_(expr)`|Kommentiert eine Funktion und gibt an, dass die in POST-Anforderung Zustand der Funktion von einem die Sperrenanzahl des Sperren-Objekts erhöht, die von dem Namen `expr`.|  
|`_Acquires_nonreentrant_lock_(expr)`|Die Sperre, die von dem Namen `expr` wird abgerufen.  Ein Fehler wird gemeldet, wenn die Sperre bereits verwendet wird.|  
|`_Acquires_shared_lock_(expr)`|Kommentiert eine Funktion und gibt an, dass die in POST-Anforderung Zustand der Funktion von einem die freigegebene Sperrenanzahl von das Sperrobjekt erhöht sich mit dem Namen von `expr`.|  
|`_Create_lock_level_(name)`|Eine Anweisung, die das Symbol deklariert `name` einer Sperrebene sein, damit sie in den Anmerkungen verwendet werden kann `_Has_Lock_level_` und `_Lock_level_order_`.|  
|`_Has_lock_kind_(kind)`|Kommentiert ein Objekt, um die Typinformationen von einem Ressourcenobjekt zu optimieren. Manchmal ist kein gemeinsamer Typ für verschiedene Arten von Ressourcen verwendet, und der überladene Typ ist nicht ausreichend, um die semantischen Anforderungen zwischen verschiedenen Ressourcen zu unterscheiden. Es folgt eine Liste der vordefinierten `kind` Parameter:<br /><br /> `_Lock_kind_mutex_`<br /> Typ-ID für Mutexe zu sperren.<br /><br /> `_Lock_kind_event_`<br /> Typ-ID für die Ereignisse zu sperren.<br /><br /> `_Lock_kind_semaphore_`<br /> Typ-ID für die Semaphore zu sperren.<br /><br /> `_Lock_kind_spin_lock_`<br /> Typ-ID für Spinlocks zu sperren.<br /><br /> `_Lock_kind_critical_section_`<br /> Typ-ID für kritische Abschnitte zu sperren.|  
|`_Has_lock_level_(name)`|Kommentiert eine Sperrobjekt und weist ihm die Sperrebene von `name`.|  
|`_Lock_level_order_(name1, name2)`|Eine Anweisung, die die Reihenfolge für die Sperre erhalten `name1` und `name2`.|  
|`_Post_same_lock_(expr1, expr2)`|Kommentiert eine Funktion und gibt an, dass die in POST-Anforderung die zwei Sperren, Status `expr1` und `expr2`, werden behandelt, als wären sie das gleiche Sperrobjekt.|  
|`_Releases_exclusive_lock_(expr)`|Kommentiert eine Funktion und gibt an, dass die in Post verringert die von einem die exklusive Sperre-Anzahl, der das Sperrobjekt Zustand mit dem Namen von `expr`.|  
|`_Releases_lock_(expr)`|Kommentiert eine Funktion und gibt an, dass die in Post verringert die von einem die Sperrenanzahl des Objekts Sperre Zustand mit dem Namen von `expr`.|  
|`_Releases_nonreentrant_lock_(expr)`|Die Sperre, die von dem Namen `expr` veröffentlicht wird. Ein Fehler wird gemeldet, wenn die Sperre im Moment nicht aufrechterhalten wird.|  
|`_Releases_shared_lock_(expr)`|Kommentiert eine Funktion und gibt an, dass die in Post verringert die von einem die freigegebene Sperre-Anzahl, der das Sperrobjekt Zustand mit dem Namen von `expr`.|  
|`_Requires_lock_held_(expr)`|Kommentiert eine Funktion und gibt an, dass die Anzahl der Sperren des Objekts in vor mit dem Namen Status von `expr` ist mindestens eine.|  
|`_Requires_lock_not_held_(expr)`|Kommentiert eine Funktion und gibt an, dass die Anzahl der Sperren des Objekts in vor mit dem Namen Status von `expr` ist 0 (null).|  
|`_Requires_no_locks_held_`|Kommentiert eine Funktion, und gibt an, dass die Sperrenanzahl aller sperren, die die Prüfung von bekannt sind, 0 (null).|  
|`_Requires_shared_lock_held_(expr)`|Kommentiert eine Funktion und gibt an, dass die Anzahl der freigegebenen Sperren des Objekts in vor mit dem Namen Status von `expr` ist mindestens eine.|  
|`_Requires_exclusive_lock_held_(expr)`|Kommentiert eine Funktion und gibt an, dass die Anzahl der exklusiven Sperren des Objekts in vor mit dem Namen Status von `expr` ist mindestens eine.|  
  
## <a name="sal-intrinsics-for-unexposed-locking-objects"></a>Systeminterne SAL-Funktionen für nicht verfügbare Sperrobjekte  
 Bestimmte Sperrobjekte nicht durch die Implementierung von der zugeordneten Sperren Funktionen verfügbar gemacht werden.  Die folgende Tabelle enthält die systeminterne SAL-Variablen, die Anmerkungen für Funktionen zu ermöglichen, die für diese Sperrobjekte nicht verfügbar gemachte ausgeführt werden.  
  
|Anmerkung|Beschreibung|  
|----------------|-----------------|  
|`_Global_cancel_spin_lock_`|Beschreibt den SpinLock "Abbrechen".|  
|`_Global_critical_region_`|Beschreibt die kritischen Bereich.|  
|`_Global_interlock_`|Beschreibt die interlocked-Vorgänge.|  
|`_Global_priority_region_`|Beschreibt die Priorität der Region.|  
  
## <a name="shared-data-access-annotations"></a>Anmerkungen zum freigegebenen Datenzugriff  
 Die folgende Tabelle enthält die Anmerkungen für den Datenzugriff.  
  
|Anmerkung|Beschreibung|  
|----------------|-----------------|  
|`_Guarded_by_(expr)`|Kommentiert eine Variable aus, und gibt an, dass jedes Mal, wenn die Variable zugegriffen wird, die Anzahl der Sperren des Objekts mit dem Namen von Sperren `expr` ist mindestens eine.|  
|`_Interlocked_`|Kommentiert eine Variable und entspricht `_Guarded_by_(_Global_interlock_)`.|  
|`_Interlocked_operand_`|Der Parameter mit Anmerkung versehenen Funktion ist der Target-Operand, der eine der verschiedenen Interlocked-Funktionen.  Die Operanden müssen bestimmte zusätzliche Eigenschaften.|  
|`_Write_guarded_by_(expr)`|Kommentiert eine Variable aus, und gibt an, dass jedes Mal, wenn die Variable geändert wird, wird die Anzahl der Sperren des Objekts mit dem Namen von Sperren `expr` ist mindestens eine.|  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von SAL-Anmerkungen zum Reduzieren von C/C++-Codefehlern](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Einführung in SAL](../code-quality/understanding-sal.md)   
 [Hinzufügen einer Anmerkung zu Funktionsparametern und Rückgabewerten](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Zum Funktionsverhalten](../code-quality/annotating-function-behavior.md)   
 [Hinzufügen einer Anmerkung zu Strukturen und Klassen](../code-quality/annotating-structs-and-classes.md)   
 [Angeben, wann und wo eine Anmerkung gültig ist](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Systeminterne Funktionen](../code-quality/intrinsic-functions.md)   
 [Empfohlene Vorgehensweisen und Beispiele](../code-quality/best-practices-and-examples-sal.md)   
 [Code Analysis-Teamblog](http://go.microsoft.com/fwlink/p/?LinkId=251197)
