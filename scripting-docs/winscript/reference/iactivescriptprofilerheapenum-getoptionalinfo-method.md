---
title: 'Iactivescriptprofilerheapenum:: Getoptionalinfo-Methode | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 99ed9df5-71cf-4c25-b189-af9accc466ee
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e6ad237f2feb173408e895984dab7e7455004d16
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724680"
---
# <a name="iactivescriptprofilerheapenumgetoptionalinfo-method"></a>IActiveScriptProfilerHeapEnum::GetOptionalInfo-Methode
Ruft die optionale Informationen für das angegebene Objekt ab (aus dem Satz der Heap-Objekte zurückgegeben, die von der [iactivescriptprofilercontrol3:: Enumheap-Methode](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)).  
  
 Sie sollten den zurückgegebenen Arbeitsspeicher, der den zurückgegebenen Objekten zugewiesen ist, nicht freigeben. Rufen Sie stattdessen sollte der [iactivescriptprofilerheapenum:: Freeobjectandoptionalinfo-Methode](../../winscript/reference/iactivescriptprofilerheapenum-freeobjectandoptionalinfo-method.md).  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT GetOptionalInfo (    [in] PROFILER_HEAP_OBJECT* heapObject,    [in] ULONG celt,    [out, size_is(celt)] PROFILER_HEAP_OBJECT_OPTIONAL_INFO* optionalInfo);  
```  
  
#### <a name="parameters"></a>Parameter  
 `heapObject`  
 Die [PROFILER_HEAP_OBJECT-Struktur](../../winscript/reference/profiler-heap-object-structure.md) für die die Informationen zurückgegeben werden sollen.  
  
 `celt`  
 Die Anzahl der [PROFILER_HEAP_OBJECT_OPTIONAL_INFO-Struktur](../../winscript/reference/profiler-heap-object-optional-info-structure.md) Strukturen zurückgeben.  
  
 `optionalInfo`  
 [out] Ein Array von [PROFILER_HEAP_OBJECT_OPTIONAL_INFO-Struktur](../../winscript/reference/profiler-heap-object-optional-info-structure.md) Strukturen für das angegebene Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Das HRESULT.