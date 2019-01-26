---
title: IDebugAddress::GetAddress | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugAddress::GetAddress
helpviewer_keywords:
- IDebugAddress:GetAddress method
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e91b90fd54ea70aed729707e927ad2394d756139
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54917678"
---
# <a name="idebugaddressgetaddress"></a>IDebugAddress::GetAddress
Gibt eine Struktur, die beschreibt ein Objekt und seinen Speicherort in seinem Bereich oder den Container zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetAddress (  
   DEBUG_ADDRESS * pAddress  
);  
```  
  
```csharp  
int GetAddress(  
   DEBUG_ADDRESS[] pAddress  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pAddress`  
 [in, out] Ein [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) -Struktur, die von dieser Methode angegeben ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Die [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) Struktur an diese Methode, die es sich die entsprechenden Informationen dann füllt übergeben wird. Wie diese Informationen interpretiert werden, hängt von der Art von Informationen zurückgegeben, und der Symbol-Handler selbst ab. Finden Sie unter [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) Weitere Details.  
  
## <a name="see-also"></a>Siehe auch  
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)