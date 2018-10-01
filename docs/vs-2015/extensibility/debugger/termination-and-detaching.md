---
title: Beenden und trennen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7742ec8ef896006bc00bcbdfcf4961c15acdf746
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47513017"
---
# <a name="termination-and-detaching"></a>Beenden und Trennen
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [beenden und trennen](https://docs.microsoft.com/visualstudio/extensibility/debugger/termination-and-detaching).  
  
Im folgenden wird die normalen Beendigung beschrieben.  
  
## <a name="discussion"></a>Diskussion  
 Nach der [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) oder [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) Schnittstelle wird fortgesetzt, wenn es sind keine Haltepunkte, Ausnahmen, Laufzeitfehlern führen oder Endlosschleifen in der Anwendung, die debuggt werden, das derzeit debuggte Programm wird bis zum Abschluss ausgeführt. Dies ist die normale Beendigung.  
  
 Senden Sie eine [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) normalen Beendigung zu implementieren. Dies erfordert die Implementierung der [IDebugProgramDestroyEvent2::GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen einer benutzerdefinierten Debug-Engine](../../extensibility/debugger/creating-a-custom-debug-engine.md)

