---
title: IDebugComPlusSymbolProvider::IsFunctionDeleted | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider::IsFunctionDeleted
ms.assetid: b276bd25-6658-4898-bc36-04ecdf92aa2f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 904eb54729298f29b98b5ae7dae0aa759a1119de
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68187213"
---
# <a name="idebugcomplussymbolproviderisfunctiondeleted"></a>IDebugComPlusSymbolProvider::IsFunctionDeleted
Ermittelt, dass die Funktion an der angegebenen Debug-Adresse gelöscht wird.

## <a name="syntax"></a>Syntax

```cpp
HRESULT IsFunctionDeleted(
    IDebugAddress* pAddress
);
```

```csharp
int IsFunctionDeleted(
    IDebugAddress pAddress
);
```

#### <a name="parameters"></a>Parameter
`pAddress`

 [in] Die debugadresse dargestellt werden, indem ein [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) Schnittstelle. Diese Adresse muss es sich um eine METHOD_ADDRESS sein.

## <a name="return-value"></a>Rückgabewert
Gibt zurück, wenn die Funktion gelöscht wird, `S_OK`. Wenn die Funktion vorhanden ist, gibt `S_FALSE`.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt, wie Sie die Implementierung dieser Methode für eine **CDebugSymbolProvider** -Objekt, das macht die [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) Schnittstelle.

```cpp
HRESULT CDebugSymbolProvider::IsFunctionDeleted(
    IDebugAddress* pAddress
)
{
    HRESULT hr = S_OK;
    CDEBUG_ADDRESS address;
    CComPtr<CModule> pModule;

    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));
    ASSERT(IsValidInterfacePtr(pAddress, IDebugAddress));

    METHOD_ENTRY( CDebugSymbolProvider::IsFunctionDeleted );

    IfFalseGo( pAddress, S_FALSE );
    IfFailGo( pAddress->GetAddress( &address ) );

    ASSERT(address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD);
    IfFalseGo( address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD, S_FALSE );

    IfFailGo( GetModule( address.GetModule(), &pModule) );

    if (!pModule->IsFunctionDeleted( address.addr.addr.addrMethod.tokMethod,
                                     address.addr.addr.addrMethod.dwVersion,
                                     address.addr.addr.addrMethod.dwOffset ))
    {

        // S_FALSE indicates the function is not deleted

        hr = S_FALSE;
    }

Error:

    METHOD_EXIT( CDebugSymbolProvider::IsFunctionDeleted, hr );

    if (!SUCCEEDED(hr))
    {
        hr = S_FALSE;
    }

    return hr;
}
```

## <a name="see-also"></a>Siehe auch
- [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
