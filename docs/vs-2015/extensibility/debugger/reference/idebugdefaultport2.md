---
title: IDebugDefaultPort2 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugDefaultPort2
helpviewer_keywords:
- IDebugDefaultPort2 interface
ms.assetid: 7b3452af-9a96-4c4c-9946-4339b72d3d7b
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d9367968f08116a21ea51fc1d0167fa57a5e3bd7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51724489"
---
# <a name="idebugdefaultport2"></a>IDebugDefaultPort2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Schnittstelle bietet mehrere Methoden für den Zugriff auf einen Port für den Server und Notification-Funktionen.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugDefaultPort2 : IDebugPort2  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Visual Studio implementiert diese Schnittstelle, um das Debuggen Port für den Zugriff auf Programme darstellen. Ein benutzerdefinierter Port Lieferant kann auch diese Schnittstelle implementieren, wenn die Methode behandelt das Remotedebuggen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Ein Argument auf Methoden in der [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) Schnittstelle stellt diese Schnittstelle. Aufrufen von [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) auf eine [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) Schnittstelle kann auch abrufen, diese Schnittstelle.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Zusätzlich zu den Methoden, die in definierten [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md), diese Schnittstelle implementiert die folgenden Methoden:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md)|Ruft die Port-Notification-Schnittstelle von diesem Port ab.|  
|[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)|Ruft die Schnittstelle auf dem Hostserver diesen Port ab.|  
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugdefaultport2-queryislocal.md)|Bestimmt, ob dieser Port auf dem lokalen Computer ausgeführt wird.|  
  
## <a name="remarks"></a>Hinweise  
 Der Name "`IDebugDefaultPort2`" wird von ein wenig irreführend, da es keinen Standardport darstellt. Sie können "IDebugPort3." aufgerufen werden  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)

