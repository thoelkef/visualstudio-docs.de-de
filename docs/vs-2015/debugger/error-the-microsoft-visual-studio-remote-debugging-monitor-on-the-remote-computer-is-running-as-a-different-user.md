---
title: 'Fehler: Der Microsoft Visual Studio-Remotedebugmonitor auf dem Remotecomputer wird als ein anderer Benutzer ausgeführt | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- -anyuser option
- anyuser option
- Remote Debugging Monitor
- remote debugging, Remote Debugging Monitor
- msvsmon.exe
ms.assetid: e5b18734-2daf-4c58-b5de-24ae1295703e
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5256feb22e09eb75fa8f4d5a50e8beafeec8f97d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47515374"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user"></a>Fehler: Der Microsoft Visual Studio-Remotedebugmonitor auf dem Remotecomputer wird als anderer Benutzer ausgeführt
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Fehler: der Microsoft Visual Studio-Remotedebugmonitor auf dem Remotecomputer ausgeführt wird, als ein anderer Benutzer](https://docs.microsoft.com/visualstudio/debugger/error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user).  
  
Wenn Sie versuchen, Remotedebuggen auszuführen, wird möglicherweise folgende Fehlermeldung angezeigt:  
  
 Der Microsoft Visual Studio-Remotedebugmonitor auf dem Remotecomputer wird als anderer Benutzer ausgeführt.  
  
## <a name="cause"></a>Ursache  
 Diese Meldung wird angezeigt, wenn Sie sich im Modus "Keine Authentifizierung debuggen" befinden, und der Benutzer, der "msvsmon" gestartet hat, nicht mit dem Benutzer identisch ist, der Visual Studio ausführt.  
  
## <a name="solution"></a>Lösung  
 Die sicherste und beste Lösung besteht darin, den Remotedebugmonitor (msvsmon.exe) unter demselben Benutzerkonto auszuführen wie Visual Studio. Wenn dies nicht möglich ist, können Sie Remotedebugmonitor ausführen, unter dem anderen Konto mit der **ermöglichen allen Benutzern das Debugging** des Remotedebugmonitors die Option **Optionen** Dialogfeld.  
  
> [!CAUTION]
>  Indem anderen Benutzern die Berechtigung zum Herstellen einer Verbindung gewährt wird, besteht die Möglichkeit, dass unbeabsichtigt eine Verbindung mit der falschen Remotedebugsitzung hergestellt wird. Debuggen in **keine Authentifizierung** Modus ist immer unsicher und sollte mit Vorsicht verwendet werden.  
  
 Weitere Informationen finden Sie unter [Starten des Remotedebugmonitors](http://msdn.microsoft.com/library/55b60ce7-834b-4e83-a10e-fe4248260a4c).  
  
## <a name="see-also"></a>Siehe auch  
 [Remotedebuggen – Fehler und Problembehandlung](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remotedebuggen](../debugger/remote-debugging.md)



