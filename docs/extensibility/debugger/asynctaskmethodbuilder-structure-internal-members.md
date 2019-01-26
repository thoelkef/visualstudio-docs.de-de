---
title: AsyncTaskMethodBuilder-Struktur – interne Member | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, AsyncTaskMethodBuilder structure [.NET Framework]
- AsyncTaskMethodBuilder structure [.NET Framework debug engines]
ms.assetid: f32f5857-7ef8-45fd-8b5a-7f644eb98b11
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 22e011012ee798712c42100f4eb7041d38a4c8e6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54976354"
---
# <a name="asynctaskmethodbuilder-structure---internal-members"></a>AsyncTaskMethodBuilder-Struktur – interne Member
In diesem Thema wird beschrieben, die internen Member des der <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> Klasse. Allgemeine Informationen zu dieser Klasse finden Sie unter den <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> Referenzthema.  
  
 **Namespace:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **Assembly:** "mscorlib" (in "mscorlib.dll")  
  
 Da Sie diese internen Member von .NET Framework zugreifen können, wird die folgende Syntax in Common Intermediate Language (CIL) bereitgestellt.  
  
## <a name="syntax"></a>Syntax  
  
```csharp  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## <a name="internal-members"></a>Interne Member  
  
|name|Beschreibung|  
|----------|-----------------|  
|[ObjectIdForDebugger-Eigenschaft](../../extensibility/debugger/asynctaskmethodbuilder-objectidfordebugger-property.md)|Ruft ein Objekt, das zur eindeutigen Identifizierung von diesem Generator für den Debugger verwendet werden kann.|  
|[M_builder-Feld](../../extensibility/debugger/asynctaskmethodbuilder-m-builder-field.md)|Das generische Generatorobjekt, zu dem diese Instanz nicht generische Delegaten, darstellt.|  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>   
 [Merkmale von parallelen Erweiterung für .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)