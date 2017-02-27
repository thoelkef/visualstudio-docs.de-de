---
title: "IEEDataStorage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEEDataStorage"
helpviewer_keywords: 
  - "IEEDataStorage-Schnittstelle"
ms.assetid: 704e932d-2325-410e-89c4-ce88c6ec19da
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IEEDataStorage
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle stellt ein Bytearray dar.  
  
## Syntax  
  
```  
IEEDataStorage : IUnknown  
```  
  
## Hinweise für Implementierer  
 Die Ausdrucksauswertung \(EE\) implementiert diese Schnittstelle, um ein Bytearray darzustellen \(wird durch den Typ schnellansichten, um Daten von der [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)\-Schnittstelle abzurufen und zu ändern.\)  Die EE normalerweise implementiert diese Schnittstelle, um externe Typ schnellansichten zu unterstützen.  
  
## Hinweise für Aufrufer  
 Alle Methoden für die `IPropertyProxyEESide`\-Schnittstelle geben diese Schnittstelle zurück.  [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) Aufruf zum Abrufen der [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)\-Schnittstelle.  Rufen Sie [QueryInterface](/visual-cpp/atl/queryinterface) auf einer Schnittstelle dargestellt [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) zum Abrufen der [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)\-Schnittstelle.  
  
## Methoden in die Vtable\-Reihenfolge  
 Die `IEEDataStorage`\-Schnittstelle implementiert die folgenden Methoden:  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)|Ruft die angegebene Anzahl von Bytes der Daten in einen angegebenen Puffer ab.|  
|[GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)|Ruft die Anzahl der verfügbaren Bytes Daten ab oder legt diese fest.|  
  
## Hinweise  
 Diese Schnittstelle wird von einer Typ schnellansicht auf Daten verwendet, die für ein bestimmtes Objekt angehalten werden.  Die Daten werden als Bytearray behandelt. Dadurch kann der Typ schnellansicht, um sie in bearbeiten, welche Methode erforderlich ist, um sie dem Benutzer darstellt.  
  
 Ein benutzerdefinierter Viewer kann diese Schnittstelle auch verwenden, wenn dies erforderlich ist, obwohl in der Regel einen benutzerdefinierten Viewer eine benutzerdefinierte Schnittstelle, [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) oder [GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md) verwenden würde \(für stringorientierte Daten\).  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [Typ\-Schnellansicht und benutzerdefinierten Viewer](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)