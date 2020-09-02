---
title: 'TaskScheduler-Klasse: interne Member | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- TaskScheduler class [.NET Framework debug engines]
- debug engines, TaskScheduler class [.NET Framework]
ms.assetid: 87f1c969-0217-4464-8907-7609c1bf61d3
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 427a84b3dcda0471f5ec9d71883a5a8e859bb92d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68176697"
---
# <a name="taskscheduler-class---internal-members"></a>TaskScheduler-Klasse – interne Member
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In diesem Thema werden die internen Member der- <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> Klasse beschrieben, die Ihnen bei der Implementierung eines benutzerdefinierten Debuggers helfen. Allgemeine Informationen zu dieser Klasse finden Sie im <xref:System.Threading.Tasks.TaskScheduler> Referenz Thema.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (in mscorlib.dll)  
  
 Da Sie nicht auf diese internen Member vom .NET Framework aus zugreifen können, wird die folgende Syntax in Common Intermediate Language (CIL) bereitgestellt.  
  
## <a name="syntax"></a>Syntax  
  
```  
.class public abstract auto ansi beforefieldinit System.Threading.Tasks.TaskScheduler  
       extends System.Object  
```  
  
## <a name="members"></a>Member  
  
### <a name="methods"></a>Methoden  
  
|Name|Beschreibung|  
|----------|-----------------|  
|[GetScheduledTasksForDebugger](../../extensibility/debugger/getscheduledtasksfordebugger-method.md)|Ruft ein Array aller geplanten Tasks ab.|  
|[Gettaskschedulersfordebugger](../../extensibility/debugger/gettaskschedulersfordebugger-method.md)|Ruft ein Array aller- <xref:System.Threading.Tasks.TaskScheduler> Objekte ab, die derzeit aktiv sind.|  
  
## <a name="remarks"></a>Bemerkungen  
  
## <a name="see-also"></a>Weitere Informationen  
 <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>   
 [Interne Elemente der parallelen Erweiterung für das .NET-Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
