---
title: IDebugDefaultPort2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugDefaultPort2
helpviewer_keywords:
- IDebugDefaultPort2 interface
ms.assetid: 7b3452af-9a96-4c4c-9946-4339b72d3d7b
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: d048bf55d8a8cb721e8ebf85444e49c3bfa771b9
ms.lasthandoff: 04/05/2017

---
# <a name="idebugdefaultport2"></a>IDebugDefaultPort2
Diese Schnittstelle bietet mehrere Methoden für den Zugriff auf einen Port Server- und Notification-Funktionen.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugDefaultPort2 : IDebugPort2  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Visual Studio implementiert diese Schnittstelle, um die Debugport für den Zugriff auf Programme darstellen. Ein benutzerdefinierten Port Lieferanten kann auch diese Schnittstelle implementieren, wenn sie Remotedebuggen behandelt.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Ein Argument an die Methoden für die [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) Schnittstelle stellt diese Schnittstelle bereit. Aufrufen von [QueryInterface](/cpp/atl/queryinterface) auf eine [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) Schnittstelle auch möglich, diese Schnittstelle.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Zusätzlich zu den Methoden, die in definierten [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md), diese Schnittstelle implementiert, die folgenden Methoden:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md)|Ruft die Port-Benachrichtigung-Schnittstelle von diesem Port ab.|  
|[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)|Ruft die Schnittstelle auf dem Hostserver diesen Port.|  
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugdefaultport2-queryislocal.md)|Bestimmt, ob dieser Port auf dem lokalen Computer ausgeführt wird.|  
  
## <a name="remarks"></a>Hinweise  
 Der Name "`IDebugDefaultPort2`" ist ein wenig irreführend, da es keinen Standardport darstellt. Es könnte "IDebugPort3." aufgerufen werden  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
