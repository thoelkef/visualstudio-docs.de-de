---
title: IDebugSymbolProvider::GetClassTypeByName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetClassTypeByName
helpviewer_keywords:
- IDebugSymbolProvider::GetClassTypeByName method
ms.assetid: 2c748909-51dc-49b7-b193-19f96fca1138
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a1be0aaaf9e960b95deaa7c949993a950647ce89
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719425"
---
# <a name="idebugsymbolprovidergetclasstypebyname"></a>IDebugSymbolProvider::GetClassTypeByName
Diese Methode ruft den Klassenfeldtyp ab, der einen vollqualifizierten Klassennamen darstellt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetClassTypeByName( 
   LPCOLESTR          pszClassName,
   NAME_MATCH         nameMatch,
   IDebugClassField** ppField
);
```

```csharp
int GetClassTypeByName(
   string               pszClassName,
   NAME_MATCH           nameMatch,
   out IDebugClassField ppField
);
```

## <a name="parameters"></a>Parameter
`pszClassName`\
[in] Der Klassenname.

`nameMatch`\
[in] Wählt den Typ der Übereinstimmung aus, z. B. groß, wenn die Groß-/Kleinschreibung beachtet wird. Ein Wert [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) aus der NAME_MATCH-Enumeration.

`ppField`\
[out] Gibt den Klassentyp zurück, der von der [IDebugClassField-Schnittstelle](../../../extensibility/debugger/reference/idebugclassfield.md) dargestellt wird.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
