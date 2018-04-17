---
title: Parallele Erweiterung Mechanismen für das .NET Framework | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, internals [.NET Framework]
ms.assetid: 93e07cfa-91fa-464c-b866-8bf5570411df
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4936efe50023ed1e193d0c2ec0d9c3423ac5cc64
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="parallel-extension-internals-for-the-net-framework"></a>Parallele Erweiterung Internals für .NET Framework
In diesem Abschnitt wird beschrieben, die internen Typen, Methoden und Felder von Klassen, mit denen Sie implementieren einen benutzerdefinierte Debugger für die parallele Erweiterungen für .NET Framework.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Task-Klasse](../../extensibility/debugger/task-class-internal-members.md)  
 Beschreibt die interne Datenmember von der <xref:System.Threading.Tasks.Task?displayProperty=fullName> Klasse.  
  
 [TaskScheduler-Klasse](../../extensibility/debugger/taskscheduler-class-internal-members.md)  
 Beschreibt die interne Datenmember von der <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> Klasse.  
  
 [ContingentProperties-Klasse](../../extensibility/debugger/contingentproperties-class-internal-members.md)  
 Beschreibt die interne Datenmember von der `System.Threading.Tasks.ContingentProperties` Klasse.  
  
 [AsyncTaskMethodBuilder-Struktur](../../extensibility/debugger/asynctaskmethodbuilder-structure-internal-members.md)  
 Beschreibt die internen Member des der <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> Struktur.  
  
 [AsyncTaskMethodBuilder\<TResult > Struktur](../../extensibility/debugger/asynctaskmethodbuilder-tresult-structure-internal-members.md)  
 Beschreibt die internen Member des der <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> Struktur.  
  
 [AsyncVoidMethodBuilder-Struktur](../../extensibility/debugger/asyncvoidmethodbuilder-structure-internal-members.md)  
 Beschreibt die internen Member des der <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> Struktur.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Threading.Tasks.Task?displayProperty=fullName>   
 <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>   
 [Visual Studio-Debugger-Erweiterbarkeit](../../extensibility/debugger/visual-studio-debugger-extensibility.md)   
 [Parallele Programmierung](/dotnet/standard/parallel-programming/index)