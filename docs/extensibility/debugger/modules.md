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
ms.openlocfilehash: cdcaa4afb2191c80a8b5bed1bedf68f4c217f029
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55008308"
---
# <a name="modules"></a>Module
Im Hinblick auf die Debugger-Architektur eine *Modul*:  
  
-   Ist ein physischer Container von Code, z.B. eine ausführbare Datei oder eine DLL-Datei.  
  
-   Laden die Symbole und selbst beschreiben können. Modulbeschreibungen werden im Fenster "Module" von der IDE angezeigt.  
  
-   Wird durch dargestellt eine [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) Schnittstelle, die von einer Debug-Engine, um das Modul beschreiben erstellt.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggerkonzepte](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)