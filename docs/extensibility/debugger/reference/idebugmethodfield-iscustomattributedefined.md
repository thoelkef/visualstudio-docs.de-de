---
title: IDebugMethodField::IsCustomAttributeDefined | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::IsCustomAttributeDefined
helpviewer_keywords:
- IDebugMethodField::IsCustomAttributeDefined method
ms.assetid: 1b5d95a8-cc87-4acb-9e6a-3928f3632b7c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f088a3e0fb3cd88d2b5d178ed61441d52c9efe16
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324123"
---
# <a name="idebugmethodfieldiscustomattributedefined"></a>IDebugMethodField::IsCustomAttributeDefined
Bestimmt, ob ein bestimmtes benutzerdefiniertes Attribut definiert wurde.

## <a name="syntax"></a>Syntax

```cpp
HRESULT IsCustomAttributeDefined( 
   LPCOLESTR pszCustomAttributeName
);
```

```csharp
int IsCustomAttributeDefined(
   [In] string pszCustomAttributeName
);
```

## <a name="parameters"></a>Parameter
`pszCustomAttributeName`\
[in] Eine Zeichenfolge, die mit dem Namen des zu suchenden benutzerdefinierten Attributs.

## <a name="return-value"></a>Rückgabewert
 Gibt zurück, S_OK Wenn das benutzerdefinierte Attribut für diese Methode definiert ist, andernfalls S_FALSE zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)