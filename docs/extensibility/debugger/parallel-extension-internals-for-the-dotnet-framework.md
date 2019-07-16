---
title: Parallele Erweiterung-Interna für .NET Framework | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, internals [.NET Framework]
ms.assetid: 93e07cfa-91fa-464c-b866-8bf5570411df
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1ecc13be90259c68fa4d37daa5139b27b4ea8c7f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351484"
---
# <a name="parallel-extension-internals-for-the-net-framework"></a>Merkmale von parallelen Erweiterung für .NET Framework
In diesem Abschnitt wird beschrieben, die internen Typen, Methoden und Felder von Klassen, mit denen Sie einen benutzerdefinierten Debugger für die parallelerweiterungen für .NET Framework zu implementieren.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Task-Klasse](../../extensibility/debugger/task-class-internal-members.md) beschreibt die Elemente der internen Daten von der <xref:System.Threading.Tasks.Task?displayProperty=fullName> Klasse.

 [TaskScheduler-Klasse](../../extensibility/debugger/taskscheduler-class-internal-members.md) beschreibt die Elemente der internen Daten von der <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> Klasse.

 [ContingentProperties-Klasse](../../extensibility/debugger/contingentproperties-class-internal-members.md) beschreibt die Elemente der internen Daten von der `System.Threading.Tasks.ContingentProperties` Klasse.

 [AsyncTaskMethodBuilder-Struktur](../../extensibility/debugger/asynctaskmethodbuilder-structure-internal-members.md) wird beschrieben, die internen Member des der <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> Struktur.

 [AsyncTaskMethodBuilder\<TResult >-Struktur](../../extensibility/debugger/asynctaskmethodbuilder-tresult-structure-internal-members.md) wird beschrieben, die internen Member des der <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> Struktur.

 [AsyncVoidMethodBuilder-Struktur](../../extensibility/debugger/asyncvoidmethodbuilder-structure-internal-members.md) wird beschrieben, die internen Member des der <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> Struktur.

## <a name="see-also"></a>Siehe auch
- <xref:System.Threading.Tasks.Task?displayProperty=fullName>
- <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>
- [Visual Studio-Debugger-Erweiterbarkeit](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
- [Parallele Programmierung](/dotnet/standard/parallel-programming/index)