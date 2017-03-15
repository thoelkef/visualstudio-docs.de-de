---
title: "Task-Klasse - interne Member | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Debugmodule, Task-Klasse [.NET Framework]"
  - "Task-Klasse [Debugmodule [.NET Framework]"
ms.assetid: 28e47c3b-9323-424a-80ac-6cc3bf19e09b
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Task-Klasse - interne Member
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

In diesem Thema wird beschrieben, die internen Member des der <xref:System.Threading.Tasks.Task?displayProperty=fullName> Klasse, mit denen Sie einen benutzerdefinierten Debugger implementieren. Allgemeine Informationen zu dieser Klasse finden Sie unter der <xref:System.Threading.Tasks.Task> Referenzthema.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** Mscorlib \(in "mscorlib.dll"\)  
  
 Da Sie diese interne Member von .NET Framework zugreifen können, wird die folgende Syntax gemeinsam Intermediate Language \(CIL\) bereitgestellt.  
  
## Syntax  
  
```  
.class public auto ansi System.Threading.Tasks.Task  
       extends System.Object  
       implements System.Threading.IThreadPoolWorkItem,  
                  System.IAsyncResult,  
                  System.IDisposable,  
                  System.Threading.ICancelableOperation  
```  
  
## Mitglieder  
  
### Methoden  
  
|Name|Beschreibung|  
|----------|------------------|  
|[SetNotificationForWaitCompletion\-Methode](../../extensibility/debugger/setnotificationforwaitcompletion-method.md)|Aktiviert oder deaktiviert das TASK\_STATE\_WAIT\_COMPLETION\_NOTIFICATION Zustand Bit.|  
|[NotifyDebuggerOfWaitCompletion\-Methode](../../extensibility/debugger/notifydebuggerofwaitcompletion-method.md)|Platzhalter\-Methode, die als haltepunktziel vom Debugger verwendet.|  
  
### Felder  
  
|Name|Beschreibung|  
|----------|------------------|  
|[m\_action](../../extensibility/debugger/m-action-field.md)|Der Delegat, der den Code zum Ausführen in der <xref:System.Threading.Tasks.Task> Objekt.|  
|[m\_contingentProperties](../../extensibility/debugger/m-contingentproperties-field.md)|Speichert zusätzliche Eigenschaften für die <xref:System.Threading.Tasks.Task> Objekt.|  
|[m\_Parent](../../extensibility/debugger/m-parent-field.md)|Das dahinter liegende Feld für die <xref:System.Threading.Tasks.Task?displayProperty=fullName> parent\-Eigenschaft.|  
|[m\_stateFlags](../../extensibility/debugger/m-stateflags-field.md)|Speichert Informationen über den aktuellen Status des der <xref:System.Threading.Tasks.Task> Objekt.|  
|[m\_stateObject](../../extensibility/debugger/m-stateobject-field.md)|Ein Objekt, das Daten darstellt, die von der Aktion verwendet werden.|  
|[m\_taskId](../../extensibility/debugger/m-taskid-field.md)|Das dahinter liegende Feld für die <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=fullName> Eigenschaft.|  
|[s\_taskIdCounter](../../extensibility/debugger/s-taskidcounter-field.md)|Den nächsten verfügbaren Bezeichner für ein <xref:System.Threading.Tasks.Task> Objekt.|  
|[TASK\_STATE\_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)|Gibt an, dass die Aufgabe abgebrochen wurde, bevor er den Ausführungsstatus erreicht oder die Aufgabe den Abbruch bestätigt und ohne Ausnahme abgeschlossen wurde.|  
|[TASK\_STATE\_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)|Gibt an, dass die Aufgabe ausgeführt wird.|  
|[TASK\_STATE\_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)|Gibt an, dass der Vorgang aufgrund einer nicht behandelten Ausnahme abgeschlossen.|  
|[TASK\_STATE\_RAN\_TO\_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)|Gibt an, dass die Aufgabe erfolgreich ausgeführt.|  
|[TASK\_STATE\_WAITING\_ON\_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)|Gibt an, dass die Aufgabe die Ausführung seines Delegaten beendet und wartet implizit angefügte untergeordnete Aufgaben beendet hat.|  
  
## Hinweise  
 Die folgenden internen Methoden sind nützlich, um ein Debugmodul, da sie den Zugang zu markieren <xref:System.Threading.Tasks.Task> code ausführen:  
  
-   `Execute`  
  
-   `ExecuteEntry`  
  
-   `ExecuteWithThreadLocal`  
  
-   `Finish`  
  
-   `InnerInvoke`  
  
-   `InternalWait`  
  
## Siehe auch  
 <xref:System.Threading.Tasks.Task?displayProperty=fullName>   
 [Parallelen Erweiterung Internals für .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)