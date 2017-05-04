---
title: "IDebugApplication110::AsynchronousCallInMainThread | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplication110::AsynchronousCallInMainThread"
ms.assetid: 13b80ff0-4bed-48c1-8031-d4147b51bf6c
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugApplication110::AsynchronousCallInMainThread
Führt einen asynchronen Aufruf im Hauptausführungsthread auf.  
  
> [!IMPORTANT]
>  [IDebugApplication110\-Schnittstelle](../../winscript/reference/idebugapplication110-interface.md) wird durch PDM v11.0 und höher implementiert.  Fundumgebung activdbg100.h.  
  
## Syntax  
  
```cpp  
HRESULT AsynchronousCallInMainThread([in] IDebugThreadCall* pptc, [in] DWORD_PTR dwParam1, [in] DWORD_PTR dwParam2, [in] DWORD_PTR dwParam3);  
  
```  
  
#### Parameter  
 `pptc`  
 Das Objekt [IDebugThreadCall\-Schnittstelle](../../winscript/reference/idebugthreadcall-interface.md) rufen Sie auf.  
  
 `dwParam1`  
 Der erste Parameter des Aufrufs.  
  
 `dwParam1`  
 Der erste Parameter des Aufrufs.  
  
 `dwParam2`  
 Der zweite Parameter des Aufrufs.  
  
 `dwParam3`  
 Der dritte Parameter des Aufrufs.  
  
## Siehe auch  
 [IDebugApplication110\-Schnittstelle](../../winscript/reference/idebugapplication110-interface.md)