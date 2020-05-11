---
title: m_action Feld | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_action field, Task class [.NET Framework debug engines]
ms.assetid: 201838c2-260d-4071-b6c3-f526874e19c9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 925141733356ac7730e2708673ebdad793fd465b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738435"
---
# <a name="m_action-field"></a>m_action Feld
Der Delegat, der den <xref:System.Threading.Tasks.Task> Code darstellt, der im Objekt ausgeführt werden soll.

 **Namespace:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Baugruppe:** mscorlib (in *mscorlib.dll*)

 Da Sie über .NET Framework nicht auf dieses interne Element zugreifen können, wird die folgende Syntax in Common Intermediate Language (CIL) bereitgestellt.

## <a name="syntax"></a>Syntax

```csharp
.field assembly object m_action
```

## <a name="remarks"></a>Bemerkungen
 Dies `action` ist der <xref:System.Threading.Tasks.Task.%23ctor%2A> Parameter im Konstruktor.

## <a name="see-also"></a>Weitere Informationen
- [Task-Klasse](../../extensibility/debugger/task-class-internal-members.md)
