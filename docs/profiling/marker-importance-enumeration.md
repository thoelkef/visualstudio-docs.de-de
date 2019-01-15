---
title: marker_importance Enumeration | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_importance
helpviewer_keywords:
- Concurrency::diagnostic::marker_importance enumeration
ms.assetid: d5524ea0-0227-4d8e-9122-332291042df5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 330ba15fa62272bd2c2f7ea7b40d6b527ab237c3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53841689"
---
# <a name="markerimportance-enumeration"></a>marker_importance-Enumeration
Stellt die Wichtigkeitsstufe eines Markers für die Nebenläufigkeitsschnellansicht dar.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum marker_importance;  
```  
  
## <a name="members"></a>Member  
  
### <a name="values"></a>Werte  
  
|name|Beschreibung|  
|----------|-----------------|  
|`critical_importance`|Gibt an, dass der Marker kritisch wichtig ist|  
|`high_importance`|Gibt an, dass der Marker hoch wichtig ist|  
|`low_importance`|Gibt an, dass der Marker weniger wichtig ist|  
|`normal_importance`|Gibt an, dass der Marker normal wichtig ist|  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** *cvmarkersobj.h*  
  
 **Namespace:** Concurrency::diagnostic  
  
## <a name="see-also"></a>Siehe auch  
 [diagnostic-Namespace](../profiling/diagnostic-namespace.md)