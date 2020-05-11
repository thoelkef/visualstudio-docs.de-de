---
title: IDebugEnumField::GetStringFromValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetStringFromValue
helpviewer_keywords:
- IDebugEnumField::GetStringFromValue method
ms.assetid: 5f95fd0c-fdce-497f-9f54-2ad8749494e9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5de59c573f7e233ea2aacb0dfa38826051c59373
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730283"
---
# <a name="idebugenumfieldgetstringfromvalue"></a>IDebugEnumField::GetStringFromValue
Diese Methode ruft den Namen der Enumerationskonstante unter dem Wert ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetStringFromValue(
   ULONGLONG value,
   BSTR*     pbstrValue
);
```

```csharp
int GetStringFromValue(
   ulong      value,
   out string pbstrValue
);
```

## <a name="parameters"></a>Parameter
`value`\
[in] Der Wert, für den der Name der Enumerationskonstante abruft.

`pbstrValue`\
[out] Gibt den Namen der Enumerationskonstante zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, `S_OK`kehrt zurück; Andernfalls wird `S_FALSE` zurückgegeben, wenn dem Wert kein Name zugeordnet ist, oder gibt einen Fehlercode zurück.

## <a name="remarks"></a>Bemerkungen
 Wenn mehr als ein Name mit demselben Wert verknüpft ist, wird der in der Enumeration definierte Vorname zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
