---
title: 'DA0003: Viele Kernelbeispiele | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DA0003
- vs.performance.DA0003
- vs.performance.3
- vs.performance.rules.DAManyKernelSamples
ms.assetid: c1f46f77-eb95-42e5-b340-d86bc9de41b4
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: aa60d16eec09255f39e18b86b468a2fef2269aff
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54782633"
---
# <a name="da0003-many-kernel-samples"></a>DA0003: Zahlreiche Kernelbeispiele
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Regel-Id | DA0003 |  
| Kategorie | Verwendung der Profilerstellungstools |  
| Profilerstellungsmethoden | Erstellen von Stichproben |  
| Nachricht | Sie haben einen hohen Anteil von Beispielen im Kernelmodus ausgeführt. Dies deutet auf ein hohes Maß an E/A-Aktivitäten oder auf häufige Kontextwechsel hin. Erstellen Sie nach Möglichkeit ein neues Profil für die Anwendung, und verwenden Sie dabei den Instrumentierungsmodus.|  
| Regeltyp | Informationen |  
  
## <a name="cause"></a>Ursache  
 Ein großer Teil der Aufruflistensamples, die für die Anwendung gesammelt wurden, wurden im Kernelmodus ausgeführt. Gegebenenfalls sollten Sie das Profil für Ihre Anwendung mit einer anderen Methode erstellen.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 In Windows kann Code im Kernel- oder im Benutzermodus ausgeführt werden. Der Kernelmodus wird auch privilegierter Modus genannt. Nur Systemcode einer niedrigeren Ebene wie ein Gerätetreiber wird im Kernelmodus ausgeführt. Eine Anwendung im Benutzermodus kann in den Kernelmodus wechseln, um E/A-Vorgänge auszuführen, um auf Thread- oder Prozesssynchronisierungsprimitive zu warten oder um Systemaufrufe auszuführen.  
  
 Sampling ist am effektivsten, wenn Sie Profile für Anwendungen erstellen, die sich die meiste Zeit im Benutzermodus befinden. Die Anzahl der Samples, die während der Ausführung der Anwendung im Kernelmodus erfasst wurden, kann auf häufige E/A-Vorgänge oder häufige Kontextwechsel hindeuten. Keiner dieser Vorgänge kann mithilfe der Samplingmethode untersucht werden. Wenn zu viele Samples im Kernelmodus entnommen werden, enthalten die Samplingdaten möglicherweise zu wenig Samples aus dem Benutzermodus, um statistisch signifikant zu sein.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Erstellen Sie nach Möglichkeit ein neues Profil für die Anwendung, und verwenden Sie dabei eine der folgenden Optionen:  
  
-   Profilerstellung mit der Instrumentierungsmethode  
  
-   Erhöhen der Samplingrate, um weitere Samples im Benutzermodus zu sammeln
