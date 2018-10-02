---
title: Kryptografiewarnungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
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
ms.openlocfilehash: 947721de606cb6117ed2fd5f84bbc51e20e08203
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47524051"
---
# <a name="cryptography-warnings"></a>Kryptografiewarnungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Kryptografiewarnungen](https://docs.microsoft.com/visualstudio/code-quality/cryptography-warnings).  
  
Kryptografiewarnungen unterstützen sicherere Bibliotheken und Anwendungen durch die korrekte Verwendung von Kryptografie. Diese Warnungen tragen dazu bei, Sicherheitsmängel im Programm zu vermeiden. Wenn Sie eine dieser Warnungen deaktivieren, sollten Sie den Grund dafür im Code deutlich angeben und außerdem den für Ihr Entwicklungsprojekt zuständigen Sicherheitsbeauftragten informieren.  
  
|Regel|Beschreibung|  
|----------|-----------------|  
|[CA5350: Verwenden Sie keine schwachen kryptografischen Algorithmen](../code-quality/ca5350-do-not-use-weak-cryptographic-algorithms.md)|Unsichere Verschlüsselungsalgorithmen und Hashfunktionen werden heute aus verschiedenen Gründen verwendet, sollten jedoch nicht verwendet werden, um die Vertrauenswürdigkeit oder Integrität der Daten, die sie schützen, zu gewährleisten.        Dieser Regel wird ausgelöst, wenn im Code TripleDES-, SHA1- oder RIPEMD160-Algorithmen gefunden werden.|  
|[CA5351: Verwenden Sie keine unterbrochenen kryptografischen Algorithmen](../code-quality/ca5351-do-not-use-broken-cryptographic-algorithms.md)|Unterbrochene kryptografische Algorithmen werden nicht als sicher betrachtet; ihre Verwendung sollte unbedingt unterbunden werden. Diese Regel wird ausgelöst, wenn der MD5-Hash-Algorithmus oder DES- bzw. RC2-Verschlüsselungsalgorithmen im Code gefunden werden.|



