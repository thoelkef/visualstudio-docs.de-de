---
title: "IJsDebugDataTarget::ReadMemory-Methode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.ReadMemory
apilocation: jscript9diag.dll
ms.assetid: 664e0f7d-2007-45f4-b993-36fe8b1944e5
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugDataTarget::ReadMemory-Methode
Liest den Arbeitsspeicher des Zielprozesses.  
  
## Syntax  
  
```  
HRESULT ReadMemory(  
   UINT64 address,  
   JsDebugReadMemoryFlags flags,  
   BYTE *pBuffer,  
   DWORD size,  
   DWORD *pBytesRead  
);  
```  
  
#### Parameter  
 `address`  
 \[in\] Die Basisadresse, aus der der Arbeitsspeicher des Zielprozesses zu lesen ist.  
  
 `flags`  
 \[in\] Flags, die das Verhalten von ReadMemory steuern.  
  
 `pBuffer`  
 \[out\] Ein Puffer, der den Inhalt vom Adressbereich des Zielprozesses empfängt.  Beim Fehlschlagen wird der Inhalt dieses Puffers nicht angegeben.  
  
 `size`  
 \[in\] Die Anzahl an Bytes, die aus dem Prozess gelesen werden sollen.  
  
 `pBytesRead`  
 \[out\] Gibt die Anzahl der Bytes an, die aus dem Zielprozess gelesen wurden.  Wenn "JsDebugAllowPartialRead" nicht aktiviert ist, wird bei Erfolg dieser Wert immer genau der Eingabegröße entsprechen.  Wenn "JsDebugAllowPartialRead" angegeben ist, wird bei Erfolg dieser Wert größer als null sein.  
  
## Rückgabewert  
  
## Hinweise  
 Gibt bei Erfolg S\_OK zurück, und Fehlercodes werden für jeden Fehler verwendet.  Gibt E\_JsDEBUG\_INVALID\_MEMORY\_ADDRESS zurück, wenn die Adresse ungültig ist.  Weitere Informationen finden Sie unter "JsDebugAllowPartialRead".  
  
## Anforderungen  
 **Header:**  jscript9diag.h  
  
## Siehe auch  
 [IJsDebugDataTarget\-Schnittstelle](../../winscript/reference/ijsdebugdatatarget-interface.md)