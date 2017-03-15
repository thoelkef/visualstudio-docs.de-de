---
title: "IDebugModOpt | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugModOpt-Schnittstelle"
ms.assetid: ebd525e3-d140-4071-9d8c-41871de4125e
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugModOpt
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Stellt einen Debugbuild optionaler Modifizierer dar.  
  
## Syntax  
  
```  
IDebugModOpt : IUnknown  
```  
  
## Hinweise für Aufrufer  
 Abrufen von einem [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)\-Objekt, das eine Klasse oder eine Methode darstellt.  
  
## Methoden  
 Diese Schnittstelle implementiert die folgende Weise:  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetModOpts](../../../extensibility/debugger/reference/idebugmodopt-getmodopts.md)|Ruft eine Liste optionaler Modifizierer ab.|  
  
## Anforderungen  
 Header: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll