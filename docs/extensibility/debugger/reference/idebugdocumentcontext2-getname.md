---
title: IDebugDocumentContext2::GetName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetName
helpviewer_keywords:
- IDebugDocumentContext2::GetName
ms.assetid: 546c5b2e-f166-4edb-9e61-57d797ca98a1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 253ef509a60e8bb2ce177235f4b93b370e66f484
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731813"
---
# <a name="idebugdocumentcontext2getname"></a>IDebugDocumentContext2::GetName
Ruft den angezeigten Namen des Dokuments ab, das diesen Dokumentkontext enthält.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetName(
    GETNAME_TYPE gnType,
    BSTR*        pbstrFileName
);
```

```csharp
int GetName(
    enum_GETNAME_TYPE  gnType,
    out string         pbstrFileName
);
```

## <a name="parameters"></a>Parameter
`gnType`\
[in] Ein Wert [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md) aus der GETNAME_TYPE-Enumeration, der den zurückzugebenden Namenstyp angibt.

`pbstrFileName`\
[out] Gibt den Namen der Datei zurück.

## <a name="return-value"></a>Rückgabewert
Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
Diese Methode leitet den Aufruf in der Regel an die [GetName-Methode](../../../extensibility/debugger/reference/idebugdocument2-getname.md) weiter, es sei denn, der Dokumentkontext wird geschrieben, um den Dokumentnamen selbst zu speichern (wie das Beispiel zeigt).

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt, wie diese `CDebugContext` Methode für ein einfaches Objekt implementiert wird, das die [IDebugDocumentContext2-Schnittstelle](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) verfügbar macht.

```cpp
HRESULT CDebugContext::GetName(GETNAME_TYPE gnType, BSTR* pbstrFileName)
{
    HRESULT hr;

    // Check for a valid file name argument.
    if (pbstrFileName)
    {
        *pbstrFileName = NULL;

        switch (gnType)
        {
            case GN_NAME:
            case GN_FILENAME:
            {
                // Copy the member file name into the local file name.
                *pbstrFileName = SysAllocString(m_sbstrFileName);
                // Check for successful copy.
                hr = (*pbstrFileName) ? S_OK : E_OUTOFMEMORY;
                break;
            }
            default:
            {
                hr = E_FAIL;
                break;
            }
        }
    }
    else
    {
        hr = E_INVALIDARG;
    }

    return hr;
}
```

## <a name="see-also"></a>Weitere Informationen
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)
