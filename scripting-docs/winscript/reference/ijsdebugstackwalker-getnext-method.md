---
title: "IJsDebugStackWalker::GetNext-Methode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugStackWalker.GetNext
apilocation: jscript9diag.dll
ms.assetid: 0b124768-50d3-4a69-876c-1aa337839a4e
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugStackWalker::GetNext-Methode
Ruft den nächsten Frame ab.  
  
## Syntax  
  
```  
HRESULT GetNext(  
   IJsDebugFrame **ppFrame  
);  
```  
  
#### Parameter  
 `ppFrame`  
 \[out\] Objekt, das den Stapelrahmen darstellt.  
  
## Rückgabewert  
  
## Hinweise  
 Gibt E\_JsDEBUG\_OUTSIDE\_OF\_VM zurück, wenn keine weiteren Stapelrahmen aufgelistet werden müssen  
  
## Anforderungen  
 **Header:**  jscript9diag.h  
  
## Siehe auch  
 [IJsDebugStackWalker\-Schnittstelle](../../winscript/reference/ijsdebugstackwalker-interface.md)