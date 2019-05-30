---
title: IDebugProcess2::CauseBreak | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::CauseBreak
helpviewer_keywords:
- IDebugProcess2::CauseBreak
ms.assetid: efda8865-2319-4d53-90bf-6d9d74cd5195
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fbe4f3cac40306467e6efc7d87ca860a6d6f3f0e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353231"
---
# <a name="idebugprocess2causebreak"></a>IDebugProcess2::CauseBreak
Fordert an, dass es sich bei der nächsten Ausführung von Code in diesem Prozess, Programmieren Sie angehalten, und senden eine [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) Ereignisobjekt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT CauseBreak( 
   void
);
```

```csharp
int CauseBreak();
```

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)