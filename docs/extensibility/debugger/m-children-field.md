---
title: M_children-Feld | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0f8ea4f053d28ea14c05a50e3bc187faf6f6e207
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54966854"
---
# <a name="mchildren-field"></a>M_children-Feld
Die Liste der untergeordneten Aufgaben, die mit dieser Aufgabe registriert sind.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** "mscorlib" (in *"mscorlib.dll"*)  
  
 Da Sie diesen internen Member von .NET Framework zugreifen können, wird die folgende Syntax in Common Intermediate Language (CIL) bereitgestellt.  
  
## <a name="syntax"></a>Syntax  
  
```csharp 
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children  
```  
  
## <a name="remarks"></a>Hinweise  
 Während die Aufgabe ausgeführt wird, sollten nur der Thread, der die Aufgabe ausgeführt wird. dieses Array zugreifen.  
  
 Wenn die Aufgabe abgeschlossen ist, können andere Threads in diesem Feld zugreifen, solange nichts hinzugefügt oder daraus Alles entfernen nicht.  
  
## <a name="see-also"></a>Siehe auch  
 [ContingentProperties-Klasse](../../extensibility/debugger/contingentproperties-class-internal-members.md)