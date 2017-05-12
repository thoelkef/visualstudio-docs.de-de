---
title: "IJsDebugDataTarget::GetThreadContext-Methode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.GetThreadContext
apilocation: jscript9diag.dll
ms.assetid: faf2a689-6c49-4a7d-b5a6-2b323e2257a7
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugDataTarget::GetThreadContext-Methode
Ruft den Kontext zum angegebenen Thread ab.  
  
## Syntax  
  
```  
HRESULT GetThreadContext(  
   DWORD threadId,  
   ULONG32 contextFlags,  
   ULONG32 contextSize,  
   void *pContext  
);  
```  
  
#### Parameter  
 `threadId`  
 \[in\] Im Zielprozess ausgeführter Thread.  
  
 `contextFlags`  
 \[in\] Gibt Kontextflags an.  Dies ist mit dem "ContextFlags"\-Feld von CONTEXT identisch \(weitere Informationen finden Sie unter "winnt.h", suchen Sie nach "CONTEXT\_ALL"\).  
  
 `contextSize`  
 \[in\] Die Größe des durch "pContext" angegebenen Puffers.  
  
 `pContext`  
 \[out\] Empfängt plattformspezifische CONTEXT\-Struktur in den Puffer, der von "pContext" angegeben wird.  
  
## Rückgabewert  
  
## Anforderungen  
 **Header:**  jscript9diag.h  
  
## Siehe auch  
 [IJsDebugDataTarget\-Schnittstelle](../../winscript/reference/ijsdebugdatatarget-interface.md)