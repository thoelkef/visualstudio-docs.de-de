---
title: Kryptografiewarnungen | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d96723ea-a293-488d-b9db-adb437e50cdd
caps.latest.revision: "7"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 5270a9b2cb2801d80dc9a087821e73d6c54bfe1c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="cryptography-warnings"></a>Kryptografiewarnungen
Kryptografiewarnungen unterstützen sicherere Bibliotheken und Anwendungen durch die korrekte Verwendung von Kryptografie. Diese Warnungen tragen dazu bei, Sicherheitsmängel im Programm zu vermeiden. Wenn Sie eine dieser Warnungen deaktivieren, sollten Sie den Grund dafür im Code deutlich angeben und außerdem den für Ihr Entwicklungsprojekt zuständigen Sicherheitsbeauftragten informieren.  
  
|Regel|Beschreibung|  
|----------|-----------------|  
|[CA5350: Verwenden Sie keine schwachen kryptografischen Algorithmen](../code-quality/ca5350-do-not-use-weak-cryptographic-algorithms.md)|Unsichere Verschlüsselungsalgorithmen und Hashfunktionen werden heute aus verschiedenen Gründen verwendet, sollten jedoch nicht verwendet werden, um die Vertrauenswürdigkeit oder Integrität der Daten, die sie schützen, zu gewährleisten.        Dieser Regel wird ausgelöst, wenn im Code TripleDES-, SHA1- oder RIPEMD160-Algorithmen gefunden werden.|  
|[CA5351: Verwenden Sie keine unterbrochenen kryptografischen Algorithmen](../code-quality/ca5351-do-not-use-broken-cryptographic-algorithms.md)|Unterbrochene kryptografische Algorithmen werden nicht als sicher betrachtet; ihre Verwendung sollte unbedingt unterbunden werden. Diese Regel wird ausgelöst, wenn der MD5-Hash-Algorithmus oder DES- bzw. RC2-Verschlüsselungsalgorithmen im Code gefunden werden.|