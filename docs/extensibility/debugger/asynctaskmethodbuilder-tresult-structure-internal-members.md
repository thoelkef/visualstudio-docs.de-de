---
title: AsyncTaskMethodBuilder&lt;TResult&gt; Struktur – interne Member | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- AsyncTaskMethodBuilder<TResult> structure [.NET Framework debug engines]
- debug engines, AsyncTaskMethodBuilder<TResult> structure [.NET Framework]
ms.assetid: 17ebc340-8170-4aff-bf54-dc4548c83632
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c944671b3bdb42f72928822903ccb05742401f7e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350975"
---
# <a name="asynctaskmethodbuilderlttresultgt-structure---internal-members"></a>AsyncTaskMethodBuilder&lt;TResult&gt; Struktur – interne Member
In diesem Thema wird beschrieben, die internen Member des der <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> Klasse. Allgemeine Informationen zu dieser Klasse finden Sie unter den <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> Referenzthema.

 **Namespace:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **Assembly:** "mscorlib" (in "mscorlib.dll")

 Da Sie diese internen Member von .NET Framework zugreifen können, wird die folgende Syntax in Common Intermediate Language (CIL) bereitgestellt.

## <a name="syntax"></a>Syntax

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder`1<TResult>
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>Interne Member

|Name|Beschreibung|
|----------|-----------------|
|[ObjectIdForDebugger-Eigenschaft](../../extensibility/debugger/asynctaskmethodbuilder-tresult-objectidfordebugger-property.md)|Ruft ein Objekt, das zur eindeutigen Identifizierung von diesem Generator für den Debugger verwendet werden kann.|
|[M_task-Feld](../../extensibility/debugger/asynctaskmethodbuilder-tresult-m-task-field.md)|Stellt dar, die verzögert initialisierte Aufgabe erstellt.|

## <a name="see-also"></a>Siehe auch
- <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>
- [Merkmale von parallelen Erweiterung für .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)