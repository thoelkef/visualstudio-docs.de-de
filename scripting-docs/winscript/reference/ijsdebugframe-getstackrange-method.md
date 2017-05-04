---
title: "IJsDebugFrame::GetStackRange-Methode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugFrame.GetStackRange
apilocation: jscript9diag.dll
ms.assetid: a6d1d8be-efc0-442d-9756-1959c8f102bd
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugFrame::GetStackRange-Methode
Gibt den Bereich der absoluten Adresse des logischen JavaScript\-Stapelrahmens zurück.  
  
## Syntax  
  
```  
HRESULT GetStackRange(  
   UINT64 *pStart,  
   UINT64 *pEnd  
);  
```  
  
#### Parameter  
 `pStart`  
 \[out\] Unterster Stapelzeiger des Frames.  
  
 `pEnd`  
 \[out\] Oberster Stapelzeiger des Frames.  
  
## Rückgabewert  
  
## Hinweise  
 Diese Methode ist für die Zusammenführung überlappender Stapelüberwachungen nützlich, die aus mehreren Laufzeiten erfasst wird.  Der Anfangs\- sowie Endstapelzeiger kann mehrere Stapelrahmen des physischen Computers umfassen \(für interpretierte JavaScript\-Laufzeitrahmen\). "start \> end" während der Stapel von hohen zu niedrigen Adressen zunimmt.  
  
## Anforderungen  
 **Header:**  jscript9diag.h  
  
## Siehe auch  
 [IJsDebugFrame\-Schnittstelle](../../winscript/reference/ijsdebugframe-interface.md)