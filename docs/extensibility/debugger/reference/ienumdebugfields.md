---
title: IEnumDebugFields | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugFields
helpviewer_keywords: IEnumDebugFields interface
ms.assetid: 403c2a51-3ba5-431f-a1dd-2f3b2046c00c
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ed697205a5cd7d866df639e2908e3cc0b4fa2f72
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ienumdebugfields"></a>IEnumDebugFields
Diese Schnittstelle stellt eine Auflistung von Objekten, die Implementierung der [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) Schnittstelle.  
  
## <a name="syntax"></a>Syntax  
  
```  
IEnumDebugFields : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Diese Schnittstelle wird von Gruppen von Objekten bereitstellen, die implementiert den Symbol-Anbieter implementiert die [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) Schnittstelle. Beachten Sie, dass dies keiner standardmäßigen COM-Enumeration kann wegen des Vorhandenseins der [GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md) Methode.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Diese Schnittstelle zurückgegebenes [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md) und [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md).  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Diese Schnittstelle implementiert die folgenden Methoden.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[Nächste](../../../extensibility/debugger/reference/ienumdebugfields-next.md)|Ruft den nächsten Satz von [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) Objekte aus der Enumeration.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugfields-skip.md)|Überspringt eine angegebene Anzahl von Einträgen.|  
|[Zurücksetzen](../../../extensibility/debugger/reference/ienumdebugfields-reset.md)|Setzt die Enumeration an den ersten Eintrag zurück.|  
|[Klon](../../../extensibility/debugger/reference/ienumdebugfields-clone.md)|Ruft eine Kopie der aktuellen Enumeration.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md)|Ruft die Anzahl der Einträge in der Enumeration ab.|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="requirements"></a>Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Symbol-Anbieter-Schnittstellen](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)   
 [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)