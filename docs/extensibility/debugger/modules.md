---
title: Module | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- modules
- debugging [Debugging SDK], modules
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b231ee1eb84f41115a0892cda42a8b7e781e5e53
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350675"
---
# <a name="modules"></a>Module
Im Hinblick auf die Debugger-Architektur eine *Modul*:

- Ist ein physischer Container von Code, z.B. eine ausführbare Datei oder eine DLL-Datei.

- Laden die Symbole und selbst beschreiben können. Modulbeschreibungen werden im Fenster "Module" von der IDE angezeigt.

- Wird durch dargestellt eine [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) Schnittstelle, die von einer Debug-Engine, um das Modul beschreiben erstellt.

## <a name="see-also"></a>Siehe auch
- [Debuggerkonzepte](../../extensibility/debugger/debugger-concepts.md)
- [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)