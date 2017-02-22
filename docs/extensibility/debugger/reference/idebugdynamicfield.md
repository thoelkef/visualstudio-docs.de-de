---
title: "IDebugDynamicField | Microsoft Docs"
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
  - "IDebugDynamicField"
helpviewer_keywords: 
  - "IDebugDynamicField-Schnittstelle"
ms.assetid: caffbd95-7596-4714-84b1-b964e89a78bb
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDynamicField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle stellt einen Typ Variable dar.  
  
## Syntax  
  
```  
IDebugDynamicField : IDebugField  
```  
  
## Hinweise für Implementierer  
 Diese Schnittstelle wird von Symbol Textanbieter als Basisklasse für jeden Typ implementiert, der zur Laufzeit bestimmt werden kann.  Dies ist nur für verwalteten Code.  
  
## Hinweise für Aufrufer  
 Diese Schnittstelle stellt eine Basisklasse dar, von der spezielle mehr Schnittstellen abgeleitet werden können.  
  
## Methoden in die Vtable\-Reihenfolge  
 Diese Schnittstelle stellt keine Methoden bereit, die andere als die von `IDebugField`vererbt werden.  
  
## Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Symbol\-Provider\-Schnittstellen](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)