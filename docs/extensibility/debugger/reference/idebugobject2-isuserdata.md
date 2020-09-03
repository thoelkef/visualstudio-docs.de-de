---
title: 'IDebugObject2:: isuserdata | Microsoft-Dokumentation'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726086"
---
# <a name="idebugobject2isuserdata"></a>IDebugObject2::IsUserData
Bestimmt, ob das-Objekt Benutzerdaten darstellt.

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
vorgenommen Gibt einen Wert ungleich 0 (null) zurück ( `TRUE` ), wenn das-Objekt Benutzerdaten darstellt, andernfalls NULL ( `FALSE` ).

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Bei Benutzerdaten handelt es sich um ein beliebiges Objekt, das Teil eines als JustMyCode bezeichneten Moduls ist (eine vom benutzerkonfigurierbare Option, die ein Modul als Benutzercode markiert und daher in einer Stapel Überwachung sichtbar ist).

## <a name="see-also"></a>Weitere Informationen
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
