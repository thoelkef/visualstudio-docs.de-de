---
title: "IJsDebugDataTarget::FreeVirtualMemory-Methode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.FreeVirtualMemory
apilocation: jscript9diag.dll
ms.assetid: ea54bad3-9ae3-436b-974d-70fc7fffefd6
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugDataTarget::FreeVirtualMemory-Methode
Führt Freigabe und\/oder Aufhebung der Zusage eines Arbeitsspeicherbereich innerhalb des virtuellen Adressraums des Zielprozesses aus.  
  
## Syntax  
  
```  
HRESULT FreeVirtualMemory(  
   UINT64 address,  
   DWORD size,  
   DWORD freeType  
);  
```  
  
#### Parameter  
 `address`  
 \[in\] Adresse innerhalb des Zielprozesses, in dem der Arbeitsspeicher freigegeben werden soll.  
  
 `size`  
 \[in\] Anzahl der aufzuhebenden Bytes.  Um einen Bereich des Arbeitsspeichers freizugeben, muss dieser Wert null sein.  
  
 `freeType`  
 \[in\] Gibt den Typ des auszuführenden freigegebenen Vorgangs an.  Dies ist in der Regel MEM\_RELEASE \(0x8000\), was den angegebenen Bereich von Seiten freigibt.  Nach dem Vorgang sind die Seiten freigegeben.  "MEM\_DECOMMIT \(0x4000\)" kann stattdessen verwendet werden, um die Zusage der Seiten aufzuheben, ohne sie freizugeben.  
  
## Rückgabewert  
  
## Hinweise  
 Weitere Informationen finden Sie in der VirtualFree\-Win32\-API.  
  
## Anforderungen  
 **Header:**  jscript9diag.h  
  
## Siehe auch  
 [IJsDebugDataTarget\-Schnittstelle](../../winscript/reference/ijsdebugdatatarget-interface.md)