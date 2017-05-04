---
title: "IJsDebugDataTarget::GetTlsValue-Methode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.GetTlsValue
apilocation: jscript9diag.dll
ms.assetid: db575be9-7b24-45c5-9008-e4f2f76d6757
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugDataTarget::GetTlsValue-Methode
Für den Thread, der debuggt wird, wird der Wert im Slot des lokalen Speichers des Threads \(TLS\) für den angegebenen TLS\-Index abgerufen.  
  
## Syntax  
  
```  
HRESULT GetTlsValue(  
   DWORD threadId,  
   UINT32 tlsIndex,  
   UINT64 *pValue  
);  
```  
  
#### Parameter  
 `threadId`  
 \[in\] Im Zielprozess ausgeführter Thread, aus dem gelesen werden soll.  
  
 `tlsIndex`  
 \[in\] Der TLS\-Index, der belegt wurde, als der Zielprozess die TlsAlloc\-Funktion aufrief.  
  
 `pValue`  
 \[out\] Der Wert mit Zeigergröße, der im TLS\-Slot des Threads gespeichert wurde.  Wenn der Zielthread 32\-Bit ist, sind die oberen 32\-Bit dieses Werts null.  
  
## Rückgabewert  
  
## Hinweise  
 Jeder Thread eines Prozesses hat seinen eigenen Slot für jeden TLS\-Index.  
  
## Anforderungen  
 **Header:**  jscript9diag.h  
  
## Siehe auch  
 [IJsDebugDataTarget\-Schnittstelle](../../winscript/reference/ijsdebugdatatarget-interface.md)