---
title: Parallele Erweiterungsinterne für .NET Framework | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, internals [.NET Framework]
ms.assetid: 93e07cfa-91fa-464c-b866-8bf5570411df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6a3583e94a0bfff4474db03aa9d083add921f3da
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738272"
---
# <a name="parallel-extension-internals-for-the-net-framework"></a>Parallele Erweiterungsinterne für .NET Framework
In diesem Abschnitt werden die internen Typen, Methoden und Klassenfelder beschrieben, mit denen Sie einen benutzerdefinierten Debugger für die parallelen Erweiterungen von .NET Framework implementieren können.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Task-Klasse](../../extensibility/debugger/task-class-internal-members.md) Beschreibt die internen Datenmember der <xref:System.Threading.Tasks.Task?displayProperty=fullName> Klasse.

 [TaskScheduler-Klasse](../../extensibility/debugger/taskscheduler-class-internal-members.md) Beschreibt die internen Datenmember der <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> Klasse.

 [ContingentProperties-Klasse](../../extensibility/debugger/contingentproperties-class-internal-members.md) Beschreibt die internen Datenmember der `System.Threading.Tasks.ContingentProperties` Klasse.

 [AsyncTaskMethodBuilder-Struktur](../../extensibility/debugger/asynctaskmethodbuilder-structure-internal-members.md) Beschreibt die internen <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> Elemente der Struktur.

 [AsyncTaskMethodBuilder\<TResult> Struktur](../../extensibility/debugger/asynctaskmethodbuilder-tresult-structure-internal-members.md) Beschreibt <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> die internen Member der Struktur.

 [AsyncVoidMethodBuilder-Struktur](../../extensibility/debugger/asyncvoidmethodbuilder-structure-internal-members.md) Beschreibt die internen <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> Elemente der Struktur.

## <a name="see-also"></a>Weitere Informationen
- <xref:System.Threading.Tasks.Task?displayProperty=fullName>
- <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>
- [Erweiterbarkeit des Visual Studio-Debuggers](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
- [Parallele Programmierung](/dotnet/standard/parallel-programming/index)
