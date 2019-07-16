---
title: M_stateObject-Feld | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_stateObject field, Task class [.NET Framework debug engines]
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 95947a1367ea1ddf4aa88689f731971d5c7d0a6c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66330833"
---
# <a name="mstateobject-field"></a>M_stateObject-Feld
Ein Objekt, das Daten darstellt, die die Aktion verwendet wird.

 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** "mscorlib" (in *"mscorlib.dll"* )

 Da Sie diesen internen Member von .NET Framework zugreifen können, wird die folgende Syntax in Common Intermediate Language (CIL) bereitgestellt.

## <a name="syntax"></a>Syntax

```
.field assembly object m_stateObject
```

## <a name="remarks"></a>Hinweise
 Dies ist die `state` Parameter in der <xref:System.Threading.Tasks.Task.%23ctor%2A> Konstruktor. Es ist auch das dahinter liegende Feld für die <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName> Eigenschaft.

## <a name="see-also"></a>Siehe auch
- [Task class (Task-Klasse)](../../extensibility/debugger/task-class-internal-members.md)