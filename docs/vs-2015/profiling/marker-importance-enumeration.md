---
title: marker_importance Enumeration | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_importance
helpviewer_keywords:
- Concurrency::diagnostic::marker_importance enumeration
ms.assetid: d5524ea0-0227-4d8e-9122-332291042df5
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a4451a7b222b66f0fe5bea2b0e5f2b8499c9033c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54779036"
---
# <a name="markerimportance-enumeration"></a>marker_importance-Enumeration
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Stellt die Wichtigkeitsstufe eines Markers für die Nebenläufigkeitsschnellansicht dar.  
  
## <a name="syntax"></a>Syntax  
  
```  
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
 **Header:** cvmarkersobj.h  
  
 **Namespace:** Concurrency::diagnostic  
  
## <a name="see-also"></a>Siehe auch  
 [diagnostic-Namespace](../profiling/diagnostic-namespace.md)
