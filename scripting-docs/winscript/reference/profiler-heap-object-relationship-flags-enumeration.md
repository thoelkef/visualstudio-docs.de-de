---
title: "PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS-Enumeration | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 1a41b642-c9a9-4d83-b943-d59b232eebf6
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS-Enumeration
Flags, die angeben, ob ein Heapobjekt, auf das in einer Objektbeziehung verwiesen wird, eine Getter\- oder eine Setter\-Methode ist.  Wird in der [EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md)\-Methode verwendet, wenn der Wert von PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_FLAGS im `enumFlags`\-Parameter angegeben ist.  
  
## Syntax  
  
```  
typedef [v1_enum] enum {  
    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_NONE                      = 0x00000000,  
    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_GET_ACCESSOR           = 0x00010000,  
    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_SET_ACCESSOR           = 0x00020000,  
} PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS;  
  
```  
  
## Member  
  
|Member|Wert|Beschreibung|  
|------------|----------|------------------|  
|PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_FLAGS\_NONE|0x00000000|Dieses Heapobjekt, auf das in einer Objektbeziehung verwiesen wird, wird weder als Getter\- noch als Set\-Methode identifiziert.|  
|PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_FLAGS\_IS\_GET\_ACCESSOR|0x00010000|Das Heapobjekt, auf das in einer Objektbeziehung verwiesen wird, ist eine Getter\-Methode.  Diese Informationen werden in den oberen 2 Bytes \(16 Bits\) des Felds [PROFILER\_HEAP\_OBJECT\_RELATIONSHIP.relationshipInfo](../../winscript/reference/profiler-heap-object-relationship-structure.md) gespeichert.|  
|PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_FLAGS\_IS\_SET\_ACCESSOR|0x00020000|Das Heapobjekt, auf das in einer Objektbeziehung verwiesen wird, ist eine Setter\-Methode.  Diese Informationen werden in den oberen 2 Bytes \(16 Bits\) des Felds `PROFILER_HEAP_OBJECT_RELATIONSHIP.relationshipInfo` gespeichert.|