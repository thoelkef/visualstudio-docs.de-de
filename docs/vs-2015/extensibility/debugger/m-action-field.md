---
title: M_action-Feld | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- m_action field, Task class [.NET Framework debug engines]
ms.assetid: 201838c2-260d-4071-b6c3-f526874e19c9
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 68d526fe4266f9c8f7c0d3dc4790c8b5893f72ea
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47513787"
---
# <a name="maction-field"></a>m_action-Feld
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [M_action-Feld](https://docs.microsoft.com/visualstudio/extensibility/debugger/m-action-field).  
  
Der Delegat, der den auszuführenden in Code stellt dar, die <xref:System.Threading.Tasks.Task> Objekt.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** "mscorlib" (in "mscorlib.dll")  
  
 Da Sie diesen internen Member von .NET Framework zugreifen können, wird die folgende Syntax in Common Intermediate Language (CIL) bereitgestellt.  
  
## <a name="syntax"></a>Syntax  
  
```  
.field assembly object m_action  
```  
  
## <a name="remarks"></a>Hinweise  
 Dies ist die `action` Parameter in der <xref:System.Threading.Tasks.Task.%23ctor%2A> Konstruktor.  
  
## <a name="see-also"></a>Siehe auch  
 [Aufgabenklasse](../../extensibility/debugger/task-class-internal-members.md)

