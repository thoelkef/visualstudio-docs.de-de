---
title: AsyncTaskMethodBuilder-Struktur - Interne Member | Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739373"
---
# <a name="asynctaskmethodbuilder-structure---internal-members"></a>AsyncTaskMethodBuilder-Struktur - interne Member
In diesem Thema werden <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> die internen Member der Klasse beschrieben. Allgemeine Informationen zu dieser Klasse <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> finden Sie im Referenzthema.

 **Namespace:**<xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **Baugruppe:** mscorlib (in mscorlib.dll)

 Da Sie über .NET Framework nicht auf diese internen Member zugreifen können, wird die folgende Syntax in Common Intermediate Language (CIL) bereitgestellt.

## <a name="syntax"></a>Syntax

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>Interne Mitglieder

|Name|BESCHREIBUNG|
|----------|-----------------|
|[ObjectIdForDebugger-Eigenschaft](../../extensibility/debugger/asynctaskmethodbuilder-objectidfordebugger-property.md)|Ruft ein Objekt ab, das verwendet werden kann, um diesen Builder für den Debugger eindeutig zu identifizieren.|
|[m_builder Feld](../../extensibility/debugger/asynctaskmethodbuilder-m-builder-field.md)|Stellt das generische Builder-Objekt dar, an das diese nicht generische Instanz delegiert.|

## <a name="see-also"></a>Weitere Informationen
- <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>
- [Parallele Erweiterungsinterne für .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
