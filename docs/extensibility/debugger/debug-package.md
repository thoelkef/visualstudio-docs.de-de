---
title: Debug-Paket | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6ca438b7ed8c9b6a4b84693f975144040f998f01
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="debug-package"></a>Debug-Paket
Das debugpaket in der Visual Studio-Shell ausgeführt und verarbeitet alle der Benutzeroberfläche. Verarbeitet die Visual Studio Debugschnittstellen und kommuniziert mit der Sitzungs-Manager (SDM).  
  
 Break-Ereignisse, die durch die SDM gesendeten wechseln Sie den Debugger aus Ausführungsmodus Unterbrechungsmodus und ändern Sie den Fokus an das Programm, in dem die Unterbrechung aufgetreten ist. Das debugpaket verfolgt den Stapelrahmen und den Thread aus den Informationen, die an ihn gesendet werden, indem Sie die Ereignisse an.  
  
 Das debugpaket verfügt über keine Sprache oder Abhängigkeiten-Laufzeitumgebung. Es ist nicht erforderlich, das debugpaket zu implementieren.  
  
 Das debugpaket wird vom vsdebug.dll implementiert.  
  
## <a name="see-also"></a>Siehe auch  
 [Sitzungs-Debug-Manager](../../extensibility/debugger/session-debug-manager.md)   
 [Stapelrahmen](../../extensibility/debugger/stack-frames.md)   
 [Threads](../../extensibility/debugger/threads.md)   
 [Debuggerkomponenten](../../extensibility/debugger/debugger-components.md)