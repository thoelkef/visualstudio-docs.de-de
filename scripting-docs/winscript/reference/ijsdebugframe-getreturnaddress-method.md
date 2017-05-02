---
title: "IJsDebugFrame::GetReturnAddress-Methode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugFrame.GetReturnAddress
apilocation: jscript9diag.dll
ms.assetid: 7f10c1d6-d7b9-402e-9020-04cded37f9d3
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugFrame::GetReturnAddress-Methode
Ruft die Rückgabeadresse ab, die beim "Start" des Frames mit "Push" übertragen wird \(siehe GetStackRange\).  
  
## Syntax  
  
```  
HRESULT GetReturnAddress(  
   UINT64 *pReturnAddress  
);  
```  
  
#### Parameter  
 `pReturnAddress`  
 \[out\] Die Rückgabeadresse.  
  
## Rückgabewert  
  
## Anforderungen  
 **Header:**  jscript9diag.h  
  
## Siehe auch  
 [IJsDebugFrame\-Schnittstelle](../../winscript/reference/ijsdebugframe-interface.md)