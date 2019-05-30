---
title: NotifyDebuggerOfWaitCompletion-Methode | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- NotifyDebuggerOfWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9a3280a24ad7f9d4045c9a1bff6ca2b44c724325
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350641"
---
# <a name="notifydebuggerofwaitcompletion-method"></a>NotifyDebuggerOfWaitCompletion-Methode
Platzhalter-Methode, die als Ziel der Haltepunkt vom Debugger verwendet. Diese Methode darf nicht inline oder optimiert sein.

 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** "mscorlib" (in *"mscorlib.dll"* )

## <a name="syntax"></a>Syntax

```vb
private void NotifyDebuggerOfWaitCompletion()
```

## <a name="remarks"></a>Hinweise
 Alle Joinvorgänge mit einer Aufgabe sollten diese Methode aufrufen, wenn die Debugger-Notification-Bit festgelegt ist.

## <a name="requirements"></a>Anforderungen

## <a name="see-also"></a>Siehe auch
- [Task class (Task-Klasse)](../../extensibility/debugger/task-class-internal-members.md)