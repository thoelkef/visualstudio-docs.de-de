---
title: "IJsDebug::OpenVirtualProcess-Methode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJSDebug.OpenVirtualProcess
apilocation: jscript9diag.dll
ms.assetid: 5612bf1b-a4e3-4eaf-ac5e-c2e1f147c395
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebug::OpenVirtualProcess-Methode
Factorymethode, die zum Erstellen eines neuen virtuellen Prozessobjekts verwendet wird.  
  
## Syntax  
  
```  
 HRESULT OpenVirtualProcess(  
   DWORD processId,  
   UINT64 runtimeJsBaseAddress,  
   IJsDebugDataTarget *pDataTarget,  
   IJsDebugProcess **ppProcess  
);  
```  
  
#### Parameter  
 `processId`  
 \[in\] Prozess\-ID, an die der Debugger anzufügen ist.  
  
 `runtimeJsBaseAddress`  
 \[in\] Die Basisadresse, an der die JavaScript\-Laufzeit in den Zielprozess geladen wurde.  
  
 `pDataTarget`  
 \[in\] Debugger hat Schnittstelle angegeben, an der der Zustand des Prozesses abgefragt werden kann.  
  
 `ppProcess`  
 \[out\] Neues Debugprozessobjekt  
  
## Rückgabewert  
  
## Hinweise  
 Gibt "E\_JsDEBUG\_MISMATCHED\_RUNTIME" zurück, wenn "Jscript9diag" und "Jscript9" nicht übereinstimmen.  
  
## Anforderungen  
 **Header:**  jscript9diag.h  
  
## Siehe auch  
 [IJsDebug\-Schnittstelle](../../winscript/reference/ijsdebug-interface.md)