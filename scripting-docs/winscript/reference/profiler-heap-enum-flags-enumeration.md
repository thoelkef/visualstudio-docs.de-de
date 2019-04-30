---
title: PROFILER_HEAP_ENUM_FLAGS-Enumeration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 17936b7a-40d5-4774-b92b-b24ee391591e
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d613ed3bcb4699f20d521f08b6c34d55d8363ba4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62830356"
---
# <a name="profilerheapenumflags-enumeration"></a>PROFILER_HEAP_ENUM_FLAGS-Enumeration
Flags, die angeben, ob zusätzliche Informationen zu einem Heapobjekt, auf das in einer Objektbeziehung verwiesen wird, verfügbar gemacht werden. Verwendet die [EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md) Methode.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
typedef [v1_enum] enum {    PROFILER_HEAP_ENUM_FLAGS_NONE                      = 0x00000000,    PROFILER_HEAP_ENUM_FLAGS_STORE_RELATIONSHIP_FLAGS  = 0x00000001,} PROFILER_HEAP_ENUM_FLAGS;  
```  
  
## <a name="members"></a>Member  
  
|Member|Wert|Beschreibung|  
|------------|-----------|-----------------|  
|PROFILER_HEAP_ENUM_FLAGS_NONE|0x00000000|Dieses Heapobjekt macht keine zusätzliche Informationen zu einer Objektbeziehung verfügbar. Dieses heapobjekt verhält sich auf die gleiche Weise wie [iactivescriptprofilercontrol3:: Heapenum](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).|  
|PROFILER_HEAP_ENUM_ENUM_ STORE_RELATIONSHIP_FLAGS|0x00000001|Dieses Heapobjekt macht Informationen dazu verfügbar, ob ein Objekt, auf das in einer Objektbeziehung verwiesen wird, eine Getter- oder eine Setter-Methode ist. Diese Informationen werden in den oberen 2 Bytes (16 Bits) gespeichert werden, der die [PROFILER_HEAP_OBJECT_RELATIONSHIP.relationshipInfo](../../winscript/reference/profiler-heap-object-relationship-structure.md) Feld als eines der [PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS](../../winscript/reference/profiler-heap-object-relationship-flags-enumeration.md) Enumerationswerte.|  
|PROFILER_HEAP_ENUM_FLAGS_SUBSTRINGS|0x00000002|Dieses heapobjekt wird verwendet, damit die Teilzeichenfolge richtig angezeigt.|  
|PROFILER_HEAP_ENUM_FLAGS_RELATIONSHIP_SUBSTRINGS|PROFILER_HEAP_ENUM_FLAGS_STORE_RELATIONSHIP_FLAGS &#124; PROFILER_HEAP_ENUM_FLAGS_SUBSTRINGS|Dieses heapobjekt wird verwendet, damit die Teilzeichenfolge richtig angezeigt.|