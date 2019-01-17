---
title: PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS-Enumeration | Microsoft-Dokumentation
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
ms.openlocfilehash: b78285f332b339533d81228de5877043f699a67c
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349139"
---
# <a name="profilerheapobjectrelationshipflags-enumeration"></a>PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS-Enumeration
Flags, die angeben, ob ein Heapobjekt, auf das in einer Objektbeziehung verwiesen wird, eine Getter- oder eine Setter-Methode ist. Verwendet die [EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md) Methode, wenn der PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS-Wert, in angegeben wird der `enumFlags` Parameter.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
typedef [v1_enum] enum {    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_NONE                      = 0x00000000,    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_GET_ACCESSOR           = 0x00010000,    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_SET_ACCESSOR           = 0x00020000,} PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS;  
```  
  
## <a name="members"></a>Member  
  
|Member|Wert|Beschreibung|  
|------------|-----------|-----------------|  
|PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_NONE|0x00000000|Dieses Heapobjekt, auf das in einer Objektbeziehung verwiesen wird, wird weder als Getter- noch als Set-Methode identifiziert.|  
|PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_GET_ACCESSOR|0x00010000|Das Heapobjekt, auf das in einer Objektbeziehung verwiesen wird, ist eine Getter-Methode. Diese Informationen werden in den oberen 2 Bytes (16 Bits) gespeichert werden, der die [PROFILER_HEAP_OBJECT_RELATIONSHIP.relationshipInfo](../../winscript/reference/profiler-heap-object-relationship-structure.md) Feld.|  
|PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_SET_ACCESSOR|0x00020000|Das Heapobjekt, auf das in einer Objektbeziehung verwiesen wird, ist eine Setter-Methode. Diese Informationen werden in den oberen 2 Bytes (16 Bits) des Felds `PROFILER_HEAP_OBJECT_RELATIONSHIP.relationshipInfo` gespeichert.|