---
title: Module | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- modules
- debugging [Debugging SDK], modules
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1f31e3760a0697be8c9fc80eb811c99df79d32b1
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56718910"
---
# <a name="modules"></a>Module
Im Hinblick auf die Debugger-Architektur eine *Modul*:

-   Ist ein physischer Container von Code, z.B. eine ausführbare Datei oder eine DLL-Datei.

-   Laden die Symbole und selbst beschreiben können. Modulbeschreibungen werden im Fenster "Module" von der IDE angezeigt.

-   Wird durch dargestellt eine [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) Schnittstelle, die von einer Debug-Engine, um das Modul beschreiben erstellt.

## <a name="see-also"></a>Siehe auch
- [Debuggerkonzepte](../../extensibility/debugger/debugger-concepts.md)
- [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)