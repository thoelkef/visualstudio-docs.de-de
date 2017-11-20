---
title: 'Iactivescriptprofilercontrol3:: Enumheap-Methode | Microsoft Docs'
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 2799d06d-20dd-4c12-9646-554c0ea3606e
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7d6fc79a9d6d35e35181c3505e07af2d9a1962c2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercontrol3enumheap-method"></a>IActiveScriptProfilerControl3::EnumHeap-Methode
Gibt eine Schnittstelle zurück ([IActiveScriptProfilerHeapEnum-Schnittstelle](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)), der zum Durchlaufen der GC-heapobjekten im Kontext des Datenbankmoduls zugeordnete Skript verwendet werden kann.  
  
 Sie können diese Methode entweder im Debug- oder Releasemodus aufrufen. Diese Methode sollte aufgerufen werden, wenn sich der UI-Thread im Leerlauf befindet. Nachdem die Methode aufgerufen wurde, sollten keine Vorgänge ausgeführt werden, für das Skriptmodul außer [iactivescriptprofilerheapenum:: Next-Methode](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md) bis [iactivescriptprofilerheapenum:: Next-Methode](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md)gibt S_FALSE zurück oder [IActiveScriptProfilerHeapEnum-Schnittstelle](../../winscript/reference/iactivescriptprofilerheapenum-interface.md) Schnittstellenzeiger freigegeben wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT EnumHeap([out] IActiveScriptProfilerHeapEnum** ppEnum);  
```  
  
#### <a name="parameters"></a>Parameter  
 ppEnum  
 [out] Gibt die [IActiveScriptProfilerHeapEnum-Schnittstelle](../../winscript/reference/iactivescriptprofilerheapenum-interface.md).  
  
## <a name="return-value"></a>Rückgabewert  
 Das HRESULT.