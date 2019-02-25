---
title: IDebugModule3::IsUserCode | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::IsUserCode
helpviewer_keywords:
- IDebugModule3::IsUserCode
ms.assetid: 77022946-bb8b-4114-aa81-614df6e54b13
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 39bbef1e8b831473b196d0609459b80a05e5fc2c
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56718494"
---
# <a name="idebugmodule3isusercode"></a>IDebugModule3::IsUserCode
Ruft Informationen zu gibt an, ob das Modul Benutzercode oder nicht darstellt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT IsUserCode(
   BOOL* pfUser
);
```

```csharp
int IsUserCode(
   out int pfUser
);
```

#### <a name="parameters"></a>Parameter
 `pfUser`

 [out] Ungleich Null (`TRUE`), wenn das Modul Benutzercode darstellt, NULL (`FALSE`), wenn dies nicht der Fall.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt den Fehlercode zurück.

## <a name="see-also"></a>Siehe auch
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)