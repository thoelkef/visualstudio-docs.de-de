---
title: Module | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- modules
- debugging [Debugging SDK], modules
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8371bb2fd985062f6e44d97ae720878ad54b06d3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="modules"></a>Module
Im Hinblick auf die Architektur des Debuggers einen **Modul**:  
  
-   Ist ein physischen Container von Code, z. B. eine ausführbare Datei oder DLL.  
  
-   Laden die Symbole und selbst beschreiben können. Modulbeschreibungen werden im Fenster "Module" von der IDE angezeigt.  
  
-   Wird durch dargestellt ein [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) Schnittstelle, die erstellt, indem ein Debugmodul an das Modul zu beschreiben.  
  
## <a name="see-also"></a>Siehe auch  
 [Debugger-Konzepte](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)