---
title: marker_importance Enumeration | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_importance
helpviewer_keywords:
- Concurrency::diagnostic::marker_importance enumeration
ms.assetid: d5524ea0-0227-4d8e-9122-332291042df5
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: ae7bb9f300a1d57707966a3b4dbae202eea78d8c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="markerimportance-enumeration"></a>marker_importance-Enumeration
Stellt die Wichtigkeitsstufe eines Markers für die Nebenläufigkeitsschnellansicht dar.  
  
## <a name="syntax"></a>Syntax  
  
```  
enum marker_importance;  
```  
  
## <a name="members"></a>Member  
  
### <a name="values"></a>Werte  
  
|name|description|  
|----------|-----------------|  
|`critical_importance`|Gibt an, dass der Marker kritisch wichtig ist|  
|`high_importance`|Gibt an, dass der Marker hoch wichtig ist|  
|`low_importance`|Gibt an, dass der Marker weniger wichtig ist|  
|`normal_importance`|Gibt an, dass der Marker normal wichtig ist|  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** cvmarkersobj.h  
  
 **Namespace:** Concurrency::diagnostic  
  
## <a name="see-also"></a>Siehe auch  
 [diagnostic-Namespace](../profiling/diagnostic-namespace.md)