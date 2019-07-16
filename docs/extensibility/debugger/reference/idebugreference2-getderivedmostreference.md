---
title: IDebugReference2::GetDerivedMostReference | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::GetDerivedMostReference
helpviewer_keywords:
- IDebugReference2::GetDerivedMostReference
ms.assetid: 07253b74-7d39-48e0-8e85-ac8dfd919f6e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8775087b9ec212f7e7d7e1547d01a5f175c4dc22
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66329825"
---
# <a name="idebugreference2getderivedmostreference"></a>IDebugReference2::GetDerivedMostReference
Ruft den am stärksten abgeleitete-Verweis, der einen Verweis ab. Für zukünftige Verwendung reserviert.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetDerivedMostReference( 
   IDebugReference2** ppDerivedMost
);
```

```csharp
int GetDerivedMostReference( 
   out IDebugReference2 ppDerivedMost
);
```

## <a name="parameters"></a>Parameter
`ppDerivedMost`\
[out] Gibt eine [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) -Objekt, das die am stärksten abgeleitete Eigenschaft darstellt.

## <a name="return-value"></a>Rückgabewert
 Gibt immer `E_NOTIMPL` zurück.

## <a name="remarks"></a>Hinweise
 Z. B., wenn diese Eigenschaft auf ein Objekt beschreibt, die implementiert `ClassRoot` , aber dies ist tatsächlich eine Instanziierung von `ClassDerived` abgeleitete `ClassRoot`, gibt diese Methode eine [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) Objekt Ein Verweis auf die `ClassDerived` Objekt.

## <a name="see-also"></a>Siehe auch
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)