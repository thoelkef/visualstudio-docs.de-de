---
title: IDebugProperty2::GetDerivedMostProperty | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetDerivedMostProperty
helpviewer_keywords:
- IDebugProperty2::GetDerivedMostProperty
ms.assetid: cc86b461-62d1-4340-8209-c65037fd8b02
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2086aded4361049d722ec36ba1d470ed8f7ac6e5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721502"
---
# <a name="idebugproperty2getderivedmostproperty"></a>IDebugProperty2::GetDerivedMostProperty
Ruft die am weitesten abgeleitete Eigenschaft einer Eigenschaft ab.

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
[out] Gibt ein [IDebugProperty2-Objekt](../../../extensibility/debugger/reference/idebugproperty2.md) zurück, das die am weitesten abgeleitete Eigenschaft darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, `S_OK`kehrt zurück; Andernfalls wird Fehlercode zurückgegeben. Gibt `S_GETDERIVEDMOST_NO_DERIVED_MOST` zurück, wenn keine abgeleitete Eigenschaft zum Abrufen vorhanden ist.

## <a name="remarks"></a>Bemerkungen
 Wenn diese Eigenschaft beispielsweise ein Objekt `ClassRoot` beschreibt, das implementiert, aber `ClassDerived` tatsächlich eine `ClassRoot`Instanziierung davon ist, die von `ClassDerived` abgeleitet wird, gibt diese Methode ein [IDebugProperty2-Objekt](../../../extensibility/debugger/reference/idebugproperty2.md) zurück, das das Objekt beschreibt.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
