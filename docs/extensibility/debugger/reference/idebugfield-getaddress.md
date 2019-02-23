---
title: IDebugField::GetAddress | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetAddress
helpviewer_keywords:
- IDebugField::GetAddress method
ms.assetid: 6981bf03-66ef-4bf9-87ea-f6c9624486cb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 417e19eb9c7d014b6c1ca353147f6a8ac96f222e
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56678266"
---
# <a name="idebugfieldgetaddress"></a>IDebugField::GetAddress
Diese Methode ruft die debugadresse eines Felds ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetAddress( 
   IDebugAddress** ppAddress
);
```

```csharp
int GetAddress(
   out IDebugAddress ppAddress
);
```

#### <a name="parameters"></a>Parameter
 `ppAddress`

 [out] Gibt die Adresse als eine [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) Objekt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls einen Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)