---
title: "IDebugApplicationThread110::IsThreadCallable | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationThread110::IsThreadCallable"
ms.assetid: 2a75a366-801d-47e0-bba3-51aa669e03a7
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IDebugApplicationThread110::IsThreadCallable
Bestimmt, ob dieser Thread in einem Zustand, der die Aufrufe verarbeitet, die mithilfe der Thread\-Umschaltungsmechanismen des PDMS gemacht werden, wie SynchronousCallInThread ist.  
  
> [!IMPORTANT]
>  [IDebugApplicationThread110\-Schnittstelle](../../winscript/reference/idebugapplicationthread110-interface.md) wird durch PDM v11.0 und höher implementiert.  Fundumgebung activdbg100.h.  
  
## Syntax  
  
```cpp  
HRESULT IsThreadCallable([out, annotation("_Out_")] BOOL * pfIsCallable);  
```  
  
#### Parameter  
 `pfIsCallable`  
 \[out\] `true`, wenn der Thread aufgerufen werden kann; andernfalls `false`.  
  
## Siehe auch  
 [IDebugApplicationThread110\-Schnittstelle](../../winscript/reference/idebugapplicationthread110-interface.md)