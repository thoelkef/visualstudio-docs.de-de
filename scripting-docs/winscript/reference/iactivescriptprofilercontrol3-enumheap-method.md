---
title: "IActiveScriptProfilerControl3::EnumHeap-Methode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 2799d06d-20dd-4c12-9646-554c0ea3606e
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IActiveScriptProfilerControl3::EnumHeap-Methode
Gibt eine Schnittstelle zurück \([IActiveScriptProfilerHeapEnum\-Schnittstelle](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)\) die verwendet werden kann, um die GC\-Heapobjekten im Kontext des zugeordneten Skriptmoduls zu durchlaufen.  
  
 Sie können diese Methode entweder in aufrufen debuggen oder Releasemodus.  Diese Methode sollte aufgerufen werden, wenn UI\-Thread im Leerlauf befindet.  Nachdem die Methode aufgerufen wurde, können keine Vorgänge für das Skriptmodul außer [IActiveScriptProfilerHeapEnum::Next\-Methode](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md) ausgeführt werden, bis [IActiveScriptProfilerHeapEnum::Next\-Methode](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md) S\_FALSE zurückgibt, oder der [IActiveScriptProfilerHeapEnum\-Schnittstelle](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)\-Schnittstellenzeiger freigegeben wird.  
  
## Syntax  
  
```  
HRESULT EnumHeap([out] IActiveScriptProfilerHeapEnum** ppEnum);  
  
```  
  
#### Parameter  
 ppEnum  
 \[out\] Gibt das [IActiveScriptProfilerHeapEnum\-Schnittstelle](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)\-Objekt zurück.  
  
## Rückgabewert  
 Das HRESULT.