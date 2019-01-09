---
title: 'Iactivescriptprofilercontrol5:: Enumheap2-Methode | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: a25859eb-ac28-4a97-bcb3-33788982a76b
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 21661953edbdba2314b88aad5fb55451b06b51a8
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097629"
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