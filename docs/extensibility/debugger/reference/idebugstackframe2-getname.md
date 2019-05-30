---
title: IDebugStackFrame2::GetName | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetName
helpviewer_keywords:
- IDebugStackFrame2::GetName
ms.assetid: 069d4f96-363f-404e-9c89-5318c4c9821b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3d50fc1b711c673d8582be0d1208bc1d56e0f38b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352103"
---
# <a name="idebugstackframe2getname"></a>IDebugStackFrame2::GetName
Ruft den Namen des Stapelrahmens.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetName ( 
   BSTR* pbstrName
);
```

```csharp
int GetName ( 
   out string pbstrName
);
```

## <a name="parameters"></a>Parameter
`pbstrName`\
[out] Gibt den Namen des Stapelrahmens zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Der Name des ein Stapelrahmen ist in der Regel der Name der Methode ausgeführt wird.

## <a name="see-also"></a>Siehe auch
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)