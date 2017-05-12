---
title: "IJsDebugDataTarget::ReadNullTerminatedString-Methode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.ReadNullTerminatedString
apilocation: jscript9diag.dll
ms.assetid: 64683b39-6fc2-40c4-82ae-2a6f58d392d5
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugDataTarget::ReadNullTerminatedString-Methode
Liest die angegebene Anzahl von Zeichen aus dem Ziel.  
  
## Syntax  
  
```  
HRESULT ReadNullTerminatedString(  
   UINT64 address,  
   UINT16 characterSize,  
   UINT32 maxCharacters,  
   BSTR *pString  
);  
```  
  
#### Parameter  
 `address`  
 \[in\] Die Adresse, von der gelesen werden muss.  
  
 `characterSize`  
 \[in\] Größe jedes Zeichens in der Zeichenfolge  
  
 `maxCharacters`  
 \[in\] Die maximale Anzahl der zu lesenden Zeichen. maxCharacters sollte angemessen sein.  Jede Anforderung von mehr als 128 MB Arbeitsspeicher schlägt fehl.  Wenn die Zeichenfolge größer als maxCharacters ist, wird die Ergebniszeichenfolge nach maxCharacters abgeschnitten.  
  
 `pString`  
 \[out\] Das BSTR\-Lesen vom Ziel.  
  
## Rückgabewert  
  
## Hinweise  
 Gibt S\_FALSE zurück, wenn es abgeschnitten wird.  
  
## Anforderungen  
 **Header:**  jscript9diag.h  
  
## Siehe auch  
 [IJsDebugDataTarget\-Schnittstelle](../../winscript/reference/ijsdebugdatatarget-interface.md)