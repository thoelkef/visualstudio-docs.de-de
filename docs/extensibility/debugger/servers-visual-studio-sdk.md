---
title: "Server (Visual Studio-SDK) | Microsoft Docs"
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
  - "Debuggen-Servern"
  - "Debuggen von Servern [Debugging-SDK]"
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# Server (Visual Studio-SDK)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Im Hinblick auf die Architektur der Debugger ein **Server**:  
  
-   Ist ein Container Ports und Anschlusslieferanten und wird verwendet, um Ports auf die Sitzung und Anschlusslieferanten Debuggen Manager \(SDM\) und debuggen Module.  
  
-   Kann sich anhand ihres Namens identifizieren und listet seine Ports und Anschlusslieferanten auf.  
  
-   Wird von einer [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)\-Schnittstelle dargestellt, die nur von Visual Studio implementiert wird \(eine Instanz eines Servers für jede Instanz von Visual Studio\-Betriebs\).  
  
## Siehe auch  
 [Ports](../../extensibility/debugger/ports.md)   
 [Port\-Lieferanten](../../extensibility/debugger/port-suppliers.md)   
 [Debugger\-Konzepte](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)