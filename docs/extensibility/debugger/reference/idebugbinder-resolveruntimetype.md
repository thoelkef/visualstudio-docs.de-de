---
title: 'Idebugbinder:: resolveruntimetype | Microsoft-Dokumentation'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80735959"
---
# <a name="idebugbinderresolveruntimetype"></a>IDebugBinder::ResolveRuntimeType
Diese Methode bestimmt den Lauf Zeittyp eines Objekts.

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
in Das zu lösende [idebugobject-Objekt](../../../extensibility/debugger/reference/idebugobject.md) .

`ppResolved`\
vorgenommen Gibt den Typ des Objekts als [idebugfield](../../../extensibility/debugger/reference/idebugfield.md)zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Der Lauf Zeittyp eines Objekts ist zur Kompilierzeit nicht immer bekannt. Beispielsweise kann mithilfe von Polymorphie ein Argument an eine Funktion als Basisklasse, z. b. eine Schaltflächen Klasse, übermittelt werden. Das tatsächliche Argument kann eine abgeleitete Klasse sein, z. b. eine Optionsfeld Klasse.

## <a name="see-also"></a>Weitere Informationen
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
