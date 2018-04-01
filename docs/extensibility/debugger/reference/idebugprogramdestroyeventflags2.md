---
title: IDebugProgramDestroyEventFlags2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugProgramDestroyEventFlags2 interface
ms.assetid: d384ff71-dc71-40b9-a871-801f8b6a3418
caps.latest.revision: 7
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 3a3bb34435bc7c6411fe694e4476eb9ffeacfe1d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogramdestroyeventflags2"></a>IDebugProgramDestroyEventFlags2
Ermöglicht ein Debugmodul an das Standardverhalten außer Kraft setzen die [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] UI, wenn Sie eine Debugsitzung zu beenden.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugProgramDestroyEventFlags2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Diese Schnittstelle wird von Debugmodule implementiert. Es ist hilfreich für Hosts, die möglicherweise erstellen und Zerstören von mehreren Programmen über die Lebensdauer eines Prozesses.  
  
## <a name="methods"></a>Methoden  
 Die folgende Tabelle zeigt die Methoden der `IDebugProgramDestroyEventFlags2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|Ruft ab, das Programm Flags zu zerstören.|  
  
## <a name="remarks"></a>Hinweise  
 Das Standardverhalten der [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Benutzeroberfläche ist, um zurück in den Entwurfsmodus zu wechseln, nachdem alle Programme, ein Programm gesendet haben Ereignis zu zerstören. Diese Schnittstelle ermöglicht ein Debugging-Modul, um dieses Verhalten zu ändern.  
  
## <a name="requirements"></a>Anforderungen  
 Header: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll