---
title: PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS-Enumeration | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 1a41b642-c9a9-4d83-b943-d59b232eebf6
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ab542225e0238dbd40f90d9de66d43d0791e05e0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24734010"
---
# <a name="profilerheapobjectrelationshipflags-enumeration"></a>PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS-Enumeration
Flags, die angeben, ob ein Heapobjekt, auf das in einer Objektbeziehung verwiesen wird, eine Getter- oder eine Setter-Methode ist. Verwendet die [EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md) Methode, wenn der Wert von profiler_heap_object_relationship_flags, in angegeben wird der `enumFlags` Parameter.  
  
## <a name="syntax"></a>Syntax  
  
```  
typedef [v1_enum] enum {    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_NONE                      = 0x00000000,    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_GET_ACCESSOR           = 0x00010000,    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_SET_ACCESSOR           = 0x00020000,} PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS;  
```  
  
## <a name="members"></a>Member  
  
|Member|Wert|Beschreibung|  
|------------|-----------|-----------------|  
|PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_NONE|0x00000000|Dieses Heapobjekt, auf das in einer Objektbeziehung verwiesen wird, wird weder als Getter- noch als Set-Methode identifiziert.|  
|PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_GET_ACCESSOR|0x00010000|Das Heapobjekt, auf das in einer Objektbeziehung verwiesen wird, ist eine Getter-Methode. Diese Informationen werden in den oberen 2 Bytes (16 Bits) gespeichert werden, der die [PROFILER_HEAP_OBJECT_RELATIONSHIP.relationshipInfo](../../winscript/reference/profiler-heap-object-relationship-structure.md) Feld.|  
|PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_SET_ACCESSOR|0x00020000|Das Heapobjekt, auf das in einer Objektbeziehung verwiesen wird, ist eine Setter-Methode. Diese Informationen werden in den oberen 2 Bytes (16 Bits) des Felds `PROFILER_HEAP_OBJECT_RELATIONSHIP.relationshipInfo` gespeichert.|