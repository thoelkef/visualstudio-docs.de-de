---
title: SetNotificationForWaitCompletion Methode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
caps.latest.revision: 5
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: f5e35933e59fb4d8ff9f13db4bef8c23891bac2f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="setnotificationforwaitcompletion-method"></a>SetNotificationForWaitCompletion-Methode
Aktiviert oder deaktiviert das TASK_STATE_WAIT_COMPLETION_NOTIFICATION Zustand Bit.  
  
 **Namespace:**<xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** "mscorlib" (in "mscorlib.dll")  
  
## <a name="syntax"></a>Syntax  
  
```vb  
internal void SetNotificationForWaitCompletion(bool enabled)  
```  
  
#### <a name="parameters"></a>Parameter  
 `enabled`  
  
 `true`Das Bit festgelegt; `false` zu Festlegung das Bit.  
  
## <a name="exceptions"></a>Ausnahmen  
  
## <a name="remarks"></a>Hinweise  
 Der Debugger setzt dieses Bit Schritt aus einer asynchronen Methodentext zu. Wenn `enabled` ist `true`, diese Methode muss aufgerufen werden, nur auf eine Aufgabe, die noch nicht abgeschlossen wurde. Wenn `enabled` ist `false`, diese Methode möglicherweise für abgeschlossene Aufgaben aufgerufen werden. In jedem Fall sollten sie nur für Promise-Stil Aufgaben verwendet werden.  
  
## <a name="requirements"></a>Anforderungen  
  
## <a name="see-also"></a>Siehe auch  
 [Task-Klasse](../../extensibility/debugger/task-class-internal-members.md)