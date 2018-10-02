---
title: 'DA0008: Es wurden nur wenige Beispiele aufgelistet | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.rules.DATooFewSamples
- vs.performance.8
- vs.performance.DA0008
- vs.performance.rules.DA0008
ms.assetid: 8a5b78aa-7b3d-476c-a47d-abfaff3fae7c
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 205bedf2baa7c9fa1e1c5f40ccbaa4041427074b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47524683"
---
# <a name="da0008-few-samples-collected"></a>DA0008: Es wurden nur wenige Beispiele aufgelistet
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [DA0008 es wurden nur: wenige Beispiele aufgelistet](https://docs.microsoft.com/visualstudio/profiling/da0008-few-samples-collected).  
  
Regel-Id | DA0008 ES WURDEN NUR |  
| Kategorie | Verwendung der Profilerstellungstools |  
| Profilerstellungsmethode | Erstellen von Stichproben |  
| Nachricht | Es wurden nur wenige Samplings gesammelt. Erwägen Sie eine längere Ausführung oder eine schnellere Samplingrate aussagekräftigere Ergebnisse zu erzielen. |  
| Regeltyp | Informationen |  
  
## <a name="cause"></a>Ursache  
 Während der Profilerstellung wurden nur wenige Samplings gesammelt.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Wenn die Samplingmethode verwendet wird, sollten Sie eine statistisch signifikante Anzahl von Samplings sammeln, um sicherzustellen, dass die Daten für das tatsächliche Programmverhalten repräsentativ sind. Um Samplingfehler zu minimieren, sollten Sie versuchen, mindestens 1.000 Samplings für Programmanweisungsausführungsverhalten zu sammeln. Wenn Sie nicht genug Samplings sammeln, kann die Analyse der Profilerstellungsdaten irreführend sein.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Überlegen Sie, das Profil bei einer längeren Ausführung der Anwendung zu erstellen oder eine schnellere Samplingrate zu verwenden, um statistisch signifikante Ergebnisse zu erzielen. Weitere Informationen zum Ändern der Samplingrate in der Visual Studio-IDE finden Sie unter [How to: Choose Sampling Events (Vorgehensweise: Auswählen von Samplingereignissen)](../profiling/how-to-choose-sampling-events.md). Weitere Informationen zum Ändern der Samplingrate über die Befehlszeile des Profilerstellungstools finden Sie unter [Timer (Zeitgeber)](../profiling/timer.md) in der [VSPerfCmd](../profiling/vsperfcmd.md)-Referenz.



