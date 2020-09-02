---
title: 'Asynctaskmethodbuilder-Struktur: interne Member | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, AsyncTaskMethodBuilder structure [.NET Framework]
- AsyncTaskMethodBuilder structure [.NET Framework debug engines]
ms.assetid: f32f5857-7ef8-45fd-8b5a-7f644eb98b11
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c918890551515ab9fadbf329d4c3ee96621c7aae
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739373"
---
# <a name="asynctaskmethodbuilder-structure---internal-members"></a>Asynctaskmethodbuilder-Struktur: interne Member
In diesem Thema werden die internen Member der- <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> Klasse beschrieben. Allgemeine Informationen zu dieser Klasse finden Sie im <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> Referenz Thema.

 **Namespace:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **Assembly:** mscorlib (in mscorlib.dll)

 Da Sie nicht auf diese internen Member vom .NET Framework aus zugreifen können, wird die folgende Syntax in Common Intermediate Language (CIL) bereitgestellt.

## <a name="syntax"></a>Syntax

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>Interne Member

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Objectidfordebugger-Eigenschaft](../../extensibility/debugger/asynctaskmethodbuilder-objectidfordebugger-property.md)|Ruft ein Objekt ab, das verwendet werden kann, um diesen Generator für den Debugger eindeutig zu identifizieren.|
|[m_builder Feld](../../extensibility/debugger/asynctaskmethodbuilder-m-builder-field.md)|Stellt das generische Generator Objekt dar, an das diese nicht generische Instanz delegiert.|

## <a name="see-also"></a>Weitere Informationen
- <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>
- [Parallele Erweiterungs internale für die .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
