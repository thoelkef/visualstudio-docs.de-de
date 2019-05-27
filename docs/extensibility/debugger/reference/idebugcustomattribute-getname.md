---
title: IDebugCustomAttribute::GetName | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetName
helpviewer_keywords:
- IDebugCustomAttribute::GetName
ms.assetid: ba509cc5-5816-4925-a094-4c72d88c360c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2556a424e5109e75b667e9f32ecac5cc26ca781b
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2019
ms.locfileid: "66205335"
---
# <a name="idebugcustomattributegetname"></a>IDebugCustomAttribute::GetName
Ruft den Namen des benutzerdefinierten Attributs.

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
[out] Gibt eine Zeichenfolge, die mit dem Namen des benutzerdefinierten Attributs.

## <a name="return-value"></a>Rückgabewert
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Die von dieser Methode zurückgegebene benannte entspricht dem Namen der Klasse verwendet, um das Attribut zu deklarieren. Dies möglicherweise nicht genau auf den Namen der benutzerdefinierten Attributklasse selbst entsprechen, wie in c# können das Suffix "Attribute" aus einem benutzerdefinierten Attributnamen gelöscht werden soll, wenn er in einer Deklaration verwendet wird.

## <a name="see-also"></a>Siehe auch
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)