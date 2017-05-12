---
title: "IActiveScriptProfilerControl::SetProfilerEventMask | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerControl.SetProfilerEventMask
apilocation: scrobj.dll
ms.assetid: 207e192f-e12e-4fcb-b4d8-eaee50ecb86e
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptProfilerControl::SetProfilerEventMask
Legt eine 4\-Byte\-Bitmaske fest, die die Ereignistypen angibt, die das Skriptmodul auslösen soll.  
  
## Syntax  
  
```  
RESULT SetProfilerEventMask(  
    [in] DWORD dwEventMask);  
```  
  
#### Parameter  
 `dwEventMask`  
 \[in\] Eine 4\-Byte\-Bitmaske, die die Ereignistypen angibt.  Die Bits werden in [PROFILER\_EVENT\_MASK\-Enumeration](../../winscript/reference/profiler-event-mask-enumeration.md) definiert.  
  
## Rückgabewert  
 Gibt ein HRESULT zurück.  Folgende Werte sind möglich:  
  
|Rückgabewert|Bedeutung|  
|------------------|---------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Profilerstellung ist nicht aktiviert.|  
  
## Siehe auch  
 [IActiveScriptProfilerControl\-Schnittstelle](../../winscript/reference/iactivescriptprofilercontrol-interface.md)