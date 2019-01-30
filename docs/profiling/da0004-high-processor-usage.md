---
title: 'DA0004: Hohe Prozessorauslastung | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DAHighProcessorUsage
- vs.performance.rules.DA0004
- vs.performance.DA0004
- vs.performance.4
ms.assetid: 2c4fb569-929e-4f1d-8c50-b590ee371351
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 274027f1877c5274e0f78da7634c7ac5109380ac
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54990068"
---
# <a name="da0004-high-processor-usage"></a>DA0004: Hohe Prozessorauslastung

|||  
|-|-|  
|Regel-ID|DA0004|  
|Kategorie|Verwendung der Profilerstellungstools|  
|Profilerstellungsmethoden|Instrumentierung<br /><br /> Sampling|  
|Meldung|Die Prozessorauslastung liegt permanent über 75 %. Sie sollten die Verwendung des Samplingmodus für CPU-gebundene Anwendungen in Betracht ziehen.|  
|Regeltyp|Information|  

 Wenn Sie Profile mithilfe der Sampling-, .NET-Arbeitsspeicher- oder Ressourcenkonfliktmethode Profile erstellen, müssen mindestens 10 Samplings erfasst werden, damit diese Regel ausgelöst wird.  

## <a name="cause"></a>Ursache  
 Die Auslastung des Prozessors (der CPU) war in den Profilerstellungsdaten hoch, die mithilfe der Instrumentierungsmethode gesammelt wurden. Sie bei der Profilerstellung für eine CPU-gebundene Anwendung ggf. die Samplingmethode zur Profilerstellung.  

## <a name="rule-description"></a>Regelbeschreibung  
 Während dieser Profilerstellung war der Prozessor (oder die Prozessoren) gleichbleibend stark ausgelastet. Eine hohe CPU-Auslastung kann auf eine CPU-gebundene Anwendung hindeuten. Instrumentierte Profile sind nicht die effektivste Möglichkeit, CPU-Verwendungsszenarios zu untersuchen. Sampling ist wirksamer, wenn Sie Anwendungen profilieren, die viel Zeit mit dem Ausführen von Anweisungen auf dem Prozessor verbringen.  

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Wiederholen Sie die Profilerstellung für Ihre Anwendung, wobei Sie diesmal anstelle der Instrumentierungsmethode die Samplingmethode verwenden, es sei denn, Sie benötigen Funktionstimings oder Sie möchten sich nicht so sehr über Prozessorengpässe als vielmehr über die Ein-/Ausgabe informieren.