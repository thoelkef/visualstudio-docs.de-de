---
title: ContingentProperties-Klasse – interne Member | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- ContingentProperties class [.NET Framework debug engines]
- debug engines, ContingentProperties class [.NET Framework]
ms.assetid: c49d1362-ab1c-4b6d-9950-fcae40e0e66b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8e3497b31e663967417544d8e87d40d860c2e4a8
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2018
ms.locfileid: "39204413"
---
# <a name="contingentproperties-class---internal-members"></a>ContingentProperties-Klasse – interne Member
Enthält zusätzliche Eigenschaften für eine <xref:System.Threading.Tasks.Task> Objekt.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** "mscorlib" (in "mscorlib.dll")  
  
 Da Sie diese internen Member von .NET Framework zugreifen können, wird die folgende Syntax in Common Intermediate Language (CIL) bereitgestellt.  
  
## <a name="syntax"></a>Syntax  
  
```csharp  
.class auto ansi nested assembly beforefieldinit ContingentProperties  
       extends System.Object  
```  
  
## <a name="members"></a>Member  
  
### <a name="fields"></a>Felder  
  
|name|Beschreibung|  
|----------|-----------------|  
|[m_children](../../extensibility/debugger/m-children-field.md)|Die Liste der untergeordneten Aufgaben, die mit dieser Aufgabe registriert sind.|  
  
## <a name="remarks"></a>Hinweise  
 .NET Framework initialisiert die Felder dieser Klasse nur, wenn sie benötigt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Merkmale von parallelen Erweiterung für .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)