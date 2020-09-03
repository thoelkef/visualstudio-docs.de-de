---
title: Server (Visual Studio SDK) | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 32fdbb5afca40c3b4fced468d2f9ef0ea5226c00
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712898"
---
# <a name="servers-visual-studio-sdk"></a>Server (Visual Studio SDK)
In der Debugger-Architektur ist ein *Server*:

- Ist ein Container von Ports und Port Lieferanten und kommuniziert Ports und Port Lieferanten mit dem sitzungsdebug-Manager (SDM) und Debug-engines.

- Kann sich selbst anhand des Namens identifizieren und seine Ports und Port Lieferanten auflisten.

- Wird durch eine [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md) -Schnittstelle dargestellt, die nur von Visual Studio implementiert wird (eine Instanz eines Servers für jede Instanz von Visual Studio, die ausgeführt wird).

## <a name="see-also"></a>Weitere Informationen
- [Ports](../../extensibility/debugger/ports.md)
- [Port Lieferanten](../../extensibility/debugger/port-suppliers.md)
- [Debugger-Konzepte](../../extensibility/debugger/debugger-concepts.md)
- [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)
