---
title: "IDebugDynamicFieldCOMPlus | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugDynamicFieldCOMPlus-Schnittstelle"
ms.assetid: c3a25f27-327a-4bdb-b026-27d436ddcd0c
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDynamicFieldCOMPlus
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Stellt ein dynamisches Feld für ein [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)\-Objekt dar.  
  
## Syntax  
  
```  
IDebugDynamicFieldCOMPlus : IDebugDynamicField  
```  
  
## Methoden  
 Zusätzlich zu den Methoden der [IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md)\-Schnittstelle implementiert diese Schnittstelle die folgenden Methoden:  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetTypeFromPrimitive](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus-gettypefromprimitive.md)|Ruft einen angegebenen Typ sein Typ ab.|  
|[GetTypeFromTypeDef](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus-gettypefromtypedef.md)|Ruft einen angegebenen Typ das Token ab.|  
  
## Anforderungen  
 Header: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll