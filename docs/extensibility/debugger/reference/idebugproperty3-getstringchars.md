---
title: 'IDebugProperty3:: getstringchars | Microsoft-Dokumentation'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80721079"
---
# <a name="idebugproperty3getstringchars"></a>IDebugProperty3::GetStringChars
Ruft die Zeichenfolge ab, die dieser Eigenschaft zugeordnet ist, und speichert Sie in einem vom Benutzer bereitgestellten Puffer.

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
in Maximale Anzahl von Zeichen, die der vom Benutzer bereitgestellte Puffer enthalten kann.

`rgString`\
vorgenommen Gibt die Zeichenfolge zurück.

 [Nur C++], `rgString` ist ein Zeiger auf einen Puffer, der die Unicode-Zeichen der Zeichenfolge empfängt. Dieser Puffer muss mindestens `buflen` Zeichen (nicht Bytes) groß sein.

`pceltFetched`\
vorgenommen Gibt an, wo die Anzahl der tatsächlich im Puffer gespeicherten Zeichen zurückgegeben wird. (Kann `NULL` in C++ sein.)

## <a name="return-value"></a>Rückgabewert
Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
In C++ muss sorgfältig vorgegangen werden, um sicherzustellen, dass der Puffer mindestens `buflen` Unicode-Zeichen lang ist. Beachten Sie, dass ein Unicode-Zeichen 2 Bytes lang ist.

> [!NOTE]
> In C++ ist in der zurückgegebenen Zeichenfolge kein abschließendes NULL-Zeichen enthalten. Wenn angegeben, `pceltFetched` wird die Anzahl der Zeichen in der Zeichenfolge angegeben.

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
