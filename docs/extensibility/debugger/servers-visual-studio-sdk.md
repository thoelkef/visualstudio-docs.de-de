---
title: Server (Visual Studio SDK) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2904641e8188abc6ef2382b2da272a9f96fd0f81
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31125491"
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