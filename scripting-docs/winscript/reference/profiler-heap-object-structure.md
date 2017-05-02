---
title: "PROFILER_HEAP_OBJECT-Struktur | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 9f35362c-6856-4cfb-b990-031a156a58eb
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# PROFILER_HEAP_OBJECT-Struktur
Stellt die Heapobjekte dar, die von [IActiveScriptProfilerControl3::EnumHeap\-Methode](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md) erfasst werden.  
  
## Syntax  
  
```  
typedef struct _PROFILER_HEAP_OBJECT  
{  
    UINT size;  
    union {  
        PROFILER_HEAP_OBJECT_ID objectId;  
        PROFILER_EXTERNAL_OBJECT_ADDRESS externalObjectAddress;  
    };  
    PROFILER_HEAP_OBJECT_NAME_ID typeNameId;  
    USHORT flags;   
    USHORT optionalInfoCount;  
} PROFILER_HEAP_OBJECT;  
```  
  
## Mitglieder  
  
|Member|Text \[Type\]|Description|  
|------------|-------------------|-----------------|  
|objectId|[PROFILER\_HEAP\_OBJECT\_ID\-Typ](../../winscript/reference/profiler-heap-object-id-type.md)|Die ID des Heapobjekts.|  
|externalObjectAddress|[PROFILER\_EXTERNAL\_OBJECT\_ADDRESS\-Typ](../../winscript/reference/profiler-external-object-address-type.md)|Die externe Objektadresse eines Objekts, wie ein Objekt \+\+\-allocated, das außerhalb von JavaScript\-Heaps ist.|  
|typeNameId|[PROFILER\_HEAP\_OBJECT\_NAME\_ID\-Typ](../../winscript/reference/profiler-heap-object-name-id-type.md)|Die ID des Heapobjekttypnamens abgerufen, von [IActiveScriptProfilerHeapEnum::GetNameIdMap](../../winscript/reference/iactivescriptprofilerheapenum-getnameidmap.md).  Nur eine von `externalObjectAddress` oder von `typeName` ist je nach `flags`\-Wert vorhanden.|  
|flags|[PROFILER\_HEAP\_OBJECT\_FLAGS\-Enumeration](../../winscript/reference/profiler-heap-object-flags-enumeration.md)|Die Flags, die grundlegende Informationen zum Heapobjekt enthalten.|  
|optionalInfoCount|USHORT|Die Anzahl der [PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO\-Struktur](../../winscript/reference/profiler-heap-object-optional-info-structure.md) Datensätzen, die für das Heapobjekt verfügbar sind.|