---
title: IDebugPortRequest2 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
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
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7873d3d73556bae671cc1150525eb3d08a136e27
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47523592"
---
# <a name="idebugportrequest2"></a>IDebugPortRequest2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugPortRequest2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugportrequest2).  
  
Diese Schnittstelle wird beschrieben, einen Port. Diese Beschreibung wird verwendet, um den Port an einen Lieferanten Port hinzuzufügen.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugPortRequest2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Diese Schnittstelle beim Abrufen eines Debug-Ports von eines portanbieters wird von Visual Studio in der Regel implementiert.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Diese Schnittstelle übergebenen [Port hinzufügen](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) So erstellen Sie einen Debugport. Ein Aufruf von [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md) gibt diese Schnittstelle, die die Anforderung verwendet, um die im ersten Schritt erstellen Sie den Port darstellt.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugPortRequest2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetPortName](../../../extensibility/debugger/reference/idebugportrequest2-getportname.md)|Ruft den Namen des Ports erstellen.|  
  
## <a name="remarks"></a>Hinweise  
 Eine Debug-Engine ist in der Regel interagiert nicht mit eines portanbieters und hat keine Verwendung für diese Schnittstelle.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Port hinzufügen](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)   
 [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)

