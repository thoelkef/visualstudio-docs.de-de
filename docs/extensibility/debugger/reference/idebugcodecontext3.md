---
title: "IDebugCodeContext3 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugCodeContext3-Schnittstelle"
ms.assetid: 524eb882-0ad5-4bfb-95eb-eb3abb3d0237
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCodeContext3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Erweitert die [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)\-Schnittstelle, um den Abruf des Moduls und der Prozess Schnittstellen zu aktivieren.  
  
## Syntax  
  
```  
IDebugCodeContext3 : IDebugCodeContext2  
```  
  
## Hinweise für Implementierer  
 Wird von Debugsymbolinformationen auf Module und durch das Debuggen Paket [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] genutzt.  
  
## Methoden  
 Zusätzlich zu den Methoden der `IDebugCodeContext2`\-Schnittstelle implementiert diese Schnittstelle die folgenden Methoden:  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetModule](../../../extensibility/debugger/reference/idebugcodecontext3-getmodule.md)|Ruft einen Verweis auf die Schnittstelle des Debugmoduls ab.|  
|[GetProcess](../../../extensibility/debugger/reference/idebugcodecontext3-getprocess.md)|Ruft einen Verweis auf die Schnittstelle Debuggen des Prozesses ab.|  
  
## Hinweise  
 Hierbei handelt es sich um eine optionale Schnittstelle, die im Allgemeinen nicht implementiert werden muss.  
  
## Anforderungen  
 Header: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll