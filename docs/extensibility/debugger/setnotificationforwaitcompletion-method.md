---
title: SetNotificationForWaitCompletion-Methode | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 226ac41c8e3b7427ac3b9aba7bea08dbb7329d16
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712864"
---
# <a name="setnotificationforwaitcompletion-method"></a>SetNotificationForWaitCompletion-Methode
Legt das TASK_STATE_WAIT_COMPLETION_NOTIFICATION-Statusbit fest oder löscht es.

 **Namespace:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Baugruppe:** mscorlib (in *mscorlib.dll*)

## <a name="syntax"></a>Syntax

```vb
internal void SetNotificationForWaitCompletion(bool enabled)
```

### <a name="parameters"></a>Parameter
 `enabled`

 `true`, um das Bit festzulegen; `false` , um das Bit zu unterlassen.

## <a name="exceptions"></a>Ausnahmen

## <a name="remarks"></a>Bemerkungen
 Der Debugger legt dieses Bit so fest, dass er aus einem asynchronen Methodentext herausspringt. Wenn `enabled` `true`dies der Fall ist, muss diese Methode nur für eine Aufgabe aufgerufen werden, die noch nicht abgeschlossen wurde. Wenn `enabled` `false`dies der Zeitpunkt ist, kann diese Methode für abgeschlossene Aufgaben aufgerufen werden. In beiden Fall sollte es nur für Aufgaben im Versprechenstil verwendet werden.

## <a name="requirements"></a>Requirements (Anforderungen)

## <a name="see-also"></a>Weitere Informationen
- [Task-Klasse](../../extensibility/debugger/task-class-internal-members.md)
