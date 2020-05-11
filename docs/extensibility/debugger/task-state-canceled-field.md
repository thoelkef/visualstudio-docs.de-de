---
title: TASK_STATE_CANCELED Feld | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_CANCELED field, Task class [.NET Framework debug engines]
ms.assetid: f4f5a96a-8230-493d-9696-8d2716bda261
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d59335a418febef45ebe35d4590c72b486921639
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712748"
---
# <a name="task_state_canceled-field"></a>TASK_STATE_CANCELED Feld
Die Aufgabe wurde abgebrochen, bevor sie den ausgeführten Status erreichte, oder sie bestätigte den Abbruch und wurde ausnahmslos abgeschlossen.

 **Namespace:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Baugruppe:** mscorlib (in mscorlib.dll)

 Da Sie über .NET Framework nicht auf dieses interne Element zugreifen können, wird die folgende Syntax in Common Intermediate Language (CIL) bereitgestellt.

## <a name="syntax"></a>Syntax

```csharp
.field static assembly literal int32 TASK_STATE_CANCELED = int32(0x00800000)
```

## <a name="remarks"></a>Bemerkungen
 Wenn das [Feld m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) diesen <xref:System.Threading.Tasks.Task.Status%2A> Wert <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>enthält, gibt die Eigenschaft zurück.

## <a name="see-also"></a>Weitere Informationen
- [Task-Klasse](../../extensibility/debugger/task-class-internal-members.md)
