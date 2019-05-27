---
title: IDebugEnumField::GetStringFromValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetStringFromValue
helpviewer_keywords:
- IDebugEnumField::GetStringFromValue method
ms.assetid: 5f95fd0c-fdce-497f-9f54-2ad8749494e9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 25becdae62dbdda78e04404528eeb099a4914265
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212394"
---
# <a name="idebugenumfieldgetstringfromvalue"></a>IDebugEnumField::GetStringFromValue
Diese Methode ruft den Namen der Enumerationskonstante erhält den Wert ab.

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
[in] Der Wert für das der Name der Enumeration Konstanten abgerufen werden soll.

`pbstrValue`\
[out] Der Name der Enumerationskonstante zurückgegeben.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` , wenn der Wert keinen zugeordneten Namen hat, oder gibt einen Fehlercode zurück.

## <a name="remarks"></a>Hinweise
 Ist mehr als einen Namen, die den gleichen Wert zugeordnet, wird der Vorname in der Enumeration definierte zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)