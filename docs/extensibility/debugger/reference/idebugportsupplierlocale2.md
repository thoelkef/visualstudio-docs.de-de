---
title: "IDebugPortSupplierLocale2 | Microsoft Docs"
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
  - "IDebugPortSupplierLocale2-Schnittstelle"
ms.assetid: 910e7220-da2a-4339-9fff-9fb1bad3c28c
caps.latest.revision: 4
caps.handback.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPortSupplierLocale2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Bietet Unterstützung für das Gebietsschema für den Anschlusslieferanten.  
  
## Syntax  
  
```  
IDebugPortSupplierLocale2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 Ein benutzerdefinierter Port lieferant implementiert diese Schnittstelle, um das Gebietsschema festlegen.  
  
## Methoden  
 In der folgenden Tabelle werden die Methoden von **IDebugPortSupplierLocale2**an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[SetLocale](../../../extensibility/debugger/reference/idebugportsupplierlocale2-setlocale.md)|Legt das Gebietsschema für den Anschlusslieferanten ab.|  
  
## Anforderungen  
 Header: Portpriv.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)