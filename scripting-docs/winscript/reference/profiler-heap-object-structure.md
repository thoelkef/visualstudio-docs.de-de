---
title: PROFILER_HEAP_OBJECT-Struktur | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 9f35362c-6856-4cfb-b990-031a156a58eb
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a1652c6ebffff88782ffcc879158a5142f22395d
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58151192"
---
# <a name="profilerheapobject-structure"></a>PROFILER_HEAP_OBJECT-Struktur
Stellt die Heapobjekte zu, indem erfassen [iactivescriptprofilercontrol3:: Enumheap-Methode](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).  
  
## <a name="syntax"></a>Syntax  
  
```cpp
typedef struct _PROFILER_HEAP_OBJECT  
{  
    UINT size;    union {        PROFILER_HEAP_OBJECT_ID objectId;        PROFILER_EXTERNAL_OBJECT_ADDRESS externalObjectAddress;    };    PROFILER_HEAP_OBJECT_NAME_ID typeNameId;    USHORT flags;     USHORT optionalInfoCount;} PROFILER_HEAP_OBJECT;  
```  
  
## <a name="members"></a>Member  
  
|Member|Typ|Beschreibung|  
|------------|----------|-----------------|  
|objectId|[PROFILER_HEAP_OBJECT_ID-Typ](../../winscript/reference/profiler-heap-object-id-type.md)|Die ID des Heapobjekts.|  
|externalObjectAddress|[PROFILER_EXTERNAL_OBJECT_ADDRESS-Typ](../../winscript/reference/profiler-external-object-address-type.md)|Die externe Objektadresse eines Objekts, z. B. eine reservierte C++-Objekt, das außerhalb der JavaScript-Heap befindet.|  
|typeNameId|[PROFILER_HEAP_OBJECT_NAME_ID-Typ](../../winscript/reference/profiler-heap-object-name-id-type.md)|Die ID des der Typname der Heap-Objekt, aus abgerufen [IActiveScriptProfilerHeapEnum::GetNameIdMap](../../winscript/reference/iactivescriptprofilerheapenum-getnameidmap.md). Nur einer der `externalObjectAddress` oder `typeName` ist vorhanden, je nachdem auf die `flags` Wert.|  
|Flags|[PROFILER_HEAP_OBJECT_FLAGS-Enumeration](../../winscript/reference/profiler-heap-object-flags-enumeration.md)|Die Flags, die grundlegende Informationen über das heapobjekt enthalten.|  
|optionalInfoCount|USHORT|Die Anzahl der [PROFILER_HEAP_OBJECT_OPTIONAL_INFO-Struktur](../../winscript/reference/profiler-heap-object-optional-info-structure.md) Datensätze, die für das heapobjekt verfügbar sind.|