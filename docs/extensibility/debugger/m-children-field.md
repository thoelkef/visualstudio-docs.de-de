---
title: m_children Feld | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 07933fd4c9f359e72714600abdf8b4ee29268f84
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738428"
---
# <a name="m_children-field"></a>m_children Feld
Die Liste der untergeordneten Vorgänge, die für diese Aufgabe registriert sind.

 **Namespace:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Baugruppe:** mscorlib (in *mscorlib.dll*)

 Da Sie über .NET Framework nicht auf dieses interne Element zugreifen können, wird die folgende Syntax in Common Intermediate Language (CIL) bereitgestellt.

## <a name="syntax"></a>Syntax

```csharp
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children
```

## <a name="remarks"></a>Bemerkungen
 Während die Aufgabe ausgeführt wird, sollte nur der Thread, der die Aufgabe ausführt, auf dieses Array zugreifen.

 Wenn die Aufgabe abgeschlossen ist, können andere Threads auf dieses Feld zugreifen, solange sie nichts hinzufügen oder etwas daraus entfernen.

## <a name="see-also"></a>Weitere Informationen
- [ContingentProperties-Klasse](../../extensibility/debugger/contingentproperties-class-internal-members.md)
