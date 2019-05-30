---
title: IDebugArrayObject::GetCount | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetCount
helpviewer_keywords:
- IDebugArrayObject::GetCount method
ms.assetid: 7931f3f7-033c-4bf8-8abd-95183952ebb0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ac21ac30e1f4511efa1ec8a7fe27129bf2ddb3a1
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66321663"
---
# <a name="idebugarrayobjectgetcount"></a>IDebugArrayObject::GetCount
Ruft die Anzahl der Elemente im Array ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetCount( 
   DWORD* pdwElements
);
```

```csharp
int GetCount(
   out uint pdwElements
);
```

## <a name="parameters"></a>Parameter
`pdwElements`\
[out] Die Anzahl zurückgegeben.

## <a name="return-value"></a>Rückgabewert
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Diese Methode sieht alle Elemente eines Arrayobjekts als ein eindimensionales Array, selbst wenn das Arrayobjekt mehrdimensionale ist. Angenommen, das Array `myarray[3][2][6]`, 36, die in von dieser Methode zurückgegeben werden würde die `pdwElements` Parameter. Verwenden der [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) Methode, um die einzelnen Elemente einer einzeln ab.

## <a name="see-also"></a>Siehe auch
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)