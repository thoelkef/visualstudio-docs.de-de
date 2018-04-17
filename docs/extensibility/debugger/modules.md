---
title: Module | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- modules
- debugging [Debugging SDK], modules
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f587e015263336436588d14edeeb5c6935872950
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="modules"></a>Module
Im Hinblick auf die Architektur des Debuggers einen **Modul**:  
  
-   Ist ein physischen Container von Code, z. B. eine ausführbare Datei oder DLL.  
  
-   Laden die Symbole und selbst beschreiben können. Modulbeschreibungen werden im Fenster "Module" von der IDE angezeigt.  
  
-   Wird durch dargestellt ein [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) Schnittstelle, die erstellt, indem ein Debugmodul an das Modul zu beschreiben.  
  
## <a name="see-also"></a>Siehe auch  
 [Debugger-Konzepte](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)