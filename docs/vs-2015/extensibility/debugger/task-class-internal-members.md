---
title: Task-Klasse – interne Member | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debug engines, Task class [.NET Framework]
- Task class [.NET Framework debug engines]
ms.assetid: 28e47c3b-9323-424a-80ac-6cc3bf19e09b
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 92ddc4b00f9d8eb37893e1db7ae44802e04e9c46
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51764828"
---
# <a name="task-class---internal-members"></a>Task-Klasse – interne Member
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In diesem Thema wird beschrieben, die internen Member des der <xref:System.Threading.Tasks.Task?displayProperty=fullName> implementieren einen benutzerdefinierten Debugger-Klasse, die Ihnen helfen. Allgemeine Informationen zu dieser Klasse finden Sie unter den <xref:System.Threading.Tasks.Task> Referenzthema.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** "mscorlib" (in "mscorlib.dll")  
  
 Da Sie diese internen Member von .NET Framework zugreifen können, wird die folgende Syntax in Common Intermediate Language (CIL) bereitgestellt.  
  
## <a name="syntax"></a>Syntax  
  
```  
.class public auto ansi System.Threading.Tasks.Task  
       extends System.Object  
       implements System.Threading.IThreadPoolWorkItem,  
                  System.IAsyncResult,  
                  System.IDisposable,  
                  System.Threading.ICancelableOperation  
```  
  
## <a name="members"></a>Member  
  
### <a name="methods"></a>Methoden  
  
|Name|Beschreibung|  
|----------|-----------------|  
|[SetNotificationForWaitCompletion-Methode](../../extensibility/debugger/setnotificationforwaitcompletion-method.md)|Legt fest oder löscht das TASK_STATE_WAIT_COMPLETION_NOTIFICATION Zustand Bit.|  
|[NotifyDebuggerOfWaitCompletion-Methode](../../extensibility/debugger/notifydebuggerofwaitcompletion-method.md)|Platzhalter-Methode, die als Ziel der Haltepunkt vom Debugger verwendet.|  
  
### <a name="fields"></a>Felder  
  
|name|Beschreibung|  
|----------|-----------------|  
|[m_action](../../extensibility/debugger/m-action-field.md)|Der Delegat, der den auszuführenden in Code stellt dar, die <xref:System.Threading.Tasks.Task> Objekt.|  
|[m_contingentProperties](../../extensibility/debugger/m-contingentproperties-field.md)|Speichert zusätzliche Eigenschaften für die <xref:System.Threading.Tasks.Task> Objekt.|  
|[m_Parent](../../extensibility/debugger/m-parent-field.md)|Das dahinter liegende Feld für die <xref:System.Threading.Tasks.Task?displayProperty=fullName> parent-Eigenschaft.|  
|[m_stateFlags](../../extensibility/debugger/m-stateflags-field.md)|Speichert Informationen zu den aktuellen Zustand des der <xref:System.Threading.Tasks.Task> Objekt.|  
|[m_stateObject](../../extensibility/debugger/m-stateobject-field.md)|Ein Objekt, das Daten darstellt, die von der Aktion verwendet werden.|  
|[m_taskId](../../extensibility/debugger/m-taskid-field.md)|Das dahinter liegende Feld für die <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=fullName> Eigenschaft.|  
|[s_taskIdCounter](../../extensibility/debugger/s-taskidcounter-field.md)|Der nächste verfügbare Bezeichner für eine <xref:System.Threading.Tasks.Task> Objekt.|  
|[TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)|Gibt an, dass der Task abgebrochen wurde, bevor sie den Ausführungsstatus erreicht oder die Aufgabe der Abbruch bestätigt und ohne Ausnahme abgeschlossen wurde.|  
|[TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)|Gibt an, dass die Aufgabe ausgeführt wird.|  
|[TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)|Gibt an, dass die Aufgabe aufgrund eines Ausnahmefehlers abgeschlossen.|  
|[TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)|Gibt an, dass der Task die Ausführung erfolgreich abgeschlossen.|  
|[TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)|Gibt an, dass die Aufgabe der Delegat Ausführung abgeschlossen hat, und implizit wartet auf den Abschluss angefügter untergeordneter Aufgaben.|  
  
## <a name="remarks"></a>Hinweise  
 Die folgenden internen Methoden sind nützlich, um ein Debugmodul, da sie zu "entrance" zu markieren <xref:System.Threading.Tasks.Task> code Ausführung:  
  
-   `Execute`  
  
-   `ExecuteEntry`  
  
-   `ExecuteWithThreadLocal`  
  
-   `Finish`  
  
-   `InnerInvoke`  
  
-   `InternalWait`  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Threading.Tasks.Task?displayProperty=fullName>   
 [Interne Elemente der parallelen Erweiterung für das .NET-Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)

