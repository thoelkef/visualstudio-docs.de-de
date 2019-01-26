---
title: IDebugProgramDestroyEventFlags2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugProgramDestroyEventFlags2 interface
ms.assetid: d384ff71-dc71-40b9-a871-801f8b6a3418
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 95205705d53b7040df1f8ee8fc68aab66018a362
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54934451"
---
# <a name="idebugprogramdestroyeventflags2"></a>IDebugProgramDestroyEventFlags2
Ermöglicht es eine Debug-Engine, um das Standardverhalten überschreiben die [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Benutzeroberfläche, wenn Sie eine Debugsitzung zu beenden.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugProgramDestroyEventFlags2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Diese Schnittstelle wird von Debug-Engines implementiert. Es ist nützlich für Hosts, die möglicherweise zu erstellen und Zerstören von mehreren Programmen während der Lebensdauer eines Prozesses.  
  
## <a name="methods"></a>Methoden  
 Die folgende Tabelle zeigt die Methoden der `IDebugProgramDestroyEventFlags2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|Ruft ab, die Anwendung Zerstören von Flags.|  
  
## <a name="remarks"></a>Hinweise  
 Das Standardverhalten der [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Benutzeroberfläche ist in den Entwurfsmodus zurückkehren, nachdem alle Programme, ein Programm gesendet haben Ereignis zerstört. Diese Schnittstelle ermöglicht eine Debug-Engine, um dieses Verhalten zu ändern.  
  
## <a name="requirements"></a>Anforderungen  
 Header: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll