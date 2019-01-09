---
title: 'Iactivescriptprofilercontrol3:: Enumheap-Methode | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 2799d06d-20dd-4c12-9646-554c0ea3606e
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 25e81a4aa631c142d4444c0578742f68001a108d
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097018"
---
# <a name="iactivescriptprofilercontrol3enumheap-method"></a>IActiveScriptProfilerControl3::EnumHeap-Methode
Gibt eine Schnittstelle zurück ([IActiveScriptProfilerHeapEnum-Schnittstelle](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)), der zum Durchlaufen der GC-Heapobjekte im Kontext des zugeordneten Skriptmoduls verwendet werden kann.  
  
 Sie können diese Methode entweder im Debug- oder Releasemodus aufrufen. Diese Methode sollte aufgerufen werden, wenn sich der UI-Thread im Leerlauf befindet. Nachdem die Methode aufgerufen wurde, sollten keine Vorgänge ausgeführt werden, für das Skriptmodul außer [iactivescriptprofilerheapenum:: Next-Methode](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md) bis [iactivescriptprofilerheapenum:: Next-Methode](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md)gibt S_FALSE zurück, oder die [IActiveScriptProfilerHeapEnum-Schnittstelle](../../winscript/reference/iactivescriptprofilerheapenum-interface.md) -Schnittstellenzeiger freigegeben.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT EnumHeap([out] IActiveScriptProfilerHeapEnum** ppEnum);  
```  
  
#### <a name="parameters"></a>Parameter  
 ppEnum  
 [out] Gibt die [IActiveScriptProfilerHeapEnum-Schnittstelle](../../winscript/reference/iactivescriptprofilerheapenum-interface.md).  
  
## <a name="return-value"></a>Rückgabewert  
 Das HRESULT.