---
title: "IActiveScriptProfilerHeapEnum::Next-Methode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 0336286f-1dcd-4df9-adf5-76b59b4e74bb
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IActiveScriptProfilerHeapEnum::Next-Methode
Ruft das folgende Objekt ab, oder Objekte im Satz von Heapobjekten aus [IActiveScriptProfilerControl3::EnumHeap\-Methode](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md) ein.  
  
## Syntax  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] PROFILER_HEAP_OBJECT** heapObjects,   
    [out] ULONG *pceltFetched);  
  
```  
  
#### Parameter  
 `celt`  
 Die Anzahl von Objekten, die zurückgegeben werden soll.  
  
 `heapObjects`  
 \[out\] Die folgenden [PROFILER\_HEAP\_OBJECT\-Struktur](../../winscript/reference/profiler-heap-object-structure.md)\-Strukturen.  
  
 `pceltFetched`  
 \[out\] Die Anzahl der zurückgegebenen Objekte,  
  
## Rückgabewert  
 Das HRESULT.