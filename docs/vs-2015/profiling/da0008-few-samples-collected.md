---
title: 'DA0008: Es wurden nur wenige Beispiele aufgelistet | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DATooFewSamples
- vs.performance.8
- vs.performance.DA0008
- vs.performance.rules.DA0008
ms.assetid: 8a5b78aa-7b3d-476c-a47d-abfaff3fae7c
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 03fd9b6fd794320faf76119616900b79d5bf4333
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187861"
---
# <a name="da0008-few-samples-collected"></a>DA0008: Es wurden nur wenige Beispiele aufgelistet
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Regel-ID | DA0008 |  
| Kategorie | Profilerstellungstools Verwendung |  
| Profil Erstellungs Methode | Stichprobenentnahme |  
| Meldung | Es wurden nur wenige Samplings gesammelt. Sie sollten eine längere Ausführung oder eine schnellere Samplingrate in Betracht ziehen, um aussagekräftigere Ergebnisse zu erzielen.|  
| Regeltyp | Informationen |  
  
## <a name="cause"></a>Ursache  
 Während der Profilerstellung wurden nur wenige Samplings gesammelt.  
  
## <a name="rule-description"></a>Beschreibung der Regel  
 Wenn die Samplingmethode verwendet wird, sollten Sie eine statistisch signifikante Anzahl von Samplings sammeln, um sicherzustellen, dass die Daten für das tatsächliche Programmverhalten repräsentativ sind. Um Samplingfehler zu minimieren, sollten Sie versuchen, mindestens 1.000 Samplings für Programmanweisungsausführungsverhalten zu sammeln. Wenn Sie nicht genug Samplings sammeln, kann die Analyse der Profilerstellungsdaten irreführend sein.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Überlegen Sie, das Profil bei einer längeren Ausführung der Anwendung zu erstellen oder eine schnellere Samplingrate zu verwenden, um statistisch signifikante Ergebnisse zu erzielen. Informationen zum Ändern der Samplingrate in der Visual Studio-IDE finden Sie unter Gewusst [wie: Auswählen von Samplingereignissen](../profiling/how-to-choose-sampling-events.md). Weitere Informationen zum Ändern der Samplingrate über die Befehlszeile des Profilerstellungstools finden Sie unter [Timer (Zeitgeber)](../profiling/timer.md) in der [VSPerfCmd](../profiling/vsperfcmd.md)-Referenz.
