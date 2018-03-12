---
title: diagnostic-Namespace | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic
helpviewer_keywords:
- Concurrency::diagnostic namespace
ms.assetid: ad786b19-7c4c-46ee-bfb6-c4752b373a09
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 3fb9b831562e2d9e4ce7d686f49ac484d58f6804
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="diagnostic-namespace"></a>diagnostic-Namespace
Der `diagnostics`-Namespace stellt Funktionen zum Ausgeben von Markern für Nebenläufigkeitsschnellansichten bereit.  
  
## <a name="syntax"></a>Syntax  
  
```  
namespace diagnostic;  
```  
  
## <a name="members"></a>Member  
  
### <a name="classes"></a>Klassen  
  
|name|description|  
|----------|-----------------|  
|[marker_series-Klasse](../profiling/marker-series-class.md)|Stellt einen seriellen Kanal mit Ereignissen dar, die von einem einzelnen Anbieter generiert werden.|  
|[span-Klasse](../profiling/span-class.md)|Definiert eine Phase der Anwendung.|  
  
### <a name="enumerations"></a>Enumerationen  
  
|name|description|  
|----------|-----------------|  
|[marker_importance-Enumeration](../profiling/marker-importance-enumeration.md)|Stellt die Wichtigkeitsstufe eines Markers für die Nebenläufigkeitsschnellansicht dar.|  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** cvmarkersobj.h  
  
 **Namespace:** Parallelität  
  
## <a name="see-also"></a>Siehe auch  
 [Concurrency-Namespace (Parallelitätsschnellansicht)](../profiling/concurrency-namespace-concurrency-visualizer.md)