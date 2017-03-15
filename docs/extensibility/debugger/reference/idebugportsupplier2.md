---
title: "IDebugPortSupplier2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortSupplier2"
helpviewer_keywords: 
  - "IDebugPortSupplier2-Schnittstelle"
ms.assetid: 37067324-2ea6-4a01-8829-a6e9c7a70068
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugPortSupplier2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Stellt anschlüsse dieser Schnittstelle auf die Sitzung debuggen Manager \(SDM\).  
  
## Syntax  
  
```  
IDebugPortSupplier2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 Ein benutzerdefinierter Port lieferant implementiert diese Schnittstelle, um einen Anschlusslieferanten darzustellen.  
  
## Hinweise für Aufrufer  
 Ein Aufruf von `CoCreateInstance` mit `GUID` des Anschlusslieferanten gibt diese Schnittstelle zurück \(dies ist die typische Methode zum Abrufen dieser Schnittstelle\).  Beispiele:  
  
```cpp#  
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
  
 Ein Aufruf von [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md) gibt diese Schnittstelle zurück und stellt den aktuellen Anschlusslieferanten dar, der von [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]verwendet wird.  
  
 [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md) gibt diese Schnittstelle zurück und stellt den Anschlusslieferanten dar, der den Port erstellt hat.  
  
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) stellt eine Liste von `IDebugPortSupplier`\-Schnittstellen dar \(die `IEnumDebugPortSuppliers`\-Schnittstelle wird von [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)abgerufen und stellt alle Anschlusslieferanten dar, die mit [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]registriert sein\).  
  
 Ein Debuggen Modul in der Regel interagiert nicht mit einem Anschlusslieferanten.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDebugPortSupplier2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetPortSupplierName](../../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md)|Ruft den Namen des Anschlusslieferanten ab oder legt diese fest.|  
|[GetPortSupplierId](../../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)|Ruft den Bezeichner des Anschlusslieferanten ab oder legt diese fest.|  
|[GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md)|Ruft einen Port aus einem Anschlusslieferanten ab.|  
|[EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)|Listet die Anschlüsse, die bereits vorhanden sind.|  
|[CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)|Überprüft, ob ein Anschluss lieferant das Hinzufügen neuer Anschlüssen unterstützt.|  
|[Port hinzufügen](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)|Fügt einen Port hinzufügen.|  
|[RemovePort](../../../extensibility/debugger/reference/idebugportsupplier2-removeport.md)|Entfernt einen Anschluss.|  
  
## Hinweise  
 Ein Port lieferant ID und kann anhand des Namens identifizieren, Ports hinzufügen und entfernen und alle Ports auflisten, die der Port lieferant bereitstellt.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)   
 [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)   
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)