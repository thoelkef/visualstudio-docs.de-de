---
title: ContingentProperties-Klasse – interne Member | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ContingentProperties class [.NET Framework debug engines]
- debug engines, ContingentProperties class [.NET Framework]
ms.assetid: c49d1362-ab1c-4b6d-9950-fcae40e0e66b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a7b9775ed74e7ae81768f180e596f171b2c99cba
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66344318"
---
# <a name="contingentproperties-class---internal-members"></a>ContingentProperties-Klasse – interne Member
Enthält zusätzliche Eigenschaften für eine <xref:System.Threading.Tasks.Task> Objekt.

 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** "mscorlib" (in "mscorlib.dll")

 Da Sie diese internen Member von .NET Framework zugreifen können, wird die folgende Syntax in Common Intermediate Language (CIL) bereitgestellt.

## <a name="syntax"></a>Syntax

```csharp
.class auto ansi nested assembly beforefieldinit ContingentProperties
       extends System.Object
```

## <a name="members"></a>Member

### <a name="fields"></a>Felder

|Name|Beschreibung|
|----------|-----------------|
|[m_children](../../extensibility/debugger/m-children-field.md)|Die Liste der untergeordneten Aufgaben, die mit dieser Aufgabe registriert sind.|

## <a name="remarks"></a>Hinweise
 .NET Framework initialisiert die Felder dieser Klasse nur, wenn sie benötigt werden.

## <a name="see-also"></a>Siehe auch
- [Merkmale von parallelen Erweiterung für .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)