---
title: Aktivieren eines Programms zu debuggende | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1f301de66421ef1327b86d900305cb4ecbfb5623
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62889693"
---
# <a name="enable-a-program-to-be-debugged"></a>Aktivieren Sie zu debuggenden Programm
Bevor der Debug-Engine (DE) ein Programm debuggen kann, müssen Sie die DE starten oder fügen Sie ihn an ein vorhandenes Programm.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Erhalten Sie einen Port](../../extensibility/debugger/getting-a-port.md) beschreibt, wie Sie einen Port als der erste Schritt zum Aktivieren eines Programms zu debuggende zu erhalten.

 [Registrieren Sie das Programm](../../extensibility/debugger/registering-the-program.md) wird erläutert, der nächste Schritt bei der Aktivierung der zu debuggenden Programm: Registrieren sie mit dem Port. Nach der Registrierung kann die Anwendung debuggt werden entweder durch den Prozess anfügen oder das Debuggen von just-in-Time (JIT).

 [Anfügen an das Programm](../../extensibility/debugger/attaching-to-the-program.md) im nächsten Schritt erläutert: Anfügen des Debuggers an die Anwendung.

 [Start-basierten anhängen](../../extensibility/debugger/launch-based-attachment.md) beschreibt startbasiertes um ein Programm, das automatisch beim Start durch die SDM ist.

 [Senden Sie die erforderlichen Ereignisse](../../extensibility/debugger/sending-the-required-events.md) führt Sie schrittweise durch die erforderlichen Ereignisse, die beim Erstellen einer Debug-Engine (DE), und fügen Sie diesen mit einem Programm.

## <a name="related-sections"></a>Verwandte Abschnitte
 [Erstellen einer benutzerdefinierten Debug-Engine](../../extensibility/debugger/creating-a-custom-debug-engine.md) eine Debug-Engine (DE) definiert und beschreibt die Dienste, die über die DE-Schnittstellen und wie sie den Debugger für den Übergang zwischen verschiedenen Betriebsmodi verursachen können.