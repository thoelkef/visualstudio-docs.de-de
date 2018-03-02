---
title: IDebugProgramNode2::DetachDebugger_V7 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: fdf4875c30bebaeed925af57c0d80910f8fcbf21
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/28/2018
---
# <a name="idebugprogramnode2detachdebuggerv7"></a>IDebugProgramNode2::DetachDebugger_V7

> [!Note]
> ALS VERALTET MARKIERT. DARF NICHT VERWENDET WERDEN.

## <a name="syntax"></a>Syntax

```cpp
HRESULT DetachDebugger_V7 (
   void 
);
```

```csharp
int DetachDebugger_V7 ();
```

## <a name="return-value"></a>Rückgabewert

Eine Implementierung sollte stets `E_NOTIMPL`.

## <a name="remarks"></a>Hinweise

> [!WARNING]
> Ab Visual Studio 2005, diese Methode wird nicht mehr verwendet und sollten stets `E_NOTIMPL`.

Diese Methode wird aufgerufen, wenn der Debugger unerwartet beendet wird. Wenn diese Methode aufgerufen wird, sollte DE das Programm fortgesetzt, als ob der Benutzer von ihm getrennt. Keine weiteren Debuggingereignisse gesendet werden soll. Das Programm sollte sich in einem Zustand, wo es von einer anderen Instanz des Debuggers anfügbar ist.

## <a name="see-also"></a>Siehe auch

[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)