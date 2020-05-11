---
title: Aufgabenklasse - Interne Mitglieder | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, Task class [.NET Framework]
- Task class [.NET Framework debug engines]
ms.assetid: 28e47c3b-9323-424a-80ac-6cc3bf19e09b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dcf278c0248b344cea4be7cf161ecc91581f5f2e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712736"
---
# <a name="task-class---internal-members"></a>Aufgabenklasse - interne Member
In diesem Artikel werden <xref:System.Threading.Tasks.Task?displayProperty=fullName> die internen Member der Klasse beschrieben, die Sie beim Implementieren eines benutzerdefinierten Debuggers unterstützen. Allgemeine Informationen zu dieser Klasse <xref:System.Threading.Tasks.Task> finden Sie im Referenzartikel.

 **Namespace:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Baugruppe:** mscorlib (in *mscorlib.dll*)

 Da Sie über .NET Framework nicht auf diese internen Member zugreifen können, wird die folgende Syntax in Common Intermediate Language (CIL) bereitgestellt.

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

|Name|BESCHREIBUNG|
|----------|-----------------|
|[SetNotificationForWaitCompletion-Methode](../../extensibility/debugger/setnotificationforwaitcompletion-method.md)|Legt das TASK_STATE_WAIT_COMPLETION_NOTIFICATION-Statusbit fest oder löscht es.|
|[NotifyDebuggerOfWaitCompletion-Methode](../../extensibility/debugger/notifydebuggerofwaitcompletion-method.md)|Platzhaltermethode, die vom Debugger als Haltepunktziel verwendet wird.|

### <a name="fields"></a>Felder

|Name|BESCHREIBUNG|
|----------|-----------------|
|[m_action](../../extensibility/debugger/m-action-field.md)|Der Delegat, der den <xref:System.Threading.Tasks.Task> Code darstellt, der im Objekt ausgeführt werden soll.|
|[m_contingentProperties](../../extensibility/debugger/m-contingentproperties-field.md)|Speichert zusätzliche Eigenschaften <xref:System.Threading.Tasks.Task> des Objekts.|
|[m_parent](../../extensibility/debugger/m-parent-field.md)|Das Sicherungsfeld <xref:System.Threading.Tasks.Task?displayProperty=fullName> für die übergeordnete Eigenschaft.|
|[m_stateFlags](../../extensibility/debugger/m-stateflags-field.md)|Speichert Informationen über den <xref:System.Threading.Tasks.Task> aktuellen Status des Objekts.|
|[m_stateObject](../../extensibility/debugger/m-stateobject-field.md)|Ein Objekt, das Daten darstellt, die von der Aktion verwendet werden.|
|[m_taskId](../../extensibility/debugger/m-taskid-field.md)|Das Sicherungsfeld <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=fullName> für die Eigenschaft.|
|[s_taskIdCounter](../../extensibility/debugger/s-taskidcounter-field.md)|Der nächste verfügbare <xref:System.Threading.Tasks.Task> Bezeichner für ein Objekt.|
|[TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)|Gibt an, dass die Aufgabe abgebrochen wurde, bevor sie den ausgeführten Status erreichte, oder dass die Aufgabe ihren Abbruch bestätigt und ausnahmslos abgeschlossen hat.|
|[TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)|Gibt an, dass die Aufgabe ausgeführt wird.|
|[TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)|Gibt an, dass die Aufgabe aufgrund einer nicht behandelten Ausnahme abgeschlossen wurde.|
|[TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)|Gibt an, dass die Ausführung der Aufgabe erfolgreich abgeschlossen wurde.|
|[TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)|Gibt an, dass die Aufgabe die Ausführung des Delegaten abgeschlossen hat und implizit darauf wartet, dass angefügte untergeordnete Aufgaben abgeschlossen sind.|

## <a name="remarks"></a>Bemerkungen
 Die folgenden internen Methoden sind für ein Debuggermodul <xref:System.Threading.Tasks.Task> nützlich, da sie den Eingang zur Codeausführung markieren:

- `Execute`

- `ExecuteEntry`

- `ExecuteWithThreadLocal`

- `Finish`

- `InnerInvoke`

- `InternalWait`

## <a name="see-also"></a>Weitere Informationen
- <xref:System.Threading.Tasks.Task?displayProperty=fullName>
- [Parallele Erweiterungsinterne für .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
