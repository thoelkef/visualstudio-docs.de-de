---
title: NotifyDebuggerOfWaitCompletion-Methode | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- NotifyDebuggerOfWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8963e29a067754c0e8c89b9db336b239ac682ce1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738332"
---
# <a name="notifydebuggerofwaitcompletion-method"></a>NotifyDebuggerOfWaitCompletion-Methode
Platzhaltermethode, die vom Debugger als Haltepunktziel verwendet wird. Diese Methode darf nicht inline oder optimiert werden.

 **Namespace:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Baugruppe:** mscorlib (in *mscorlib.dll*)

## <a name="syntax"></a>Syntax

```vb
private void NotifyDebuggerOfWaitCompletion()
```

## <a name="remarks"></a>Bemerkungen
 Alle Join-Vorgänge mit einer Aufgabe sollten diese Methode aufrufen, wenn ihr Debuggerbenachrichtigungsbit festgelegt ist.

## <a name="requirements"></a>Requirements (Anforderungen)

## <a name="see-also"></a>Weitere Informationen
- [Task-Klasse](../../extensibility/debugger/task-class-internal-members.md)
