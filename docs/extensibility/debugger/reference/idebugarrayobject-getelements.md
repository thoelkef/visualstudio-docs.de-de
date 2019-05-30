---
title: IDebugArrayObject::GetElements | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetElements
helpviewer_keywords:
- IDebugArrayObject::GetElements method
ms.assetid: f6a6262f-5183-46ce-8a45-33ef46088b98
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 915724fa5790c6b8c9fde2706b1222db239cb4ab
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351796"
---
# <a name="idebugarrayobjectgetelements"></a>IDebugArrayObject::GetElements
Ruft einen Enumerator aller Elemente des Arrays ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetElements( 
   IEnumDebugObjects** ppEnum
);
```

```csharp
int GetElements(
   out IEnumDebugObjects ppEnum
);
```

## <a name="parameters"></a>Parameter
`ppEnum`\
[out] Gibt eine [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md) Objekt, das ermöglicht, über alle Elemente auflisten.

## <a name="return-value"></a>Rückgabewert
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Verwenden Sie alternativ die [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) und [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) Methoden zum Durchlaufen der Elemente.

## <a name="see-also"></a>Siehe auch
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)