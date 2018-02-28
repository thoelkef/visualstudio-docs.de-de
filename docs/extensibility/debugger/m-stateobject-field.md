---
title: M_stateObject Feld | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- m_stateObject field, Task class [.NET Framework debug engines]
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 9638be7b2f3f3a6c235a4768cdb493fea701a4dd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="mstateobject-field"></a>M_stateObject Feld
Ein Objekt, das Daten darstellt, die die Aktion verwendet wird.  
  
 **Namespace:**<xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** "mscorlib" (in "mscorlib.dll")  
  
 Da dieses interne Member von .NET Framework zugegriffen werden kann, wird die folgende Syntax gemeinsame Intermediate Language (CIL) bereitgestellt.  
  
## <a name="syntax"></a>Syntax  
  
```  
.field assembly object m_stateObject  
```  
  
## <a name="remarks"></a>Hinweise  
 Dies ist die `state` Parameter in der <xref:System.Threading.Tasks.Task.%23ctor%2A> Konstruktor. Es ist auch das dahinter liegende Feld für die <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName> Eigenschaft.  
  
## <a name="see-also"></a>Siehe auch  
 [Task-Klasse](../../extensibility/debugger/task-class-internal-members.md)