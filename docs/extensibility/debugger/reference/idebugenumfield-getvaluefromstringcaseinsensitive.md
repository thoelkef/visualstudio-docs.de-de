---
title: IDebugEnumField::GetValueFromStringCaseInsensitive | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive
helpviewer_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive method
ms.assetid: ef95b38e-d9b2-4fb5-a166-7c2e14641dc7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 551945ded9d1ba3e973f18c21463a896cbd478c8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730255"
---
# <a name="idebugenumfieldgetvaluefromstringcaseinsensitive"></a>IDebugEnumField::GetValueFromStringCaseInsensitive
Bei dieser Methode wird bei einer Suche ohne Groß-/Kleinschreibung der Wert zurückgegeben, der dem Namen einer Enumerationskonstante zugeordnet ist.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetValueFromStringCaseInsensitive(
   LPCOLESTR  pszValue,
   ULONGLONG* pvalue
);
```

```csharp
int GetValueFromStringCaseInsensitive(
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
 Bei dieser Methode wird die Groß-/Kleinschreibung nicht berücksichtigt. Wenn eine Suche mit Groß-/Kleinschreibung erforderlich ist (z. B. in einer Sprache wie C++, in der die Groß-/Kleinschreibung beachtet wird), verwenden Sie [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md).

## <a name="see-also"></a>Weitere Informationen
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
- [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)
