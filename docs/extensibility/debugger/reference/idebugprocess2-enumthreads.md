---
title: IDebugProcess2::EnumThreads | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::EnumThreads
helpviewer_keywords:
- IDebugProcess2::EnumThreads
ms.assetid: 05677385-7a7f-4545-8438-af00dde85db0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 52383649fc45eae6bbac6831f9bb233b9c0a2fde
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724073"
---
# <a name="idebugprocess2enumthreads"></a>IDebugProcess2::EnumThreads
Ruft eine Liste aller Threads ab, die im Prozess ausgeführt werden.

## <a name="syntax"></a>Syntax

```cpp
HRESULT EnumThreads(
   IEnumDebugThreads2** ppEnum
);
```

```csharp
int EnumThreads(
   out IEnumDebugThreads2 ppEnum
);
```

## <a name="parameters"></a>Parameter
`ppEnum`\
[out] Gibt ein [IEnumDebugThreads2-Objekt](../../../extensibility/debugger/reference/ienumdebugthreads2.md) zurück, das eine Liste aller Threads in allen Programmen im Prozess enthält.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode zählt die threads auf, die in jedem Programm ausgeführt werden, und kombiniert sie dann in einer Prozessansicht der Threads. Ein einzelner Thread kann in mehreren Programmen ausgeführt werden. Diese Methode zählt diesen Thread nur einmal auf.

 Diese Methode stellt eine Liste der Prozessthreads ohne Duplikate dar. Verwenden Sie andernfalls die [EnumThreads-Methode,](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) um die Threads aufzuzählen, die in einem bestimmten Programm ausgeführt werden.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)
