---
title: "IDebugApplicationThread110::IsSuspendedForBreakPoint | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationThread110::IsSuspendedForBreakPoint"
ms.assetid: 60688222-557f-4a43-a19b-846cee393cd0
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IDebugApplicationThread110::IsSuspendedForBreakPoint
Bestimmt, ob [IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md) um diesem Thread aufgerufen wurde und noch nicht abgeschlossen ist.  
  
> [!IMPORTANT]
>  [IDebugApplicationThread110\-Schnittstelle](../../winscript/reference/idebugapplicationthread110-interface.md) wird durch PDM v11.0 und höher implementiert.  Fundumgebung activdbg100.h.  
  
## Syntax  
  
```cpp  
HRESULT IsSuspendedForBreakPoint([out, annotation("_Out_")] BOOL * pfIsSuspended);  
```  
  
#### Parameter  
 `pfIsSuspended`  
 \[out\] `true`, wenn der Thread für einen Haltepunkt unterbrochen wird; andernfalls `false`.  
  
## Siehe auch  
 [IDebugApplicationThread110\-Schnittstelle](../../winscript/reference/idebugapplicationthread110-interface.md)