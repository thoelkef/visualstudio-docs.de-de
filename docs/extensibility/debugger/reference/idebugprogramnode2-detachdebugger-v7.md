---
title: IDebugProgramNode2::DetachDebugger_V7 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 603c459d39f8141789b22955e916e3e8520214fb
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53924149"
---
# <a name="idebugprogramnode2detachdebuggerv7"></a>IDebugProgramNode2::DetachDebugger_V7

> [!Note]
> ALS VERALTET MARKIERT. VERWENDEN SIE NICHT.

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

Eine Implementierung sollte immer zurückgeben `E_NOTIMPL`.

## <a name="remarks"></a>Hinweise

> [!WARNING]
> Ab Visual Studio 2005, diese Methode wird nicht mehr verwendet und sollte immer zurückgeben `E_NOTIMPL`.

Diese Methode wird aufgerufen, wenn der Debugger unerwartet beendet wird. Wenn diese Methode aufgerufen wird, sollte die DE das Programm fortgesetzt, als ob der Benutzer von ihm getrennt. Keine weiteren Debuggingereignisse gesendet werden soll. Das Programm sollte sich in einem Zustand, in denen es anfügbaren Member aus einer anderen Instanz des Debuggers ist.

## <a name="see-also"></a>Siehe auch

[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)