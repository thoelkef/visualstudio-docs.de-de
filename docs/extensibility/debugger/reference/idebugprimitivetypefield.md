---
title: "IDebugPrimitiveTypeField | Microsoft Docs"
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
  - "IDebugPrimitiveTypeField-Schnittstelle"
ms.assetid: 73a428fd-797e-4ceb-8392-ba16f1c5226b
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPrimitiveTypeField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Stellt einen Typ enumerationswert aus einer [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)\-Schnittstelle dar.  
  
## Syntax  
  
```  
IDebugPrimitiveTypeField : IDebugField  
```  
  
## Methoden  
 Zusätzlich zu den Methoden der [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)\-Schnittstelle implementiert diese Schnittstelle die folgende Methode:  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetPrimitiveType](../../../extensibility/debugger/reference/idebugprimitivetypefield-getprimitivetype.md)|Ruft den Typ ab, dem dieses Feld zugeordnet ist.|  
  
## Anforderungen  
 Header: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll