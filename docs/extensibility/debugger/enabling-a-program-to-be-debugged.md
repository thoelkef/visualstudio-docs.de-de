---
title: Aktivieren eines Zullassensprogramms | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 17c6218cd0b25c0cf0134351fd5efd7490b6a1f3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738897"
---
# <a name="enable-a-program-to-be-debugged"></a>Aktivieren des Debuggens eines Programms
Bevor Ihr Debugmodul (DE) ein Programm debuggen kann, müssen Sie zuerst die DE starten oder an ein vorhandenes Programm anfügen.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Holen Sie sich einen Port](../../extensibility/debugger/getting-a-port.md) Erläutert, wie ein Port als erster Schritt zum Debuggen eines Programms erhalten wird.

 [Registrieren des Programms](../../extensibility/debugger/registering-the-program.md) Erläutert den nächsten Schritt, in dem ein Programm gedebuggiert werden kann: Registrieren beim Port. Nach der Registrierung kann das Programm entweder durch das Anhängen oder das Just-in-Time-Debuggen (JIT) gedebuggég werden.

 [An das Programm anhängen](../../extensibility/debugger/attaching-to-the-program.md) Erläutert den nächsten Schritt: Anfügen des Debuggers an das Programm.

 [Launch-basiertes Anfügen](../../extensibility/debugger/launch-based-attachment.md) Beschreibt die startbasierte Anlage zu einem Programm, die beim Start durch das SDM automatisch erfolgt.

 [Senden der erforderlichen Ereignisse](../../extensibility/debugger/sending-the-required-events.md) Führt Sie beim Erstellen eines Debugmoduls (DE) und Anfügen an ein Programm die erforderlichen Ereignisse durch.

## <a name="related-sections"></a>Verwandte Abschnitte
 [Erstellen eines benutzerdefinierten Debugmoduls](../../extensibility/debugger/creating-a-custom-debug-engine.md) Definiert ein Debugmodul (DE) und beschreibt Dienste, die über die DE-Schnittstellen implementiert wurden, und beschreibt, wie sie dazu führen können, dass der Debugger zwischen verschiedenen Betriebsmodi wechselt.
