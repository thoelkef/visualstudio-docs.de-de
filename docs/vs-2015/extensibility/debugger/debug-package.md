---
title: Paket Debuggen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dda8b1ac6eaa2cd5352d441600ae720c3aac321c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68181289"
---
# <a name="debug-package"></a>Debuggen eines Pakets
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Das Debugpaket wird in der Visual Studio-Shell ausgeführt und verarbeitet die gesamte Benutzeroberfläche. Dabei werden die Visual Studio-debuggingschnittstellen verarbeitet und mit dem sitzungsdebug-Manager (SDM) kommuniziert.  
  
 Break-Ereignisse, die über den SDM gesendet werden, wechseln den Debugger vom Lauf Modus in den Break-Modus und ändern den Fokus auf das Programm, in dem die Unterbrechung aufgetreten ist Das Debugpaket verfolgt den Stapel Rahmen und den Thread aus den Informationen, die von den Ereignissen an ihn gesendet werden.  
  
 Das Debugpaket hat keine sprach-oder Lauf Zeit Umgebungs Abhängigkeiten. Das Debugpaket muss nicht implementiert oder geändert werden.  
  
 Das Debugpaket wird von vsdebug.dll implementiert.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sitzungs-Debug-Manager](../../extensibility/debugger/session-debug-manager.md)   
 [Stapel Rahmen](../../extensibility/debugger/stack-frames.md)   
 [Threads](../../extensibility/debugger/threads.md)   
 [Debuggerkomponenten](../../extensibility/debugger/debugger-components.md)
