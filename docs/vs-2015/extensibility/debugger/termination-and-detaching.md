---
title: Beendigung und trennen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d92fe88826baf19ba66b200990aee7797e91f87b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68176672"
---
# <a name="termination-and-detaching"></a>Beenden und Trennen
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Im folgenden wird die normale Beendigung von beschrieben.  
  
## <a name="discussion"></a>Diskussion (Discussion)  
 Wenn die [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) -oder [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) -Schnittstelle fortgesetzt wird und keine Haltepunkte, Ausnahmen, Laufzeitfehler oder Endlosschleifen in der zu debuggenden Anwendung vorhanden sind, wird das Programm, das gedebuggt wird, bis zum Abschluss ausgeführt. Dies ist der normale Abbruch.  
  
 Zum Implementieren der normalen Beendigung müssen Sie ein [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) senden. Hierfür muss die [IDebugProgramDestroyEvent2:: getexitcode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) -Methode implementiert werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen einer benutzerdefinierten Debug-Engine](../../extensibility/debugger/creating-a-custom-debug-engine.md)
