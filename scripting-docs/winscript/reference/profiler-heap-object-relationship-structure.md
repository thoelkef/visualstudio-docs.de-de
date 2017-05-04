---
title: "PROFILER_HEAP_OBJECT_RELATIONSHIP-Struktur | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 3ab3d986-3314-4c7b-a1c8-18ed691a8b9c
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# PROFILER_HEAP_OBJECT_RELATIONSHIP-Struktur
Stellt eine Beziehung eines Heapobjekts dar.  
  
## Syntax  
  
```  
typedef struct _PROFILER_HEAP_OBJECT_RELATIONSHIP  
{  
    PROFILER_HEAP_OBJECT_NAME_ID relationshipId;  
    PROFILER_RELATIONSHIP_INFO relationshipInfo;  
    [switch_type(PROFILER_RELATIONSHIP_INFO), switch_is(relationshipInfo)] union  
    {  
        [case(PROFILER_PROPERTY_TYPE_NUMBER)] double numberValue;  
        [case(PROFILER_PROPERTY_TYPE_STRING)] LPCWSTR stringValue;  
        [case(PROFILER_PROPERTY_TYPE_HEAP_OBJECT)] PROFILER_HEAP_OBJECT_ID objectId;  
        [case(PROFILER_PROPERTY_TYPE_EXTERNAL_OBJECT)] PROFILER_EXTERNAL_OBJECT_ADDRESS externalObjectAddress;  
    };  
} PROFILER_HEAP_OBJECT_RELATIONSHIP;  
  
```  
  
## Mitglieder  
  
|Member|Wert|Description|  
|------------|----------|-----------------|  
|relationshipId|[PROFILER\_HEAP\_OBJECT\_NAME\_ID\-Typ](../../winscript/reference/profiler-heap-object-name-id-type.md)|Die ID des Beziehungsnamens, von [IActiveScriptProfilerHeapEnum::GetNameIdMap](../../winscript/reference/iactivescriptprofilerheapenum-getnameidmap.md).|  
|relationshipInfo|[PROFILER\_RELATIONSHIP\_INFO\-Enumeration](../../winscript/reference/profiler-relationship-info-enumeration.md)|Informationen über die Beziehung.|  
|numberValue|double|Der Zahlenwert.  Nur ein von `numberValue`\/`stringValue`\/`objectId`\/`externalObjectAddress` wird, auf dem `relationshipInfo`\-Wert festgelegt.|  
|stringValue|LPCWSTR|Der Zeichenfolgenwert.|  
|objectId|[PROFILER\_HEAP\_OBJECT\_ID\-Typ](../../winscript/reference/profiler-heap-object-id-type.md)|Die ID des Heapobjekts.|  
|externalObjectAddress|[PROFILER\_EXTERNAL\_OBJECT\_ADDRESS\-Typ](../../winscript/reference/profiler-external-object-address-type.md)|Die externe Objektadresse.|