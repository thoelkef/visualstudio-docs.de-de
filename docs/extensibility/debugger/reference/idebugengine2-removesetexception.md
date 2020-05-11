---
title: IDebugEngine2::RemoveSetException | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::RemoveSetException
helpviewer_keywords:
- IDebugEngine2::RemoveSetException
ms.assetid: bdd25097-0e9d-4218-b417-0497ea48d2e8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0e811ce2e387c299ff3655799bf35185c1d2029b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730920"
---
# <a name="idebugengine2removesetexception"></a>IDebugEngine2::RemoveSetException
Entfernt die angegebene Ausnahme, sodass sie nicht mehr vom Debugmodul behandelt wird.

## <a name="syntax"></a>Syntax

```cpp
HRESULT RemoveSetException( 
   EXCEPTION_INFO* pException
);
```

```csharp
int RemoveSetException( 
   EXCEPTION_INFO[] pException
);
```

## <a name="parameters"></a>Parameter
`pException`\
[in] Eine [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) Struktur, die die zu entfernende Ausnahme beschreibt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Die zu entfernende Ausnahme muss zuvor durch einen früheren Aufruf der [SetException-Methode](../../../extensibility/debugger/reference/idebugengine2-setexception.md) festgelegt worden sein.

 Um alle festgelegten Ausnahmen gleichzeitig zu entfernen, rufen Sie die [RemoveAllSetExceptions-Methode](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md) auf.

## <a name="see-also"></a>Weitere Informationen
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
