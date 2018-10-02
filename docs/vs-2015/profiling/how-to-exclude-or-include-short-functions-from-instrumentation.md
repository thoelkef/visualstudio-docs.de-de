---
title: 'Vorgehensweise: Ausschließen oder Einschließen kurzer Funktionen in die Instrumentierung | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- profiling tools, instrument events
- profiling tools, include short functions
- profiling tools, exclude short functions
ms.assetid: eaeead79-aafe-4490-86ff-6ed4cad9c15f
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f02e34e9fdb399aa8078342d3a8441f077a60f66
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47524864"
---
# <a name="how-to-exclude-or-include-short-functions-from-instrumentation"></a>Gewusst wie: Ausschließen oder Einschließen kurzer Funktionen in die Instrumentation
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Vorgehensweise: ausschließen oder Einschließen kurzer Funktionen in die Instrumentierung](https://docs.microsoft.com/visualstudio/profiling/how-to-exclude-or-include-short-functions-from-instrumentation).  
  
Die Profilerstellungstools schließen standardmäßig *Kleine Funktionen* von der Instrumentation aus. Kleine Funktionen sind kurze Funktionen, die keine Funktionsaufrufe ausführen. Das Ausschließen dieser kleinen Funktionen sorgt für weniger Instrumentation-Overhead und verbessert dadurch die Instrumentierungsgeschwindigkeit. Der Ausschluss kleiner Funktionen reduziert auch die Größe der Leistungsprofilerstellungsdatendatei (.vsp) und die Zeit, die für die Analyse erforderlich ist. Wenn kleine Funktionen ausgeschlossen werden, zählt die Zeit, die in den kleinen Funktionen verbracht wird, gegen die exklusive und inklusive Zeit der übergeordneten Funktionen. Kleine Funktionen können in die Instrumentation ausgeschlossen oder eingeschlossen werden, wie im folgenden Verfahren beschrieben wird.  
  
### <a name="to-exclude-or-include-short-functions-from-instrumentation"></a>So schließen Sie kurze Funktionen in die Instrumentierung ein oder aus  
  
1.  Klicken Sie im **Leistungs-Explorer** mit der rechten Maustaste auf **Leistungssitzung**, und wählen Sie **Eigenschaften** aus.  
  
     Das Dialogfeld **Eigenschaftenseiten** wird angezeigt.  
  
2.  Klicken Sie auf den **Eigenschaftenseiten** auf die Eigenschaften von **Instrumentierung**.  
  
3.  Wählen Sie zum Ausschließen von kleinen Funktionen in die Instrumentierung **Kleine Funktionen in die Instrumentierung ausschließen** Dies ist die Standardeinstellung.  
  
     - oder -   
  
     Deaktivieren Sie zum Einschließen von kleinen Funktionen in die Instrumentierung **Kleine Funktionen in die Instrumentierung ausschließen**  
  
4.  Klicken Sie auf **OK**.  
  
## <a name="see-also"></a>Siehe auch  
 [Steuern der Datensammlung](../profiling/controlling-data-collection.md)   
 [Eigenschaften von Leistungssitzungen](../profiling/performance-session-properties.md)



