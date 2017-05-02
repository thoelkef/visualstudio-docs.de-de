---
title: "PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST-Struktur | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 46ca87ea-5b0f-437d-a33f-b2d9a457e036
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST-Struktur
Stellt eine Liste von Beziehungen dar, die einem Heapobjekt gehören.  
  
## Syntax  
  
```  
typedef struct _PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST  
{  
    UINT count;  
    [size_is(count)] PROFILER_HEAP_OBJECT_RELATIONSHIP elements[];  
} PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST;  
  
```  
  
## Mitglieder  
  
|Member|Text \[Type\]|Description|  
|------------|-------------------|-----------------|  
|count|UINT|Die Anzahl von Beziehungen eines Heapobjekts.|  
|Elemente|[PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\-Struktur](../../winscript/reference/profiler-heap-object-relationship-structure.md)|Die Beziehungen eines Heapobjekts.|