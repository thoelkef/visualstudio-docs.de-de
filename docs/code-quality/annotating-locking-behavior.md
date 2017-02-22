---
title: "Hinzuf&#252;gen einer Anmerkung zum Sperrverhalten | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_Releases_nonreentrant_lock_"
  - "_Lock_kind_mutex_"
  - "_Lock_kind_critical_section_"
  - "_Acquires_lock_"
  - "_Releases_lock_"
  - "_Has_lock_kind_"
  - "_Releases_exclusive_lock_"
  - "_Post_same_lock_"
  - "_Requires_exclusive_lock_held_"
  - "_Requires_shared_lock_held_"
  - "_Lock_kind_semaphore_"
  - "_Requires_lock_held_"
  - "_Acquires_exclusive_lock_"
  - "_Create_lock_level_"
  - "_Acquires_nonreentrant_lock_"
  - "_Releases_shared_lock_"
  - "_Has_lock_level_"
  - "_Lock_kind_spin_lock_"
  - "_Requires_lock_not_held_"
  - "_Acquires_shared_lock_"
  - "_Requires_no_locks_held_"
  - "_Lock_level_order_"
  - "_Lock_kind_event_"
ms.assetid: 07769c25-9b97-4ab7-b175-d1c450308d7a
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Hinzuf&#252;gen einer Anmerkung zum Sperrverhalten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Um Parallelitätsfehler in einem Multithreadprogramm zu vermeiden, immer nach einer entsprechenden Sperrendisziplin und verwenden Sie SAL\-Anmerkungen.  
  
 Parallelitätsfehler sind notorisch schwierig zu reproduzieren, zu ermitteln und zu debuggen, da sie nicht deterministisch sind.  Die Schlussfolgerungen über das Threadverschachteln ist bestenfalls schwierig, und ist nicht empfehlenswert, wenn Sie einen Codeabschnitt, der mehr verfügt, als einige Threads entwerfen.  Daher ist es empfehlenswert, einer Sperrendisziplin in den Programmen Multithreadanwendung folgen.  Beispielsweise kann eine Sperre befolgend sortieren Sie beim Abrufen mehrerer Sperren, die unterstützt Deadlocks vermeiden, und die richtige Schützensperre, bevor Sie auf die eine freigegebene Ressource zugreifen, Abrufen Abwehr Racebedingungen.  
  
 Leider können scheinbar einfache Sperrenregeln überraschend schwer, in der Praxis zu folgen.  Eine grundlegende Einschränkung in den heutigen Programmiersprachen und Compiler ist, dass sie nicht direkt die Spezifikation und die Analyse von Nebenläufigkeitsanforderungen unterstützen.  Programmierer müssen auf informellen Codekommentare verlassen, um auszudrücken ihre Absichten darüber, wie sie Sperren verwenden.  
  
 Parallelität SAL\-Anmerkungen wurden entworfen, um Ihnen helfen, Sperrennebeneffekten, Sperrenverantwortung, Data Protection, Sperrenreihenfolgenhierarchie und anderem erwartetem Sperrverhalten anzugeben.  Indem implizite Regeln explizit aufstellen, stellen SALZnebenläufigkeitsanmerkungen eine konsistente Navigationsmöglichkeit zur Verfügung, sodass Sie dokumentieren, wie der Code Sperrenregeln verwendet.  Nebenläufigkeitsanmerkungen erhöhen auch die Möglichkeit von Codeanalysetools, Racebedingungen, Deadlocks, nicht übereinstimmende Synchronisierungsoperationen und andere kleinere Parallelitätsfehler zu suchen.  
  
## Allgemeine Richtlinien  
 Mit Anmerkungen werden, können Sie die Verträge berücksichtigen, die über Funktionsdefinitionen zwischen Implementierungen \(Aufgerufenen\) und Clients \(Aufrufern\) bedeutet werden, und drücken invariante Elemente und andere Eigenschaften des Programms aus, Analyse das weiter verbessern kann.  
  
 SAL unterstützt viele verschiedene Arten von Sperre Primitive – z. B. kritischen Abschnitten, Mutexe, Spinlocks und andere Ressourcen.  Viele Nebenläufigkeitsanmerkungen akzeptieren einen Sperrenausdruck als Parameter.  Standardmäßig wird eine Sperre von den Pfadausdruck des zugrunde liegenden Sperrenobjekts bezeichnet.  
  
 Einige Anwendungen Besitzregeln zu beachten:  
  
-   Spinlocks sind uncounted Sperren, die dabei Threadbesitz haben.  
  
-   Mutexe und kritischen Abschnitten sind gezählte Sperren, die dabei Threadbesitz haben.  
  
-   Semaphoren und Ereignisse sind gezählte Sperren, die nicht Threadbesitz klaren haben.  
  
## Sperren von Anmerkungen  
 Die folgende Tabelle zeigt die Sperrenanmerkungen auf.  
  
|Anmerkung|**Beschreibung**|  
|---------------|----------------------|  
|`_Acquires_exclusive_lock_(expr)`|Kommentiert eine Funktion und gibt das im Funktionsinkremente durch eine Nachbedingung die exklusive die Sperrenanzahl des Sperrenobjekts an, das durch `expr`.|  
|`_Acquires_lock_(expr)`|Kommentiert eine Funktion und gibt das im Funktionsinkremente die durch eine Nachbedingung die Sperrenanzahl des Sperrenobjekts an, das durch `expr`.|  
|`_Acquires_nonreentrant_lock_(expr)`|Die Sperre, die durch `expr`, abgerufen wird.  Ein Fehler wird ausgegeben, wenn die Sperre noch angehalten wird.|  
|`_Acquires_shared_lock_(expr)`|Kommentiert eine Funktion und gibt das im Funktionsinkremente durch eine Nachbedingung die die Anzahl der gemeinsamen Sperre des Sperrenobjekts an, das durch `expr`.|  
|`_Create_lock_level_(name)`|Eine Anweisung, die das Symbol `name` deklariert, um eine Sperrenebene sein, damit sie in den Anmerkungen `_Has_Lock_level_` und `_Lock_level_order_` verwendet werden kann.|  
|`_Has_lock_kind_(kind)`|Kommentiert jedes Objekt, um die Typinformationen eines Ressourcenobjekts zu optimieren.  Manchmal ist ein allgemeiner Typ für unterschiedliche Arten von Ressourcen verwendet und der überladene Typ befindet nicht ausreichend, die Semantik\- Anforderungen unter verschiedenen Ressourcen zu unterscheiden.  Im Folgenden eine Liste vordefinierter `kind`\-Parametern:<br /><br /> `_Lock_kind_mutex_`<br /> Sperre interessante ID für Mutexe einrichten.<br /><br /> `_Lock_kind_event_`<br /> Sperre interessante ID für Ereignisse.<br /><br /> `_Lock_kind_semaphore_`<br /> Sperre interessante ID für Semaphore.<br /><br /> `_Lock_kind_spin_lock_`<br /> Sperre interessante ID für Spinlocks.<br /><br /> `_Lock_kind_critical_section_`<br /> Sperre interessante ID für kritische Abschnitte.|  
|`_Has_lock_level_(name)`|Kommentiert ein Sperrenobjekt und gibt es die Sperre, die von `name` ausgeführt wird.|  
|`_Lock_level_order_(name1, name2)`|Eine Anweisung, die die Sperrenreihenfolge zwischen `name1` und `name2` besteht.|  
|`_Post_same_lock_(expr1, expr2)`|Kommentiert eine Funktion und gibt das im Nachbedingung die zwei Sperren, `expr1` und `expr2`, werden behandelt, als ob sie auf dasselbe Sperrenobjekt sind.|  
|`_Releases_exclusive_lock_(expr)`|Kommentiert eine Funktion und gibt das im Funktionsdekremente durch eine Nachbedingung die exklusive die Sperrenanzahl des Sperrenobjekts an, das durch `expr`.|  
|`_Releases_lock_(expr)`|Kommentiert eine Funktion und gibt das im Funktionsdekremente die durch eine Nachbedingung die Sperrenanzahl des Sperrenobjekts an, das durch `expr`.|  
|`_Releases_nonreentrant_lock_(expr)`|Die Sperre, die von `expr`, sind freigegeben.  Ein Fehler wird ausgegeben, wenn die Sperre nicht nur unterbrochen wird.|  
|`_Releases_shared_lock_(expr)`|Kommentiert eine Funktion und gibt das im Funktionsdekremente durch eine Nachbedingung die die Anzahl der gemeinsamen Sperre des Sperrenobjekts an, das durch `expr`.|  
|`_Requires_lock_held_(expr)`|Kommentiert eine Funktion und verleiht dem Einchecken angeben vor die Sperrenanzahl des Objekts an, das von `expr` ist mindestens eines mit dem Namen.|  
|`_Requires_lock_not_held_(expr)`|Kommentiert eine Funktion und verleiht dem Einchecken angeben vor die Sperrenanzahl des Objekts an, das von `expr` ist null ".|  
|`_Requires_no_locks_held_`|Kommentiert eine Funktion und gibt an, dass die Sperrenanzahlen aller Sperren, die dem Prüfer wird, gleich sind.|  
|`_Requires_shared_lock_held_(expr)`|Kommentiert eine Funktion und verleiht dem Einchecken angeben vor die Anzahl des gemeinsamen Sperre des Objekts an, das von `expr` ist mindestens eines mit dem Namen.|  
|`_Requires_exclusive_lock_held_(expr)`|Kommentiert eine Funktion und verleiht dem Einchecken angeben vor die exklusive Sperrenanzahl des Objekts an, das von `expr` ist mindestens eines mit dem Namen.|  
  
## Systeminterne SAL\-Funktionen für nicht verfügbare Sperrobjekte  
 Bestimmte Sperrenobjekte werden nicht von der Implementierung der zugeordneten Sperrenfunktionen verfügbar gemacht.  Die folgende Tabelle zeigt systeminterne Variablen des SALZES auf, die Anmerkungen auf Funktionen aktivieren, die an diese nicht verfügbar gemachten Sperrenobjekte ausführen.  
  
|Anmerkung|**Beschreibung**|  
|---------------|----------------------|  
|`_Global_cancel_spin_lock_`|Beschreibt den Löschenspinlock.|  
|`_Global_critical_region_`|Beschreibt den kritischen Bereich.|  
|`_Global_interlock_`|Beschreibt kann Vorgänge Netz.|  
|`_Global_priority_region_`|Beschreibt den Prioritätsbereich.|  
  
## Anmerkungen zum freigegebenen Datenzugriff  
 In der folgenden Tabelle sind die Anmerkungen für freigegebenen Datenzugriff auf.  
  
|Anmerkung|**Beschreibung**|  
|---------------|----------------------|  
|`_Guarded_by_(expr)`|Kommentiert eine Variable und gibt an, dass, wenn auf die Variable zugegriffen wird, die Sperrenanzahl des Sperrenobjekts, das von `expr`, mindestens eines ist.|  
|`_Interlocked_`|Kommentiert eine Variable und entspricht `_Guarded_by_(_Global_interlock_)`.|  
|`_Interlocked_operand_`|Der Funktionsparameter mit Anmerkungen ist der Zieloperand einer der verschiedenen ineinandergegriffenen Funktionen.  Diese Operanden müssen bestimmte zusätzliche Eigenschaften haben.|  
|`_Write_guarded_by_(expr)`|Kommentiert eine Variable und gibt an, dass, wenn die Variablen geändert wird, die Sperrenanzahl des Sperrenobjekts, das von `expr`, mindestens eines ist.|  
  
## Siehe auch  
 [Verwenden von SAL\-Anmerkungen zum Reduzieren von C\/C\+\+\-Codefehlern](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Einführung in SAL](../code-quality/understanding-sal.md)   
 [Hinzufügen einer Anmerkung zu Funktionsparametern und Rückgabewerten](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Hinzufügen einer Anmerkung zum Funktionsverhalten](../code-quality/annotating-function-behavior.md)   
 [Hinzufügen einer Anmerkung zu Strukturen und Klassen](../code-quality/annotating-structs-and-classes.md)   
 [Angeben, wann und wo eine Anmerkung gültig ist](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Systeminterne Funktionen](../code-quality/intrinsic-functions.md)   
 [Empfohlene Vorgehensweisen und Beispiele](../code-quality/best-practices-and-examples-sal.md)   
 [Codeanalyse\-Team\-Blog](http://go.microsoft.com/fwlink/p/?LinkId=251197)