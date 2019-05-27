---
title: IDebugFunctionObject2::CreateStringObjectWithLength | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- CreateStringObjectWithLength
- IDebugFunctionObject2::CreateStringObjectWithLength
ms.assetid: 1f43ec66-1615-4a4c-8b9d-e933f549f96d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cae1d7cbcad9af39da75d3f006274137dc886fc2
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2019
ms.locfileid: "66200699"
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