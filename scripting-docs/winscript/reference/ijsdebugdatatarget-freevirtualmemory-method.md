---
title: 'Ijsdebugdatatarget:: FreeVirtualMemory-Methode | Microsoft Docs'
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugDataTarget.FreeVirtualMemory
apilocation: jscript9diag.dll
ms.assetid: ea54bad3-9ae3-436b-974d-70fc7fffefd6
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3b53d7f80227a1c4eb0ef0293093543c09c5a367
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugdatatargetfreevirtualmemory-method"></a>IJsDebugDataTarget::FreeVirtualMemory-Methode
Führt Freigabe und/oder Aufhebung der Zusage eines Arbeitsspeicherbereich innerhalb des virtuellen Adressraums des Zielprozesses aus.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT FreeVirtualMemory(  
   UINT64 address,  
   DWORD size,  
   DWORD freeType  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `address`  
 [in] Adresse innerhalb des Zielprozesses, in dem der Arbeitsspeicher freigegeben werden soll.  
  
 `size`  
 [in] Anzahl der aufzuhebenden Bytes. Um einen Bereich des Arbeitsspeichers freizugeben, muss dieser Wert null sein.  
  
 `freeType`  
 [in] Gibt den Typ des auszuführenden freigegebenen Vorgangs an. Dies ist in der Regel MEM_RELEASE (0x8000), was den angegebenen Bereich von Seiten freigibt. Nach dem Vorgang sind die Seiten freigegeben. "MEM_DECOMMIT (0x4000)" kann stattdessen verwendet werden, um die Zusage der Seiten aufzuheben, ohne sie freizugeben.  
  
## <a name="return-value"></a>Rückgabewert  
  
## <a name="remarks"></a>Hinweise  
 Weitere Informationen finden Sie in der VirtualFree-Win32-API.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** "jscript9diag.h"  
  
## <a name="see-also"></a>Siehe auch  
 [IJsDebugDataTarget-Schnittstelle](../../winscript/reference/ijsdebugdatatarget-interface.md)