---
title: Zuverlässigkeitswarnungen
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e7a93ea20edc4b27b3c0e6f41fef2f45bd7f407a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53845414"
---
# <a name="reliability-warnings"></a>Zuverlässigkeitswarnungen
Zuverlässigkeitswarnungen unterstützen Bibliotheks- und anwendungszuverlässigkeit, z. B. richtige Verwendung von Speicher- und threadverwendung.

## <a name="in-this-section"></a>In diesem Abschnitt

|Regel|Beschreibung|
|----------|-----------------|
|[CA2000: Objekte verwerfen, bevor Bereich verloren geht](../code-quality/ca2000-dispose-objects-before-losing-scope.md)|Da eine Ausnahme auftreten kann, durch die die Ausführung eines Objektfinalizers verhindert wird, sollte das Objekt explizit verworfen werden, bevor sich sämtliche Verweise auf dieses außerhalb des Bereichs befinden.|
|[CA2001: Keine problematischen Methoden aufrufen](../code-quality/ca2001-avoid-calling-problematic-methods.md)|Ein Member ruft eine möglicherweise gefährliche oder problematische Methode auf.|
|[CA2002: Klicken Sie auf Objekten mit schwacher Identität nicht sperren](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|Ein Objekt hat eine schwache Identität, wenn ein Zugriff darauf über Grenzen von Anwendungsdomänen hinweg möglich ist. Ein Thread, der eine Sperre für ein Objekt zu erhalten versucht, das über eine schwache Identität verfügt, kann durch einen zweiten Thread in einer anderen Anwendungsdomäne blockiert werden, der eine Sperre für das gleiche Objekt besitzt.|
|[CA2003: Fibers nicht als Threads behandeln](../code-quality/ca2003-do-not-treat-fibers-as-threads.md)|Ein verwalteter Thread wird als ein Win32-Thread behandelt wird.|
|[CA2004: Entfernen Sie Aufrufe von GC. KeepAlive](../code-quality/ca2004-remove-calls-to-gc-keepalive.md)|Wenn Sie zur Verwendung von SafeHandle konvertieren, entfernen Sie alle Aufrufe von GC. KeepAlive (Objekt). In diesem Fall sollten Klassen keine GC aufgerufen. KeepAlive, vorausgesetzt, sie haben keinen Finalizer, sondern verlassen sich auf SafeHandle, um das Betriebssystem abschließen-handle für diese.|
|[CA2006: SafeHandle verwenden, um systemeigene Ressourcen zu kapseln](../code-quality/ca2006-use-safehandle-to-encapsulate-native-resources.md)|Die Verwendung von IntPtr in verwaltetem Code kann auf ein potenzielles Sicherheitsrisiko und Zuverlässigkeitsproblem hinweisen. Alle Vorkommen von IntPtr müssen daher überprüft werden, um festzustellen, ob stattdessen die Verwendung von SafeHandle (oder einer ähnlichen Technologie) erforderlich ist.|