---
title: Zuverlässigkeitswarnungen
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.reliabilityrules
helpviewer_keywords:
- warnings, reliability
- reliability warnings
- managed code analysis warnings, reliability warnings
ms.assetid: 77886846-10a2-4585-968a-7eb60ebe07e8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: db99a9628992c40ef65699fee72d65b891ed1e24
ms.sourcegitcommit: 26178b116cbf7353fee6ca989b8d872114f7b405
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/31/2020
ms.locfileid: "89219607"
---
# <a name="reliability-warnings"></a>Zuverlässigkeitswarnungen

Zuverlässigkeits Warnungen unterstützen die Zuverlässigkeit von Bibliotheken und Anwendungen, z. b. die korrekte Arbeitsspeicher-und Thread Verwendung Die Zuverlässigkeits Regeln umfassen Folgendes:

|Regel|Beschreibung|
|----------|-----------------|
|[CA2000: Objekte verwerfen, bevor Bereich verloren geht.](../code-quality/ca2000.md)|Da eine Ausnahme auftreten kann, durch die die Ausführung eines Objektfinalizers verhindert wird, sollte das Objekt explizit verworfen werden, bevor sich sämtliche Verweise auf dieses außerhalb des Bereichs befinden.|
|[CA2001: Keine problematischen Methoden aufrufen.](../code-quality/ca2001.md)|Ein Member ruft eine möglicherweise gefährliche oder problematische Methode auf.|
|[CA2002: Auf Objekten mit schwacher Identität nicht sperren.](../code-quality/ca2002.md)|Ein Objekt hat eine schwache Identität, wenn ein Zugriff darauf über Grenzen von Anwendungsdomänen hinweg möglich ist. Ein Thread, der eine Sperre für ein Objekt zu erhalten versucht, das über eine schwache Identität verfügt, kann durch einen zweiten Thread in einer anderen Anwendungsdomäne blockiert werden, der eine Sperre für das gleiche Objekt besitzt.|
|[CA2003: Fibers nicht als Threads behandeln.](../code-quality/ca2003.md)|Ein verwalteter Thread wird als Win32-Thread behandelt.|
|[CA2004: Aufrufe an GC.KeepAlive entfernen.](../code-quality/ca2004.md)|Wenn Sie eine Umstellung auf die SafeHandle-Verwendung durchlaufen, entfernen Sie alle Aufrufe von GC. KeepAlive (-Objekt). In diesem Fall dürfen Klassen nicht GC abrufen. KeepAlive, angenommen, Sie verfügen über keinen Finalizer, verwenden jedoch SafeHandle, um das Betriebssystem Handle für Sie zu finalisieren.|
|[CA2006: SafeHandle verwenden, um native Ressourcen zu kapseln.](../code-quality/ca2006.md)|Die Verwendung von IntPtr in verwaltetem Code kann auf ein potenzielles Sicherheitsrisiko und Zuverlässigkeitsproblem hinweisen. Alle Vorkommen von IntPtr müssen daher überprüft werden, um festzustellen, ob stattdessen die Verwendung von SafeHandle (oder einer ähnlichen Technologie) erforderlich ist.|
|[CA2007: Eine Aufgabe nicht direkt abwarten](../code-quality/ca2007.md)|Eine asynchrone Methode [erwartet](/dotnet/csharp/language-reference/keywords/await) <xref:System.Threading.Tasks.Task> direkt ein.|
|[CA2008: Erstellen Sie keine Aufgaben, ohne einen TaskScheduler zu übergeben.](../code-quality/ca2008.md)|Ein Task Erstellungs-oder Fortsetzungs Vorgang verwendet eine Methoden Überladung, die keinen <xref:System.Threading.Tasks.TaskScheduler> Parameter angibt.|
|[CA2009: „ToImmutableCollection“ nicht für einen ImmutableCollection-Wert aufrufen.](../code-quality/ca2009.md)|`ToImmutable` die Methode wurde für eine unveränderliche Auflistung aus dem <xref:System.Collections.Immutable> Namespace unnötig aufgerufen.|
|[CA2011: Eigenschaft nicht innerhalb ihres Setters zuweisen](../code-quality/ca2011.md) | Einer Eigenschaft wurde versehentlich ein Wert innerhalb ihrer eigenen [Set-Zugriffs](/dotnet/csharp/programming-guide/classes-and-structs/using-properties#the-set-accessor)Methode zugewiesen. |
|[CA2012: Verwenden Sie ValueTasks ordnungsgemäß.](../code-quality/ca2012.md) | Valuetasks, die von Element aufrufen zurückgegeben wurden, sollen direkt gewartet werden.  Versucht, eine valuetask mehrmals zu verwenden oder direkt auf das Ergebnis zuzugreifen, bevor es als abgeschlossen bezeichnet wird, kann zu einer Ausnahme oder Beschädigung führen.  Das ignorieren einer solchen valuetask ist wahrscheinlich ein Hinweis auf einen Funktionsfehler und kann die Leistung beeinträchtigen. |
|[CA2013: Verwenden Sie ReferenceEquals nicht mit Werttypen.](../code-quality/ca2013.md) | Beim Vergleichen von Werten mit werden bei <xref:System.Object.ReferenceEquals%2A?displayProperty=fullName> objA und objB Werttypen verwendet, bevor Sie an die-Methode übermittelt werden <xref:System.Object.ReferenceEquals%2A> . Dies bedeutet, dass auch dann, wenn objA und objB dieselbe Instanz eines Werttyps darstellen, die <xref:System.Object.ReferenceEquals%2A> Methode trotzdem false zurückgibt. |
|[CA2014: Verwenden Sie stackzuweisung nicht in Schleifen.](../code-quality/ca2014.md) | Der von stackzugewiesc zugewiesene Stapel Speicher wird nur am Ende des Aufruf der aktuellen Methode freigegeben.  Die Verwendung in einer-Schleife kann zu unbegrenzten Stapel Vergrößerung und letztlichen Stapelüberlauf Bedingungen führen. |
|[CA2015: Finalizer nicht für Typen definieren, die von memorymanager &lt; T abgeleitet sind&gt;](../code-quality/ca2015.md) | Durch das Hinzufügen eines Finalizers zu einem von abgeleiteten Typ <xref:System.Buffers.MemoryManager%601> kann der Speicher freigegeben werden, während er noch von einem verwendet wird <xref:System.Span%601> . |
|[CA2016: Parameter "CancellationToken" an Methoden weiterleiten, die diesen Parameter akzeptieren.](ca2016.md) | Leiten Sie den- `CancellationToken` Parameter an Methoden weiter, die einen annehmen, um sicherzustellen, dass die Vorgangs Abbruch Benachrichtigungen ordnungsgemäß weitergegeben werden, oder übergeben Sie `CancellationToken.None` explizit, um anzugeben, dass das Token absichtlich nicht |
