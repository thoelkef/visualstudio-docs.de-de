---
title: Server (Visual Studio SDK) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7ed2ce924b22827a82a67664e3e473f0930a87e3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199405"
---
# <a name="servers-visual-studio-sdk"></a>Server (Visual Studio SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Im Hinblick auf die Debugger-Architektur ist ein **Server**:  
  
- Bei handelt es sich um einen Container von Ports und Port Lieferanten, der zum Kommunizieren von Ports und Port Lieferanten an den sitzungsdebug-Manager (SDM) und die Debug-engines verwendet wird.  
  
- Kann sich selbst anhand des Namens identifizieren und seine Ports und Port Lieferanten auflisten.  
  
- Wird durch eine [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md) -Schnittstelle dargestellt, die nur von Visual Studio implementiert wird (eine Instanz eines Servers für jede Instanz von Visual Studio, die ausgeführt wird).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Landungen](../../extensibility/debugger/ports.md)   
 [Port Lieferanten](../../extensibility/debugger/port-suppliers.md)   
 [Debugger-Konzepte](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)
