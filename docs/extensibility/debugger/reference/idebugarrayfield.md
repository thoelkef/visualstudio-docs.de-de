---
title: "IDebugArrayField | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugArrayField"
helpviewer_keywords: 
  - "IDebugArrayField-Schnittstelle"
ms.assetid: 9667b0a5-4295-46cc-9388-b75c1350be15
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugArrayField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle beschreibt ein Array oder ein Symbol Typ.  
  
## Syntax  
  
```  
IDebugArrayField : IDebugContainerField  
```  
  
## Hinweise für Implementierer  
 Der Anbieter implementiert diese Schnittstelle Symbol für dasselbe Objekt, das die [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)\-Schnittstelle implementiert.  Diese Schnittstelle ist eine Spezialisierung, die Arrayobjekte darstellt.  
  
## Hinweise für Aufrufer  
 Verwenden Sie [QueryInterface](/visual-cpp/atl/queryinterface) , um diese Schnittstelle aus der [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)\-Schnittstelle abzurufen, wenn [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) das Flag `FIELD_TYPE_ARRAY`zurückgibt.  
  
## Methoden in die Vtable\-Reihenfolge  
 Zusätzlich zu den Methoden für den [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) und Schnittstellen implementiert diese Schnittstelle Folgendes:  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetNumberOfElements](../../../extensibility/debugger/reference/idebugarrayfield-getnumberofelements.md)|Ruft die Anzahl der Elemente im Array ab.|  
|[GetElementType](../../../extensibility/debugger/reference/idebugarrayfield-getelementtype.md)|Ruft den Typ des Elements im Array ab.|  
|[GetRank](../../../extensibility/debugger/reference/idebugarrayfield-getrank.md)|Ruft den Rang des Arrays ab.|  
  
## Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Symbol\-Provider\-Schnittstellen](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)