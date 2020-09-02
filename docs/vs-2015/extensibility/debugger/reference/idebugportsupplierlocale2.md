---
title: IDebugPortSupplierLocale2 | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierLocale2 interface
ms.assetid: 910e7220-da2a-4339-9fff-9fb1bad3c28c
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 789d9f97958b9662db5f792f28a75c0f6b46a8c8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188152"
---
# <a name="idebugportsupplierlocale2"></a>IDebugPortSupplierLocale2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Stellt Gebiets Schema Unterstützung für einen Port Lieferanten bereit.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugPortSupplierLocale2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Ein benutzerdefinierter Port Lieferant implementiert diese Schnittstelle, um das Gebiets Schema festzulegen.  
  
## <a name="methods"></a>Methoden  
 In der folgenden Tabelle sind die Methoden von **IDebugPortSupplierLocale2**aufgeführt.  
  
|Methode|BESCHREIBUNG|  
|------------|-----------------|  
|[SetLocale](../../../extensibility/debugger/reference/idebugportsupplierlocale2-setlocale.md)|Legt das Gebiets Schema für den Port Lieferanten fest.|  
  
## <a name="requirements"></a>Anforderungen  
 Header: portpriv. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Kern Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
