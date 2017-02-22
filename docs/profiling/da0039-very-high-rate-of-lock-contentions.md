---
title: "DA0039: Sehr hohes Ma&#223; an Sperrkonflikten | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.39"
  - "vs.performance.DA0039"
  - "vs.performance.rules.DA0039"
ms.assetid: 5a9fc57d-9097-413b-af0c-8726b1a57048
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0039: Sehr hohes Ma&#223; an Sperrkonflikten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|Regel\-ID|DA0039|  
|Kategorie \(Category\)|.NET Framework\-Verwendung|  
|Profilerstellungsmethoden|Sampling<br /><br /> Instrumentation<br /><br /> .NET\-Arbeitsspeicher|  
|Meldung|Ein sehr hohes Maß an .NET\-Sperrkonflikten wurde festgestellt.  Untersuchen Sie die Ursache für diesen Sperrkonflikt durch Ausführen eines Parallelitätsprofils.|  
|Regeltyp|Warnung|  
  
 Wenn Sie mit der Sampling\-, .NET\-Arbeitsspeicher\- oder Ressourcenkonfliktmethode Profile erstellen, müssen mindestens 25 Samplings erfasst werden, damit diese Regel ausgelöst wird.  
  
## Ursache  
 Die zusammen mit den Profilerstellungsdaten erfassten Systemleistungsdaten deuten darauf hin, dass während der Anwendungsausführung ein übermäßig hohes Maß an Sperrkonflikten aufgetreten ist.  Führen Sie eine erneute Profilerstellung unter Verwendung der Parallelitätsmethode aus, um die Ursache des Konflikts zu ermitteln.  
  
## Regelbeschreibung  
 Sperren werden verwendet, um in einer Multithreadanwendung kritische Abschnitte von Code zu schützen, der seriell von jeweils einem Thread ausgeführt werden muss.  Von der Microsoft .NET Common Language Runtime \(CLR\) wird ein vollständiger Satz von Synchronisierungs\- und Sperrprimitiven bereitgestellt.  Von der Programmiersprache C\# wird beispielsweise eine lock\-Anweisung \(SyncLock in Visual Basic\) unterstützt.  Von einer verwalteten Anwendung können die Methoden "Monitor.Enter" und "Monitor.Exit" im Namespace "System.Threading" aufgerufen werden, um direkt eine Sperre einzurichten oder freizugeben.  Von .NET Framework werden zusätzliche Synchronisierungs\- und Sperrprimitive unterstützt – einschließlich Klassen, von denen Mutexe, ReaderWriterLocks und Semaphore unterstützt werden.  Weitere Informationen finden Sie unter [Übersicht über Synchronisierungs\-Primitiven](http://go.microsoft.com/fwlink/?LinkId=177867) auf der MSDN\-Website im .NET Framework\-Entwicklerhandbuch.  Die .NET Framework\-Klassen selbst befinden sich auf Ebenen, die den in das Betriebssystem Windows integrierten Synchronisierungsdiensten niedrigerer Ebenen übergeordnet sind.  Dazu gehören Objekte für kritische Abschnitte sowie viele verschiedene Wait\- und Ereignissignalisierungsfunktionen.  Weitere Informationen finden Sie im [Synchronisierung](http://go.microsoft.com/fwlink/?LinkId=177869)\-Abschnitt für die Win32\- und COM\-Entwicklung in der MSDN Library  
  
 Sowohl den .NET Framework\-Klassen als auch den systemeigenen Windows\-Objekten, die für die Synchronisierung und für Sperren verwendet werden, liegen freigegebene Speicherbereiche zugrunde, die mithilfe von Interlocked\-Vorgängen geändert werden müssen.  Von Interlocked\-Vorgängen werden hardwarespezifische Anweisungen verwendet, die in freigegebenen Speicherbereichen ausgeführt werden, um deren Zustand mithilfe von unteilbaren Vorgängen zu ändern.  Unteilbare Vorgänge sind für alle Prozessoren des Computers garantiert konsistent.  Sperren und WaitHandles sind .NET\-Objekte, von denen automatisch Interlocked\-Vorgänge verwendet werden, wenn sie festgelegt oder zurückgesetzt werden.  Unter Umständen sind in der Anwendung auch andere Datenstrukturen mit freigegebenem Speicher vorhanden, für die ebenfalls Interlocked\-Vorgänge verwendet werden müssen, um eine threadsichere Aktualisierung zu gewährleisten.  Weitere Informationen finden Sie unter [Interlocked\-Vorgänge](http://go.microsoft.com/fwlink/?LinkId=177870) in der MSDN Library im .NET Framework\-Abschnitt  
  
 Synchronisierung und Sperrung sind Mechanismen, mit denen sichergestellt wird, dass Multithreadanwendungen ordnungsgemäß ausgeführt werden.  Jeder Thread einer Multithreadanwendung ist eine unabhängige und unabhängig geplante Ausführungseinheit.  Zu einem Sperrkonflikt kommt es immer dann, wenn für einen Thread, von dem versucht wird, eine Sperre einzurichten, eine Verzögerung auftritt, da die Sperre von einem anderen Thread zurückgehalten wird.  
  
 Sperren sind häufig geschachtelt.  Eine Schachtelung tritt auf, wenn von einem Thread, von dem ein kritischer Abschnitt ausgeführt wird, eine Funktion ausgeführt wird, für die eine weitere Sperre erforderlich ist.  Ein gewisses Maß an Sperrschachtelungen lässt sich nicht vermeiden.  Durch den kritischen Abschnitt wird möglicherweise eine .NET Framework\-Methode aufgerufen, deren Threadsicherheit auf Sperren beruht.  Der Aufruf einer Framework\-Methode, von der mithilfe eines anderen Sperrhandles ebenfalls eine Sperre eingerichtet wird und der aus einem kritischen Abschnitt in der Anwendung erfolgt, hat eine Schachtelung der Sperren zur Folge.  Geschachtelte Sperrbedingungen können zu Leistungsproblemen führen, die sich meist nur sehr schwer nachvollziehen und beheben lassen.  
  
 Diese Regel wird ausgelöst, wenn die während der Profilerstellung ermittelten Werte auf ein sehr hohes Maß an Sperrkonflikten hindeuten.  Durch Sperrkonflikte verzögert sich die Ausführung von Threads, von denen auf die Sperre gewartet wird.  Es empfiehlt sich, selbst eine recht geringe Anzahl von Sperrenkonflikten in Komponenten\- oder Auslastungstests zu untersuchen, die auf weniger leistungsfähiger Hardware ausgeführt werden.  
  
> [!NOTE]
>  Wenn das Maß an gemeldeten Sperrenkonflikten in den Profilerstellungsdaten zwar hoch, aber nicht übermäßig hoch ist, wird statt dieser Warnmeldung die Informationsmeldung [DA0038: Hohes Maß an Sperrkonflikten](../profiling/da0038-high-rate-of-lock-contentions.md) ausgelöst.  
  
## Vorgehensweise bei der Überprüfung einer Warnung  
 Doppelklicken Sie auf die Meldung, um zur Ansicht [Markierungen](../profiling/marks-view.md) der Profilerstellungsdaten zu navigieren.  Suchen Sie die Spalte **.NET CLR\-Sperren und Threads\\Konfliktrate\/Sek.**.  Ermitteln Sie, ob das Maß an Sperrkonflikten in bestimmten Phasen der Programmausführung besonders hoch ausfällt.  
  
 Diese Regel wird nur ausgelöst, wenn die Parallelitätsmethode zur Profilerstellung nicht verwendet wird.  Die Parallelitätsmethode zur Profilerstellung ist das am besten geeignete Tool, um Leistungsprobleme im Zusammenhang mit Sperrkonflikten in der Anwendung zu untersuchen.  Sammeln Sie Parallelitätsprofilerstellungsdaten, um das Sperrverhalten der Anwendung zu verstehen.  Ermitteln Sie hierzu, für welche Sperren eine hohe Anzahl von Konflikten vorliegt, um wie viel sich die Threadausführungszeit durch das Warten auf Sperren mit Konflikten verlängert und welcher Code impliziert wird.  In Parallelitätsprofilen werden Daten zu allen Sperrkonflikten gesammelt. Dies schließt auch das Sperrverhalten von systemeigenen Windows\-Funktionen, .NET Framework\-Klassen und beliebigen anderen Bibliotheken von Drittanbietern ein, auf die von der Anwendung verwiesen wird.  Informationen zur Parallelitätsprofilerstellung mithilfe der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-IDE finden Sie unter [Sammeln von Parallelitätsdaten zu Threads und Prozessen](../profiling/collecting-thread-and-process-concurrency-data.md).  Links zu Informationen zur Parallelitätsprofilerstellung mithilfe der Befehlszeile finden Sie unter [Verwenden von Profilerstellungsmethoden über die Befehlszeile](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md) im Abschnitt **Using the Concurrency Method to Collect Resource Contention and Thread Activity Data**.