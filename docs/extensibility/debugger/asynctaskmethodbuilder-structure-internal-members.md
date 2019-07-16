---
title: AsyncTaskMethodBuilder-Struktur – interne Member | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, AsyncTaskMethodBuilder structure [.NET Framework]
- AsyncTaskMethodBuilder structure [.NET Framework debug engines]
ms.assetid: f32f5857-7ef8-45fd-8b5a-7f644eb98b11
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3f080e7a0fef7a03b878c253f09661338b5704df
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66317631"
---
# <a name="asynctaskmethodbuilder-structure---internal-members"></a>AsyncTaskMethodBuilder-Struktur – interne Member
In diesem Thema wird beschrieben, die internen Member des der <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> Klasse. Allgemeine Informationen zu dieser Klasse finden Sie unter den <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> Referenzthema.

 **Namespace:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **Assembly:** "mscorlib" (in "mscorlib.dll")

 Da Sie diese internen Member von .NET Framework zugreifen können, wird die folgende Syntax in Common Intermediate Language (CIL) bereitgestellt.

## <a name="syntax"></a>Syntax

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>Interne Member

|Name|Beschreibung|
|----------|-----------------|
|[ObjectIdForDebugger-Eigenschaft](../../extensibility/debugger/asynctaskmethodbuilder-objectidfordebugger-property.md)|Ruft ein Objekt, das zur eindeutigen Identifizierung von diesem Generator für den Debugger verwendet werden kann.|
|[M_builder-Feld](../../extensibility/debugger/asynctaskmethodbuilder-m-builder-field.md)|Das generische Generatorobjekt, zu dem diese Instanz nicht generische Delegaten, darstellt.|

## <a name="see-also"></a>Siehe auch
- <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>
- [Merkmale von parallelen Erweiterung für .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)