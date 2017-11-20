---
title: PROFILER_HEAP_OBJECT_RELATIONSHIP-Struktur | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 3ab3d986-3314-4c7b-a1c8-18ed691a8b9c
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2b992b020c0aa42a6f27e484d55fe89a514c0198
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="profilerheapobjectrelationship-structure"></a>PROFILER_HEAP_OBJECT_RELATIONSHIP-Struktur
Stellt eine Beziehung eines Heapobjekts dar.  
  
## <a name="syntax"></a>Syntax  
  
```  
typedef struct _PROFILER_HEAP_OBJECT_RELATIONSHIP{    PROFILER_HEAP_OBJECT_NAME_ID relationshipId;    PROFILER_RELATIONSHIP_INFO relationshipInfo;    [switch_type(PROFILER_RELATIONSHIP_INFO), switch_is(relationshipInfo)] union    {        [case(PROFILER_PROPERTY_TYPE_NUMBER)] double numberValue;        [case(PROFILER_PROPERTY_TYPE_STRING)] LPCWSTR stringValue;        [case(PROFILER_PROPERTY_TYPE_HEAP_OBJECT)] PROFILER_HEAP_OBJECT_ID objectId;        [case(PROFILER_PROPERTY_TYPE_EXTERNAL_OBJECT)] PROFILER_EXTERNAL_OBJECT_ADDRESS externalObjectAddress;    };} PROFILER_HEAP_OBJECT_RELATIONSHIP;  
```  
  
## <a name="members"></a>Member  
  
|Member|Wert|Beschreibung|  
|------------|-----------|-----------------|  
|relationshipId|[PROFILER_HEAP_OBJECT_NAME_ID-Typ](../../winscript/reference/profiler-heap-object-name-id-type.md)|Die ID der Beziehung aus Name [IActiveScriptProfilerHeapEnum::GetNameIdMap](../../winscript/reference/iactivescriptprofilerheapenum-getnameidmap.md).|  
|relationshipInfo|[PROFILER_RELATIONSHIP_INFO-Enumeration](../../winscript/reference/profiler-relationship-info-enumeration.md)|Informationen über die Beziehung.|  
|numberValue|double|Der Zahlenwert. Nur eine der `numberValue` / `stringValue` / `objectId` / `externalObjectAddress` festgelegt ist, basierend auf den `relationshipInfo` Wert.|  
|StringValue|LPCWSTR|Der Zeichenfolgenwert.|  
|ObjectId|[PROFILER_HEAP_OBJECT_ID-Typ](../../winscript/reference/profiler-heap-object-id-type.md)|Die ID des Heapobjekts.|  
|externalObjectAddress|[PROFILER_EXTERNAL_OBJECT_ADDRESS-Typ](../../winscript/reference/profiler-external-object-address-type.md)|Die externe Objektadresse.|  
|subString|[PROFILER_PROPERTY_TYPE_SUBSTRING_INFO-Struktur](../../winscript/reference/profiler-property-type-substring-info-structure.md)|Die Informationen über den Typ der Teilzeichenfolge.|