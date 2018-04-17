---
title: Portieren von Lieferanten | Microsoft Docs
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
ms.openlocfilehash: 1f1ba09c1802bdeb1c6a402e95a6de408b277532
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="port-suppliers"></a>Port-Lieferanten
Im Hinblick auf die Architektur des Debuggers einen **Port Lieferanten**:  
  
-   Ein Server enthalten ist, und Ports Anforderung für diesen Server enthält.  
  
-   Hinzufügen und Ports vom enthaltenden Server entfernen können.  
  
-   Alle Ports, die sie mit dem Server bereitgestellt wurde, können aufgelistet werden.  
  
-   Dargestellt durch eine [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) -Schnittstelle, die durch die Registrierung mit Visual Studio registriert wurde. Diese Schnittstelle kann abgerufen werden, durch den Aufruf [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md).  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Stellt eine standardmäßige Port Supplier "und" einen Standardport. Wenn ein benutzerdefinierter Port werden implementiert muss, muss ein benutzerdefinierten Port Lieferanten ebenfalls implementiert werden, um die benutzerdefinierte Ports angeben.  
  
## <a name="see-also"></a>Siehe auch  
 [Server](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Ports](../../extensibility/debugger/ports.md)   
 [Debugger-Konzepte](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)