---
title: 'Idebugenenfield:: getvaluefromstring | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetValueFromString
helpviewer_keywords:
- IDebugEnumField::GetValueFromString method
ms.assetid: 1ef8ac5e-a3e0-4078-b876-7f5615aedcbb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bb340721c9f446b740c2723dc3f6dc05452e74de
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80730263"
---
# <a name="idebugenumfieldgetvaluefromstring"></a>IDebugEnumField::GetValueFromString
Diese Methode gibt den Wert zurück, der dem Namen einer Enumerationskonstante zugeordnet ist.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetValueFromString(
   LPCOLESTR  pszValue,
   ULONGLONG* pvalue
);
```

```csharp
int GetValueFromString(
   string    pszValue,
   out ulong pValue
);
```

## <a name="parameters"></a>Parameter
`pszValue`\
in Eine Zeichenfolge, die den Namen angibt, für den der Wert zu erhalten ist. Beachten Sie, dass dies für C++ eine Zeichenfolge mit breit Zeichen ist.

`pValue`\
vorgenommen Gibt den zugeordneten numerischen Wert zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird zurückgegeben `S_FALSE` , wenn der Name nicht Teil der-Enumeration ist, oder ein Fehlercode.

## <a name="remarks"></a>Bemerkungen
 Bei dieser Methode wird die Groß-/Kleinschreibung beachtet. Wenn eine Suche ohne Berücksichtigung der Groß-/Kleinschreibung erforderlich ist (z. b. in einer Sprache wie Visual Basic, in der die Groß-/Kleinschreibung nicht beachtet wird), verwenden Sie [getvaluefromstringcaseinsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)

## <a name="see-also"></a>Weitere Informationen
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
- [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)
