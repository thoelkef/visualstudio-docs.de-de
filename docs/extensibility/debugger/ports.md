---
title: Ports | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f925bda151809bb4554fcfed7f46131d51a25179
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351519"
---
# <a name="ports"></a>Ports
Architektur der Debugger eine *Port*:

- Ist ein Container für eine Reihe von Prozessen auf einem Server ausgeführt werden. Beispielsweise kann ein Port eine Verbindung mit einem Windows CE-basierten Gerät durch ein serielles Kabel oder an einen Computer im Netzwerk nicht-DCOM darstellen. Ein spezieller Port wird aufgerufen, den lokalen Port, enthält alle auf dem lokalen Computer ausgeführten Prozesse.

- Kann sich selbst nach Name oder ID identifizieren.

- Können Auflisten aller Prozesse, die auf den Port ausgeführt wird, und starten und die folgenden Prozesse beendet.

- Wird durch dargestellt eine [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) -Schnittstelle, die übergeben wurde ein [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) Argument [Port hinzufügen](../../extensibility/debugger/reference/idebugportsupplier2-addport.md).

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Stellt einen Standardport, der alle Windows-basierten Prozesse systemeigenen und verwalteten behandelt. Ein benutzerdefinierter Port muss für Verbindungen mit externen Geräten eingerichtet werden, die nicht Windows-basiert sind. Um diese benutzerdefinierte Ports angeben, müssen Sie auch einen benutzerdefinierten Port Lieferanten einrichten.

## <a name="see-also"></a>Siehe auch
- [Server](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [Prozesse](../../extensibility/debugger/processes.md)
- [Debuggerkonzepte](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)
- [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)
- [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)