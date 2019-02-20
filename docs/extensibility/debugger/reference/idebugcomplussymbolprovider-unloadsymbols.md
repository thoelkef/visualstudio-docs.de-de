---
title: IDebugComPlusSymbolProvider::UnloadSymbols | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- UnloadSymbols
- IDebugComPlusSymbolProvider::UnloadSymbols
ms.assetid: 53e3ddc1-ab47-4097-8fef-b26e5504b37a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9374220e8cc9433d8420820d87e685175061a2b0
ms.sourcegitcommit: 7153e2fc717d32e0e9c8a9b8c406dc4053c9fd53
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2019
ms.locfileid: "56413071"
---
# <a name="idebugcomplussymbolproviderunloadsymbols"></a>IDebugComPlusSymbolProvider::UnloadSymbols
Entlädt die Debugsymbolen für das angegebene Modul aus dem Arbeitsspeicher.

## <a name="syntax"></a>Syntax

```cpp
HRESULT UnloadSymbols(
    ULONG32 ulAppDomainID,
    GUID    guidModule
);
```

```csharp
int UnloadSymbols(
    uint ulAppDomainID,
    Guid guidModule
);
```

#### <a name="parameters"></a>Parameter
`ulAppDomainID`  
[in] Der Bezeichner der Anwendungsdomäne.

`guidModule`  
[in] Eindeutiger Bezeichner des Moduls.

## <a name="return-value"></a>Rückgabewert
Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt, wie Sie die Implementierung dieser Methode für eine **CDebugSymbolProvider** -Objekt, das macht die [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) Schnittstelle.

```cpp
HRESULT CDebugSymbolProvider::UnloadSymbols(
    ULONG32 ulAppDomainID,
    GUID guidModule
)
{
    HRESULT hr = S_OK;
    CComPtr<CModule> pmodule;
    Module_ID idModule(ulAppDomainID, guidModule);

    METHOD_ENTRY( CDebugSymbolProvider::UnloadSymbols );

#if DEBUG

    DebugVerifyModules();
#endif

    IfFailGo( GetModule( idModule, &pmodule ) );

#if DEBUG

    DebugVerifyModules();
#endif

    RemoveModule( pmodule );
    pmodule->Cleanup();

Error:
#if DEBUG

    DebugVerifyModules();
#endif

    METHOD_EXIT( CDebugSymbolProvider::UnloadSymbols, hr );

    return hr;
}
```

## <a name="see-also"></a>Siehe auch
[IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
