---
title: ContingentProperties-Klasse – interne Member | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- ContingentProperties class [.NET Framework debug engines]
- debug engines, ContingentProperties class [.NET Framework]
ms.assetid: c49d1362-ab1c-4b6d-9950-fcae40e0e66b
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3f6778aef90361a7751ccd744fcf93822f8f97db
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58946976"
---
# <a name="contingentproperties-class---internal-members"></a>ContingentProperties-Klasse – interne Member
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Enthält zusätzliche Eigenschaften für eine <xref:System.Threading.Tasks.Task> Objekt.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** "mscorlib" (in "mscorlib.dll")  
  
 Da Sie diese internen Member von .NET Framework zugreifen können, wird die folgende Syntax in Common Intermediate Language (CIL) bereitgestellt.  
  
## <a name="syntax"></a>Syntax  
  
```  
.class auto ansi nested assembly beforefieldinit ContingentProperties  
       extends System.Object  
```  
  
## <a name="members"></a>Member  
  
### <a name="fields"></a>Felder  
  
|Name|Beschreibung|  
|----------|-----------------|  
|[m_children](../../extensibility/debugger/m-children-field.md)|Die Liste der untergeordneten Aufgaben, die mit dieser Aufgabe registriert sind.|  
  
## <a name="remarks"></a>Hinweise  
 .NET Framework initialisiert die Felder dieser Klasse nur, wenn sie benötigt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Interne Elemente der parallelen Erweiterung für das .NET-Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
