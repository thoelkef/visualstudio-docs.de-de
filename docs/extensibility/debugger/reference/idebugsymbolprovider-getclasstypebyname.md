---
title: IDebugSymbolProvider::GetClassTypeByName | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetClassTypeByName
helpviewer_keywords:
- IDebugSymbolProvider::GetClassTypeByName method
ms.assetid: 2c748909-51dc-49b7-b193-19f96fca1138
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9f701415c011b304ac886669de5da8f813b26220
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56699599"
---
# <a name="idebugsymbolprovidergetclasstypebyname"></a>IDebugSymbolProvider::GetClassTypeByName
Diese Methode ruft den Klassentyp-Feld, das einen vollqualifizierten Klassennamen darstellt.

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

#### <a name="parameters"></a>Parameter
 `pszClassName`

 [in] Name der Klasse.

 `nameMatch`

 [in] Wählt den Typ der Übereinstimmung, z. B. Groß-/Kleinschreibung beachtet. Ein Wert aus der [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) Enumeration.

 `ppField`

 [out] Gibt den Klassentyp zurück, dargestellt durch die [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) Schnittstelle.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)