---
title: IDebugThread2::GetProgram | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetProgram
helpviewer_keywords:
- IDebugThread2::GetProgram
ms.assetid: 8c9c5ea1-2031-472e-bc8f-30e22e754566
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bc803d08e26780712dbec6318a928022c3ce862e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66320257"
---
# <a name="idebugthread2getprogram"></a>IDebugThread2::GetProgram
Ruft ab, das Programm, in dem ein Thread ausgeführt wird.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetProgram ( 
   IDebugProgram2** ppProgram
);
```

```csharp
int GetProgram ( 
   out IDebugProgram2 ppProgram
);
```

## <a name="parameters"></a>Parameter
`ppProgram`\
[out] Gibt eine [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) -Objekt, das Programm darstellt, in diesem Thread ausgeführt wird.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)