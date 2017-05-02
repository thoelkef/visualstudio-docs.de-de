---
title: "IJsDebugDataTarget::ReadBSTR-Methode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.ReadBSTR
apilocation: jscript9diag.dll
ms.assetid: 4b571db7-04b9-42a0-9a3e-310ac9d0e659
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugDataTarget::ReadBSTR-Methode
Liest ein BSTR vom Debugziel.  
  
## Syntax  
  
```  
HRESULT ReadBSTR(  
   UINT64 address,  
   BSTR *pString  
);  
```  
  
#### Parameter  
 `address`  
 \[in\] Die Adresse, von der gelesen werden muss.  
  
 `pString`  
 \[out\] Das BSTR\-Lesen vom Debugziel.  
  
## Rückgabewert  
  
## Hinweise  
 Gibt E\_JsDEBUG\_INVALID\_MEMORY\_ADDRESS zurück, wenn die Adresse ungültig ist.  
  
## Anforderungen  
 **Header:**  jscript9diag.h  
  
## Siehe auch  
 [IJsDebugDataTarget\-Schnittstelle](../../winscript/reference/ijsdebugdatatarget-interface.md)