---
title: Task-Klasse – interne Member | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, Task class [.NET Framework]
- Task class [.NET Framework debug engines]
ms.assetid: 28e47c3b-9323-424a-80ac-6cc3bf19e09b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 34c8da8d661dcb0a8096576617403209a0a70c56
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53872790"
---
# <a name="task-class---internal-members"></a>Task-Klasse – interne Member
In diesem Artikel wird beschrieben, die internen Member des der <xref:System.Threading.Tasks.Task?displayProperty=fullName> implementieren einen benutzerdefinierten Debugger-Klasse, die Ihnen helfen. Allgemeine Informationen zu dieser Klasse finden Sie unter den <xref:System.Threading.Tasks.Task> Referenzartikel.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** "mscorlib" (in *"mscorlib.dll"*)  
  
 Da Sie diese internen Member von .NET Framework zugreifen können, wird die folgende Syntax in Common Intermediate Language (CIL) bereitgestellt.  
  
## <a name="syntax"></a>Syntax  
  
```csharp  
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
|[TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)|Gibt an, dass die Aufgabe abgebrochen wird, bevor sie den Ausführungsstatus erreicht oder die Aufgabe der Abbruch bestätigt und ohne Ausnahme abgeschlossen wurde.|  
|[TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)|Gibt an, dass die Aufgabe ausgeführt wird.|  
|[TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)|Gibt an, dass die Aufgabe aufgrund eines Ausnahmefehlers abgeschlossen.|  
|[TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)|Gibt an, dass der Task die Ausführung erfolgreich abgeschlossen.|  
|[TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)|Gibt an, dass die Aufgabe, die der Delegat Ausführung beendet und implizit wartet auf den Abschluss angefügter untergeordneter Aufgaben.|  
  
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
 [Merkmale von parallelen Erweiterung für .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)