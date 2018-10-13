---
title: Kryptografiewarnungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d96723ea-a293-488d-b9db-adb437e50cdd
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 4d795d9c6b6cefcf15c19867cc954ab898215a36
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49201499"
---
# <a name="cryptography-warnings"></a>Kryptografiewarnungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kryptografiewarnungen unterstützen sicherere Bibliotheken und Anwendungen durch die korrekte Verwendung von Kryptografie. Diese Warnungen tragen dazu bei, Sicherheitsmängel im Programm zu vermeiden. Wenn Sie eine dieser Warnungen deaktivieren, sollten Sie den Grund dafür im Code deutlich angeben und außerdem den für Ihr Entwicklungsprojekt zuständigen Sicherheitsbeauftragten informieren.  
  
|Regel|Beschreibung|  
|----------|-----------------|  
|[CA5350: Verwenden Sie keine schwachen kryptografischen Algorithmen](../code-quality/ca5350-do-not-use-weak-cryptographic-algorithms.md)|Unsichere Verschlüsselungsalgorithmen und Hashfunktionen werden heute aus verschiedenen Gründen verwendet, sollten jedoch nicht verwendet werden, um die Vertrauenswürdigkeit oder Integrität der Daten, die sie schützen, zu gewährleisten.        Dieser Regel wird ausgelöst, wenn im Code TripleDES-, SHA1- oder RIPEMD160-Algorithmen gefunden werden.|  
|[CA5351: Verwenden Sie keine unterbrochenen kryptografischen Algorithmen](../code-quality/ca5351-do-not-use-broken-cryptographic-algorithms.md)|Unterbrochene kryptografische Algorithmen werden nicht als sicher betrachtet; ihre Verwendung sollte unbedingt unterbunden werden. Diese Regel wird ausgelöst, wenn der MD5-Hash-Algorithmus oder DES- bzw. RC2-Verschlüsselungsalgorithmen im Code gefunden werden.|



