---
title: ContingentProperties-Klasse - Interne Mitglieder | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ContingentProperties class [.NET Framework debug engines]
- debug engines, ContingentProperties class [.NET Framework]
ms.assetid: c49d1362-ab1c-4b6d-9950-fcae40e0e66b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c6441cafcc34a06464061b41691ea5faa32fc359
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739098"
---
# <a name="contingentproperties-class---internal-members"></a>ContingentProperties-Klasse - interne Member
Enthält zusätzliche Eigenschaften <xref:System.Threading.Tasks.Task> für ein Objekt.

 **Namespace:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Baugruppe:** mscorlib (in mscorlib.dll)

 Da Sie über .NET Framework nicht auf diese internen Member zugreifen können, wird die folgende Syntax in Common Intermediate Language (CIL) bereitgestellt.

## <a name="syntax"></a>Syntax

```csharp
.class auto ansi nested assembly beforefieldinit ContingentProperties
       extends System.Object
```

## <a name="members"></a>Member

### <a name="fields"></a>Felder

|Name|BESCHREIBUNG|
|----------|-----------------|
|[m_children](../../extensibility/debugger/m-children-field.md)|Die Liste der untergeordneten Vorgänge, die für diese Aufgabe registriert sind.|

## <a name="remarks"></a>Bemerkungen
 .NET Framework initialisiert die Felder dieser Klasse nur, wenn sie benötigt werden.

## <a name="see-also"></a>Weitere Informationen
- [Parallele Erweiterungsinterne für .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
