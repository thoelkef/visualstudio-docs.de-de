---
title: "IEnumJsStackFrames::Next-Methode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumJsStackFrames.Next
apilocation: jscript9diag.dll
ms.assetid: efceb3a1-9239-4f55-9cbb-94670679988b
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IEnumJsStackFrames::Next-Methode
Ruft die angegebene Anzahl an Frames ab.  
  
## Syntax  
  
```  
HRESULT Next(  
   ULONG cFrameCount,  
   JS_NATIVE_FRAME *pFrames,  
   ULONG *pcFetched  
);  
```  
  
#### Parameter  
 `cFrameCount`  
 \[in\] Die Anzahl der abzurufenden Frames.  
  
 `pFrames`  
 \[out\] Das Array, um die Frames zu speichern.  
  
 `pcFetched`  
 \[out\] Die Anzahl der zurückgegebenen Frames.  
  
## Rückgabewert  
  
## Anforderungen  
 **Header:**  jscript9diag.h  
  
## Siehe auch  
 [IEnumJsStackFrames\-Schnittstelle](../../winscript/reference/ienumjsstackframes-interface.md)