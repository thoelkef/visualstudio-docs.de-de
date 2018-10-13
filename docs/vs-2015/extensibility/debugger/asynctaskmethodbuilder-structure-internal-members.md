---
title: AsyncTaskMethodBuilder-Struktur – interne Member | Microsoft-Dokumentation
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
- debug engines, AsyncTaskMethodBuilder structure [.NET Framework]
- AsyncTaskMethodBuilder structure [.NET Framework debug engines]
ms.assetid: f32f5857-7ef8-45fd-8b5a-7f644eb98b11
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b4f0c8cc8e011edb6f69b274816d295046bc76da
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49210755"
---
# <a name="asynctaskmethodbuilder-structure---internal-members"></a>AsyncTaskMethodBuilder-Struktur – interne Member
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In diesem Thema wird beschrieben, die internen Member des der <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> Klasse. Allgemeine Informationen zu dieser Klasse finden Sie unter den <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> Referenzthema.  
  
 **Namespace:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **Assembly:** "mscorlib" (in "mscorlib.dll")  
  
 Da Sie diese internen Member von .NET Framework zugreifen können, wird die folgende Syntax in Common Intermediate Language (CIL) bereitgestellt.  
  
## <a name="syntax"></a>Syntax  
  
```  
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
 [Interne Elemente der parallelen Erweiterung für das .NET-Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)

