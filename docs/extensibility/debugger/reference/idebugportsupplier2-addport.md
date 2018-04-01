---
title: IDebugPortSupplier2::AddPort | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugPortSupplier2::AddPort
helpviewer_keywords:
- IDebugPortSupplier2::AddPort
ms.assetid: df491161-6bf3-4fcc-b478-b9ec88ec995f
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 6f77b0dd072c0e1acdbe642a0ded64a554f809f1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugportsupplier2addport"></a>IDebugPortSupplier2::AddPort
Fügt einen Port an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT AddPort(   
   IDebugPortRequest2* pRequest,  
   IDebugPort2**       ppPort  
);  
```  
  
```csharp  
int AddPort(   
   IDebugPortRequest2 pRequest,  
   out IDebugPort2    ppPort  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRequest`  
 [in] Ein [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) -Objekt, das beschreibt, den Port hinzugefügt werden.  
  
 `ppPort`  
 [out] Gibt eine [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) Objekt, das den Port darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode erstellt tatsächlich den angeforderten Port sowie die Port-Lieferanten interne Liste der aktiven Ports hinzugefügt. Die [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) Methode kann zuerst aufgerufen werden, um mögliche zeitaufwändig Verzögerungen zu vermeiden.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)