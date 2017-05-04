---
title: "IDebugApplicationThread110::GetActiveThreadRequestCount | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationThread110::GetActiveThreadRequestCount"
ms.assetid: 025d2072-1d7f-4448-8aa3-38a014313570
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugApplicationThread110::GetActiveThreadRequestCount
Gibt die Anzahl der Thread aus den Thread\-Umschaltungsmechanismen des PDMS zurück, die gerade verarbeitet werden.  Diese Zahl ist normalerweise 0 oder 1.  jedoch eventuell die Zahl, wenn ein Threadaufruf Verarbeitung jedoch die Trigger startet, ein synchrones, vom Thread auszurufen, oder enthält andernfalls den Thread und die eingehenden höher erneut verarbeitet werden Anrufe, \(beispielsweise durch das Starten eines [IRemoteDebugApplicationEvents\-Schnittstelle](../../winscript/reference/iremotedebugapplicationevents-interface.md)\-Ereignisses, das auf dem Debuggerthread ausgegeben wird.\)  
  
> [!IMPORTANT]
>  [IDebugApplicationThread110\-Schnittstelle](../../winscript/reference/idebugapplicationthread110-interface.md) wird durch PDM v11.0 und höher implementiert.  Fundumgebung activdbg100.h.  
  
## Syntax  
  
```cpp  
HRESULT GetActiveThreadRequestCount([out, annotation("_Out_")] UINT * puiThreadRequests);  
  
```  
  
#### Parameter  
 `puiThreadRequests`  
 \[out\] Die Anzahl der Thread.  
  
## Siehe auch  
 [IDebugApplicationThread110\-Schnittstelle](../../winscript/reference/idebugapplicationthread110-interface.md)