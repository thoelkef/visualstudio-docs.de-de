---
title: Ports | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b0da318ac0845cdfe074847eecadcfb12138e447
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62925462"
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