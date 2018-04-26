---
title: Hinzufügen einer Anmerkung zum Sperrverhalten
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 21c67bb8b99c2772e107ded9063a99940a7fac74
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="annotating-locking-behavior"></a>Hinzufügen einer Anmerkung zum Sperrverhalten
Um Parallelitätsfehler in einem Multithreadprogramm zu vermeiden, führen Sie eine entsprechende Sperren Disziplin immer, und Verwenden von SAL-Anmerkungen an.

 Parallelitätsfehler sind bekanntermaßen schwierig zu reproduzieren, diagnose und Debuggen, da sie nicht deterministisch sind. Schlussfolgern über Thread überlappen bestenfalls schwierig ist, und wird alleine nicht durchführbar, wenn Sie einen Codeabschnitt entwerfen, die mehr als ein paar Threads hat. Daher ist es empfiehlt sich, eine Sperre Disziplin in Ihre Multithreadprogrammen folgen. Können Sie beispielsweise mithilfe eine Sperre Reihenfolge obeying, während mehrere Sperren Deadlocks zu vermeiden kann und die Sperre der richtigen guarding vor dem Zugriff auf eine freigegebene Ressource Racebedingungen zu verhindern.

 Leider können scheinbar einfache Sperre Regeln erstaunlich schwierig, führen die in der Praxis sein. Eine grundlegende Beschränkung in heutigen Programmiersprachen und Compiler ist, dass sie nicht direkt die Spezifikation und die Analyse der parallelitätsanforderungen unterstützen. Programmierer können informelle Codekommentare für ihre Absichten darüber, wie sie Sperren verwenden express abhängig ist.

 Parallelität SAL-Anmerkungen dienen Sie Sperren Nebeneffekte, Sperren dafür verantwortlich, Daten genießen Reihenfolge Sperrhierarchie und andere Sperren erwartet angeben. Durch implizite Regeln explizites, konsistentes SAL Parallelität Anmerkungen zur Verwendungsweise von Sperren Regeln in des Codes zu dokumentieren. Parallelität Anmerkungen erhöhen auch die Fähigkeit des Codeanalysetools, Racebedingungen, Deadlocks nicht übereinstimmende Synchronisierungsvorgänge und andere subtile Parallelitätsfehlern zu finden.

## <a name="general-guidelines"></a>Allgemeine Richtlinien
 Verwenden von Anmerkungen, können Sie die Verträge, die von Funktionsdefinitionen zwischen Implementierungen (aufgerufenen) und Clients (Aufrufer) impliziert werden Status und express Invarianten und andere Eigenschaften des Programms, der weiter können Verbesserung der Analyse.

 SAL unterstützt viele verschiedene Arten von Sperren primitiven Typen – z. B. kritische Abschnitte, Mutexe Spinlocks und andere Ressourcenobjekte. Viele Parallelität Anmerkungen in Anspruch nehmen einen Sperrausdruck als Parameter. Gemäß der Konvention wird eine Sperre durch die Path-Ausdruck des zugrunde liegenden Objekts der Sperre gekennzeichnet.

 Einige Threads Besitzregeln zu beachten:

-   Drehfeld-Sperren sind ungezählte sperren, bei die Threadbesitz deaktivieren zugewiesen werden.

-   Mutexe und kritische Abschnitte werden Sperren gezählt, die klar Threadbesitz zugewiesen werden.

-   Semaphoren und Ereignisse werden Sperren gezählt, die keine klare Threadbesitz sind.

## <a name="locking-annotations"></a>Sperren von Anmerkungen
 Die folgende Tabelle enthält die Sperren von Anmerkungen.

|Anmerkung|Beschreibung|
|----------------|-----------------|
|`_Acquires_exclusive_lock_(expr)`|Kommentiert eine Funktion und gibt an, dass in Post Zustand der Funktion eine die exklusive Sperrenanzahl das Sperrenobjekt mit dem Namen inkrementiert von `expr`.|
|`_Acquires_lock_(expr)`|Kommentiert eine Funktion und gibt an, dass in Post Zustand der Funktion eine die Anzahl der Sperren des Objekts Sperre, die inkrementiert von dem Namen `expr`.|
|`_Acquires_nonreentrant_lock_(expr)`|Die Sperre mit dem Namen von `expr` wird abgerufen.  Ein Fehler wird gemeldet, wenn Sie bereits die Sperre aufrechterhalten wird.|
|`_Acquires_shared_lock_(expr)`|Kommentiert eine Funktion und gibt an, dass in Post Zustand der Funktion eine die Anzahl der freigegebenen Sperren des Objekts Sperre mit dem Namen inkrementiert von `expr`.|
|`_Create_lock_level_(name)`|Eine Anweisung, die das Symbol deklariert `name` eine sperrenebene sein, damit er in den Anmerkungen verwendet werden kann `_Has_Lock_level_` und `_Lock_level_order_`.|
|`_Has_lock_kind_(kind)`|Fügt ein Objekt, um die Typinformationen von einem Ressourcenobjekt optimieren. In einigen Fällen wird kein gemeinsamer Typ für verschiedene Arten von Ressourcen verwendet, und der überladene Typ ist nicht ausreichend, um die semantischen Anforderungen auf verschiedene Ressourcen zu unterscheiden. Hier ist eine Liste der vordefinierten `kind` Parameter:<br /><br /> `_Lock_kind_mutex_`<br /> Kind-ID für Mutexe zu sperren.<br /><br /> `_Lock_kind_event_`<br /> Kind-ID für Ereignisse zu sperren.<br /><br /> `_Lock_kind_semaphore_`<br /> Kind-ID für Semaphoren zu sperren.<br /><br /> `_Lock_kind_spin_lock_`<br /> Kind-ID für Spinlocks zu sperren.<br /><br /> `_Lock_kind_critical_section_`<br /> Kind-ID für kritische Abschnitte zu sperren.|
|`_Has_lock_level_(name)`|Kommentiert eine Sperrenobjekt und vergibt für das Maß an Sperren `name`.|
|`_Lock_level_order_(name1, name2)`|Eine Anweisung, die die Sperre, die Reihenfolge zwischen bietet `name1` und `name2`.|
|`_Post_same_lock_(expr1, expr2)`|Kommentiert eine Funktion und gibt an, dass im Beitrag der zwei Sperren Status `expr1` und `expr2`, behandelt, als ob sie die gleiche Sperrobjekt sind.|
|`_Releases_exclusive_lock_(expr)`|Kommentiert eine Funktion und gibt an, dass im Beitrag der Funktion verringert um eins die exklusive Sperrenanzahl der Sperrobjekt, die angeben von dem Namen `expr`.|
|`_Releases_lock_(expr)`|Kommentiert eine Funktion und gibt an, dass im Beitrag der Funktion verringert um eins der Anzahl der Sperren des Objekts Sperre mit dem Namen Status von `expr`.|
|`_Releases_nonreentrant_lock_(expr)`|Die Sperre mit dem Namen von `expr` freigegeben wird. Ein Fehler wird gemeldet, wenn die Sperre im Moment nicht aufrechterhalten wird.|
|`_Releases_shared_lock_(expr)`|Kommentiert eine Funktion und gibt an, dass im Beitrag der Funktion verringert um eins die freigegebene Sperrenanzahl der Sperrobjekt, die angeben von dem Namen `expr`.|
|`_Requires_lock_held_(expr)`|Kommentiert eine Funktion und gibt an, dass die Anzahl der Sperren des Objekts in vor mit dem Namen Status von `expr` mindestens ein ist.|
|`_Requires_lock_not_held_(expr)`|Kommentiert eine Funktion und gibt an, dass die Anzahl der Sperren des Objekts in vor mit dem Namen Status von `expr` 0 (null).|
|`_Requires_no_locks_held_`|Eine Funktion merkt, und gibt an, dass die Sperre aller sperren, die das Überprüfungsprogramm bekannt sind, 0 (null) sind.|
|`_Requires_shared_lock_held_(expr)`|Kommentiert eine Funktion und gibt an, dass die Anzahl der freigegebenen Sperren des Objekts in vor mit dem Namen Status von `expr` mindestens ein ist.|
|`_Requires_exclusive_lock_held_(expr)`|Kommentiert eine Funktion und gibt an, dass die Anzahl der exklusiven Sperren des Objekts in vor mit dem Namen Status von `expr` mindestens ein ist.|

## <a name="sal-intrinsics-for-unexposed-locking-objects"></a>Systeminterne SAL-Funktionen für nicht verfügbare Sperrobjekte
 Bestimmte Sperrobjekte werden nicht von der Implementierung der zugeordneten Sperren Funktionen verfügbar gemacht.  Die folgende Tabelle enthält die systeminterne SAL-Variablen, die Anmerkungen auf Funktionen zu ermöglichen, die für diese Sperrobjekte nicht verfügbar gemachte ausgeführt werden.

|Anmerkung|Beschreibung|
|----------------|-----------------|
|`_Global_cancel_spin_lock_`|Beschreibt den SpinLock "Abbrechen".|
|`_Global_critical_region_`|Beschreibt die kritischen Bereichs an.|
|`_Global_interlock_`|Beschreibt die interlocked-Vorgänge.|
|`_Global_priority_region_`|Beschreibt die Priorität Region an.|

## <a name="shared-data-access-annotations"></a>Anmerkungen zum freigegebenen Datenzugriff
 Die folgende Tabelle enthält die Anmerkungen für den Zugriff auf freigegebene Daten.

|Anmerkung|Beschreibung|
|----------------|-----------------|
|`_Guarded_by_(expr)`|Kommentiert eine Variable aus, und gibt an, dass bei jedem der Variablen zugegriffen wird, die Anzahl der Sperren des Sperrobjekt mit dem Namen von `expr` ist mindestens ein.|
|`_Interlocked_`|Kommentiert eine Variable und entspricht dem `_Guarded_by_(_Global_interlock_)`.|
|`_Interlocked_operand_`|Der mit Anmerkung versehenen Funktion-Parameter ist der Ziel-Operand, der zu den verschiedenen Interlocked-Funktionen.  Die Operanden müssen bestimmte zusätzliche Eigenschaften aufweisen.|
|`_Write_guarded_by_(expr)`|Kommentiert eine Variable aus, und gibt an, dass immer die Variable geändert wird, wird die Anzahl der Sperren des Sperrobjekt mit dem Namen von `expr` mindestens ein ist.|

## <a name="see-also"></a>Siehe auch
 [Verwenden von SAL-Anmerkungen zum Reduzieren von C/C++-Codefehlern](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md) [Grundlegendes zu SAL](../code-quality/understanding-sal.md) [Hinzufügen einer Anmerkung zu Funktionsparametern und Rückgabewerten](../code-quality/annotating-function-parameters-and-return-values.md) [Funktionsverhalten](../code-quality/annotating-function-behavior.md) [Hinzufügen einer Anmerkung zu Strukturen und Klassen](../code-quality/annotating-structs-and-classes.md) [angeben, wann und wo eine Anmerkung gültig](../code-quality/specifying-when-and-where-an-annotation-applies.md) [systeminterne Funktionen](../code-quality/intrinsic-functions.md) [Best Practices und Beispiele für](../code-quality/best-practices-and-examples-sal.md) [Code Analysis-Teamblog](http://go.microsoft.com/fwlink/p/?LinkId=251197)