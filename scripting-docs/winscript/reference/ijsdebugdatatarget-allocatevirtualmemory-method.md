---
title: "IJsDebugDataTarget::AllocateVirtualMemory-Methode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.AllocateVirtualMemory
apilocation: jscript9diag.dll
ms.assetid: 1d3a77b0-c1de-4a0c-a759-3e0c68fd96dd
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugDataTarget::AllocateVirtualMemory-Methode
Reserviert und\/oder führt Commit eines Arbeitsspeicherbereich innerhalb des virtuellen Adressraums des Zielprozesses aus.  
  
## Syntax  
  
```  
HRESULT AllocateVirtualMemory(  
   UINT64 address,  
   DWORD size,  
   DWORD allocationType,  
   DWORD pageProtection,  
   UINT64 *pAllocatedAddress  
);  
```  
  
#### Parameter  
 `address`  
 \[in\] Die Adresse innerhalb des Zielprozesses, wo der Commit des Arbeitsspeichers ausgeführt oder selbiger reserviert werden soll.  Dieser Wert ist normalerweise null. In diesem Fall wählt das System eine Adresse aus.  
  
 `size`  
 \[in\] Die Größe des zuzuordnenden Arbeitsspeicherbereichs in Bytes.  Das System rundet automatisch bis zur Grenze der folgenden Seite auf.  
  
 `allocationType`  
 \[in\] Gibt den Typ der auszuführenden Speicherbelegung an.  Dies ist normalerweise MEM\_COMMIT &#124; MEM\_RESERVE \(0x3000\), das eine Speicherbelegung in einem Schritt reserviert und übergibt.  
  
 `pageProtection`  
 \[in\] Der Arbeitsspeicherschutz für den Bereich der Seiten, die zugeordnet werden sollen.  Wenn ein Commit der Seiten ausgeführt wird, können Sie eine der Speicherschutzkonstanten \(beispielsweise, PAGE\_READWRITE, PAGE\_EXECUTE\) angeben.  
  
 `pAllocatedAddress`  
 \[out\] Basisadresse des zugeordneten Bereichs der Seiten.  
  
## Rückgabewert  
  
## Hinweise  
 Die Funktion initialisiert den Speicher, den sie Null zuordnet, es sei denn, MEM\_RESET wird verwendet.  Weitere Informationen finden Sie in der VirtualAlloc\-Win32\-API.  
  
## Anforderungen  
 **Header:**  jscript9diag.h  
  
## Siehe auch  
 [IJsDebugDataTarget\-Schnittstelle](../../winscript/reference/ijsdebugdatatarget-interface.md)