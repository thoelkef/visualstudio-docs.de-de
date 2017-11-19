---
title: AsyncVoidMethodBuilder-Struktur - interne Member | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, AsyncVoidMethodBuilder structure [.NET Framework]
- AsyncVoidMethodBuilder structure [.NET Framework debug engines]
ms.assetid: fe2970ab-d4c5-4355-a8e4-772ee0a57178
caps.latest.revision: "4"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8e2a8b9f7e287ccf8bc63a8d7392cba0d58cb9bb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="asyncvoidmethodbuilder-structure---internal-members"></a>AsyncVoidMethodBuilder-Struktur - interne Member
In diesem Thema wird beschrieben, die internen Member des der <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> Klasse. Allgemeine Informationen zu dieser Klasse finden Sie unter der <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> Referenzthema.  
  
 **Namespace:**<xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **Assembly:** "mscorlib" (in "mscorlib.dll")  
  
 Da diese internen Member von .NET Framework zugegriffen werden kann, wird die folgende Syntax gemeinsame Intermediate Language (CIL) bereitgestellt.  
  
## <a name="syntax"></a>Syntax  
  
```  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncVoidMethodBuilder  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## <a name="internal-members"></a>Interne Mitglieder  
  
|Name|Beschreibung|  
|----------|-----------------|  
|[ObjectIdForDebugger-Eigenschaft](../../extensibility/debugger/asyncvoidmethodbuilder-objectidfordebugger-property.md)|Ruft ein Objekt, das zur eindeutigen Identifizierung von diesem Generator für den Debugger verwendet werden kann.|  
|[M_objectIdForDebugger-Feld](../../extensibility/debugger/asyncvoidmethodbuilder-m-objectidfordebugger-field.md)|Stellt die verzögert initialisierte Objekt, das vom Debugger verwendet wird, um die Identifizierung von diesem Generator dar.|  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>   
 [Interne Elemente der parallelen Erweiterung für das .NET-Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)