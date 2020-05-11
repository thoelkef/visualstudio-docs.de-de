---
title: IDebugProgram2::GetProcess | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetProcess
helpviewer_keywords:
- IDebugProgram2::GetProcess
ms.assetid: 1d602485-ebaf-451c-9165-f2e226f20a90
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aca1842e92e7e1c164a6468e6c1e94a352ef67c0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722782"
---
# <a name="idebugprogram2getprocess"></a>IDebugProgram2::GetProcess
Erhalten Sie den Prozess, in dem dieses Programm ausgeführt wird.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetProcess(
   IDebugProcess2** ppProcess
);
```

```csharp
int GetProcess(
   out IDebugProcess2 ppProcess
);
```

## <a name="parameters"></a>Parameter
`ppProcess`\
[out] Gibt die [IDebugProcess2-Schnittstelle](../../../extensibility/debugger/reference/idebugprocess2.md) zurück, die den Prozess darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Sofern ein Debugmodul (DE) die [IDebugEngineLaunch2-Schnittstelle](../../../extensibility/debugger/reference/idebugenginelaunch2.md) nicht implementiert, sollte `E_NOTIMPL` die DE-Implementierung dieser Methode immer zurückgegeben werden, da eine DE nicht bestimmen kann, in welchem Prozess sie ausgeführt wird, und daher eine Implementierung dieser Methode nicht erfüllen kann.

 Die `IDebugEngineLaunch2` Implementierung der Schnittstelle bedeutet, dass die DE wissen muss, wie ein Prozess erstellt wird; Daher ist die De-Implementierung der [IDebugProgram2-Schnittstelle](../../../extensibility/debugger/reference/idebugprogram2.md) in der Lage zu wissen, in welchem Prozess sie ausgeführt wird.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
