---
title: Portieren von Lieferanten | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5909587cbed118d618ea1605c8a169024028adf0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351463"
---
# <a name="port-suppliers"></a>Portanbieter
Architektur der Debugger eine *anschlusslieferant*:

- Von einem Server enthalten ist, und bietet von Ports für die Anforderung für diesen Server.

- Können hinzufügen und entfernen Sie die Ports auf dem Server enthält.

- Alle Ports, die sie mit dem Server bereitgestellt wurde, können aufgezählt werden.

- Wird durch dargestellt eine [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) -Schnittstelle, die mit Visual Studio über die Registrierung registriert ist. Diese Schnittstelle abgerufen werden kann, durch den Aufruf [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md).

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bietet eine Standard-anschlusslieferant und einen Standardport. Wenn ein benutzerdefinierter Port implementiert werden muss, muss ein benutzerdefinierten Port Lieferanten ebenfalls implementiert werden, um diese benutzerdefinierte Ports angeben.

## <a name="see-also"></a>Siehe auch
- [Server](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [Ports](../../extensibility/debugger/ports.md)
- [Debuggerkonzepte](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)
- [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)