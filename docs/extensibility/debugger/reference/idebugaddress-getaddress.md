---
title: IDebugAddress::GetAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress::GetAddress
helpviewer_keywords:
- IDebugAddress:GetAddress method
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 162a64c9118bdcde23208082350005e607a237b8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736602"
---
# <a name="idebugaddressgetaddress"></a>IDebugAddress::GetAddress
Gibt eine Struktur zurück, die ein Objekt und seine Position innerhalb seines Bereichs oder Containers beschreibt.

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

## <a name="parameters"></a>Parameter
`pAddress`\
[in, out] Eine [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) Struktur, die mit dieser Methode ausgefüllt wird.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, kehrt S_OK zurück; Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Die [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) Struktur wird an diese Methode übergeben, die sie dann mit den entsprechenden Informationen ausfüllt. Wie diese Informationen interpretiert werden, hängt von der Art der zurückgegebenen Informationen und dem Symbolhandler selbst ab. Weitere Informationen finden Sie [in DEBUG_ADDRESS.](../../../extensibility/debugger/reference/debug-address.md)

## <a name="see-also"></a>Weitere Informationen
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
