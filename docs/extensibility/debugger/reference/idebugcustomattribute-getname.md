---
title: IDebugCustomAttribute::GetName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetName
helpviewer_keywords:
- IDebugCustomAttribute::GetName
ms.assetid: ba509cc5-5816-4925-a094-4c72d88c360c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 15d435d043d0e3863358628fa12016431a417918
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732772"
---
# <a name="idebugcustomattributegetname"></a>IDebugCustomAttribute::GetName
Ruft den Namen des benutzerdefinierten Attributs ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetName( 
   BSTR* bstrName
);
```

```csharp
int GetName(
   out string bstrName
);
```

## <a name="parameters"></a>Parameter
`bstrName`\
[out] Gibt eine Zeichenfolge zurück, die den Namen des benutzerdefinierten Attributs enthält.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, kehrt S_OK zurück; Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Der von dieser Methode zurückgegebene Name entspricht dem Namen der Klasse, die zum Deklarieren des Attributs verwendet wird. Dies entspricht möglicherweise nicht genau dem Namen der benutzerdefinierten Attributklasse selbst, da das Suffix "Attribut" von einem benutzerdefinierten Attributnamen gelöscht werden kann, wenn es in einer Deklaration verwendet wird.

## <a name="see-also"></a>Weitere Informationen
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
