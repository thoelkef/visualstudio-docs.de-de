---
title: IDebugProperty2::GetDerivedMostProperty | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetDerivedMostProperty
helpviewer_keywords:
- IDebugProperty2::GetDerivedMostProperty
ms.assetid: cc86b461-62d1-4340-8209-c65037fd8b02
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6b08ca2ad569935a117b8b1255bc740bf395c2ed
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66343161"
---
# <a name="idebugproperty2getderivedmostproperty"></a>IDebugProperty2::GetDerivedMostProperty
Ruft den am stärksten abgeleitete Eigenschaft einer Eigenschaft ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetDerivedMostProperty ( 
   IDebugProperty2** ppDerivedMost
);
```

```csharp
int GetDerivedMostProperty ( 
   out IDebugProperty2 ppDerivedMost
);
```

## <a name="parameters"></a>Parameter
`ppDerivedMost`\
[out] Gibt eine [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) -Objekt, das die am stärksten abgeleitete Eigenschaft darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`; gibt andernfalls den Fehlercode zurück. Gibt `S_GETDERIVEDMOST_NO_DERIVED_MOST` Wenn keine Eigenschaft "am stärksten abgeleitete ist" abgerufen.

## <a name="remarks"></a>Hinweise
 Z. B., wenn diese Eigenschaft auf ein Objekt beschreibt, die implementiert `ClassRoot` , aber dies ist tatsächlich eine Instanziierung von `ClassDerived` abgeleitete `ClassRoot`, gibt diese Methode eine [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) Objekt Beschreibt die `ClassDerived` Objekt.

## <a name="see-also"></a>Siehe auch
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)