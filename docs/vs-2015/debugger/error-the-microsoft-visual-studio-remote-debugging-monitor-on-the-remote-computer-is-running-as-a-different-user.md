---
title: 'Fehler: Der Microsoft Visual Studio-Remotedebugmonitor auf dem Remotecomputer wird als ein anderer Benutzer ausgeführt | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
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
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2961aed55df241bce3c67eaa4c8630bac1e65f65
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51722122"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user"></a>Fehler: Der Microsoft Visual Studio-Remotedebugmonitor auf dem Remotecomputer wird als anderer Benutzer ausgeführt
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
 [Remote Debugging](../debugger/remote-debugging.md)



