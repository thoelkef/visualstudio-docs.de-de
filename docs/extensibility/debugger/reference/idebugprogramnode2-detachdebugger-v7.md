---
title: IDebugProgramNode2::DetachDebugger_V7 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 925f1b07662ece35d21f9b647681bc898428c4c7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722109"
---
# <a name="idebugprogramnode2detachdebugger_v7"></a>IDebugProgramNode2::DetachDebugger_V7

> [!Note]
> Veraltet. NICHT VERWENDEN.

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

Eine Implementierung sollte `E_NOTIMPL`immer zurückgegeben werden.

## <a name="remarks"></a>Bemerkungen

> [!WARNING]
> Ab Visual Studio 2005 wird diese Methode nicht `E_NOTIMPL`mehr verwendet und sollte immer zurückgegeben werden.

Diese Methode wird aufgerufen, wenn der Debugger unerwartet beendet wird. Wenn diese Methode aufgerufen wird, sollte die DE das Programm so fortsetzen, als ob sich der Benutzer von ihr getrennt hätte. Es sollten keine weiteren Debugereignisse gesendet werden. Das Programm sollte sich in einem Zustand befinden, in dem es von einer anderen Instanz des Debuggers anhängen kann.

## <a name="see-also"></a>Weitere Informationen

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
