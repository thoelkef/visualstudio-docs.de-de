---
title: M_stateObject-Feld | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- m_stateObject field, Task class [.NET Framework debug engines]
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 20b90379732dc854c397c8b8ba31ee82274deb65
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49274013"
---
# <a name="mstateobject-field"></a>m_stateObject-Feld
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ein Objekt, das Daten darstellt, die die Aktion verwendet wird.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** "mscorlib" (in "mscorlib.dll")  
  
 Da Sie diesen internen Member von .NET Framework zugreifen können, wird die folgende Syntax in Common Intermediate Language (CIL) bereitgestellt.  
  
## <a name="syntax"></a>Syntax  
  
```  
.field assembly object m_stateObject  
```  
  
## <a name="remarks"></a>Hinweise  
 Dies ist die `state` Parameter in der <xref:System.Threading.Tasks.Task.%23ctor%2A> Konstruktor. Es ist auch das dahinter liegende Feld für die <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName> Eigenschaft.  
  
## <a name="see-also"></a>Siehe auch  
 [Aufgabenklasse](../../extensibility/debugger/task-class-internal-members.md)

