---
title: IDebugPortSupplierEx2 | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierEx2 interface
ms.assetid: dae0050a-a50a-4f35-bfbd-e538f537b20f
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e59d3eb67fe45003babf53862736a435586deeeb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62537939"
---
# <a name="idebugportsupplierex2"></a>IDebugPortSupplierEx2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bietet Unterstützung für einen Port Lieferant, der einen Kernserver auswählen und mit ihm interagieren soll.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugPortSupplierEx2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Ein benutzerdefinierter Port Lieferant implementiert diese Schnittstelle, sodass er den zu verwendenden Kernserver auswählen kann.  
  
## <a name="methods"></a>Methoden  
 In der folgenden Tabelle sind die Methoden von **IDebugPortSupplierEx2**aufgeführt.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[SetServer](../../../extensibility/debugger/reference/idebugportsupplierex2-setserver.md)|Legt den Kernserver für den Port Lieferanten fest.|  
  
## <a name="requirements"></a>Anforderungen  
 Header: portpriv. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Kern Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
