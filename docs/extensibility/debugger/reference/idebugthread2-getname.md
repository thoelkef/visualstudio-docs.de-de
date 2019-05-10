---
title: IDebugThread2::GetName | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetName
helpviewer_keywords:
- IDebugThread2::GetName
ms.assetid: eec54b8f-4a0e-4919-b0f9-81d4bd1e0b6f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9a5d4daad66ed6a4428724b20093473ba7b93856
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2019
ms.locfileid: "65226222"
---
# <a name="idebugthread2getname"></a>IDebugThread2::GetName
Ruft den Namen eines Threads.

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

 [out] Gibt den Namen des Threads.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Der abgerufene Name ist immer ein Name, der angezeigt werden kann, und dieser Name wird im Thread beschrieben. Threadname möglicherweise aus einer Runtime-Architektur abgeleitet werden, dass benannter unterstützt, Threads, oder es, einen Namen, die die Debug-Engine abgeleitet sein kann. Alternativ kann der Name des Threads festgelegt werden, durch einen Aufruf der [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md) Methode.

## <a name="see-also"></a>Siehe auch
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)