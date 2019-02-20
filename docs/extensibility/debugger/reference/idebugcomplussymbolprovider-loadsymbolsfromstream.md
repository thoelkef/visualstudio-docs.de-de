---
title: IDebugComPlusSymbolProvider::LoadSymbolsFromStream | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugComPlusSymbolProvider::LoadSymbolsFromStream
- LoadSymbolsFromStream
ms.assetid: 1de272f0-24f4-4548-8b70-a205cddd4727
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 02e88780e41b9a46163c7b66b2d83e64d190c307
ms.sourcegitcommit: 7153e2fc717d32e0e9c8a9b8c406dc4053c9fd53
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2019
ms.locfileid: "56413383"
---
# <a name="idebugcomplussymbolproviderloadsymbolsfromstream"></a>IDebugComPlusSymbolProvider::LoadSymbolsFromStream
Lädt Debugsymbole ab, der den Datenstrom angegeben ist.

## <a name="syntax"></a>Syntax

```cpp
HRESULT LoadSymbolsFromStream(
    ULONG32   ulAppDomainID,
    GUID      guidModule,
    ULONGLONG baseAddress,
    IUnknown* pUnkMetadataImport,
    IStream*  pStream
);
```

```csharp
int LoadSymbolsFromStream(
    uint    ulAppDomainID,
    Guid    guidModule,
    ulong   baseAddress,
    object  pUnkMetadataImport,
    IStream pStream
);
```

#### <a name="parameters"></a>Parameter
`ulAppDomainID`  
[in] Der Bezeichner der Anwendungsdomäne.

`guidModule`  
[in] Eindeutiger Bezeichner des Moduls.

`baseAddress`  
[in] Basis Speicheradresse.

`pUnkMetadataImport`  
[in] Objekt, das die Symbol-Metadaten enthält.

`pStream`  
[in] Datenstrom mit den Symbolen.

## <a name="return-value"></a>Rückgabewert
Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt, wie Sie die Implementierung dieser Methode für eine **CDebugSymbolProvider** -Objekt, das macht die [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) Schnittstelle. Ruft die Methode die [LoadSymbolsFromStreamWithCorModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-loadsymbolsfromstreamwithcormodule.md) Methode.

```cpp
HRESULT CDebugSymbolProvider::LoadSymbolsFromStream(
    ULONG32 ulAppDomainID,
    GUID guidModule,
    ULONGLONG baseOffset,
    IUnknown* pUnkMetadataImport,
    IStream* pStream
)
{
    return LoadSymbolsFromStreamWithCorModule (ulAppDomainID, guidModule, baseOffset, pUnkMetadataImport, NULL, pStream);
}
```

## <a name="see-also"></a>Siehe auch
[IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
