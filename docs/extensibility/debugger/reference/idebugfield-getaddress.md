---
title: IDebugField::GetAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetAddress
helpviewer_keywords:
- IDebugField::GetAddress method
ms.assetid: 6981bf03-66ef-4bf9-87ea-f6c9624486cb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1be3d839cabe3fce07cdd42720306bdac47282f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729005"
---
# <a name="idebugfieldgetaddress"></a>IDebugField::GetAddress
Diese Methode ruft die Debugadresse eines Felds ab.

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

## <a name="parameters"></a>Parameter
`ppAddress`\
[out] Gibt die Adresse als [IDebugAddress-Objekt](../../../extensibility/debugger/reference/idebugaddress.md) zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, `S_OK`kehrt zurück; Andernfalls geben Sie einen Fehlercode zurück.

## <a name="see-also"></a>Weitere Informationen
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
