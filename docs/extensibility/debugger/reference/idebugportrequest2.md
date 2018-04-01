---
title: IDebugPortRequest2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugPortRequest2
helpviewer_keywords:
- IDebugPortRequest2 interface
ms.assetid: 556e610d-7c4b-44a8-965a-76a9d02b601a
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 5b47a9bde47049c957af9f60e1d09d03b55c2359
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugportrequest2"></a>IDebugPortRequest2
Diese Schnittstelle wird beschrieben, einen Port. Diese Beschreibung wird verwendet, um den Port an einen Lieferanten Port hinzuzufügen.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugPortRequest2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Visual Studio implementiert in der Regel diese Schnittstelle gerade einen Debugport von einem anderen Port Lieferanten abrufen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Diese Schnittstelle übergebenen [hinzufügen](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) zum Erstellen eines Ports Debuggen. Ein Aufruf von [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md) gibt diese Schnittstelle, die die Anforderung verwendet, um die im ersten Schritt erstellen Sie den Port darstellt.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugPortRequest2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetPortName](../../../extensibility/debugger/reference/idebugportrequest2-getportname.md)|Ruft den Namen des Ports erstellen.|  
  
## <a name="remarks"></a>Hinweise  
 Debugging-Modul ist in der Regel interagiert nicht mit einem Port Lieferanten und verfügt über keine Verwendung für diese Schnittstelle.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Core-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Hinzufügen](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)   
 [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)