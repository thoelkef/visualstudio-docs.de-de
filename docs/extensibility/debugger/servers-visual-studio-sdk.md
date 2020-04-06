---
title: Server (Visual Studio SDK) | Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712898"
---
# <a name="servers-visual-studio-sdk"></a>Server (Visual Studio SDK)
In der Debuggerarchitektur wird ein *Server*:

- Ist ein Container von Ports und Port-Lieferanten und kommuniziert Ports und Port-Lieferanten an den Sitzungsdebug-Manager (SDM) und Debug-Engines.

- Kann sich anhand des Namens identifizieren und seine Ports und Hafenlieferanten aufzählen.

- Wird durch eine [IDebugCoreServer2-Schnittstelle](../../extensibility/debugger/reference/idebugcoreserver2.md) dargestellt, die nur von Visual Studio implementiert wird (eine Instanz eines Servers für jede Instanz von Visual Studio, die ausgeführt wird).

## <a name="see-also"></a>Weitere Informationen
- [Ports](../../extensibility/debugger/ports.md)
- [Hafenlieferanten](../../extensibility/debugger/port-suppliers.md)
- [Debuggerkonzepte](../../extensibility/debugger/debugger-concepts.md)
- [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)
