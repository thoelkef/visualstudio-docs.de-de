---
title: IDebugSymbolProvider::GetMethodFieldsByName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetMethodFieldsByName
helpviewer_keywords:
- IDebugSymbolProvider::GetMethodFieldsByName method
ms.assetid: 1f781320-81ef-4037-b068-f1864b271258
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cf123c1e7e83264a2ae4a8ef8c2b4b3207a62a5d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719223"
---
# <a name="idebugsymbolprovidergetmethodfieldsbyname"></a>IDebugSymbolProvider::GetMethodFieldsByName
Diese Methode ruft das Feld ab, das einen vollqualifizierten Methodennamen darstellt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetMethodFieldsByName( 
   LPCOLESTR          pszFullName,
   NAME_MATCH         nameMatch,
   IEnumDebugFields** ppEnum
);
```

```csharp
int GetMethodFieldsByName(
   string               pszFullName,
   NAME_MATCH           nameMatch,
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Parameter
`pszFullName`\
[in] Der Methodenname.

`nameMatch`\
[in] Wählt den Typ der Übereinstimmung aus, z. B. groß, wenn die Groß-/Kleinschreibung beachtet wird.

`ppEnum`\
[out] Gibt einen [IEnumDebugFields-Enumerator](../../../extensibility/debugger/reference/ienumdebugfields.md) für die Felder zurück, die dieser Methode zugeordnet sind.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Eine Methode kann z. B. mehreren Feldern zugeordnet werden, wenn sie überlastet ist.

## <a name="see-also"></a>Weitere Informationen
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
