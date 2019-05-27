---
title: IDebugModOpt::GetModOpts | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugModOpt::GetModOpts
- GetModOpts
ms.assetid: cb513fa9-d521-4a65-b968-f55f53a368df
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1c27c8a2a0e755fda5afa806657e918c7e7c0109
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2019
ms.locfileid: "66203128"
---
# <a name="idebugmodoptgetmodopts"></a>IDebugModOpt::GetModOpts
Ruft eine Liste optionaler Modifizierer.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetModOpts(
   ULONG  celt,
   BSTR*  rgelt,
   ULONG* pceltFetched
);
```

```csharp
int GetModOpts(
   uint         celt,
   out string[] rgelt,
   ref uint     pceltFetched
);
```

## <a name="parameters"></a>Parameter
`celt`\
[in] Anzahl der Elemente zurückgegeben werden.

`rgelt`\
[out] Gibt ein Array, das die Optionen enthält.

`pceltFetched`\
[in, out] Anzahl der Elemente, die zurückgegeben werden, der `rgelt` Array.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)