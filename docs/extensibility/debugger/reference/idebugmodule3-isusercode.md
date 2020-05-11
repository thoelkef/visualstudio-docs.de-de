---
title: IDebugModule3::IsUserCode | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::IsUserCode
helpviewer_keywords:
- IDebugModule3::IsUserCode
ms.assetid: 77022946-bb8b-4114-aa81-614df6e54b13
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 435ec50ef5437e5aca5d3722a2041115882d15f2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726831"
---
# <a name="idebugmodule3isusercode"></a>IDebugModule3::IsUserCode
Ruft Informationen darüber ab, ob das Modul Benutzercode darstellt oder nicht.

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
[out] Ein Wert`TRUE`ungleich Null ( ),`FALSE`wenn das Modul für Benutzercode steht, Null ( ), wenn dies nicht der Fall ist.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, `S_OK`kehrt zurück; Andernfalls wird Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
