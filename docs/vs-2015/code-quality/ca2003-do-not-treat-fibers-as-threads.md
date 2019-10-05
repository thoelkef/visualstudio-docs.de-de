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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0a1683c8cb9b9c6dc856f40ddbc7864d773f2101
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68189057"
---
# <a name="ca2003-do-not-treat-fibers-as-threads"></a>CA2003: Fibers nicht als Threads behandeln.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotTreatFibersAsThreads|
|CheckId|CA2003|
|Kategorie|Microsoft.Reliability|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein verwalteter Thread wird als ein Win32-Thread behandelt wird.

## <a name="rule-description"></a>Regelbeschreibung
 Führen Sie Sie nicht davon gehen Sie aus, dass ein verwalteter Thread ein Win32-Thread ist. Es ist eine Fiber. Die common Language Runtime (CLR) führt verwaltete Threads als Fibers im Kontext der realen Threads, die von der SQL gehören. Diese Threads können mehrere Anwendungsdomänen und sogar Datenbanken in SQL Server-Prozesses freigegeben werden. Mit den verwalteten Thread, die lokaler Speicher verwendet werden, aber möglicherweise nicht verwenden, nicht verwalteten threadlokalen Speicher oder davon ausgehen, dass der Code erneut auf dem aktuellen Betriebssystemthread ausgeführt wird. Ändern Sie Einstellungen wie z. B. das Gebietsschema des Threads nicht. Rufen Sie nicht CreateCriticalSection oder CreateMutex über P/Invoke, da sie erfordern, dass der Thread, der gesperrte Betriebssystemthread wieder entsperrt auch die Sperre beendet wird muss. Da dies bei der Verwendung von Fibern nicht der Fall sein wird, werden kritische Abschnitte von Win32 und Mutex-Verfahren in SQL nutzlos. Sie können die meisten der Status sicher auf ein verwaltetes System.Thread-Objekt verwenden. Dies schließt verwalteten threadlokalen Speicher und der aktuellen Kultur des Benutzers-Benutzeroberfläche (UI) des Threads. Allerdings werden Programmiermodells, es nicht möglich, die die aktuelle Kultur eines Threads zu ändern, bei der Verwendung von SQL; Dies wird durch eine neue Berechtigung erzwungen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Untersuchen Sie die Verwendung von Threads aus, und ändern Sie Ihren Code entsprechend.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Diese Regel sollte nicht unterdrückt werden.
