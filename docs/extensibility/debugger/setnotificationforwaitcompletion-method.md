---
title: SetNotificationForWaitCompletion Methode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a005ee7d624604dd716042bd839b48b7a367dd48
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="setnotificationforwaitcompletion-method"></a>SetNotificationForWaitCompletion-Methode
Aktiviert oder deaktiviert das TASK_STATE_WAIT_COMPLETION_NOTIFICATION Zustand Bit.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** "mscorlib" (in "mscorlib.dll")  
  
## <a name="syntax"></a>Syntax  
  
```vb  
internal void SetNotificationForWaitCompletion(bool enabled)  
```  
  
#### <a name="parameters"></a>Parameter  
 `enabled`  
  
 `true` Das Bit festgelegt; `false` zu Festlegung das Bit.  
  
## <a name="exceptions"></a>Ausnahmen  
  
## <a name="remarks"></a>Hinweise  
 Der Debugger setzt dieses Bit Schritt aus einer asynchronen Methodentext zu. Wenn `enabled` ist `true`, diese Methode muss aufgerufen werden, nur auf eine Aufgabe, die noch nicht abgeschlossen wurde. Wenn `enabled` ist `false`, diese Methode möglicherweise für abgeschlossene Aufgaben aufgerufen werden. In jedem Fall sollten sie nur für Promise-Stil Aufgaben verwendet werden.  
  
## <a name="requirements"></a>Anforderungen  
  
## <a name="see-also"></a>Siehe auch  
 [Task-Klasse](../../extensibility/debugger/task-class-internal-members.md)