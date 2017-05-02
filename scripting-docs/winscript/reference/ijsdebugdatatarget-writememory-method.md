---
title: "IJsDebugDataTarget::WriteMemory-Methode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.WriteMemory
apilocation: jscript9diag.dll
ms.assetid: 0d3c04c3-9ef8-4842-a145-3d29bca75062
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugDataTarget::WriteMemory-Methode
Liest den Arbeitsspeicher des Zielprozesses.  
  
## Syntax  
  
```  
HRESULT WriteMemory(  
   UINT64 address,  
   const BYTE *pMemory,  
   DWORD size  
);  
```  
  
#### Parameter  
 `address`  
 \[in\] Die Basisadresse, aus der in den Arbeitsspeicher des Zielprozesses zu schreiben ist.  
  
 `pMemory`  
 \[in\] Die Daten, die in den Adressraum des angegebenen Prozesses zu schreiben sind.  
  
 `size`  
 \[in\] Die Anzahl der Bytes, die in den Prozess geschrieben werden sollen.  
  
## Rückgabewert  
  
## Hinweise  
 Bevor die Datenübertragung erfolgt, überprüft das System, dass alle Daten in der Basisadresse und der Arbeitsspeicher in der angegebenen Größe für Schreibzugriff verfügbar ist. Wenn darauf nicht zugegriffen werden kann, löst die Funktion einen E\_JsDEBUG\_INVALID\_MEMORY\_ADDRESS\-Fehler aus.  
  
## Anforderungen  
 **Header:**  jscript9diag.h  
  
## Siehe auch  
 [IJsDebugDataTarget\-Schnittstelle](../../winscript/reference/ijsdebugdatatarget-interface.md)