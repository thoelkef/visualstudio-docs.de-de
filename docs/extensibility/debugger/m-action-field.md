---
title: M_action-Feld | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_action field, Task class [.NET Framework debug engines]
ms.assetid: 201838c2-260d-4071-b6c3-f526874e19c9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b41c5d0ae7733a2a9256882852b9016d8e05e0bc
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53944456"
---
# <a name="maction-field"></a>M_action-Feld
Der Delegat, der den auszuführenden in Code stellt dar, die <xref:System.Threading.Tasks.Task> Objekt.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** "mscorlib" (in *"mscorlib.dll"*)  
  
 Da Sie diesen internen Member von .NET Framework zugreifen können, wird die folgende Syntax in Common Intermediate Language (CIL) bereitgestellt.  
  
## <a name="syntax"></a>Syntax  
  
```csharp  
.field assembly object m_action  
```  
  
## <a name="remarks"></a>Hinweise  
 Dies ist die `action` Parameter in der <xref:System.Threading.Tasks.Task.%23ctor%2A> Konstruktor.  
  
## <a name="see-also"></a>Siehe auch  
 [Task class (Task-Klasse)](../../extensibility/debugger/task-class-internal-members.md)