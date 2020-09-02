---
title: 'Contingentproperties-Klasse: interne Member | Microsoft-Dokumentation'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62414645"
---
# <a name="contingentproperties-class---internal-members"></a>ContingentProperties-Klasse – interne Member
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Enthält zusätzliche Eigenschaften für ein- <xref:System.Threading.Tasks.Task> Objekt.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (in mscorlib.dll)  
  
 Da Sie nicht auf diese internen Member vom .NET Framework aus zugreifen können, wird die folgende Syntax in Common Intermediate Language (CIL) bereitgestellt.  
  
## <a name="syntax"></a>Syntax  
  
```  
.class auto ansi nested assembly beforefieldinit ContingentProperties  
       extends System.Object  
```  
  
## <a name="members"></a>Member  
  
### <a name="fields"></a>Felder  
  
|Name|Beschreibung|  
|----------|-----------------|  
|[m_children](../../extensibility/debugger/m-children-field.md)|Die Liste der untergeordneten Aufgaben, die bei dieser Aufgabe registriert sind.|  
  
## <a name="remarks"></a>Bemerkungen  
 Der .NET Framework initialisiert die Felder dieser Klasse nur dann, wenn Sie benötigt werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Interne Elemente der parallelen Erweiterung für das .NET-Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
