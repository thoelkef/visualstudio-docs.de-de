---
title: "Fehler: Der Microsoft Visual Studio-Remotedebugmonitor auf dem Remotecomputer wird als anderer Benutzer ausgef&#252;hrt | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "anyuser (Option)"
  - "-anyuser (Option)"
  - "msvsmon.exe"
  - "Remote Debug Monitor"
  - "Remotedebuggen, Remote Debug Monitor"
ms.assetid: e5b18734-2daf-4c58-b5de-24ae1295703e
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Fehler: Der Microsoft Visual Studio-Remotedebugmonitor auf dem Remotecomputer wird als anderer Benutzer ausgef&#252;hrt
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn Sie versuchen, Remotedebuggen auszuführen, wird möglicherweise folgende Fehlermeldung angezeigt:  
  
 Der Microsoft Visual Studio\-Remotedebugmonitor auf dem Remotecomputer wird als anderer Benutzer ausgeführt.  
  
## Ursache  
 Diese Meldung wird angezeigt, wenn Sie sich im Modus "Keine Authentifizierung debuggen" befinden, und der Benutzer, der "msvsmon" gestartet hat, nicht mit dem Benutzer identisch ist, der Visual Studio ausführt.  
  
## Lösung  
 Die sicherste und beste Lösung besteht darin, den Remotedebugmonitor \(msvsmon.exe\) unter demselben Benutzerkonto auszuführen wie Visual Studio.  Wenn dies nicht möglich ist, können Sie den Remotedebugmonitor unter dem anderen Konto ausführen, indem Sie im Dialogfeld **Optionen** des Remotedebugmonitors die Option **Allen Benutzern das Debugging ermöglichen** aktivieren.  
  
> [!CAUTION]
>  Indem anderen Benutzern die Berechtigung zum Herstellen einer Verbindung gewährt wird, besteht die Möglichkeit, dass unbeabsichtigt eine Verbindung mit der falschen Remotedebugsitzung hergestellt wird.  Das Debuggen im Modus **Keine Authentifizierung** ist immer unsicher und sollte daher nur mit Vorsicht verwendet werden.  
  
 Weitere Informationen finden Sie unter [Starten des Remotedebugmonitors](../Topic/Start%20%20the%20Remote%20Debugging%20Monitor.md).  
  
## Siehe auch  
 [Remotedebuggen – Fehler und Problembehandlung](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remotedebugging](../debugger/remote-debugging.md)