---
title: Kryptografiewarnungen
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: d96723ea-a293-488d-b9db-adb437e50cdd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 78923dfd2873b53790421cde3fe01f024e267202
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587697"
---
# <a name="cryptography-warnings"></a>Kryptografiewarnungen
Kryptografiewarnungen unterstützen sicherere Bibliotheken und Anwendungen durch die korrekte Verwendung von Kryptografie. Diese Warnungen tragen dazu bei, Sicherheitsmängel im Programm zu vermeiden. Wenn Sie eine dieser Warnungen deaktivieren, sollten Sie den Grund dafür im Code deutlich angeben und außerdem den für Ihr Entwicklungsprojekt zuständigen Sicherheitsbeauftragten informieren.

|Regel|Beschreibung|
|----------|-----------------|
|[CA5350: Verwenden Sie keine schwachen kryptografischen Algorithmen](../code-quality/ca5350.md)|Unsichere Verschlüsselungsalgorithmen und Hashfunktionen werden heute aus verschiedenen Gründen verwendet, sollten jedoch nicht verwendet werden, um die Vertrauenswürdigkeit oder Integrität der Daten, die sie schützen, zu gewährleisten.        Dieser Regel wird ausgelöst, wenn im Code TripleDES-, SHA1- oder RIPEMD160-Algorithmen gefunden werden.|
|[CA5351: Verwenden Sie keine unterbrochenen kryptografischen Algorithmen](../code-quality/ca5351.md)|Unterbrochene kryptografische Algorithmen werden nicht als sicher betrachtet; ihre Verwendung sollte unbedingt unterbunden werden. Diese Regel wird ausgelöst, wenn der MD5-Hash-Algorithmus oder DES- bzw. RC2-Verschlüsselungsalgorithmen im Code gefunden werden.|
