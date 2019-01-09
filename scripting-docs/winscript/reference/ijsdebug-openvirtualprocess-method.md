---
title: 'Ijsdebug:: OpenVirtualProcess-Methode | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJSDebug.OpenVirtualProcess
apilocation:
- jscript9diag.dll
ms.assetid: 5612bf1b-a4e3-4eaf-ac5e-c2e1f147c395
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: daa5414153ee55a431294afaf7b167ee91839bfc
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093989"
---
# <a name="ijsdebugopenvirtualprocess-method"></a>IJsDebug::OpenVirtualProcess-Methode
Factorymethode, die zum Erstellen eines neuen virtuellen Prozessobjekts verwendet wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT OpenVirtualProcess(  
   DWORD processId,  
   UINT64 runtimeJsBaseAddress,  
   IJsDebugDataTarget *pDataTarget,  
   IJsDebugProcess **ppProcess  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `processId`  
 [in] Prozess-ID, an die der Debugger anzufügen ist.  
  
 `runtimeJsBaseAddress`  
 [in] Die Basisadresse, an der die JavaScript-Laufzeit in den Zielprozess geladen wurde.  
  
 `pDataTarget`  
 [in] Debugger hat Schnittstelle angegeben, an der der Zustand des Prozesses abgefragt werden kann.  
  
 `ppProcess`  
 [out] Neues Debugprozessobjekt  
  
## <a name="return-value"></a>Rückgabewert  
  
## <a name="remarks"></a>Hinweise  
 Gibt "E_JsDEBUG_MISMATCHED_RUNTIME" zurück, wenn "Jscript9diag" und "Jscript9" nicht übereinstimmen.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** "jscript9diag.h"  
  
## <a name="see-also"></a>Siehe auch  
 [IJsDebug-Schnittstelle](../../winscript/reference/ijsdebug-interface.md)