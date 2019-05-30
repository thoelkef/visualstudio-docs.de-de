---
title: IDebugModule3::IsUserCode | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::IsUserCode
helpviewer_keywords:
- IDebugModule3::IsUserCode
ms.assetid: 77022946-bb8b-4114-aa81-614df6e54b13
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1869b9b4bda263d72db9c949be730e51fdc02d01
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66323898"
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

## <a name="parameters"></a>Parameter
`pfUser`\
[out] Ungleich Null (`TRUE`), wenn das Modul Benutzercode darstellt, NULL (`FALSE`), wenn dies nicht der Fall.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt den Fehlercode zurück.

## <a name="see-also"></a>Siehe auch
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)