---
title: IDebugReference2::Vergleichen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::Compare
helpviewer_keywords:
- IDebugReference2::Compare
ms.assetid: 3361c495-2673-4b7c-82e3-dee74e1fa58d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0d293fcb89c92a19acc4f5a3910015914ef4231a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720639"
---
# <a name="idebugreference2compare"></a>IDebugReference2::Compare
Vergleicht einen Verweis mit einem anderen. Für die zukünftige Verwendung reserviert.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Compare ( 
   REFERENCE_COMPARE dwCompare,
   IDebugReference2* pReference
);
```

```csharp
int Compare ( 
   enum_REFERENCE_COMPARE dwCompare,
   IDebugReference2       pReference
);
```

## <a name="parameters"></a>Parameter
`dwCompare`\
[in] Ein Wert [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md) aus der REFERENCE_COMPARE-Enumeration, der den Vergleichsvorgang angibt, z. B. gleich, kleiner als oder größer als.

`pReference`\
[in] Ein [IDebugReference2-Objekt,](../../../extensibility/debugger/reference/idebugreference2.md) das den zu vergleichenden Verweis darstellt.

## <a name="return-value"></a>Rückgabewert
 Gibt immer `E_NOTIMPL` zurück.

## <a name="see-also"></a>Weitere Informationen
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md)
