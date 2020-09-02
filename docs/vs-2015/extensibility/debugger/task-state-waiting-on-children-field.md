---
title: TASK_STATE_WAITING_ON_CHILDREN Feld | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_WAITING_ON_CHILDREN field, Task class [.NET Framework debug engines]
ms.assetid: 6f26b098-84ad-4f6e-ba27-6136581ba630
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e2dfb7ca683b7a05151539feda92a2575197b189
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68176716"
---
# <a name="task_state_waiting_on_children-field"></a>TASK_STATE_WAITING_ON_CHILDREN-Feld
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Der Task hat das Ausführen seines Delegaten abgeschlossen und wartet implizit auf den Abschluss angefügter untergeordneter Aufgaben.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (in mscorlib.dll)  
  
 Da Sie nicht auf dieses interne Element vom .NET Framework aus zugreifen können, wird die folgende Syntax in Common Intermediate Language (CIL) bereitgestellt.  
  
## <a name="syntax"></a>Syntax  
  
```  
.field static assembly literal int32 TASK_STATE_WAITING_ON_CHILDREN = int32(0x01000000)  
```  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn das [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) -Feld diesen Wert enthält, <xref:System.Threading.Tasks.Task.Status%2A> gibt die-Eigenschaft zurück <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName> .  
  
## <a name="see-also"></a>Weitere Informationen  
 [Task-Klasse](../../extensibility/debugger/task-class-internal-members.md)
