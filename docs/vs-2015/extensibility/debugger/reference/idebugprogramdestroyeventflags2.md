---
title: IDebugProgramDestroyEventFlags2 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugProgramDestroyEventFlags2 interface
ms.assetid: d384ff71-dc71-40b9-a871-801f8b6a3418
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 86d3a6ba48107753e5403f39d5b982b4dc88ffdd
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47523910"
---
# <a name="idebugprogramdestroyeventflags2"></a>IDebugProgramDestroyEventFlags2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugProgramDestroyEventFlags2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprogramdestroyeventflags2).  
  
Ermöglicht es eine Debug-Engine, um das Standardverhalten überschreiben die [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Benutzeroberfläche, wenn Sie eine Debugsitzung zu beenden.  
  
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
 Das Standardverhalten der [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Benutzeroberfläche ist in den Entwurfsmodus zurückkehren, nachdem alle Programme, ein Programm gesendet haben Ereignis zerstört. Diese Schnittstelle ermöglicht eine Debug-Engine, um dieses Verhalten zu ändern.  
  
## <a name="requirements"></a>Anforderungen  
 Header: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

