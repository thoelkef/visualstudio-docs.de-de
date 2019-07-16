---
title: SetNotificationForWaitCompletion-Methode | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a5d9bee2579cc3a93f657291551955f0c9b7565b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66348585"
---
# <a name="setnotificationforwaitcompletion-method"></a>SetNotificationForWaitCompletion-Methode
Legt fest oder löscht das TASK_STATE_WAIT_COMPLETION_NOTIFICATION Zustand Bit.

 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** "mscorlib" (in *"mscorlib.dll"* )

## <a name="syntax"></a>Syntax

```vb
internal void SetNotificationForWaitCompletion(bool enabled)
```

### <a name="parameters"></a>Parameter
 `enabled`

 `true` Das Bit festgelegt `false` um die Festlegung der Bit.

## <a name="exceptions"></a>Ausnahmen

## <a name="remarks"></a>Hinweise
 Der Debugger wird dieses Bit zur schrittweisen aus Text eine Async-Methode. Wenn `enabled` ist `true`, diese Methode muss aufgerufen werden, nur für eine Aufgabe, die noch nicht abgeschlossen wurde. Wenn `enabled` ist `false`, diese Methode für abgeschlossene Aufgaben aufgerufen werden kann. In jedem Fall sollten sie nur für Vorgänge des Promise-Stil verwendet werden.

## <a name="requirements"></a>Anforderungen

## <a name="see-also"></a>Siehe auch
- [Task class (Task-Klasse)](../../extensibility/debugger/task-class-internal-members.md)