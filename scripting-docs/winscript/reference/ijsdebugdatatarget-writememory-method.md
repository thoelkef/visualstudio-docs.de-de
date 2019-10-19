---
title: 'Ijsdebugdatatarget:: Write Memory-Methode | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.WriteMemory
apilocation:
- jscript9diag.dll
ms.assetid: 0d3c04c3-9ef8-4842-a145-3d29bca75062
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 33cd23ad784e222f770dfd5c0e7c2d775aa55e42
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572413"
---
# <a name="ijsdebugdatatargetwritememory-method"></a>IJsDebugDataTarget::WriteMemory-Methode
Liest den Arbeitsspeicher des Zielprozesses.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT WriteMemory(  
   UINT64 address,  
   const BYTE *pMemory,  
   DWORD size  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `address`  
 [in] Die Basisadresse, aus der in den Arbeitsspeicher des Zielprozesses zu schreiben ist.  
  
 `pMemory`  
 [in] Die Daten, die in den Adressraum des angegebenen Prozesses zu schreiben sind.  
  
 `size`  
 [in] Die Anzahl der Bytes, die in den Prozess geschrieben werden sollen.  
  
## <a name="return-value"></a>Rückgabewert  
  
## <a name="remarks"></a>Hinweise  
 Bevor die Datenübertragung erfolgt, überprüft das System, dass alle Daten in der Basisadresse und der Arbeitsspeicher in der angegebenen Größe für Schreibzugriff verfügbar ist. Wenn darauf nicht zugegriffen werden kann, löst die Funktion einen E_JsDEBUG_INVALID_MEMORY_ADDRESS-Fehler aus.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** "jscript9diag. h  
  
## <a name="see-also"></a>Siehe auch  
 [IJsDebugDataTarget-Schnittstelle](../../winscript/reference/ijsdebugdatatarget-interface.md)