---
title: IDebugComPlusSymbolProvider::GetAssemblyName | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugComPlusSymbolProvider::GetAssemblyName
- GetAssemblyName
ms.assetid: a08cd609-b9b9-47bd-bf73-cbf851285907
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 60ea9a6f498a776bc8db0b7ee0fe12aa3c23e19f
ms.sourcegitcommit: 7153e2fc717d32e0e9c8a9b8c406dc4053c9fd53
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2019
ms.locfileid: "56412928"
---
# <a name="idebugcomplussymbolprovidergetassemblyname"></a>IDebugComPlusSymbolProvider::GetAssemblyName
Ruft den Namen der Assembly bei Angabe der Modul- und Domäne ab.

## <a name="syntax"></a>Syntax

```
[C++]
HRESULT GetAssemblyName(
    ULONG32 ulAppDomainID,
    GUID    guidModule,
    BSTR*   pbstrName
);
```

```
[C#]
int GetAssemblyName(
    uint   ulAppDomainID,
    Guid   guidModule,
    string pbstrName
);
```

#### <a name="parameters"></a>Parameter
`ulAppDomainID`  
[in] Der Bezeichner für die Anwendungsdomäne.

`guidModule`  
[in] Eindeutiger Bezeichner für das Modul.

`pbstrName`  
[out] Gibt den Namen der Assembly.

## <a name="return-value"></a>Rückgabewert
Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt, wie Sie die Implementierung dieser Methode für eine **CDebugSymbolProvider** -Objekt, das macht die [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) Schnittstelle.

```cpp
HRESULT CDebugSymbolProvider::GetAssemblyName(
    ULONG32 ulAppDomainID,
    GUID guidModule,
    BSTR* pbstrName
)
{
    HRESULT hr = S_OK;
    Module_ID idModule(ulAppDomainID, guidModule);
    CComPtr<IMetaDataImport> pMetadata;

    METHOD_ENTRY( CDebugSymbolProvider::GetMetadataForModule );

    IfFalseGo( pbstrName, E_INVALIDARG );
    *pbstrName = NULL;

    IfFailGo( GetMetadata( idModule, &pMetadata ) );
    IfFailGo( GetAssemblyName( pMetadata, 0, pbstrName ) );

Error:

    METHOD_EXIT( CDebugSymbolProvider::GetMetadataForModule, hr );
    return hr;
}
```

## <a name="see-also"></a>Siehe auch
[IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
