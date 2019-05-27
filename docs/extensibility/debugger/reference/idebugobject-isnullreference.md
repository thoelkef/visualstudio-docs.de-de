---
title: IDebugObject::IsNullReference | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsNullReference
helpviewer_keywords:
- IDebugObject::IsNullReference method
ms.assetid: 6dbfcdb0-954f-4486-8fac-7ea8d003e3a9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 99f623de076f0ff2c063d5f59c52bbb768c3f89f
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2019
ms.locfileid: "66202846"
---
# <a name="idebugobjectisnullreference"></a>IDebugObject::IsNullReference
Testet, ob dieses Objekt ein null-Verweis ist.

## <a name="syntax"></a>Syntax

```cpp
HRESULT IsNullReference( 
   BOOL* pfIsNull
);
```

```csharp
int IsNullReference(
   out int pfIsNull
);
```

## <a name="parameters"></a>Parameter
`pfIsNull`\
[out] Ungleich NULL zurück (`TRUE`) Wenn dieses Objekt ein null-Verweis; andernfalls wird NULL (`FALSE`).

## <a name="return-value"></a>Rückgabewert
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Ein null-Verweis bedeutet, dass ein leeres Objekt oder ein Objekt, das nicht zugewiesen wurde.

## <a name="see-also"></a>Siehe auch
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)