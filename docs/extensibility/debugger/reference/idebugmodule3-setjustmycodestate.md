---
title: IDebugModule3::SetJustMyCodeState | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugModule3::SetJustMyCodeState
helpviewer_keywords:
- IDebugModule3::SetJustMyCodeState
ms.assetid: 68f8166d-ef64-49ae-ad5e-79604f43bbd4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: faa3348f7916e7d56cbdd4c279a09dcc2b5ccdab
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55008178"
---
# <a name="idebugmodule3setjustmycodestate"></a>IDebugModule3::SetJustMyCodeState
Markiert das Modul als Benutzercode oder nicht.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT SetJustMyCodeState(  
   BOOL fIsUserCode  
);  
```  
  
```csharp  
int SetJustMyCodeState(  
   int fIsUserCode  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `fIsUserCode`  
 [in] Ungleich Null (`TRUE`), wenn das Modul als Benutzercode angesehen werden sollte, NULL (`FALSE`) Wenn nicht.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt den Fehlercode zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)