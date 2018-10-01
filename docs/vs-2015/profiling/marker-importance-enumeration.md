---
title: marker_importance Enumeration | Microsoft-Dokumentation
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
- cvmarkersobj/Concurrency::diagnostic::marker_importance
helpviewer_keywords:
- Concurrency::diagnostic::marker_importance enumeration
ms.assetid: d5524ea0-0227-4d8e-9122-332291042df5
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1564de8b63efa48ad83b1aa09f1fce75ff3fbd75
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47522561"
---
# <a name="markerimportance-enumeration"></a>marker_importance-Enumeration
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Marker_importance-Enumeration](https://docs.microsoft.com/visualstudio/profiling/marker-importance-enumeration).  
  
Stellt die Wichtigkeitsstufe eines Markers für die Nebenläufigkeitsschnellansicht dar.  
  
## <a name="syntax"></a>Syntax  
  
```  
enum marker_importance;  
```  
  
## <a name="members"></a>Member  
  
### <a name="values"></a>Werte  
  
|Name|Beschreibung|  
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



