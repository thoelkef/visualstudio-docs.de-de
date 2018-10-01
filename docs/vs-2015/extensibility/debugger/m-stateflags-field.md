---
title: M_stateFlags-Feld | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- m_stateFlags field, Task class [.NET Framework debug engines]
ms.assetid: 82b20efc-08f2-4cd2-91f6-4e01e3da906b
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1e95457198232493518db2ff44feb53e1b4a28ba
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47516043"
---
# <a name="mstateflags-field"></a>m_stateFlags-Feld
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [M_stateFlags-Feld](https://docs.microsoft.com/visualstudio/extensibility/debugger/m-stateflags-field).  
  
Speichert Informationen zu den aktuellen Zustand des der <xref:System.Threading.Tasks.Task> Objekt.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** "mscorlib" (in "mscorlib.dll")  
  
 Da Sie diesen internen Member von .NET Framework zugreifen können, wird die folgende Syntax in Common Intermediate Language (CIL) bereitgestellt.  
  
## <a name="syntax"></a>Syntax  
  
```  
.field assembly int32 modreq(System.Runtime.CompilerServices.IsVolatile) m_stateFlags  
```  
  
## <a name="remarks"></a>Hinweise  
 In der Regel die <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=fullName> Eigenschaft, um diesen Wert zugreifen.  
  
 Dieser Member kann eine beliebige Kombination der folgenden Werte sein:  
  
-   [TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)  
  
-   [TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)  
  
-   [TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)  
  
-   [TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)  
  
-   [TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Aufgabenklasse](../../extensibility/debugger/task-class-internal-members.md)

