---
title: THREADSTATE | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADSTATE
helpviewer_keywords:
- THREADSTATE enumeration
ms.assetid: 62efdd7c-25b1-4fd3-9d06-ac1830a418a9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3019671b98d3eb17c92d97c368f2f7338ee55a1d
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/09/2019
ms.locfileid: "65460710"
---
# <a name="threadstate"></a>THREADSTATE
Gibt den Zustand des Threads.

## <a name="syntax"></a>Syntax

```cpp
enum enum_THREADSTATE { 
   THREADSTATE_RUNNING = 0x0001,
   THREADSTATE_STOPPED = 0x0002,
   THREADSTATE_FRESH   = 0x0003,
   THREADSTATE_DEAD    = 0x0004,
   THREADSTATE_FROZEN  = 0x0005
};
typedef DWORD THREADSTATE;
```

```csharp
public enum enum_THREADSTATE { 
   THREADSTATE_RUNNING = 0x0001,
   THREADSTATE_STOPPED = 0x0002,
   THREADSTATE_FRESH   = 0x0003,
   THREADSTATE_DEAD    = 0x0004,
   THREADSTATE_FROZEN  = 0x0005
};
```

## <a name="fields"></a>Felder
 `THREADSTATE_RUNNING`\
 Gibt an, dass der Thread ausgeführt wird.

 `THREADSTATE_STOPPED`\
 Gibt an, dass der Thread aufgrund von einem Haltepunkt angehalten wurde.

 `THREADSTATE_FRESH`\
 Gibt an, dass der Thread erstellt wurde, aber noch nicht Code ausgeführt wird.

 `THREADSTATE_DEAD`\
 Gibt an, dass der Thread inaktiv ist.

 `THREADSTATE_FROZEN`\
 Gibt an, dass der Thread gesperrt ist (es kann keine Ausführung ausgeführt werden).

## <a name="remarks"></a>Hinweise
 Verwendet für die `dwThreadState` Feld der [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) Struktur.

## <a name="requirements"></a>Anforderungen
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)