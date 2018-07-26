---
title: Portieren von Lieferanten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5385e006bcd2f79ab7b1c2e723e696b833991f36
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2018
ms.locfileid: "39252348"
---
# <a name="port-suppliers"></a>Portanbieter
Architektur der Debugger eine *anschlusslieferant*:  
  
-   Von einem Server enthalten ist, und bietet von Ports für die Anforderung für diesen Server.  
  
-   Können hinzufügen und entfernen Sie die Ports auf dem Server enthält.  
  
-   Alle Ports, die sie mit dem Server bereitgestellt wurde, können aufgezählt werden.  
  
-   Wird durch dargestellt eine [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) -Schnittstelle, die mit Visual Studio über die Registrierung registriert ist. Diese Schnittstelle abgerufen werden kann, durch den Aufruf [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md).  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bietet eine Standard-anschlusslieferant und einen Standardport. Wenn ein benutzerdefinierter Port implementiert werden muss, muss ein benutzerdefinierten Port Lieferanten ebenfalls implementiert werden, um diese benutzerdefinierte Ports angeben.  
  
## <a name="see-also"></a>Siehe auch  
 [Server](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Ports](../../extensibility/debugger/ports.md)   
 [Debuggerkonzepte](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)