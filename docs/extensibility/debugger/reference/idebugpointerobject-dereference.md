---
title: IDebugPointerObject::Dereference | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPointerObject::Dereference
helpviewer_keywords:
- IDebugPointerObject::Dereference method
ms.assetid: 196ec2cc-8569-4780-b217-23b24e7f50ca
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e74273d25e121ec769207d429a622eed19654a92
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54922885"
---
# <a name="idebugpointerobjectdereference"></a>IDebugPointerObject::Dereference
Ruft das Objekt, das auf den verwiesen wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT DeReference(   
   DWORD          dwIndex,  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int Dereference(  
   uint             dwIndex,   
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwIndex`  
 [in] Ein einfaches Byteoffset vom Beginn des Objekts verweist.  
  
 `ppObject`  
 [out] Gibt eine [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) Objekt, das Objekt darstellt, auf den verwiesen wird, sowie Werte für offset, sofern vorhanden.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben. Gibt E_FAIL zurück, wenn dieses Objekt nicht in ein anderes Objekt verweist.  
  
## <a name="remarks"></a>Hinweise  
 Das Objekt, das auf den verwiesen wird, kann ein primitiver Typ oder ein komplexer Typ wie z. B. eine Klasse oder Struktur sein.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)