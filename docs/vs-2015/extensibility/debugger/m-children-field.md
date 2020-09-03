---
title: m_children Feld | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 749b7a8da2cbdf8377e7f2e1fcb39787e2f42303
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149063"
---
# <a name="m_children-field"></a>m_children-Feld
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die Liste der untergeordneten Aufgaben, die bei dieser Aufgabe registriert sind.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (in mscorlib.dll)  
  
 Da Sie nicht auf dieses interne Element vom .NET Framework aus zugreifen können, wird die folgende Syntax in Common Intermediate Language (CIL) bereitgestellt.  
  
## <a name="syntax"></a>Syntax  
  
```  
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children  
```  
  
## <a name="remarks"></a>Bemerkungen  
 Während die Aufgabe ausgeführt wird, sollte nur der Thread, der die Aufgabe ausführt, auf dieses Array zugreifen.  
  
 Wenn die Aufgabe abgeschlossen ist, können andere Threads auf dieses Feld zugreifen, solange Sie nichts hinzufügen oder aus ihr entfernen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [ContingentProperties-Klasse](../../extensibility/debugger/contingentproperties-class-internal-members.md)
