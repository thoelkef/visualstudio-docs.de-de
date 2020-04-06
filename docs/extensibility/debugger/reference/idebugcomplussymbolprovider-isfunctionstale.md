---
title: IDebugComPlusSymbolProvider::IsFunctionStale | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider::IsFunctionStale
ms.assetid: dcffc090-4ed8-47b2-ba51-bce1a6b6428d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4e5b42e8bb89a84b5274669173c93db3e287755a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733693"
---
# <a name="idebugcomplussymbolproviderisfunctionstale"></a>IDebugComPlusSymbolProvider::IsFunctionStale
Bestimmt, ob die Funktion an der angegebenen Debugadresse als veraltet betrachtet wird.

## <a name="syntax"></a>Syntax

```cpp
HRESULT IsFunctionStale(
    IDebugAddress* pAddress
);
```

```csharp
int IsFunctionStale(
    IDebugAddress pAddress
);
```

## <a name="parameters"></a>Parameter
`pAddress`\
[in] Die Debugadresse, die durch eine [IDebugAddress-Schnittstelle](../../../extensibility/debugger/reference/idebugaddress.md) dargestellt wird. Diese Adresse muss eine METHOD_ADDRESS sein.

## <a name="return-value"></a>Rückgabewert
Wenn die Funktion als veraltet `S_OK`betrachtet wird, wird zurückgegeben. Wenn die Funktion nicht veraltet `S_FALSE`ist, wird zurückgegeben.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt, wie diese Methode für ein **CDebugSymbolProvider-Objekt** implementiert wird, das die [IDebugComPlusSymbolProvider-Schnittstelle](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) verfügbar macht.

```cpp
HRESULT CDebugSymbolProvider::IsFunctionStale(
    IDebugAddress* pAddress
)
{
    HRESULT hr = S_OK;
    CDEBUG_ADDRESS address;
    CComPtr<CModule> pModule;

    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));
    ASSERT(IsValidInterfacePtr(pAddress, IDebugAddress));

    METHOD_ENTRY( CDebugSymbolProvider::IsFunctionStale );

    IfFalseGo( pAddress, S_FALSE );
    IfFailGo( pAddress->GetAddress( &address ) );

    ASSERT(address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD);
    IfFalseGo( address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD, S_FALSE );

    IfFailGo( GetModule( address.GetModule(), &pModule) );

    if (!pModule->IsFunctionStale( address.addr.addr.addrMethod.tokMethod,
                                   address.addr.addr.addrMethod.dwVersion ))
    {

        // S_FALSE indicates the function is not stale

        hr = S_FALSE;
    }

Error:

    METHOD_EXIT( CDebugSymbolProvider::IsFunctionStale, hr );

    if (!SUCCEEDED(hr))
    {
        hr = S_FALSE;
    }

    return hr;
}
```

## <a name="see-also"></a>Weitere Informationen
- [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
