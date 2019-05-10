---
title: Server (Visual Studio SDK) | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 56ec28d0d9202bfd72d31e95c53038dd1fa475e9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62912996"
---
# <a name="servers-visual-studio-sdk"></a>Server (Visual Studio SDK)
Architektur der Debugger eine *Server*:

- Ist ein Container für Ports und Portanbieter und Ports und Portanbieter kommuniziert, auf die sitzungsbasierter Debug-Manager (SDM) und die Debug-Engines.

- Können Sie sich selbst identifizieren, anhand des Namens und listet die Ports und Portanbieter.

- Wird durch dargestellt eine [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md) -Schnittstelle, die nur von Visual Studio (eine Instanz eines Servers für jede Instanz von Visual Studio ausgeführt wird) implementiert wird.

## <a name="see-also"></a>Siehe auch
- [Ports](../../extensibility/debugger/ports.md)
- [Portanbieter](../../extensibility/debugger/port-suppliers.md)
- [Debuggerkonzepte](../../extensibility/debugger/debugger-concepts.md)
- [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)