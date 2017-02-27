---
title: "IDebugPortSupplierEx2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugPortSupplierEx2-Schnittstelle"
ms.assetid: dae0050a-a50a-4f35-bfbd-e538f537b20f
caps.latest.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugPortSupplierEx2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Stellt Unterstützung für einen Port lieferant mit einem zentralen Server ausgewählt und interagiert.  
  
## Syntax  
  
```  
IDebugPortSupplierEx2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 Ein benutzerdefinierter Port lieferant implementiert diese Schnittstelle, sodass er den zentralen Server auswählen kann.  
  
## Methoden  
 In der folgenden Tabelle werden die Methoden von **IDebugPortSupplierEx2**an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[SetServer](../../../extensibility/debugger/reference/idebugportsupplierex2-setserver.md)|Legt den zentralen Server für den Anschlusslieferanten ab.|  
  
## Anforderungen  
 Header: Portpriv.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)