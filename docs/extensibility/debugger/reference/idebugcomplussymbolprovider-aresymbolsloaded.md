---
title: IDebugComPlusSymbolProvider::AreSymbolsLoaded | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- AreSymbolsLoaded
- IDebugComPlusSymbolProvider::AreSymbolsLoaded
ms.assetid: bbf8707d-f89c-4177-b019-d519f1ec6f4a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 44dceaa8b5cffd3bd81b7e8527368c38a6faaf18
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734158"
---
# <a name="idebugcomplussymbolprovideraresymbolsloaded"></a>IDebugComPlusSymbolProvider::AreSymbolsLoaded
Bestimmt, ob die Debugsymbole für das angegebene Modul geladen werden, das den Anwendungsdomänenbezeichner erhält.

## <a name="syntax"></a>Syntax

```cpp
HRESULT AreSymbolsLoaded (
    ULONG32 ulAppDomainID,
    GUID    guidModule
);
```

```csharp
int AreSymbolsLoaded (
    uint ulAppDomainID,
    Guid guidModule
);
```

## <a name="parameters"></a>Parameter
`ulAppDomainID`\
[in] Bezeichner für die Anwendungsdomäne.

`guidModule`\
[in] Eindeutiger Bezeichner für das Modul.

## <a name="return-value"></a>Rückgabewert
Wenn die Debugsymbole geladen `S_OK`werden, gibt zurück ; Andernfalls kehrt `S_FALSE`zurück .

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt, wie diese Methode für ein **CDebugSymbolProvider-Objekt** implementiert wird, das die [IDebugComPlusSymbolProvider-Schnittstelle](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) verfügbar macht.

```cpp
HRESULT CDebugSymbolProvider::AreSymbolsLoaded(
    ULONG32 ulAppDomainID,
    GUID guidModule
)
{
    HRESULT hr = S_OK;
    CComPtr<CModule> pModule;
    Module_ID idModule(ulAppDomainID, guidModule);

    METHOD_ENTRY( CDebugSymbolProvider::AreSymbolsLoaded );

    IfFalseGo( GetModule( idModule, &pModule ) == S_OK, S_FALSE );
Error:

    METHOD_EXIT( CDebugSymbolProvider::AreSymbolsLoaded, hr );
    return hr;
}
```

## <a name="see-also"></a>Weitere Informationen
- [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
