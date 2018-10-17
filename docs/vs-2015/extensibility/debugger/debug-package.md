---
title: Debuggen-Pakets | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 61df51b422660a5ea116f136b0d5183e59293a02
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49286324"
---
# <a name="debug-package"></a>Debuggen eines Pakets
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Das debugpaket in der Visual Studio-Shell ausgeführt und verarbeitet alle der Benutzeroberfläche. Es nutzt die Visual Studio Debuggen von Schnittstellen und kommuniziert mit der Sitzungs-Manager (SDM).  
  
 Unterbrechungsbezogene Ereignisse, die durch die SDM gesendete wechseln Ausführungsmodus den Debugger Unterbrechungsmodus ein, und ändern Sie die Anwendung, in dem die Unterbrechung aufgetreten ist. Das debugpaket verfolgt den Stapelrahmen und den Thread aus den Informationen, die an ihn gesendet wird, durch die Ereignisse an.  
  
 Das debugpaket, weist keine Sprache oder Laufzeitumgebung Abhängigkeiten. Es ist nicht erforderlich, das debugpaket zu implementieren.  
  
 Das debugpaket wird von vsdebug.dll implementiert.  
  
## <a name="see-also"></a>Siehe auch  
 [Sitzungsbasierter Debug-Manager](../../extensibility/debugger/session-debug-manager.md)   
 [Stapelrahmen](../../extensibility/debugger/stack-frames.md)   
 [Threads](../../extensibility/debugger/threads.md)   
 [Debuggerkomponenten](../../extensibility/debugger/debugger-components.md)

