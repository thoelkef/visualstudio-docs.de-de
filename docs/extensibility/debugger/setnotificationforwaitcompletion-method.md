---
title: SetNotificationForWaitCompletion-Methode | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 468850a441cfd0bc87155fd746d8578c6b763e66
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56714386"
---
# <a name="setnotificationforwaitcompletion-method"></a>SetNotificationForWaitCompletion-Methode
Legt fest oder löscht das TASK_STATE_WAIT_COMPLETION_NOTIFICATION Zustand Bit.

 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** "mscorlib" (in *"mscorlib.dll"*)

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