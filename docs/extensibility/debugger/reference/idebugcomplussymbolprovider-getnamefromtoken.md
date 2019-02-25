---
title: IDebugComPlusSymbolProvider::GetNameFromToken | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider::GetNameFromToken
- GetNameFromToken
ms.assetid: 6e8cf468-5fd1-4655-93ed-88828d6068b7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6122e134fda4b7704385609fec8fa7cd25665968
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56682530"
---
# <a name="idebugcomplussymbolprovidergetnamefromtoken"></a>IDebugComPlusSymbolProvider::GetNameFromToken
Gibt den Namen der angegebenen Token, die die Metadaten-Objekt zugeordnet.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetNameFromToken (
    IUnknown* pMetadataImport,
    DWORD     dwToken,
    BSTR*     pbstrName
);
```

```csharp
int GetNameFromToken (
    object     pMetadataImport,
    uint       dwToken,
    out string pbstrName
);
```

#### <a name="parameters"></a>Parameter
`pMetadataImport`

 [in] Objekt, das die Metadateninformationen enthält.

`dwToken`

 [in] Token benannt wird.

`pbstrName`

 [out] Der Name, der das Token entspricht.

## <a name="return-value"></a>Rückgabewert
Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt, wie Sie die Implementierung dieser Methode für eine **CDebugSymbolProvider** -Objekt, das macht die [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) Schnittstelle.

```cpp
HRESULT CDebugSymbolProvider::GetNameFromToken(
    IUnknown* pMetadataImport,
    DWORD dwToken,
    BSTR* pbstrName
)
{
    HRESULT hr = S_OK;
    CComPtr<IMetaDataImport> pMetaData;

    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));
    ASSERT(IsValidInterfacePtr(pMetadataImport, IUnknown));

    METHOD_ENTRY(CDebugSymbolProvider::GetNameFromToken);

    IfFalseGo( pMetadataImport && pbstrName, E_INVALIDARG );

    *pbstrName = NULL;
    IfFailGo( pMetadataImport->QueryInterface( IID_IMetaDataImport,
              (void**) &pMetaData ) );

    switch ( TypeFromToken(dwToken) )
    {
        case mdtModule:
            IfFailGo( GetModuleName( pMetaData, dwToken, pbstrName) );
            break;

        case mdtTypeDef:
            IfFailGo( GetTypeName( pMetaData, dwToken, pbstrName) );
            break;

        case mdtFieldDef:
            IfFailGo( GetFieldName( pMetaData, dwToken, pbstrName) );
            break;

        case mdtMethodDef:
            IfFailGo( GetMethodName( pMetaData, dwToken, pbstrName) );
            break;

        case mdtEvent:
            IfFailGo( GetEventName( pMetaData, dwToken, pbstrName) );
            break;

        case mdtProperty:
            IfFailGo( GetPropertyName( pMetaData, dwToken, pbstrName) );
            break;

        case mdtAssembly:
            IfFailGo( GetAssemblyName( pMetaData, dwToken, pbstrName) );
            break;

        default:
            ASSERT(!"Unsupported token passed to GetNameFromToken");
            hr = E_FAIL;
            break;
    }

Error:

    METHOD_EXIT(CDebugSymbolProvider::GetNameFromToken, hr);
    return hr;
}
```

## <a name="see-also"></a>Siehe auch
- [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
