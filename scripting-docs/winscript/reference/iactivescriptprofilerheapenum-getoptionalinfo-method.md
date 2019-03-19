---
title: 'Iactivescriptprofilerheapenum:: Getoptionalinfo-Methode | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 99ed9df5-71cf-4c25-b189-af9accc466ee
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ab8096b79cfbb91e4b65256c84ab1ba01207d9ed
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58146993"
---
# <a name="iactivescriptprofilerheapenumgetoptionalinfo-method"></a>IActiveScriptProfilerHeapEnum::GetOptionalInfo-Methode
Ruft optionale Informationen für das angegebene Objekt ab (aus dem Satz der Heap-Objekte zurückgegeben, die von der [iactivescriptprofilercontrol3:: Enumheap-Methode](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)).  
  
 Sie sollten den zurückgegebenen Arbeitsspeicher, der den zurückgegebenen Objekten zugewiesen ist, nicht freigeben. Rufen Sie stattdessen die [iactivescriptprofilerheapenum:: Freeobjectandoptionalinfo-Methode](../../winscript/reference/iactivescriptprofilerheapenum-freeobjectandoptionalinfo-method.md).  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetOptionalInfo (    [in] PROFILER_HEAP_OBJECT* heapObject,    [in] ULONG celt,    [out, size_is(celt)] PROFILER_HEAP_OBJECT_OPTIONAL_INFO* optionalInfo);  
```  
  
#### <a name="parameters"></a>Parameter  
 `heapObject`  
 Die [PROFILER_HEAP_OBJECT-Struktur](../../winscript/reference/profiler-heap-object-structure.md) für die die Informationen zurückgegeben werden sollen.  
  
 `celt`  
 Die Anzahl der [PROFILER_HEAP_OBJECT_OPTIONAL_INFO-Struktur](../../winscript/reference/profiler-heap-object-optional-info-structure.md) -Strukturen, zurückgegeben.  
  
 `optionalInfo`  
 [out] Ein Array von [PROFILER_HEAP_OBJECT_OPTIONAL_INFO-Struktur](../../winscript/reference/profiler-heap-object-optional-info-structure.md) Strukturen für das angegebene Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Das HRESULT.