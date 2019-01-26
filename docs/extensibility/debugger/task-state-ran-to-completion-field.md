---
title: TASK_STATE_RAN_TO_COMPLETION-Feld | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_RAN_TO_COMPLETION field, Task class [.NET Framework debug engines]
ms.assetid: 0f4830af-fe0c-4141-b768-817f4e426b8c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ea3a68237b82873cc4c6646957832beb8880dcac
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55001372"
---
# <a name="taskstaterantocompletion-field"></a>TASK_STATE_RAN_TO_COMPLETION-Feld
Die Ausführung der Aufgabe wurde erfolgreich abgeschlossen.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** "mscorlib" (in *"mscorlib.dll"*)  
  
 Da Sie diesen internen Member von .NET Framework zugreifen können, wird die folgende Syntax in Common Intermediate Language (CIL) bereitgestellt.  
  
## <a name="syntax"></a>Syntax  
  
```csharp  
.field static assembly literal int32 TASK_STATE_RAN_TO_COMPLETION = int32(0x02000000)  
```  
  
## <a name="remarks"></a>Hinweise  
 Wenn die [M_stateFlags](../../extensibility/debugger/m-stateflags-field.md) Feld enthält diesen Wert, der <xref:System.Threading.Tasks.Task.Status%2A> -Eigenschaft gibt <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>.  
  
## <a name="see-also"></a>Siehe auch  
 [Task class (Task-Klasse)](../../extensibility/debugger/task-class-internal-members.md)