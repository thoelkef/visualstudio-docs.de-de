---
title: "Port-Lieferanten | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Port-Lieferanten"
  - "Debuggen [Debugging-SDK], port Lieferanten"
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Port-Lieferanten
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Im Hinblick auf die Architektur der Debugger ein **Anschluss lieferant**:  
  
-   Wird von einem Server und Anschlüsse Anforderung auf diesem Server bereitgestellt werden.  
  
-   Anschlüsse kann das vom enthaltenden Server hinzufügen und entfernen.  
  
-   Es können alle Ports auflisten, die auf dem Server bereitgestellt hat.  
  
-   Wird von einer [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)\-Schnittstelle dargestellt, die in Visual Studio in der Registrierung registriert ist.  Diese Schnittstelle kann abgerufen werden, indem [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)aufruft.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] stellt einen standardmäßigen Anschlusslieferanten und einen standardmäßigen Anschluss.  Wenn ein benutzerdefinierter Anschluss implementiert werden muss, muss ein benutzerdefinierter Port lieferant ebenfalls implementiert werden, um die benutzerdefinierte Ports anzugeben.  
  
## Siehe auch  
 [Server](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Ports](../../extensibility/debugger/ports.md)   
 [Debugger\-Konzepte](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)