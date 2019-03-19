---
title: 'Ijsdebugdatatarget:: Readnullterminatedstring-Methode | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.ReadNullTerminatedString
apilocation:
- jscript9diag.dll
ms.assetid: 64683b39-6fc2-40c4-82ae-2a6f58d392d5
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 178a2d3705e4904de9253c02319f6ba94e567d76
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58146655"
---
# <a name="ijsdebugdatatargetreadnullterminatedstring-method"></a>IJsDebugDataTarget::ReadNullTerminatedString-Methode
Liest die angegebene Anzahl von Zeichen aus dem Ziel.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT ReadNullTerminatedString(  
   UINT64 address,  
   UINT16 characterSize,  
   UINT32 maxCharacters,  
   BSTR *pString  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `address`  
 [in] Die Adresse, von der gelesen werden muss.  
  
 `characterSize`  
 [in] Größe jedes Zeichens in der Zeichenfolge  
  
 `maxCharacters`  
 [in] Die maximale Anzahl der zu lesenden Zeichen. MaxCharacters sollte angemessen sein. Jede Anforderung von mehr als 128 MB Arbeitsspeicher schlägt fehl.  Wenn die Zeichenfolge größer als maxCharacters ist, wird die Ergebniszeichenfolge nach maxCharacters abgeschnitten.  
  
 `pString`  
 [out] Das BSTR-Lesen vom Ziel.  
  
## <a name="return-value"></a>Rückgabewert  
  
## <a name="remarks"></a>Hinweise  
 Gibt S_FALSE zurück, wenn es abgeschnitten wird.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** "jscript9diag.h"  
  
## <a name="see-also"></a>Siehe auch  
 [IJsDebugDataTarget-Schnittstelle](../../winscript/reference/ijsdebugdatatarget-interface.md)