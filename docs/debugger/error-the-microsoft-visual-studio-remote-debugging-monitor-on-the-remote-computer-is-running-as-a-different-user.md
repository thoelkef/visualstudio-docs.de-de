---
title: "Fehler: Der Microsoft Visual Studio-Remotedebugmonitor auf dem Remotecomputer ausgeführt wird als ein anderer Benutzer | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- -anyuser option
- anyuser option
- Remote Debugging Monitor
- remote debugging, Remote Debugging Monitor
- msvsmon.exe
ms.assetid: e5b18734-2daf-4c58-b5de-24ae1295703e
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5f3f2c9e0b3f88734d21ae06f1af48409c58766a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user"></a>Fehler: Der Microsoft Visual Studio-Remotedebugmonitor auf dem Remotecomputer wird als anderer Benutzer ausgeführt
Wenn Sie versuchen, Remotedebuggen auszuführen, wird möglicherweise folgende Fehlermeldung angezeigt:  
  
 Der Microsoft Visual Studio-Remotedebugmonitor auf dem Remotecomputer wird als anderer Benutzer ausgeführt.  
  
## <a name="cause"></a>Ursache  
 Diese Meldung wird angezeigt, wenn Sie sich im Modus "Keine Authentifizierung debuggen" befinden, und der Benutzer, der "msvsmon" gestartet hat, nicht mit dem Benutzer identisch ist, der Visual Studio ausführt.  
  
## <a name="solution"></a>Lösung  
 Die sicherste und beste Lösung besteht darin, den Remotedebugmonitor (msvsmon.exe) unter demselben Benutzerkonto auszuführen wie Visual Studio. Wenn dies nicht möglich ist, können Sie Remotedebugmonitor unter dem anderen Konto Ausführen der **jeder Benutzer Debuggen** des Remotedebugmonitors die Option **Optionen** (Dialogfeld).  
  
> [!CAUTION]
>  Indem anderen Benutzern die Berechtigung zum Herstellen einer Verbindung gewährt wird, besteht die Möglichkeit, dass unbeabsichtigt eine Verbindung mit der falschen Remotedebugsitzung hergestellt wird. Debuggen in **keine Authentifizierung** Modus ist immer unsicher und sollte mit Vorsicht verwendet werden.
  
## <a name="see-also"></a>Siehe auch  
 [Remotedebuggen – Fehler und Problembehandlung](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remotedebuggen](../debugger/remote-debugging.md)