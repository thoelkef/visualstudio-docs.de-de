---
title: 'CA2003: Fibers nicht als Threads behandeln | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2003
- DoNotTreatFibersAsThreads
helpviewer_keywords:
- CA2003
- DoNotTreatFibersAsThreads
ms.assetid: 15398fb1-f384-4bcc-ad93-00e1c0fa9ddf
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a8172490b267949686dd3390c85ed6d86531b192
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85521173"
---
# <a name="ca2003-do-not-treat-fibers-as-threads"></a>CA2003: Fibers nicht als Threads behandeln.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|DoNotTreatFibersAsThreads|
|CheckId|CA2003|
|Category|Microsoft.Reliability|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein verwalteter Thread wird als Win32-Thread behandelt.

## <a name="rule-description"></a>Beschreibung der Regel
 Nehmen Sie nicht an, dass ein verwalteter Thread ein Win32-Thread ist. Dabei handelt es sich um eine Fiber. Der Common Language Runtime (CLR) führt verwaltete Threads im Zusammenhang mit echten Threads im Besitz von SQL als Fibers aus. Diese Threads können über Anwendungs Domänen und sogar Datenbanken im SQL Server Prozess gemeinsam genutzt werden. Die Verwendung des verwalteten lokalen Thread Speichers funktioniert, aber Sie dürfen nicht verwalteten lokalen Thread Speicher verwenden oder davon ausgehen, dass der Code auf dem aktuellen Betriebssystem Thread erneut ausgeführt wird. Ändern Sie nicht die Einstellungen, wie z. b. das Gebiets Schema des Threads. Rufen Sie "foratecriticalsection" oder "foratemutex" nicht über "P/aufrufen" auf, da Sie erfordern, dass der Thread, der eine Sperre eingibt, die Sperre ebenfalls beenden muss Da dies nicht der Fall ist, wenn Sie Fibers verwenden, sind die kritischen Win32-Abschnitte und Mutexe in SQL nutzlos. Möglicherweise verwenden Sie den größten Teil des Zustands für ein verwaltetes System. Thread-Objekt. Hierzu gehören der verwaltete Thread lokale Speicher und die aktuelle Benutzeroberflächen Kultur des Threads. Aus Gründen des Programmiermodells können Sie die aktuelle Kultur eines Threads jedoch nicht ändern, wenn Sie SQL verwenden. Dies wird durch eine neue Berechtigung erzwungen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Überprüfen Sie die Verwendung von Threads, und ändern Sie den Code entsprechend.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Sie sollten diese Regel nicht unterdrücken.
