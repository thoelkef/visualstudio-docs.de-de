---
title: IDebugReference2::GetDerivedMostReferenz | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::GetDerivedMostReference
helpviewer_keywords:
- IDebugReference2::GetDerivedMostReference
ms.assetid: 07253b74-7d39-48e0-8e85-ac8dfd919f6e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 15e98884d040cfb2ebf1b33a56c7edea331fbff0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720618"
---
# <a name="idebugreference2getderivedmostreference"></a>IDebugReference2::GetDerivedMostReference
Ruft den abgeleiteten Referenzpunkt eines Verweises ab. Für die zukünftige Verwendung reserviert.

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
[out] Gibt ein [IDebugReference2-Objekt](../../../extensibility/debugger/reference/idebugreference2.md) zurück, das die am weitesten abgeleitete Eigenschaft darstellt.

## <a name="return-value"></a>Rückgabewert
 Gibt immer `E_NOTIMPL` zurück.

## <a name="remarks"></a>Bemerkungen
 Wenn diese Eigenschaft beispielsweise ein Objekt `ClassRoot` beschreibt, das implementiert, aber `ClassDerived` tatsächlich eine `ClassRoot`Instanziierung davon ist, die von abgeleitet `ClassDerived` wird, gibt diese Methode ein [IDebugReference2-Objekt](../../../extensibility/debugger/reference/idebugreference2.md) zurück, das einen Verweis auf das Objekt darstellt.

## <a name="see-also"></a>Weitere Informationen
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
