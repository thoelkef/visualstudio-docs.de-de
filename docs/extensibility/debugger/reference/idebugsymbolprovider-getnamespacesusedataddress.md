---
title: IDebugSymbolProvider::GetNamespacesUsedAtAddress | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugSymbolProvider::GetNamespacesUsedAtAddress
helpviewer_keywords:
- IDebugSymbolProvider::GetNamespacesUsedAtAddress method
ms.assetid: 392de54b-9af0-4567-953b-1b41acd1e05c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 13e7aef1465ffe6e37a82fc3c685fef28bbf61e8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54978307"
---
# <a name="idebugsymbolprovidergetnamespacesusedataddress"></a>IDebugSymbolProvider::GetNamespacesUsedAtAddress
Diese Methode erstellt einen Enumerator für Namespaces, die mit der debugadresse verknüpft.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetNamespacesUsedAtAddress(   
   IDebugAddress*     pAddress,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int GetNamespacesUsedAtAddress(  
   IDebugAddress        pAddress,  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pAddress`  
 [in] Die debugadresse.  
  
 `ppEnum`  
 [out] Gibt eine [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) Enumerator für die Namespaces.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Es gibt möglicherweise mehrere Namespaces, die mit einer angegebenen Adresse z. B. verknüpfte geschachtelte Namespaces oder mehrere `using` Anweisungen.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)