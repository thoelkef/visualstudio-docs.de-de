---
title: "PROFILER_HEAP_ENUM_FLAGS-Enumeration | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 17936b7a-40d5-4774-b92b-b24ee391591e
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# PROFILER_HEAP_ENUM_FLAGS-Enumeration
Flags, die angeben, ob zusätzliche Informationen zu einem Heapobjekt, auf das in einer Objektbeziehung verwiesen wird, verfügbar gemacht werden.  Wird in der [EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md)\-Methode verwendet.  
  
## Syntax  
  
```  
typedef [v1_enum] enum {  
    PROFILER_HEAP_ENUM_FLAGS_NONE                      = 0x00000000,  
    PROFILER_HEAP_ENUM_FLAGS_STORE_RELATIONSHIP_FLAGS  = 0x00000001,  
} PROFILER_HEAP_ENUM_FLAGS;  
  
```  
  
## Member  
  
|Member|Wert|Beschreibung|  
|------------|----------|------------------|  
|PROFILER\_HEAP\_ENUM\_FLAGS\_NONE|0x00000000|Dieses Heapobjekt macht keine zusätzliche Informationen zu einer Objektbeziehung verfügbar.  Dieses Heapobjekt verhält sich auf die gleiche Weise wie [IActiveScriptProfilerControl3::HeapEnum](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).|  
|PROFILER\_HEAP\_ENUM\_ENUM\_ STORE\_RELATIONSHIP\_FLAGS|0x00000001|Dieses Heapobjekt macht Informationen dazu verfügbar, ob ein Objekt, auf das in einer Objektbeziehung verwiesen wird, eine Getter\- oder eine Setter\-Methode ist.  Diese Informationen werden in den oberen 2 Bytes \(16 Bits\) des Felds [PROFILER\_HEAP\_OBJECT\_RELATIONSHIP.relationshipInfo](../../winscript/reference/profiler-heap-object-relationship-structure.md) als einer der Enumerationswerte von [PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_FLAGS](../../winscript/reference/profiler-heap-object-relationship-flags-enumeration.md) gespeichert.|