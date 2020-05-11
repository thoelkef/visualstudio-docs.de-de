---
title: IDebugEnumField::GetValueFromString | Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
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
[in] Eine Zeichenfolge, die den Namen angibt, für den der Wert abgesendet werden soll. Beachten Sie, dass es sich bei C++ um eine breite Zeichenfolge handelt.

`pValue`\
[out] Gibt den zugeordneten numerischen Wert zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, `S_OK`kehrt zurück; Andernfalls wird `S_FALSE`zurückgegeben, wenn der Name nicht Teil der Enumeration ist, oder einen Fehlercode.

## <a name="remarks"></a>Bemerkungen
 Bei dieser Methode wird die Groß-/Kleinschreibung berücksichtigt. Wenn eine Suche ohne Groß-/Kleinschreibung erforderlich ist (z. B. in einer Sprache wie Visual Basic, in der die Groß-/Kleinschreibung nicht berücksichtigt wird), verwenden Sie [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md).

## <a name="see-also"></a>Weitere Informationen
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
- [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)
