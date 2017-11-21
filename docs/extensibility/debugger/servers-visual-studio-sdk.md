---
title: Server (Visual Studio SDK) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 496e9b361dbb7f5c3eb5cf5197a1351a1182af3e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="servers-visual-studio-sdk"></a>Server (Visual Studio SDK)
Im Hinblick auf die Architektur des Debuggers einen **Server**:  
  
-   Ist ein Container für Ports und Port Lieferanten und wird verwendet, um mit der Sitzungs-Manager (SDM) Ports und Port Lieferanten kommunizieren und Debuggen von Modulen.  
  
-   Können Sie anhand des Namens identifiziert und die Ports und Port Lieferanten auflisten.  
  
-   Dargestellt durch eine [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md) -Schnittstelle, die nur von Visual Studio (eine Instanz eines Servers für jede Instanz von Visual Studio ausgeführt wird) implementiert wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Ports](../../extensibility/debugger/ports.md)   
 [Port-Lieferanten](../../extensibility/debugger/port-suppliers.md)   
 [Debugger-Konzepte](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)