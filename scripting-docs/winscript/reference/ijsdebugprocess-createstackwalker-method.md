---
title: "IJsDebugProcess::CreateStackWalker-Methode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugProcess.CreateStackWalker
apilocation: jscript9diag.dll
ms.assetid: 9d02e21d-7900-4942-8d17-cd04a2261463
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugProcess::CreateStackWalker-Methode
Factorymethode für Stapeldurchlauf.  
  
## Syntax  
  
```  
HRESULT CreateStackWalker(  
   DWORD threadId,  
   IJsDebugStackWalker **ppStackWalker  
);  
```  
  
#### Parameter  
 `threadId`  
 \[in\] Die Thread\-ID.  
  
 `ppStackWalker`  
 \[out\] Das neue Stapeldurchlaufobjekt.  
  
## Rückgabewert  
  
## Hinweise  
 Gibt E\_JsDEBUG\_UNKNOWN\_THREAD zurück, wenn im Thread nicht JavaScript vorhanden ist.  Diese Methode darf nur aufgerufen werden, während der Zielprozess angehalten wird.  
  
## Anforderungen  
 **Header:**  jscript9diag.h  
  
## Siehe auch  
 [IJsDebugProcess\-Schnittstelle](../../winscript/reference/ijsdebugprocess-interface.md)