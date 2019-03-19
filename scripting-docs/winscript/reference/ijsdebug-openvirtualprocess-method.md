---
title: 'Ijsdebug:: OpenVirtualProcess-Methode | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 97a055bf1550d74dc6b86d93ffdb9ca406afb43d
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58151946"
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