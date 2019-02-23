---
title: Verarbeiten von Debug-Manager | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- machine debug manager
- debugging [Debugging SDK], Machine Debug Manager
ms.assetid: d0861e0c-b819-490c-9604-5e6d08ac291a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9f6a93cc87be2369ba3bc96bf6682caeb4a727c9
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56718936"
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