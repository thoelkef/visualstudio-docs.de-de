---
title: IDebugAddress2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugAddress2
helpviewer_keywords: IDebugAddress2 interface
ms.assetid: b150e0ed-4ac0-4f8c-9732-4b3e54b9d243
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 43c112da892fadf95eb5a27880d82ec9d29419c7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugaddress2"></a>IDebugAddress2
Diese Schnittstelle bietet Zugriff auf die ID des Prozesses, der das Objekt, dessen Adresse besitzt, die von dieser Schnittstelle dargestellt wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugAddress2 : IDebugAddress  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Ein Symbol-Anbieter implementiert diese Schnittstelle für das gleiche Objekt, das implementiert die [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) Schnittstelle. Diese Schnittstelle bietet Zugriff auf die ID des Prozesses, der das Objekt besitzt, das an diese Adresse verknüpft ist.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Verwendung [QueryInterface](/cpp/atl/queryinterface) beim Abrufen dieser Schnittstelle aus dem [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) Schnittstelle.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Zusätzlich zu den von geerbten Methoden der [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) diese Schnittstelle implementiert, die folgende Methode:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetProcessID](../../../extensibility/debugger/reference/idebugaddress2-getprocessid.md)|Ruft die ID des Prozesses, der Besitzer des Objekts, das von dieser Schnittstelle dargestellt ist.|  
  
## <a name="requirements"></a>Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Symbol-Anbieter-Schnittstellen](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)