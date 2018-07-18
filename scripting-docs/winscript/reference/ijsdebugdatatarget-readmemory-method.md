---
title: 'Ijsdebugdatatarget:: ReadMemory-Methode | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.ReadMemory
apilocation:
- jscript9diag.dll
ms.assetid: 664e0f7d-2007-45f4-b993-36fe8b1944e5
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fc1b67b33e17761a675d6ced9e175b4206ede2e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24728500"
---
# <a name="ijsdebugdatatargetreadmemory-method"></a>IJsDebugDataTarget::ReadMemory-Methode
Liest den Arbeitsspeicher des Zielprozesses.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT ReadMemory(  
   UINT64 address,  
   JsDebugReadMemoryFlags flags,  
   BYTE *pBuffer,  
   DWORD size,  
   DWORD *pBytesRead  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `address`  
 [in] Die Basisadresse, aus der der Arbeitsspeicher des Zielprozesses zu lesen ist.  
  
 `flags`  
 [in] Flags, die das Verhalten von ReadMemory steuern.  
  
 `pBuffer`  
 [out] Ein Puffer, der den Inhalt vom Adressbereich des Zielprozesses empfängt. Beim Fehlschlagen wird der Inhalt dieses Puffers nicht angegeben.  
  
 `size`  
 [in] Die Anzahl an Bytes, die aus dem Prozess gelesen werden sollen.  
  
 `pBytesRead`  
 [out] Gibt die Anzahl der Bytes an, die aus dem Zielprozess gelesen wurden. Wenn "JsDebugAllowPartialRead" nicht aktiviert ist, wird bei Erfolg dieser Wert immer genau der Eingabegröße entsprechen. Wenn "JsDebugAllowPartialRead" angegeben ist, wird bei Erfolg dieser Wert größer als null sein.  
  
## <a name="return-value"></a>Rückgabewert  
  
## <a name="remarks"></a>Hinweise  
 Gibt bei Erfolg S_OK zurück, und Fehlercodes werden für jeden Fehler verwendet. Gibt E_JsDEBUG_INVALID_MEMORY_ADDRESS zurück, wenn die Adresse ungültig ist. Weitere Informationen finden Sie unter "JsDebugAllowPartialRead".  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** "jscript9diag.h"  
  
## <a name="see-also"></a>Siehe auch  
 [IJsDebugDataTarget-Schnittstelle](../../winscript/reference/ijsdebugdatatarget-interface.md)