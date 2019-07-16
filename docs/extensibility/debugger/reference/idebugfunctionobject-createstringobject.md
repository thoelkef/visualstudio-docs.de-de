---
title: IDebugFunctionObject::CreateStringObject | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateStringObject
helpviewer_keywords:
- IDebugFunctionObject::CreateStringObject method
ms.assetid: fd6070ab-07d4-4ea1-8d71-b16592d6f1a7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 620aef7474f7f669e22fcb44c7df2611dc50bafb
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66313612"
---
# <a name="idebugfunctionobjectcreatestringobject"></a>IDebugFunctionObject::CreateStringObject
Erstellt ein String-Objekt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT CreateStringObject( 
   LPCOLESTR      pcstrString,
   IDebugObject** ppObject
);
```

```csharp
int CreateStringObject(
   string      pcstrString,
   out IDebugObject ppOjbect
);
```

## <a name="parameters"></a>Parameter
`pcstrString`\
[in] Der Zeichenfolgenwert für den String-Objekt.

`ppObject`\
[out] Gibt eine [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) -Objekt, das neu erstellte String-Objekt darstellt.

## <a name="return-value"></a>Rückgabewert
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Rufen Sie diese Methode zum Erstellen eines Objekts, das eine Zeichenfolge, die einen Parameter an die Funktion der darstellt durch dargestellt wird, wird die [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) Schnittstelle.

## <a name="see-also"></a>Siehe auch
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)