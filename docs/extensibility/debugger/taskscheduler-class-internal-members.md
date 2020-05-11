---
title: TaskScheduler-Klasse - Interne Mitglieder | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TaskScheduler class [.NET Framework debug engines]
- debug engines, TaskScheduler class [.NET Framework]
ms.assetid: 87f1c969-0217-4464-8907-7609c1bf61d3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a53abc8b24edb06445c23c19744d00d50de8735d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712570"
---
# <a name="taskscheduler-class---internal-members"></a>TaskScheduler-Klasse - Interne Member
In diesem Artikel werden <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> die internen Member der Klasse beschrieben, die Sie beim Implementieren eines benutzerdefinierten Debuggers unterstützen. Allgemeine Informationen zu dieser Klasse <xref:System.Threading.Tasks.TaskScheduler> finden Sie im Referenzartikel.

 **Namespace:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Baugruppe:** mscorlib (in *mscorlib.dll*)

 Da Sie über .NET Framework nicht auf diese internen Member zugreifen können, wird die folgende Syntax in Common Intermediate Language (CIL) bereitgestellt.

## <a name="syntax"></a>Syntax

```csharp
.class public abstract auto ansi beforefieldinit System.Threading.Tasks.TaskScheduler
       extends System.Object
```

## <a name="members"></a>Member

### <a name="methods"></a>Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[GetScheduledTasksForDebugger](../../extensibility/debugger/getscheduledtasksfordebugger-method.md)|Ruft ein Array aller geplanten Aufgaben ab.|
|[GetTaskSchedulersForDebugger](../../extensibility/debugger/gettaskschedulersfordebugger-method.md)|Ruft ein Array <xref:System.Threading.Tasks.TaskScheduler> aller Objekte ab, die derzeit aktiv sind.|

## <a name="remarks"></a>Bemerkungen

## <a name="see-also"></a>Weitere Informationen
- <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>
- [Parallele Erweiterungsinterne für .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
