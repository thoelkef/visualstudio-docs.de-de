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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb39bb5f59373f52d77c7cc5d13d12544d4c0314
ms.sourcegitcommit: 3e94d9fb6dc56fa8b23fbacd5d11cf8d6e7e18f1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/10/2019
ms.locfileid: "72252588"
---
# <a name="reliability-warnings"></a>Zuverlässigkeitswarnungen

Zuverlässigkeits Warnungen unterstützen die Zuverlässigkeit von Bibliotheken und Anwendungen, z. b. die korrekte Arbeitsspeicher-und Thread Verwendung Die Zuverlässigkeits Regeln umfassen Folgendes:

|Regel|Beschreibung|
|----------|-----------------|
|[CA2000: Verwerfen von Objekten vor dem Verlust des Bereichs @ no__t-0|Da eine Ausnahme auftreten kann, durch die die Ausführung eines Objektfinalizers verhindert wird, sollte das Objekt explizit verworfen werden, bevor sich sämtliche Verweise auf dieses außerhalb des Bereichs befinden.|
|[CA2001: Vermeiden Sie das Aufrufen von problematischen Methoden @ no__t-0|Ein Member ruft eine möglicherweise gefährliche oder problematische Methode auf.|
|[CA2002: Keine Sperre für Objekte mit schwacher Identität @ no__t-0|Ein Objekt hat eine schwache Identität, wenn ein Zugriff darauf über Grenzen von Anwendungsdomänen hinweg möglich ist. Ein Thread, der eine Sperre für ein Objekt zu erhalten versucht, das über eine schwache Identität verfügt, kann durch einen zweiten Thread in einer anderen Anwendungsdomäne blockiert werden, der eine Sperre für das gleiche Objekt besitzt.|
|[CA2003: Fibers nicht als Threads behandeln @ no__t-0|Ein verwalteter Thread wird als Win32-Thread behandelt.|
|[CA2004: Entfernen Sie die Aufrufe von GC. KeepAlive @ no__t-0|Wenn Sie eine Umstellung auf die SafeHandle-Verwendung durchlaufen, entfernen Sie alle Aufrufe von GC. KeepAlive (-Objekt). In diesem Fall dürfen Klassen nicht GC abrufen. KeepAlive, angenommen, Sie verfügen über keinen Finalizer, verwenden jedoch SafeHandle, um das Betriebssystem Handle für Sie zu finalisieren.|
|[CA2006: Verwenden von SafeHandle zum Kapseln nativer Ressourcen @ no__t-0|Die Verwendung von IntPtr in verwaltetem Code kann auf ein potenzielles Sicherheitsrisiko und Zuverlässigkeitsproblem hinweisen. Alle Vorkommen von IntPtr müssen daher überprüft werden, um festzustellen, ob stattdessen die Verwendung von SafeHandle (oder einer ähnlichen Technologie) erforderlich ist.|
|[CA2007: Nicht direkt auf eine Aufgabe warten @ no__t-0|Eine asynchrone Methode [erwartet](/dotnet/csharp/language-reference/keywords/await) eine <xref:System.Threading.Tasks.Task> direkt.|
