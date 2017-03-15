---
title: "marker_importance-Enumeration | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkersobj/Concurrency::diagnostic::marker_importance"
helpviewer_keywords: 
  - "Concurrency::diagnostic::marker_importance-Enumeration"
ms.assetid: d5524ea0-0227-4d8e-9122-332291042df5
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# marker_importance-Enumeration
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Stellt die Wichtigkeitsstufe eines Parallelitätsschnellansichtsmarkers dar.  
  
## Syntax  
  
```  
enum marker_importance;  
```  
  
## Member  
  
### Werte  
  
|Name|**Beschreibung**|  
|----------|----------------------|  
|`critical_importance`|Gibt an, dass der Marker von entscheidender Wichtigkeit ist.|  
|`high_importance`|Gibt an, dass der Marker von hoher Wichtigkeit ist.|  
|`low_importance`|Gibt an, dass der Marker von niedriger Wichtigkeit ist.|  
|`normal_importance`|Gibt an, dass der Marker von normaler Wichtigkeit ist.|  
  
## Anforderungen  
 **Header:**  cvmarkersobj.h  
  
 **Namespace:**  Concurrency::diagnostic  
  
## Siehe auch  
 [diagnostic\-Namespace](../profiling/diagnostic-namespace.md)