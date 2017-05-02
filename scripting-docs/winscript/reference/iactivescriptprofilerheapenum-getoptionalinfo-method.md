---
title: "IActiveScriptProfilerHeapEnum::GetOptionalInfo-Methode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 99ed9df5-71cf-4c25-b189-af9accc466ee
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScriptProfilerHeapEnum::GetOptionalInfo-Methode
Ruft optionale Informationen über das angegebene Objekt ab \(aus dem Satz der Heapobjekte, die von der [IActiveScriptProfilerControl3::EnumHeap\-Methode](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md) zurückgegeben werden\).  
  
 Sie sollten den zurückgegebenen Arbeitsspeicher, der den zurückgegebenen Objekten zugewiesen ist, nicht freigeben.  Stattdessen sollten Sie die [IActiveScriptProfilerHeapEnum::FreeObjectAndOptionalInfo\-Methode](../../winscript/reference/iactivescriptprofilerheapenum-freeobjectandoptionalinfo-method.md) aufrufen.  
  
## Syntax  
  
```  
HRESULT GetOptionalInfo (  
    [in] PROFILER_HEAP_OBJECT* heapObject,  
    [in] ULONG celt,  
    [out, size_is(celt)] PROFILER_HEAP_OBJECT_OPTIONAL_INFO* optionalInfo);  
  
```  
  
#### Parameter  
 `heapObject`  
 Das [PROFILER\_HEAP\_OBJECT\-Struktur](../../winscript/reference/profiler-heap-object-structure.md), für das die Informationen zurückgegeben werden sollen.  
  
 `celt`  
 Die Anzahl von zurückzugebenden [PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO\-Struktur](../../winscript/reference/profiler-heap-object-optional-info-structure.md)\-Strukturen.  
  
 `optionalInfo`  
 \[out\] Ein Array von [PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO\-Struktur](../../winscript/reference/profiler-heap-object-optional-info-structure.md)\-Strukturen für das angegebene Objekt.  
  
## Rückgabewert  
 Das HRESULT.