---
title: IDebugPortRequest2 | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortRequest2
helpviewer_keywords:
- IDebugPortRequest2 interface
ms.assetid: 556e610d-7c4b-44a8-965a-76a9d02b601a
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fa72ae9d2cfbe399c3507406875e9c692d18b678
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188343"
---
# <a name="idebugportrequest2"></a>IDebugPortRequest2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Schnittstelle beschreibt einen Port. Diese Beschreibung wird verwendet, um den Port einem Port Lieferanten hinzuzufügen.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugPortRequest2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Diese Schnittstelle wird von Visual Studio normalerweise implementiert, um einen Debugport von einem Port Lieferanten zu erhalten.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Diese Schnittstelle wird an [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) übermittelt, um einen Debugport zu erstellen. Ein [getportrequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md) -Rückruf gibt diese Schnittstelle zurück, die die Anforderung darstellt, die zuerst zum Erstellen des Ports verwendet wird.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugPortRequest2` .  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetPortName](../../../extensibility/debugger/reference/idebugportrequest2-getportname.md)|Ruft den Namen des zu erstellenden Ports ab.|  
  
## <a name="remarks"></a>Bemerkungen  
 Eine Debug-Engine interagiert in der Regel nicht mit einem Port Lieferanten und wird für diese Schnittstelle nicht verwendet.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Kern Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)   
 [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)
