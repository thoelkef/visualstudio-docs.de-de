---
title: IDebugProperty3::GetStringChars | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::GetStringChars
helpviewer_keywords:
- IDebugProperty3::GetStringChars
ms.assetid: 832c37f3-85cb-4227-8ab2-f27a80eafe90
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 693a29bc30ef206428713ace36275389de1b7f0a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721079"
---
# <a name="idebugproperty3getstringchars"></a>IDebugProperty3::GetStringChars
Ruft die dieser Eigenschaft zugeordnete Zeichenfolge ab und speichert sie in einem vom Benutzer bereitgestellten Puffer.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetStringChars(
    ULONG  buflen,
    WCHAR* rgString,
    ULONG* pceltFetched
);
```

```csharp
int GetStringChars(
    uint       buflen,
    out string rgString,
    out uint   pceltFetched
);
```

## <a name="parameters"></a>Parameter
`buflen`\
[in] Maximale Anzahl von Zeichen, die der vom Benutzer bereitgestellte Puffer enthalten kann.

`rgString`\
[out] Gibt die Zeichenfolge zurück.

 [Nur C++] `rgString` ist ein Zeiger auf einen Puffer, der die Unicode-Zeichen der Zeichenfolge empfängt. Dieser Puffer muss `buflen` mindestens Zeichen (nicht Bytes) in der Größe sein.

`pceltFetched`\
[out] Wobei die Anzahl der tatsächlich im Puffer gespeicherten Zeichen zurückgegeben wird. (Kann `NULL` in C++ sein.)

## <a name="return-value"></a>Rückgabewert
Wenn erfolgreich, `S_OK`kehrt zurück; andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
In C++ muss darauf geachtet werden, dass der `buflen` Puffer mindestens Unicode-Zeichen lang ist. Beachten Sie, dass ein Unicode-Zeichen 2 Byte lang ist.

> [!NOTE]
> In C++ enthält die zurückgegebene Zeichenfolge kein beendendes NULL-Zeichen. Wenn angegeben, `pceltFetched` wird die Anzahl der Zeichen in der Zeichenfolge angegeben.

## <a name="example"></a>Beispiel

```cpp
CStringW RetrievePropertyString(IDebugProperty2 *pPropInfo)
{
    CStringW returnString = L"";
    CComQIPtr<IDebugProperty3> pProp3 = pPropInfo->pProperty;
    If (pProp3 != NULL) {
        ULONG dwStrLen = 0;
        HRESULT hr;
        hr = pProp3->GetStringCharLength(&dwStrLen);
        if (SUCCEEDED(hr) && dwStrLen > 0) {
            ULONG dwRead;
            CStrBufW buf(returnString,dwStrLen,CStrBuf::SET_LENGTH);
            hr = pProp3->GetStringChars(dwStrLen,
                                        reinterpret_cast<WCHAR*>(static_cast<CStringW::PXSTR>(buf)),
                                        &dwRead);
        }
    }
    return(returnString);
}
```

## <a name="see-also"></a>Weitere Informationen
- [GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
