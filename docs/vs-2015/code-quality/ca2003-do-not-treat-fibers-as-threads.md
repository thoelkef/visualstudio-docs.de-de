---
title: 'CA2003: Fibers nicht als Threads behandeln | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
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
ms.openlocfilehash: f3d72e052decc5a26dd134aafcaac8aba6af699f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49810917"
---
# <a name="ca2003-do-not-treat-fibers-as-threads"></a>CA2003: Fibers nicht als Threads behandeln
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



