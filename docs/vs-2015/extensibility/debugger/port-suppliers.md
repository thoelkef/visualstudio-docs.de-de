---
title: Portieren von Lieferanten | Microsoft-Dokumentation
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
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3be95dfdb84f373730d087e9d6da1096891770af
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47515839"
---
# <a name="port-suppliers"></a>Portanbieter
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Portanbieter](https://docs.microsoft.com/visualstudio/extensibility/debugger/port-suppliers).  
  
Im Hinblick auf die Debugger-Architektur eine **anschlusslieferant**:  
  
-   Von einem Server enthalten ist, und bietet von Ports für die Anforderung für diesen Server.  
  
-   Können hinzufügen und entfernen Sie die Ports auf dem Server enthält.  
  
-   Alle Ports, die sie mit dem Server bereitgestellt wurde, können aufgezählt werden.  
  
-   Wird durch dargestellt eine [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) -Schnittstelle, die mit Visual Studio über die Registrierung registriert ist. Diese Schnittstelle abgerufen werden kann, durch den Aufruf [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md).  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] bietet eine Standard-anschlusslieferant und einen Standardport. Wenn ein benutzerdefinierter Port implementiert werden muss, muss ein benutzerdefinierten Port Lieferanten ebenfalls implementiert werden, um diese benutzerdefinierte Ports angeben.  
  
## <a name="see-also"></a>Siehe auch  
 [Server](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Ports](../../extensibility/debugger/ports.md)   
 [Debuggerkonzepte](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)

