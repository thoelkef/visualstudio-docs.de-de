---
title: Server (Visual Studio SDK) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e79e5e00bb4708359c19fd6a2ff95c7f31fd1179
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47524842"
---
# <a name="servers-visual-studio-sdk"></a>Server (Visual Studio SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Servern (Visual Studio SDK)](https://docs.microsoft.com/visualstudio/extensibility/debugger/servers-visual-studio-sdk).  
  
Im Hinblick auf die Debugger-Architektur eine **Server**:  
  
-   Ist ein Container für Ports und Portanbieter und wird verwendet, um die Ports und Portanbieter mit der Sitzungs-Manager (SDM) kommunizieren und debug-Engines.  
  
-   Können Sie sich selbst identifizieren, anhand des Namens und listet die Ports und Portanbieter.  
  
-   Wird durch dargestellt eine [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md) -Schnittstelle, die nur von Visual Studio (eine Instanz eines Servers für jede Instanz von Visual Studio ausgeführt wird) implementiert wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Ports](../../extensibility/debugger/ports.md)   
 [Portanbieter](../../extensibility/debugger/port-suppliers.md)   
 [Debuggerkonzepte](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)

