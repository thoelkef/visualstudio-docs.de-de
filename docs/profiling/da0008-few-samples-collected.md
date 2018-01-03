---
title: 'DA0008: Es wurden nur wenige Beispiele aufgelistet | Microsoft-Dokumentation'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.rules.DATooFewSamples
- vs.performance.8
- vs.performance.DA0008
- vs.performance.rules.DA0008
ms.assetid: 8a5b78aa-7b3d-476c-a47d-abfaff3fae7c
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b4f472be09694e4e3bcfa0d3a60a2c1703534423
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="da0008-few-samples-collected"></a>DA0008: Es wurden nur wenige Beispiele aufgelistet
|||  
|-|-|  
|Regel-ID|DA0008|  
|Kategorie|Verwendung der Profilerstellungstools|  
|Profilerstellungsmethode|Sampling|  
|Meldung|Es wurden nur wenige Samplings gesammelt. Sie sollten eine längere Ausführung oder eine schnellere Samplingrate in Betracht ziehen, um aussagekräftigere Ergebnisse zu erzielen.|  
|Regeltyp|Information|  
  
## <a name="cause"></a>Ursache  
 Während der Profilerstellung wurden nur wenige Samplings gesammelt.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Wenn die Samplingmethode verwendet wird, sollten Sie eine statistisch signifikante Anzahl von Samplings sammeln, um sicherzustellen, dass die Daten für das tatsächliche Programmverhalten repräsentativ sind. Um Samplingfehler zu minimieren, sollten Sie versuchen, mindestens 1.000 Samplings für Programmanweisungsausführungsverhalten zu sammeln. Wenn Sie nicht genug Samplings sammeln, kann die Analyse der Profilerstellungsdaten irreführend sein.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Überlegen Sie, das Profil bei einer längeren Ausführung der Anwendung zu erstellen oder eine schnellere Samplingrate zu verwenden, um statistisch signifikante Ergebnisse zu erzielen. Weitere Informationen zum Ändern der Samplingrate in der Visual Studio-IDE finden Sie unter [How to: Choose Sampling Events (Vorgehensweise: Auswählen von Samplingereignissen)](../profiling/how-to-choose-sampling-events.md). Weitere Informationen zum Ändern der Samplingrate über die Befehlszeile des Profilerstellungstools finden Sie unter [Timer (Zeitgeber)](../profiling/timer.md) in der [VSPerfCmd](../profiling/vsperfcmd.md)-Referenz.