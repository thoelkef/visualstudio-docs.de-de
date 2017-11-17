---
title: "Zuverlässigkeitswarnungen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.reliabilityrules
helpviewer_keywords:
- warnings, reliability
- reliability warnings
- managed code analysis warnings, reliability warnings
ms.assetid: 77886846-10a2-4585-968a-7eb60ebe07e8
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d3ac06911009a24640031fd3a2306110f289014f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="reliability-warnings"></a>Zuverlässigkeitswarnungen
Zuverlässigkeitswarnungen unterstützen die Bibliotheks- und anwendungszuverlässigkeit, z. B. richtige Verwendung von Arbeitsspeicher- und threadpooleigenschaften.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Regel|Beschreibung|  
|----------|-----------------|  
|[CA2000: Objekte verwerfen, bevor Bereich verloren geht](../code-quality/ca2000-dispose-objects-before-losing-scope.md)|Da eine Ausnahme auftreten kann, durch die die Ausführung eines Objektfinalizers verhindert wird, sollte das Objekt explizit verworfen werden, bevor sich sämtliche Verweise auf dieses außerhalb des Bereichs befinden.|  
|[CA2001: Keine problematischen Methoden aufrufen](../code-quality/ca2001-avoid-calling-problematic-methods.md)|Ein Member ruft eine möglicherweise gefährliche oder problematische Methode auf.|  
|[CA2002: Auf Objekten mit schwacher Identität nicht sperren](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|Ein Objekt hat eine schwache Identität, wenn ein Zugriff darauf über Grenzen von Anwendungsdomänen hinweg möglich ist. Ein Thread, der eine Sperre für ein Objekt zu erhalten versucht, das über eine schwache Identität verfügt, kann durch einen zweiten Thread in einer anderen Anwendungsdomäne blockiert werden, der eine Sperre für das gleiche Objekt besitzt.|  
|[CA2003: Fibers nicht als Threads behandeln](../code-quality/ca2003-do-not-treat-fibers-as-threads.md)|Ein verwalteter Thread wird als Win32-Thread behandelt wird.|  
|[CA2004: Aufrufe an GC.KeepAlive entfernen](../code-quality/ca2004-remove-calls-to-gc-keepalive.md)|Wenn Sie zur Verwendung von SafeHandle konvertieren, entfernen Sie alle Aufrufe von GC. "Keepalive" (Objekt). In diesem Fall sollten Klassen keine GC aufrufen. KeepAlive, vorausgesetzt, sie verfügen nicht über einen Finalizer, sondern SafeHandle zum Abschließen des Betriebssystems abhängig ist, dafür behandeln.|  
|[CA2006: SafeHandle verwenden, um systemeigene Ressourcen zu kapseln](../code-quality/ca2006-use-safehandle-to-encapsulate-native-resources.md)|Die Verwendung von IntPtr in verwaltetem Code kann auf ein potenzielles Sicherheitsrisiko und Zuverlässigkeitsproblem hinweisen. Alle Vorkommen von IntPtr müssen daher überprüft werden, um festzustellen, ob stattdessen die Verwendung von SafeHandle (oder einer ähnlichen Technologie) erforderlich ist.|