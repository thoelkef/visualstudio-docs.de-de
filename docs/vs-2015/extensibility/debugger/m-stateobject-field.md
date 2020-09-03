---
title: m_stateObject Feld | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- m_stateObject field, Task class [.NET Framework debug engines]
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8e9cfc6f689504bef2a8366f90282641d1e9e105
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149051"
---
# <a name="m_stateobject-field"></a>m_stateObject-Feld
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ein-Objekt, das Daten darstellt, die von der Aktion verwendet werden.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (in mscorlib.dll)  
  
 Da Sie nicht auf dieses interne Element vom .NET Framework aus zugreifen können, wird die folgende Syntax in Common Intermediate Language (CIL) bereitgestellt.  
  
## <a name="syntax"></a>Syntax  
  
```  
.field assembly object m_stateObject  
```  
  
## <a name="remarks"></a>Bemerkungen  
 Dies ist der `state` Parameter im <xref:System.Threading.Tasks.Task.%23ctor%2A> Konstruktor. Es ist auch das Unterstützungs Feld für die- <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName> Eigenschaft.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Task-Klasse](../../extensibility/debugger/task-class-internal-members.md)
