---
title: "IActiveScriptProfilerControl::StartProfiling | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerControl.StartProfiling
apilocation: scrobj.dll
ms.assetid: 56a7b3b7-8c21-43d0-9d8b-53bbc19fabb9
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptProfilerControl::StartProfiling
beginnt, die auf dem Skriptmodul ein Profil erstellen.  Das Skriptmodul erstellt eine Instanz des Profilerobjekts, durch einen Aufruf [CoCreateInstance](http://msdn.microsoft.com/de-de/7295a55b-12c7-4ed0-a7a4-9ecee16afdec) macht.  
  
## Syntax  
  
```  
HRESULT StartProfiling(  
    [in] REFCLSID clsidProfilerObject,  
    [in] DWORD dwEventMask,  
    [in] DWORD dwContext);  
```  
  
#### Parameter  
 `clsidProfilerObject`  
 \[in\] Klassenbezeichner \(CLSID\) des zu erstellenden Profilerobjekts.  
  
 `dwEventMask`  
 \[in\] Eine 4\-Byte\-Bitmaske, die die Ereignistypen angibt.  Die Bits werden in [PROFILER\_EVENT\_MASK\-Enumeration](../../winscript/reference/profiler-event-mask-enumeration.md) definiert.  
  
 `dwContext`  
 \[in\] Ein 4\-Byte\-Wert, der dem Profilerobjekt übergeben wird.  
  
## Rückgabewert  
 Gibt ein HRESULT zurück.  Folgende Werte sind möglich:  
  
|Rückgabewert|Bedeutung|  
|------------------|---------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`ACTIVPROF_E_PROFILER_PRESENT`|Profilerstellung ist bereits aktiviert.|  
  
## Siehe auch  
 [IActiveScriptProfilerControl\-Schnittstelle](../../winscript/reference/iactivescriptprofilercontrol-interface.md)