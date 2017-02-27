---
title: "Zuverl&#228;ssigkeitswarnungen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.reliabilityrules"
helpviewer_keywords: 
  - "Warnungen, Zuverlässigkeit"
  - "Zuverlässigkeitswarnungen"
  - "Analysen für verwalteten Code (Warnungen), Zuverlässigkeitswarnungen"
ms.assetid: 77886846-10a2-4585-968a-7eb60ebe07e8
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 21
---
# Zuverl&#228;ssigkeitswarnungen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Zuverlässigkeitswarnungen unterstützen die Bibliotheks\- und Anwendungszuverlässigkeit, z. B. richtige Verwendung von Arbeitsspeicher und Threads.  
  
## In diesem Abschnitt  
  
|Regel|**Beschreibung**|  
|-----------|----------------------|  
|[CA2000: Objekte verwerfen, bevor Bereich verloren geht](../code-quality/ca2000-dispose-objects-before-losing-scope.md)|Da eine Ausnahme auftreten kann, durch die die Ausführung eines Objektfinalizers verhindert wird, sollte das Objekt explizit verworfen werden, bevor sich sämtliche Verweise auf dieses außerhalb des Bereichs befinden.|  
|[CA2001: Keine problematischen Methoden aufrufen](../code-quality/ca2001-avoid-calling-problematic-methods.md)|Ein Member ruft eine möglicherweise gefährliche oder problematische Methode auf.|  
|[CA2002: Auf Objekten mit schwacher Identität nicht sperren](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|Ein Objekt hat eine schwache Identität, wenn ein Zugriff darauf über Grenzen von Anwendungsdomänen hinweg möglich ist.  Ein Thread, der eine Sperre für ein Objekt zu erhalten versucht, das über eine schwache Identität verfügt, kann durch einen zweiten Thread in einer anderen Anwendungsdomäne blockiert werden, der eine Sperre für das gleiche Objekt besitzt.|  
|[CA2003: Fibers nicht als Threads behandeln](../code-quality/ca2003-do-not-treat-fibers-as-threads.md)|Ein verwalteter Thread wird als Win32\-Thread behandelt.|  
|[CA2004: Aufrufe an GC.KeepAlive entfernen](../code-quality/ca2004-remove-calls-to-gc-keepalive.md)|Wenn Sie zur Verwendung von SafeHandle wechseln, entfernen Sie alle Aufrufe von GC.KeepAlive \(Objekt\).  In diesem Fall sollten Klassen GC.KeepAlive nicht aufrufen müssen, vorausgesetzt, sie weisen keinen Finalizer auf, sondern verwenden zum Beenden des Betriebssystemhandles SafeHandle.|  
|[CA2006: SafeHandle verwenden, um systemeigene Ressourcen zu kapseln](../code-quality/ca2006-use-safehandle-to-encapsulate-native-resources.md)|Die Verwendung von IntPtr in verwaltetem Code kann auf ein potenzielles Sicherheitsrisiko und Zuverlässigkeitsproblem hinweisen.  Alle Vorkommen von IntPtr müssen daher überprüft werden, um festzustellen, ob stattdessen die Verwendung von SafeHandle \(oder einer ähnlichen Technologie\) erforderlich ist.|