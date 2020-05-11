---
title: IDebugBinder::ResolveRuntimeType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::ResolveRuntimeType
helpviewer_keywords:
- IDebugBinder::ResolveRuntimeType method
ms.assetid: 6456ab3e-1c03-4f3c-91f9-16797ab7f5e7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4bdbff651618365f3b68a142a6cb1e76836876a3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735959"
---
# <a name="idebugbinderresolveruntimetype"></a>IDebugBinder::ResolveRuntimeType
Diese Methode bestimmt den Laufzeittyp eines Objekts.

## <a name="syntax"></a>Syntax

```cpp
HRESULT ResolveRuntimeType( 
   IDebugObject* pObject,
   IDebugField** ppResolved
);
```

```csharp
int ResolveRuntimeType(
   IDebugObject     pObject,
   out IDebugField  ppResolved
);
```

## <a name="parameters"></a>Parameter
`pObject`\
[in] Das zu [lösende IDebugObject.](../../../extensibility/debugger/reference/idebugobject.md)

`ppResolved`\
[out] Gibt den Typ des Objekts als [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Der Laufzeittyp eines Objekts ist zur Kompilierungszeit nicht immer bekannt. Beispielsweise kann mithilfe von Polymorphismus ein Argument an eine Funktion als Basisklasse übergeben werden, z. B. eine Schaltflächenklasse. Das eigentliche Argument kann eine abgeleitete Klasse sein, z. B. eine Optionsfeldklasse.

## <a name="see-also"></a>Weitere Informationen
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
