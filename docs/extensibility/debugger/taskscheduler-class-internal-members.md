---
title: TaskScheduler-Klasse – interne Member | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TaskScheduler class [.NET Framework debug engines]
- debug engines, TaskScheduler class [.NET Framework]
ms.assetid: 87f1c969-0217-4464-8907-7609c1bf61d3
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1801bc087311170169c752af8b50de4cd4e01da6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54926838"
---
# <a name="taskscheduler-class---internal-members"></a>TaskScheduler-Klasse – interne Member
In diesem Artikel wird beschrieben, die internen Member des der <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> implementieren einen benutzerdefinierten Debugger-Klasse, die Ihnen helfen. Allgemeine Informationen zu dieser Klasse finden Sie unter den <xref:System.Threading.Tasks.TaskScheduler> Referenzartikel.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** "mscorlib" (in *"mscorlib.dll"*)  
  
 Da Sie diese internen Member von .NET Framework zugreifen können, wird die folgende Syntax in Common Intermediate Language (CIL) bereitgestellt.  
  
## <a name="syntax"></a>Syntax  
  
```csharp  
.class public abstract auto ansi beforefieldinit System.Threading.Tasks.TaskScheduler  
       extends System.Object  
```  
  
## <a name="members"></a>Member  
  
### <a name="methods"></a>Methoden  
  
|Name|Beschreibung|  
|----------|-----------------|  
|[GetScheduledTasksForDebugger](../../extensibility/debugger/getscheduledtasksfordebugger-method.md)|Ruft ein Array aller geplanten Aufgaben.|  
|[GetTaskSchedulersForDebugger](../../extensibility/debugger/gettaskschedulersfordebugger-method.md)|Ruft ein Array aller <xref:System.Threading.Tasks.TaskScheduler> Objekte, die zurzeit aktiv sind.|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>   
 [Merkmale von parallelen Erweiterung für .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)