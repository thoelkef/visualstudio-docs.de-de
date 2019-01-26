---
title: IDebugEngine2::SetRegistryRoot | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugEngine2::SetRegistryRoot
helpviewer_keywords:
- IDebugEngine2::SetRegistryRoot
ms.assetid: d0d81202-8a4a-4bc3-b297-30a047c5ec60
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 91685a1cbc465612623370dac1699021e57eaa63
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54938632"
---
# <a name="idebugengine2setregistryroot"></a>IDebugEngine2::SetRegistryRoot
Legt den Registrierungsstamm für die Debug-Engine (DE) fest.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT SetRegistryRoot(   
   LPCOLESTR pszRegistryRoot  
);  
```  
  
```csharp  
int SetRegistryRoot(   
   string pszRegistryRoot  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pszRegistryRoot`  
 [in] Der Registrierungsstamm verwenden.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Mit dieser Methode können [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] an einen alternativen Registrierungsstamm, die die DE, zum Abrufen von registrierungseinstellungen verwenden soll; z. B. "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp".  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)