---
title: NotifyDebuggerOfWaitCompletion-Methode | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- NotifyDebuggerOfWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 28811ba402803d1ddb9a6dd08a18d32db6257386
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56679540"
---
# <a name="notifydebuggerofwaitcompletion-method"></a>NotifyDebuggerOfWaitCompletion-Methode
Platzhalter-Methode, die als Ziel der Haltepunkt vom Debugger verwendet. Diese Methode darf nicht inline oder optimiert sein.

 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** "mscorlib" (in *"mscorlib.dll"*)

## <a name="syntax"></a>Syntax

```vb
private void NotifyDebuggerOfWaitCompletion()
```

## <a name="remarks"></a>Hinweise
 Alle Joinvorgänge mit einer Aufgabe sollten diese Methode aufrufen, wenn die Debugger-Notification-Bit festgelegt ist.

## <a name="requirements"></a>Anforderungen

## <a name="see-also"></a>Siehe auch
- [Task class (Task-Klasse)](../../extensibility/debugger/task-class-internal-members.md)