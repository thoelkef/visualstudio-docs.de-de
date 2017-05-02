---
title: "IActiveScriptProfilerControl5::EnumHeap2-Methode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: a25859eb-ac28-4a97-bcb3-33788982a76b
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IActiveScriptProfilerControl5::EnumHeap2-Methode
Gibt eine Schnittstelle zurück \([IActiveScriptProfilerHeapEnum\-Schnittstelle](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)\), die verwendet werden kann, um über die GC\-Heapobjekte im Kontext des zugeordneten Skriptmoduls zu iterieren.  
  
 Sie können diese Methode entweder im Debug\- oder Releasemodus aufrufen.  Diese Methode sollte aufgerufen werden, wenn sich der UI\-Thread im Leerlauf befindet.  Nachdem die Methode aufgerufen wurde, sollten so lange keine Vorgänge für das Skriptmodul außer [IActiveScriptProfilerHeapEnum::Next\-Methode](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md) ausgeführt werden, bis [IActiveScriptProfilerHeapEnum::Next\-Methode](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md) den Wert "S\_FALSE" zurückgibt oder der [IActiveScriptProfilerHeapEnum\-Schnittstelle](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)\-Schnittstellenzeiger freigegeben wird.  
  
## Syntax  
  
```  
HRESULT EnumHeap2(  
    [in] PROFILER_HEAP_ENUM_FLAGS enumFlags,  
    [out] IActiveScriptProfilerHeapEnum** ppEnum);  
  
```  
  
#### Parameter  
 enumFlags  
 Ein Wert, der angibt, ob zusätzliche Informationen zu einem Objekt, auf das in einer Objektbeziehung verwiesen wird, verfügbar gemacht werden.  Zusätzliche Informationen geben möglicherweise an, ob das Objekt, auf das verwiesen wird, eine Getter\- oder eine Setter\-Methode ist.  Weitere Informationen hierzu finden Sie unter [PROFILER\_HEAP\_ENUM\_FLAGS\-Enumeration](../../winscript/reference/profiler-heap-enum-flags-enumeration.md).  
  
 ppEnum  
 \[out\] Gibt das [IActiveScriptProfilerHeapEnum\-Schnittstelle](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)\-Objekt zurück.  
  
## Rückgabewert  
 Gibt ein HRESULT zurück.  Folgende Werte sind möglich:  
  
|Rückgabewert|Bedeutung|  
|------------------|---------------|  
|`S_OK`|Die Heapenumeration wurde erfolgreich ausgeführt.|  
|`E_OUTOFMEMORY`|Es stand nicht genügend Arbeitsspeicher zur Verfügung, um die Heapenumeration auszuführen.|  
|`E_FAIL`|Interner Fehler.|