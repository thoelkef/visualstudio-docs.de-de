---
title: IDebugFunctionObject2::CreateStringObjectWithLength | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- CreateStringObjectWithLength
- IDebugFunctionObject2::CreateStringObjectWithLength
ms.assetid: 1f43ec66-1615-4a4c-8b9d-e933f549f96d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ce0fdafc6835fdccc87638e17d3bbd01a1415abb
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66313510"
---
# <a name="idebugfunctionobject2createstringobjectwithlength"></a>IDebugFunctionObject2::CreateStringObjectWithLength
Erstellt ein String-Objekt, das die angegebene Länge aufweist.

## <a name="syntax"></a>Syntax

```cpp
HRESULT CreateStringObjectWithLength (
   LPCOLESTR      pcstrString,
   UINT           uiLength,
   IDebugObject** ppObject
);
```

```csharp
int CreateStringObjectWithLength (
   string           pcstrString,
   uint             uiLength,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Parameter
`pcstrString`\
[in] Der Zeichenfolgenwert für den String-Objekt.

`uiLength`\
[in] Die Länge der Zeichenfolge in Bytes.

`ppObject`\
[out] Gibt eine [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) -Objekt, das neu erstellte String-Objekt darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)