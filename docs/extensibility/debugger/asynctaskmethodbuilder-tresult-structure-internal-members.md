---
title: AsyncTaskMethodBuilder&lt;TResult&gt; Structure - Interne Member | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- AsyncTaskMethodBuilder<TResult> structure [.NET Framework debug engines]
- debug engines, AsyncTaskMethodBuilder<TResult> structure [.NET Framework]
ms.assetid: 17ebc340-8170-4aff-bf54-dc4548c83632
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c4f4da7070af09937af9e047ec83142584942e6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739330"
---
# <a name="asynctaskmethodbuilderlttresultgt-structure---internal-members"></a>AsyncTaskMethodBuilder&lt;TResult-Struktur&gt; - interne Member
In diesem Thema werden <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> die internen Member der Klasse beschrieben. Allgemeine Informationen zu dieser Klasse <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> finden Sie im Referenzthema.

 **Namespace:**<xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **Baugruppe:** mscorlib (in mscorlib.dll)

 Da Sie über .NET Framework nicht auf diese internen Member zugreifen können, wird die folgende Syntax in Common Intermediate Language (CIL) bereitgestellt.

## <a name="syntax"></a>Syntax

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder`1<TResult>
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>Interne Mitglieder

|Name|BESCHREIBUNG|
|----------|-----------------|
|[ObjectIdForDebugger-Eigenschaft](../../extensibility/debugger/asynctaskmethodbuilder-tresult-objectidfordebugger-property.md)|Ruft ein Objekt ab, das verwendet werden kann, um diesen Builder für den Debugger eindeutig zu identifizieren.|
|[m_task Feld](../../extensibility/debugger/asynctaskmethodbuilder-tresult-m-task-field.md)|Stellt die verzögert initialisierte erstellte Aufgabe dar.|

## <a name="see-also"></a>Weitere Informationen
- <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>
- [Parallele Erweiterungsinterne für .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
