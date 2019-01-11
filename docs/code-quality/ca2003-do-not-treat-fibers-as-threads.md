---
title: 'CA2003: Fibers nicht als Threads behandeln'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2003
- DoNotTreatFibersAsThreads
helpviewer_keywords:
- CA2003
- DoNotTreatFibersAsThreads
ms.assetid: 15398fb1-f384-4bcc-ad93-00e1c0fa9ddf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ceedee8dc355392cae34fe3ed5fae5708b6d02d6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53844170"
---
# <a name="ca2003-do-not-treat-fibers-as-threads"></a>CA2003: Fibers nicht als Threads behandeln

|||
|-|-|
|TypeName|DoNotTreatFibersAsThreads|
|CheckId|CA2003|
|Kategorie|Microsoft.Reliability|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Ein verwalteter Thread wird als ein Win32-Thread behandelt wird.

## <a name="rule-description"></a>Regelbeschreibung

Gehen Sie nicht, dass ein verwalteter Thread ein Win32-Thread ist; Es ist eine Fiber. Die common Language Runtime (CLR) führt verwaltete Threads als Fibers im Kontext der realen Threads, die von der SQL gehören. Diese Threads können mehrere Anwendungsdomänen und sogar Datenbanken in SQL Server-Prozesses freigegeben werden. Verwendung von verwalteten Thread-lokalen Speicher funktioniert, aber möglicherweise nicht verwenden, nicht verwalteten threadlokalen Speicher oder davon ausgehen, dass der Code erneut auf dem aktuellen Betriebssystemthread ausgeführt wird. Ändern Sie Einstellungen wie z. B. das Gebietsschema des Threads nicht. Rufen Sie nicht CreateCriticalSection oder CreateMutex über P/Invoke, da sie erfordern, dass der Thread, der gesperrte Betriebssystemthread wieder entsperrt auch die Sperre beendet wird muss. Da der Thread, der eine Sperre aktiviert eine Sperre bei der Verwendung von Fibers nicht beenden, sind kritische Abschnitte von Win32 und Mutex-Verfahren nutzlos in SQL. Sicher können Sie die meisten der Status eines verwalteten <xref:System.Threading.Thread> Objekts, einschließlich verwalteten threadlokalen Speicher und der aktuellen Kultur des Benutzers-Benutzeroberfläche (UI) des Threads. Allerdings Programmiermodells, Sie nicht die aktuelle Kultur eines Threads ändern, bei der Verwendung von SQL. Diese Einschränkung wird durch eine neue Berechtigung erzwungen werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Untersuchen Sie die Verwendung von Threads aus, und ändern Sie Ihren Code entsprechend.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Unterdrücken Sie keine mit dieser Regel.