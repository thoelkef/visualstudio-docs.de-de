---
title: IDebugComPlusSymbolProvider2::GettypesByName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetTypesByName
- IDebugComPlusSymbolProvider2::GetTypesByName
ms.assetid: ef76b1a8-6910-48fe-b4af-d9045eefd23f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5e7b85fb8d5b0e3256e172ff78bc3a5f660b69b8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733421"
---
# <a name="idebugcomplussymbolprovider2gettypesbyname"></a>IDebugComPlusSymbolProvider2::GetTypesByName
Ruft einen Typ mit dem Namen ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetTypesByName(
    LPCOLESTR          pszClassName,
    NAME_MATCH         nameMatch,
    IEnumDebugFields** ppEnum
);
```

```csharp
int GetTypesByName(
    string               pszClassName,
    enum_ NAME_MATCH     nameMatch,
    out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Parameter
`pszClassName`\
[in] Name des Typs.

`nameMatch`\
[in] Wählt den Typ der Übereinstimmung aus, z. B. groß, wenn die Groß-/Kleinschreibung beachtet wird. Ein Wert [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) aus der NAME_MATCH-Enumeration.

`ppEnum`\
[out] Ein Enumerator, der den oder die Typen mit dem angegebenen Namen enthält.

## <a name="return-value"></a>Rückgabewert
Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
Bei generischen Typen wäre der Name, der nach "List\<int>" oder "List\<int,int>" sucht, "Liste". Wenn Typen mit demselben Namen in mehreren `ppEnum` Modulen angezeigt werden, enthält der Parameter alle Kopien. Sie müssen [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) verwenden und `guidModule` basierend auf dem Parameter unterscheiden.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt, wie diese Methode für ein **CDebugSymbolProvider-Objekt** implementiert wird, das die [IDebugComPlusSymbolProvider2-Schnittstelle](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md) verfügbar macht.

```cpp
HRESULT CDebugSymbolProvider::GetTypesByName(
    LPCOLESTR pszClassName,
    NAME_MATCH nameMatch,
    IEnumDebugFields** ppEnum
)
{
    HRESULT hr = S_OK;
    CModIter ModIter;
    CModule* pmodule; // the iterator owns the reference
    CFieldList listField;

    ASSERT(IsValidWideStringPtr(pszClassName));
    ASSERT(IsValidWritePtr(ppEnum, IEnumDebugFields*));

    METHOD_ENTRY( CDebugSymbolProvider::GetTypesByName );

    IfFalseGo( pszClassName && ppEnum, E_INVALIDARG );
    *ppEnum = NULL;

    IfFailGo( GetModuleIter(&ModIter) );

    hr = S_FALSE;

    if ( nameMatch == nmCaseInsensitive)
    {
        while (ModIter.GetNext(&pmodule))
        {
            if (pmodule->FindTypesByNameCaseInsensitive( pszClassName,
                    &listField,
                    this ) )
            {
                hr = S_OK;
            }
        }
    }
    else
    {
        while (ModIter.GetNext(&pmodule))
        {
            if (pmodule->FindTypesByName( pszClassName,
                                          &listField,
                                          this) )
            {
                hr = S_OK;
            }
        }
    }

    // If the list is empty then no type
    IfFalseGo( listField.GetCount(), E_FAIL );

    // Create enumerator
    IfFailGo( CreateEnumerator( ppEnum, &listField ) );

Error:

    METHOD_EXIT( CDebugSymbolProvider::GetTypesByName, hr );

    return hr;
}
```

## <a name="see-also"></a>Weitere Informationen
- [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)
