---
title: IDebugModule2::GetInfo | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugModule2::GetInfo
helpviewer_keywords:
- GetInfo method
- IDebugModule2::GetInfo method
ms.assetid: de337e66-294f-4ac9-b21e-71fac7418e36
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c8b35cb0d77f2e078cf8a66ae095a939e361fd46
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55007866"
---
# <a name="idebugmodule2getinfo"></a>IDebugModule2::GetInfo
Ruft Informationen zu diesem Modul ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetInfo(   
   MODULE_INFO_FIELDS dwFields,  
   MODULE_INFO*       pInfo  
);  
```  
  
```cpp  
int GetInfo(   
   enum_MODULE_INFO_FIELDS dwFields,  
   MODULE_INFO[]           pInfo  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwFields`  
 [in] Eine Kombination von Flags aus der [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) Enumeration, die angeben, welche Felder der `pInfo` ausgefüllt werden müssen.  
  
 `pInfo`  
 [in, out] Ein [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) -Struktur, die mit einer Beschreibung des Moduls gefüllt wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Die [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) Struktur enthält den Namen des Moduls, das angezeigt wird der **Module** Fenster.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)