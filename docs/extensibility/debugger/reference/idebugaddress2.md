---
title: "IDebugAddress2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugAddress2"
helpviewer_keywords: 
  - "IDebugAddress2-Schnittstelle"
ms.assetid: b150e0ed-4ac0-4f8c-9732-4b3e54b9d243
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugAddress2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle ermöglicht den Zugriff auf die ID des Prozesses, der das Objekt besitzt, dessen Adresse von dieser Schnittstelle dargestellt wird.  
  
## Syntax  
  
```  
IDebugAddress2 : IDebugAddress  
```  
  
## Hinweise für Implementierer  
 Ein Symbol Anbieter implementiert diese Schnittstelle für dasselbe Objekt, das die [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)\-Schnittstelle implementiert.  Diese Schnittstelle ermöglicht den Zugriff auf die ID des Prozesses, der das Objekt besitzt, das an diese Adresse.  
  
## Hinweise für Aufrufer  
 Verwenden Sie [QueryInterface](/visual-cpp/atl/queryinterface) , um diese Schnittstelle aus der [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)\-Schnittstelle zu erhalten.  
  
## Methoden in die Vtable\-Reihenfolge  
 Zusätzlich zu den Methoden, die von der [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)\-Schnittstelle geerbt werden, implementiert diese Schnittstelle die folgende Methode:  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetProcessID](../../../extensibility/debugger/reference/idebugaddress2-getprocessid.md)|Ruft die ID des Prozesses ab, der das Objekt besitzt, die von dieser Schnittstelle dargestellt wird.|  
  
## Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Symbol\-Provider\-Schnittstellen](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)