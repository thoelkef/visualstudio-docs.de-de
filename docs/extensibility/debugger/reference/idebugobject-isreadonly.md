---
title: IDebugObject::IsReadOnly | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsReadOnly
helpviewer_keywords:
- IDebugObject::IsReadOnly method
ms.assetid: c460f772-d08a-4b36-81f3-dff6a51a93fd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 19546550f916e9d42adf634b0d85958ce9697d28
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726415"
---
# <a name="idebugobjectisreadonly"></a>IDebugObject::IsReadOnly
Bestimmt, ob dieses Objekt schreibgeschützt ist.

## <a name="syntax"></a>Syntax

```cpp
HRESULT IsReadOnly( 
   BOOL* pfIsReadOnly
);
```

```csharp
int IsReadOnly(
   out int pfIsReadOnly
);
```

## <a name="parameters"></a>Parameter
`pfIsReadOnly`\
[out] Gibt einen Wert`TRUE`ungleich Null zurück ( ), wenn dieses Objekt schreibgeschützt ist; Andernfalls wird Null`FALSE`zurückgegeben ( ).

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, kehrt S_OK zurück; Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Ein schreibgeschütztes Objekt kann seinen Wert nicht ändern, nachdem es erstellt wurde.

## <a name="see-also"></a>Weitere Informationen
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
