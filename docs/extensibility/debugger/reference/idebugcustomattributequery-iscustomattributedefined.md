---
title: IDebugCustomAttributeQuery::IsCustomAttributeDefined | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugCustomAttributeQuery::IsCustomAttributeDefined
- IsCustomAttributeDefined
ms.assetid: c7425db6-4347-4f69-8f88-337ddaa34fa6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3b0be4f8afdfe5320bdf871586f8c0e8f648ae84
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732630"
---
# <a name="idebugcustomattributequeryiscustomattributedefined"></a>IDebugCustomAttributeQuery::IsCustomAttributeDefined
Bestimmt, ob das angegebene benutzerdefinierte Attribut definiert ist.

## <a name="syntax"></a>Syntax

```cpp
HRESULT IsCustomAttributeDefined(
    LPCOLESTR pszCustomAttributeName
);
```

```csharp
int IsCustomAttributeDefined(
    string pszCustomAttributeName
);
```

## <a name="parameters"></a>Parameter
`pszCustomAttributeName`\
[in] Name des benutzerdefinierten Attributs.

## <a name="return-value"></a>Rückgabewert
Wenn das benutzerdefinierte Attribut `S_OK`definiert ist, gibt zurück ; Andernfalls kehrt `S_FALSE`zurück .

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt, wie diese Methode für ein **CDebugClassFieldSymbol-Objekt** implementiert wird, das die [IDebugCustomAttributeQuery-Schnittstelle](../../../extensibility/debugger/reference/idebugcustomattributequery.md) verfügbar macht.

```cpp
HRESULT CDebugClassFieldSymbol::IsCustomAttributeDefined(
    LPCOLESTR pszCustomAttribute
)
{
    HRESULT hr = S_FALSE;
    CComPtr<IMetaDataImport> pMetadata;
    mdToken token = mdTokenNil;
    CComPtr<IDebugField> pField;
    CComPtr<IDebugCustomAttributeQuery> pCA;

    ASSERT(IsValidWideStringPtr(pszCustomAttribute));

    METHOD_ENTRY( CDebugClassFieldSymbol::IsCustomAttributeDefined );

    IfFalseGo( pszCustomAttribute, E_INVALIDARG );

    IfFailGo( m_spSH->GetMetadata( m_spAddress->GetModule(), &pMetadata ) );

    IfFailGo( CDebugCustomAttribute::GetTokenFromAddress( m_spAddress, &token) );
    IfFailGo( pMetadata->GetCustomAttributeByName( token,
              pszCustomAttribute,
              NULL,
              NULL ) );
Error:

    METHOD_EXIT( CDebugClassFieldSymbol::IsCustomAttributeDefined, hr );

    if (hr != S_OK)
    {
        hr = S_FALSE;
    }

    return hr;
}
```

## <a name="see-also"></a>Weitere Informationen
- [IDebugCustomAttributeQuery](../../../extensibility/debugger/reference/idebugcustomattributequery.md)
