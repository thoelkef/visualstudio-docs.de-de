---
title: IDebugAddress::GetAddress | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress::GetAddress
helpviewer_keywords:
- IDebugAddress:GetAddress method
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f787f041c6c39b8120a768f9288efe86649bb227
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66317993"
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

## <a name="parameters"></a>Parameter
`pAddress`\
[in, out] Ein [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) -Struktur, die von dieser Methode angegeben ist.

## <a name="return-value"></a>Rückgabewert
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Die [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) Struktur an diese Methode, die es sich die entsprechenden Informationen dann füllt übergeben wird. Wie diese Informationen interpretiert werden, hängt von der Art von Informationen zurückgegeben, und der Symbol-Handler selbst ab. Finden Sie unter [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) Weitere Details.

## <a name="see-also"></a>Siehe auch
- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)