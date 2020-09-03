---
title: Port Lieferanten | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e90871927c30399dea4691381baa749db2b3e8bf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153704"
---
# <a name="port-suppliers"></a>Portanbieter
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Im Hinblick auf die Debugger-Architektur ist ein **Port Lieferant**:  
  
- Ist in einem Server enthalten und stellt Ports auf Anforderung an diesen Server bereit.  
  
- Kann Ports hinzufügen und aus dem enthaltenden Server entfernen.  
  
- Kann alle Ports auflisten, die Sie auf dem Server bereitgestellt haben.  
  
- Wird durch eine [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) -Schnittstelle dargestellt, die in Visual Studio über die Registrierung registriert ist. Diese Schnittstelle kann durch Aufrufen von [getportsupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)abgerufen werden.  
  
  [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] stellt einen standardportlieferant und einen Standardport bereit. Wenn ein benutzerdefinierter Port implementiert werden muss, muss auch ein benutzerdefinierter Port Lieferant implementiert werden, um diese benutzerdefinierten Ports bereitzustellen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Webserver](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Landungen](../../extensibility/debugger/ports.md)   
 [Debugger-Konzepte](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
