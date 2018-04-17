---
title: IEnumDebugAddresses | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugAddresses
helpviewer_keywords:
- IEnumDebugAddresses interface
ms.assetid: 5f6f6751-e6d8-4c5a-8e81-414b6e5d8cc5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bfed705253a03ec550e7533f7e2ab323b7ead62a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="ienumdebugaddresses"></a>IEnumDebugAddresses
Diese Schnittstelle stellt eine Auflistung von Objekten, die Implementierung der [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) Schnittstelle.  
  
## <a name="syntax"></a>Syntax  
  
```  
IEnumDebugAdresses : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Diese Schnittstelle wird von Gruppen von Objekten bereitstellen, die implementiert den Symbol-Anbieter implementiert die [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) Schnittstelle. Beachten Sie, dass dies keiner standardmäßigen COM-Enumeration kann wegen des Vorhandenseins der [GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md) Methode.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Diese Schnittstelle zurückgegebenes [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md) und [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md).  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Diese Schnittstelle implementiert die folgenden Methoden.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[Nächste](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)|Ruft den nächsten Satz von [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) Objekte aus der Enumeration.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugaddresses-skip.md)|Überspringt eine angegebene Anzahl von Einträgen.|  
|[Zurücksetzen](../../../extensibility/debugger/reference/ienumdebugaddresses-reset.md)|Setzt die Enumeration an den ersten Eintrag zurück.|  
|[Klon](../../../extensibility/debugger/reference/ienumdebugaddresses-clone.md)|Ruft eine Kopie der aktuellen Enumeration.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md)|Ruft die Anzahl der Einträge in der Enumeration ab.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Schnittstelle wird durch die Debugging-Modul in der Regel verwendet, um zu ermitteln, die entsprechende Adresse, um auf die ausdrucksauswertung zu gewähren.  
  
## <a name="requirements"></a>Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Symbol-Anbieter-Schnittstellen](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)   
 [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)