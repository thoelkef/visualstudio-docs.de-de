---
title: IDebugPortSupplier2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPortSupplier2
helpviewer_keywords:
- IDebugPortSupplier2 interface
ms.assetid: 37067324-2ea6-4a01-8829-a6e9c7a70068
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e4aa26aa37b40c0e483342e6eb93cbac15bbbfc2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31119473"
---
# <a name="idebugportsupplier2"></a>IDebugPortSupplier2
Diese Schnittstelle stellt die Ports, die der Sitzung Debug-Manager (SDM) bereit.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugPortSupplier2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Ein benutzerdefinierten Port Lieferanten implementiert diese Schnittstelle, um einen Port Lieferanten darstellen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Ein Aufruf von `CoCreateInstance` mit eines Port des Lieferanten `GUID` gibt diese Schnittstelle (Dies ist das übliche Verfahren zum Abrufen dieser Schnittstelle). Zum Beispiel:  
  
```cpp  
IDebugPortSupplier2 *GetPortSupplier(GUID *pPortSupplierGuid)  
{  
    IDebugPortSupplier2 *pPS = NULL;  
    if (pPortSupplierGuid != NULL) {  
        CComPtr<IDebugPortSupplier2> spPortSupplier;  
        spPortSupplier.CoCreateInstance(*pPortSupplierGuid);  
        if (spPortSupplier != NULL) {  
            pPS = spPortSupplier.Detach();  
        }  
    }  
    return (pPS);  
}  
```  
  
 Ein Aufruf von [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md) gibt diese Schnittstelle, die den aktuellen Port Lieferanten, die vom verwendeten darstellt [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)].  
  
 [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md) gibt diese Schnittstelle, die Port-Lieferanten, die der Port erstellt darstellt.  
  
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) stellt eine Liste von `IDebugPortSupplier` Schnittstellen (die `IEnumDebugPortSuppliers` Schnittstelle abgerufenes [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md), registriert,diealleLieferantenPortdarstellt[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]).  
  
 Ein Debugmodul interagiert in der Regel nicht mit einem Port Lieferanten.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugPortSupplier2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetPortSupplierName](../../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md)|Ruft den Port Supplier Name ab.|  
|[GetPortSupplierId](../../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)|Ruft die Port-Lieferanten-ID ab.|  
|[GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md)|Ruft einen Port aus einem Port Lieferanten ab.|  
|[EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)|Listet die Ports, die bereits vorhanden.|  
|[CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)|Stellt sicher, dass ein Port Lieferant unterstützt das Hinzufügen von neuen Ports ein.|  
|[Hinzufügen](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)|Fügt einen Port an.|  
|[RemovePort](../../../extensibility/debugger/reference/idebugportsupplier2-removeport.md)|Entfernt einen Port an.|  
  
## <a name="remarks"></a>Hinweise  
 Ein Lieferant Port kann sich selbst nach Name und ID identifizieren, hinzufügen und Entfernen von Ports und alle Ports, die der Port Lieferanten auflisten.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Core-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)   
 [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)   
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)