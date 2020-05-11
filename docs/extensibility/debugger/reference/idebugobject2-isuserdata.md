---
title: IDebugObject2::IsUserData | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::IsUserData
helpviewer_keywords:
- IDebugObject2::IsUserData method
ms.assetid: 6ffa0d0e-f742-496d-acc7-db74c248bc45
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ce4a7035ac3786f0cc1644e2ebbb0c142167e2b0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726086"
---
# <a name="idebugobject2isuserdata"></a>IDebugObject2::IsUserData
Bestimmt, ob das Objekt Benutzerdaten darstellt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT IsUserData(
   BOOL* pfUser
);
```

```csharp
int IsUserData(
   out int pfUser
);
```

## <a name="parameters"></a>Parameter
`pfUser`\
[out] Gibt einen`TRUE`Wert ungleich Null zurück ( ), wenn das Objekt Benutzerdaten darstellt; Null`FALSE`( ), wenn dies nicht der Fall ist.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, kehrt S_OK zurück; Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Benutzerdaten sind jedes Objekt, das Teil eines Moduls ist, das als JustMyCode bezeichnet wird (eine vom Benutzer konfigurierbare Option, die ein Modul als Benutzercode markiert und daher in einer Stapelablaufverfolgung sichtbar ist).

## <a name="see-also"></a>Weitere Informationen
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
