---
title: 'Ijsdebugprocess:: Createstackwalker-Methode | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugProcess.CreateStackWalker
apilocation:
- jscript9diag.dll
ms.assetid: 9d02e21d-7900-4942-8d17-cd04a2261463
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8f9c39163eae1f3a9bad15697bbc5621661bc781
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088282"
---
# <a name="ijsdebugprocesscreatestackwalker-method"></a>IJsDebugProcess::CreateStackWalker-Methode
Factorymethode für Stapeldurchlauf.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT CreateStackWalker(  
   DWORD threadId,  
   IJsDebugStackWalker **ppStackWalker  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `threadId`  
 [in] Die Thread-ID.  
  
 `ppStackWalker`  
 [out] Das neue Stapeldurchlaufobjekt.  
  
## <a name="return-value"></a>Rückgabewert  
  
## <a name="remarks"></a>Hinweise  
 Gibt E_JsDEBUG_UNKNOWN_THREAD zurück, wenn im Thread nicht JavaScript vorhanden ist. Diese Methode darf nur aufgerufen werden, während der Zielprozess angehalten wird.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** "jscript9diag.h"  
  
## <a name="see-also"></a>Siehe auch  
 [IJsDebugProcess-Schnittstelle](../../winscript/reference/ijsdebugprocess-interface.md)