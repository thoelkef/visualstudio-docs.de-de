---
title: 'Ijsdebugdatatarget:: Allocatevirtualmemory-Methode | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.AllocateVirtualMemory
apilocation:
- jscript9diag.dll
ms.assetid: 1d3a77b0-c1de-4a0c-a759-3e0c68fd96dd
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c04bf21882ec39054c74f060eaa2c6f65ac0b4d6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62583066"
---
# <a name="ijsdebugdatatargetallocatevirtualmemory-method"></a>IJsDebugDataTarget::AllocateVirtualMemory-Methode
Reserviert und/oder führt Commit eines Arbeitsspeicherbereich innerhalb des virtuellen Adressraums des Zielprozesses aus.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT AllocateVirtualMemory(  
   UINT64 address,  
   DWORD size,  
   DWORD allocationType,  
   DWORD pageProtection,  
   UINT64 *pAllocatedAddress  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `address`  
 [in] Die Adresse innerhalb des Zielprozesses, wo der Commit des Arbeitsspeichers ausgeführt oder selbiger reserviert werden soll. Dieser Wert ist normalerweise null. In diesem Fall wählt das System eine Adresse aus.  
  
 `size`  
 [in] Die Größe des zuzuordnenden Arbeitsspeicherbereichs in Bytes. Das System rundet automatisch bis zur Grenze der folgenden Seite auf.  
  
 `allocationType`  
 [in] Gibt den Typ der auszuführenden Speicherbelegung an. Dies ist normalerweise MEM_COMMIT &#124; MEM_RESERVE (0 x 3000) das behält sich vor, und führt einen Commit für eine Zuordnung in einem Schritt.  
  
 `pageProtection`  
 [in] Der Arbeitsspeicherschutz für den Bereich der Seiten, die zugeordnet werden sollen. Wenn ein Commit der Seiten ausgeführt wird, können Sie eine der Speicherschutzkonstanten (beispielsweise, PAGE_READWRITE, PAGE_EXECUTE) angeben.  
  
 `pAllocatedAddress`  
 [out] Basisadresse des zugeordneten Bereichs der Seiten.  
  
## <a name="return-value"></a>Rückgabewert  
  
## <a name="remarks"></a>Hinweise  
 Die Funktion initialisiert den Speicher, den sie Null zuordnet, es sei denn, MEM_RESET wird verwendet. Weitere Informationen finden Sie in der VirtualAlloc-Win32-API.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** "jscript9diag.h"  
  
## <a name="see-also"></a>Siehe auch  
 [IJsDebugDataTarget-Schnittstelle](../../winscript/reference/ijsdebugdatatarget-interface.md)