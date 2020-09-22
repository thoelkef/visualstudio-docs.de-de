---
title: Aufgaben Klasse-interne Member | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, Task class [.NET Framework]
- Task class [.NET Framework debug engines]
ms.assetid: 28e47c3b-9323-424a-80ac-6cc3bf19e09b
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ef0cd907c25a90ee90e3ed23a773d0ae8ba0ce1f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840921"
---
# <a name="task-class---internal-members"></a>Task-Klasse – interne Member
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In diesem Thema werden die internen Member der- <xref:System.Threading.Tasks.Task?displayProperty=fullName> Klasse beschrieben, die Ihnen bei der Implementierung eines benutzerdefinierten Debuggers helfen. Allgemeine Informationen zu dieser Klasse finden Sie im <xref:System.Threading.Tasks.Task> Referenz Thema.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (in mscorlib.dll)  
  
 Da Sie nicht auf diese internen Member vom .NET Framework aus zugreifen können, wird die folgende Syntax in Common Intermediate Language (CIL) bereitgestellt.  
  
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
  
|Name|BESCHREIBUNG|  
|----------|-----------------|  
|[SetNotificationForWaitCompletion-Methode](../../extensibility/debugger/setnotificationforwaitcompletion-method.md)|Legt das TASK_STATE_WAIT_COMPLETION_NOTIFICATION Zustands Bit fest oder löscht dieses.|  
|[NotifyDebuggerOfWaitCompletion-Methode](../../extensibility/debugger/notifydebuggerofwaitcompletion-method.md)|Die Platzhalter Methode, die vom Debugger als Haltepunkt Ziel verwendet wird.|  
  
### <a name="fields"></a>Felder  
  
|Name|BESCHREIBUNG|  
|----------|-----------------|  
|[m_action](../../extensibility/debugger/m-action-field.md)|Der Delegat, der den Code darstellt, der im-Objekt ausgeführt werden soll <xref:System.Threading.Tasks.Task> .|  
|[m_contingentProperties](../../extensibility/debugger/m-contingentproperties-field.md)|Speichert zusätzliche Eigenschaften des- <xref:System.Threading.Tasks.Task> Objekts.|  
|[m_parent](../../extensibility/debugger/m-parent-field.md)|Das Unterstützungs Feld für die über <xref:System.Threading.Tasks.Task?displayProperty=fullName> geordnete Eigenschaft.|  
|[m_stateFlags](../../extensibility/debugger/m-stateflags-field.md)|Speichert Informationen zum aktuellen Zustand des <xref:System.Threading.Tasks.Task> Objekts.|  
|[m_stateObject](../../extensibility/debugger/m-stateobject-field.md)|Ein-Objekt, das Daten darstellt, die von der Aktion verwendet werden.|  
|[m_taskId](../../extensibility/debugger/m-taskid-field.md)|Das Unterstützungs Feld für die- <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=fullName> Eigenschaft.|  
|[s_taskIdCounter](../../extensibility/debugger/s-taskidcounter-field.md)|Der nächste verfügbare Bezeichner für ein- <xref:System.Threading.Tasks.Task> Objekt.|  
|[TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)|Gibt an, dass der Task abgebrochen wurde, bevor er den Ausführungs Status erreicht hat, oder dass der Task seinen Abbruch bestätigt und ohne Ausnahme abgeschlossen hat.|  
|[TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)|Gibt an, dass die Aufgabe ausgeführt wird.|  
|[TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)|Gibt an, dass der Task aufgrund einer nicht behandelten Ausnahme abgeschlossen wurde.|  
|[TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)|Gibt an, dass die Ausführung der Aufgabe erfolgreich abgeschlossen wurde.|  
|[TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)|Gibt an, dass der Task die Ausführung seines Delegaten abgeschlossen hat, und wartet implizit auf den Abschluss angefügter untergeordneter Aufgaben.|  
  
## <a name="remarks"></a>Bemerkungen  
 Die folgenden internen Methoden sind für eine Debugger-Engine nützlich, da Sie den Eingang zur <xref:System.Threading.Tasks.Task> Codeausführung markieren:  
  
- `Execute`  
  
- `ExecuteEntry`  
  
- `ExecuteWithThreadLocal`  
  
- `Finish`  
  
- `InnerInvoke`  
  
- `InternalWait`  
  
## <a name="see-also"></a>Weitere Informationen  
 <xref:System.Threading.Tasks.Task?displayProperty=fullName>   
 [Interne Elemente der parallelen Erweiterung für das .NET-Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
