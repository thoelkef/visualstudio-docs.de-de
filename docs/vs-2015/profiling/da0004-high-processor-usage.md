---
title: 'DA0004: Hohe Prozessorauslastung | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.rules.DAHighProcessorUsage
- vs.performance.rules.DA0004
- vs.performance.DA0004
- vs.performance.4
ms.assetid: 2c4fb569-929e-4f1d-8c50-b590ee371351
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a942a26bb4cd8ccca94fd442250fe8a239cba4ed
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51764026"
---
# <a name="da0004-high-processor-usage"></a>DA0004: Hohe Prozessorauslastung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Regel-Id | DA0004 |  
| Kategorie | Verwendung der Profilerstellungstools |  
| Profilerstellungsmethoden | Instrumentation Sampling |  
| Nachricht | Die prozessorauslastung liegt permanent über 75 %. Betrachten Sie die Verwendung des Samplingmodus für CPU-gebundene Anwendungen. |  
| Regeltyp | Informationen |  
  
 Wenn Sie Profile mithilfe der Sampling-, .NET-Arbeitsspeicher- oder Ressourcenkonfliktmethode Profile erstellen, müssen mindestens 10 Samplings erfasst werden, damit diese Regel ausgelöst wird.  
  
## <a name="cause"></a>Ursache  
 Die Auslastung des Prozessors (der CPU) war in den Profilerstellungsdaten, die mithilfe der Instrumentierungsmethode gesammelt wurden, sehr hoch. Sie bei der Profilerstellung für eine CPU-gebundene Anwendung ggf. die Samplingmethode zur Profilerstellung.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Während dieser Profilerstellungsausführung ist der Prozessor (oder die Prozessoren) gleichbleibend stark ausgelastet. Eine hohe CPU-Auslastung kann auf eine CPU-gebundene Anwendung hindeuten. Instrumentierte Profile sind normalerweise nicht die effektivste Möglichkeit, CPU-Verwendungsszenarios zu untersuchen. Sampling ist normalerweise wirksamer, wenn Sie Anwendungen profilieren, die viel Zeit mit dem Ausführen von Anweisungen auf dem Prozessor verbringen.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Wiederholen Sie die Profilerstellung für Ihre Anwendung, wobei Sie diesmal anstelle der Instrumentierungsmethode die Samplingmethode verwenden, es sei denn, Sie benötigen Funktionstimings oder Sie möchten sich nicht so sehr über Prozessorengpässe als vielmehr über die Ein-/Ausgabe informieren.




