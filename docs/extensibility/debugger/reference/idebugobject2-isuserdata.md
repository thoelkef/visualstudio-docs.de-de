---
title: IDebugObject2::IsUserData | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::IsUserData
helpviewer_keywords:
- IDebugObject2::IsUserData method
ms.assetid: 6ffa0d0e-f742-496d-acc7-db74c248bc45
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 04c47390f15ff59658ba25f5c8f93918a15f47d6
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56700093"
---
# <a name="idebugobject2isuserdata"></a>IDebugObject2::IsUserData
Bestimmt, ob das Objekt mit Daten des Benutzers darstellt.

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

#### <a name="parameters"></a>Parameter
 `pfUser`

 [out] Ungleich NULL zurückgibt (`TRUE`) NULL, wenn das Objekt auf Benutzerdaten; darstellt (`FALSE`), wenn dies nicht der Fall.

## <a name="return-value"></a>Rückgabewert
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Benutzerdaten sind ein Objekt, das Teil eines Moduls, das als JustMyCode (eine konfigurierbare Option, die ein Modul als Benutzercode und daher in eine stapelüberwachung sichtbar markiert) festgelegt ist.

## <a name="see-also"></a>Siehe auch
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)