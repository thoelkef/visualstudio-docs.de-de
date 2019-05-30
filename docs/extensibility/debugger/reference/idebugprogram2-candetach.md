---
title: IDebugProgram2::CanDetach | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::CanDetach
helpviewer_keywords:
- IDebugProgram2::CanDetach
ms.assetid: dcd9ab6c-49e5-447e-aa7c-89f571f4a052
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6bc8f7ac644a893049592420ad8435ac896a62b0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66311484"
---
# <a name="idebugprogram2candetach"></a>IDebugProgram2::CanDetach
Bestimmt, ob die Anwendung eine Debug-Engine (DE) trennen kann.

## <a name="syntax"></a>Syntax

```cpp
HRESULT CanDetach(
   void
);
```

```csharp
int CanDetach();
```

## <a name="return-value"></a>Rückgabewert
 Wenn können zu trennen, gibt `S_OK`ist, andernfalls ein Fehlercode zurückgegeben. Gibt `S_FALSE` , wenn das Programm die DE trennen kann nicht.

## <a name="see-also"></a>Siehe auch
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)