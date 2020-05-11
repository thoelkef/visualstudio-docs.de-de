---
title: IDebugComPlusSymbolProvider2::IsAddressSequencePoint | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider2::IsAddressSequencePoint
- IsAddressSequencePoint
ms.assetid: 89b27c57-5295-428b-8229-a402500d8cd3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5b9f1f3df8b96e9f9b25bf630206ce37bcd27635
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733405"
---
# <a name="idebugcomplussymbolprovider2isaddresssequencepoint"></a>IDebugComPlusSymbolProvider2::IsAddressSequencePoint
Bestimmt, ob die angegebene Debugadresse ein Sequenzpunkt ist.

## <a name="syntax"></a>Syntax

```cpp
HRESULT IsAddressSequencePoint(
    IDebugAddress* pAddress
);
```

```csharp
int IsAddressSequencePoint(
    IDebugAddress pAddress
);
```

## <a name="parameters"></a>Parameter
`pAddress`\
[in] Debugadresse, die durch die [IDebugAddress-Schnittstelle](../../../extensibility/debugger/reference/idebugaddress.md) dargestellt wird.

## <a name="return-value"></a>Rückgabewert
Wenn es sich bei der `S_OK`Debugadresse um einen Sequenzpunkt handelt, wird zurückgegeben; Andernfalls kehrt `S_FALSE`zurück .

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt, wie diese Methode für ein **CDebugSymbolProvider-Objekt** implementiert wird, das die [IDebugComPlusSymbolProvider2-Schnittstelle](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md) verfügbar macht.

```cpp
HRESULT CDebugSymbolProvider::IsAddressSequencePoint(
    IDebugAddress* pAddress
)
{
    HRESULT hr = S_OK;
    CDEBUG_ADDRESS address;
    CComPtr<CModule> pModule;

    METHOD_ENTRY( CDebugSymbolProvider::LoadSymbol );

    IfFalseGo( pAddress, E_INVALIDARG );

    IfFailGo( pAddress->GetAddress( &address ) );

    ASSERT(address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD);
    IfFalseGo( address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD, S_FALSE );

    IfFailGo( GetModule( address.GetModule(), &pModule) );

    if (!pModule->IsSequencePoint( address.addr.addr.addrMethod.tokMethod,
                                   address.addr.addr.addrMethod.dwVersion,
                                   address.addr.addr.addrMethod.dwOffset ))
    {

        // S_FALSE indicates this is not a sequence point

        hr = S_FALSE;
    }

Error:

    METHOD_EXIT( CDebugSymbolProvider::LoadSymbol, hr );

    return hr;
}
```

## <a name="see-also"></a>Weitere Informationen
- [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)
