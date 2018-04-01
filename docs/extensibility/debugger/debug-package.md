---
title: Debug-Paket | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
caps.latest.revision: 9
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: a2cbb124dcb2d2d7a0bbcba1bc57eb3c704dd770
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
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