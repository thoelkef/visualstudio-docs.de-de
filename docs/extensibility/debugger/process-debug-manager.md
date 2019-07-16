---
title: Verarbeiten von Debug-Manager | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- machine debug manager
- debugging [Debugging SDK], Machine Debug Manager
ms.assetid: d0861e0c-b819-490c-9604-5e6d08ac291a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c362ceb6321c49f4e868d2ae00c417e6ba6e2cee
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351450"
---
# <a name="process-debug-manager"></a>Prozessbasierter Debug-manager
Prozessbasierter Debug-Manager (PDM) ist eine Komponente von Visual Studio, die Programme verwaltet, und Prozesse, sodass sie für die Sitzung verfügbar Debuggen, Manager und die Debug-Engines.

 Das PDM verwaltet alle Prozesse, die debuggt werden können. Um gedebuggt zu werden, muss ein Programm mit der PDM registriert werden. Diese Registrierung erfolgt zum Zeitpunkt, die das Programm, indem Sie entweder einen Port oder einer Debug-Engine gestartet wird.

## <a name="see-also"></a>Siehe auch
- [Prozesse](../../extensibility/debugger/processes.md)
- [Debug-engine](../../extensibility/debugger/debug-engine.md)
- [Ports](../../extensibility/debugger/ports.md)
- [Programme](../../extensibility/debugger/programs.md)
- [Debugger-Komponenten](../../extensibility/debugger/debugger-components.md)