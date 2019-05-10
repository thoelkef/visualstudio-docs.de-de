---
title: 'Iactivescriptprofilercontrol5:: Enumheap2-Methode | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: a25859eb-ac28-4a97-bcb3-33788982a76b
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0c90c536dee76d67fdb93dd205e8f6eedff6dcc7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992938"
---
# <a name="iactivescriptprofilercontrol5enumheap2-method"></a>IActiveScriptProfilerControl5::EnumHeap2-Methode
Gibt eine Schnittstelle zurück ([IActiveScriptProfilerHeapEnum-Schnittstelle](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)), der zum Durchlaufen der GC-Heapobjekte im Kontext des zugeordneten Skriptmoduls verwendet werden kann.  
  
 Sie können diese Methode entweder im Debug- oder Releasemodus aufrufen. Diese Methode sollte aufgerufen werden, wenn sich der UI-Thread im Leerlauf befindet. Nachdem die Methode aufgerufen wurde, sollten keine Vorgänge ausgeführt werden, für das Skriptmodul außer [iactivescriptprofilerheapenum:: Next-Methode](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md) bis [iactivescriptprofilerheapenum:: Next-Methode](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md)gibt S_FALSE zurück, oder die [IActiveScriptProfilerHeapEnum-Schnittstelle](../../winscript/reference/iactivescriptprofilerheapenum-interface.md) -Schnittstellenzeiger freigegeben.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT EnumHeap2(    [in] PROFILER_HEAP_ENUM_FLAGS enumFlags,    [out] IActiveScriptProfilerHeapEnum** ppEnum);  
```  
  
#### <a name="parameters"></a>Parameter  
 enumFlags  
 Ein Wert, der angibt, ob zusätzliche Informationen zu einem Objekt, auf das in einer Objektbeziehung verwiesen wird, verfügbar gemacht werden. Zusätzliche Informationen geben möglicherweise an, ob das Objekt, auf das verwiesen wird, eine Getter- oder eine Setter-Methode ist. Weitere Informationen finden Sie unter [PROFILER_HEAP_ENUM_FLAGS-Enumeration](../../winscript/reference/profiler-heap-enum-flags-enumeration.md).  
  
 ppEnum  
 [out] Gibt die [IActiveScriptProfilerHeapEnum-Schnittstelle](../../winscript/reference/iactivescriptprofilerheapenum-interface.md).  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt ein HRESULT zurück. Folgende Werte sind möglich:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Die Heapenumeration wurde erfolgreich ausgeführt.|  
|`E_OUTOFMEMORY`|Es stand nicht genügend Arbeitsspeicher zur Verfügung, um die Heapenumeration auszuführen.|  
|`E_FAIL`|Interner Fehler.|