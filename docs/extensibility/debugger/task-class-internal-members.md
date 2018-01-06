---
title: Aufgabenklasse - interne Member | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, Task class [.NET Framework]
- Task class [.NET Framework debug engines]
ms.assetid: 28e47c3b-9323-424a-80ac-6cc3bf19e09b
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: b92a622b6b898c917710ac748b9205079d71ea5e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="task-class---internal-members"></a>Aufgabenklasse - interne Member
In diesem Thema wird beschrieben, die internen Member des der <xref:System.Threading.Tasks.Task?displayProperty=fullName> Klasse, mit denen Sie einen benutzerdefinierten Debugger zu implementieren. Allgemeine Informationen zu dieser Klasse finden Sie unter der <xref:System.Threading.Tasks.Task> Referenzthema.  
  
 **Namespace:**<xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** "mscorlib" (in "mscorlib.dll")  
  
 Da diese internen Member von .NET Framework zugegriffen werden kann, wird die folgende Syntax gemeinsame Intermediate Language (CIL) bereitgestellt.  
  
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
|[SetNotificationForWaitCompletion-Methode](../../extensibility/debugger/setnotificationforwaitcompletion-method.md)|Aktiviert oder deaktiviert das TASK_STATE_WAIT_COMPLETION_NOTIFICATION Zustand Bit.|  
|[NotifyDebuggerOfWaitCompletion-Methode](../../extensibility/debugger/notifydebuggerofwaitcompletion-method.md)|Platzhalter-Methode, die als Ziel der Haltepunkt vom Debugger verwendet.|  
  
### <a name="fields"></a>Felder  
  
|name|Beschreibung|  
|----------|-----------------|  
|[m_action](../../extensibility/debugger/m-action-field.md)|Der Delegat, der den auszuführenden in Code stellt die <xref:System.Threading.Tasks.Task> Objekt.|  
|[m_contingentProperties](../../extensibility/debugger/m-contingentproperties-field.md)|Speichert zusätzliche Eigenschaften für die <xref:System.Threading.Tasks.Task> Objekt.|  
|[m_Parent](../../extensibility/debugger/m-parent-field.md)|Das dahinter liegende Feld für die <xref:System.Threading.Tasks.Task?displayProperty=fullName> parent-Eigenschaft.|  
|[m_stateFlags](../../extensibility/debugger/m-stateflags-field.md)|Speichert Informationen über den aktuellen Status des der <xref:System.Threading.Tasks.Task> Objekt.|  
|[m_stateObject](../../extensibility/debugger/m-stateobject-field.md)|Ein Objekt, das Daten darstellt, die von der Aktion verwendet werden soll.|  
|[m_taskId](../../extensibility/debugger/m-taskid-field.md)|Das dahinter liegende Feld für die <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=fullName> Eigenschaft.|  
|[s_taskIdCounter](../../extensibility/debugger/s-taskidcounter-field.md)|Der nächste verfügbare Bezeichner für eine <xref:System.Threading.Tasks.Task> Objekt.|  
|[TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)|Gibt an, dass die Aufgabe abgebrochen wurde, bevor er den Ausführungsstatus erreicht oder die Aufgabe hat den dessen Abbruch und ohne Ausnahme abgeschlossen wurde.|  
|[TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)|Gibt an, dass die Aufgabe ausgeführt wird.|  
|[TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)|Gibt an, dass die Aufgabe aufgrund eines Ausnahmefehlers abgeschlossen.|  
|[TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)|Gibt an, dass der Task die Ausführung erfolgreich abgeschlossen.|  
|[TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)|Gibt an, dass die Aufgabe die Ausführung seines Delegaten beendet und wartet implizit angefügte untergeordnete Aufgaben beendet hat.|  
  
## <a name="remarks"></a>Hinweise  
 Die folgenden internen Methoden sind nützlich, um ein Debugmodul, da ihnen der Eingang zu gekennzeichneten <xref:System.Threading.Tasks.Task> code Ausführung:  
  
-   `Execute`  
  
-   `ExecuteEntry`  
  
-   `ExecuteWithThreadLocal`  
  
-   `Finish`  
  
-   `InnerInvoke`  
  
-   `InternalWait`  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Threading.Tasks.Task?displayProperty=fullName>   
 [Interne Elemente der parallelen Erweiterung für das .NET-Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)