---
title: "Fehler: Der Microsoft Visual Studio-Remotedebugmonitor auf dem Remotecomputer verf&#252;gt nicht &#252;ber die Berechtigung, eine Verbindung mit diesem Computer herzustellen | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.access_denied_oncallback"
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
  - "Remotedebuggen, Windows-Version-Fehler"
ms.assetid: ba08a59b-6dbc-4bbc-9c52-379d3bf5241f
caps.latest.revision: 21
caps.handback.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Fehler: Der Microsoft Visual Studio-Remotedebugmonitor auf dem Remotecomputer verf&#252;gt nicht &#252;ber die Berechtigung, eine Verbindung mit diesem Computer herzustellen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dieser Fehler tritt auf, wenn der Benutzer, der versucht, den Visual Studio\-Remotedebugmonitor \(msvsmon\) auszuführen, kein Konto auf dem lokalen Computer hat.  
  
### So beheben Sie dieses Problem  
  
-   Fügen Sie dem Hostcomputer mit dem Visual Studio Debugger ein Benutzerkonto mit demselben Namen und Kennwort wie dem Benutzerkonto hinzu, unter dem msvsmon auf dem Remotecomputer ausgeführt wird.  
  
     – oder –  
  
-   Führen Sie msvsmon als Benutzer aus, der berechtigt ist, auf dem lokalen Computer Aufrufe durchzuführen.  Dies bedeutet, dass der Benutzer ein Domänenbenutzer sein und Administratorrechte auf dem msvsmon\-Computer besitzen muss.   Sie haben zwei Möglichkeiten, um das Benutzerkonto zum Ausführen von msvsmon anzugeben:  
  
    -   Klicken Sie mit der rechten Maustaste auf das msvsmon\-Symbol, und wählen Sie im Kontextmenü **Ausführen als** aus.  
  
     – oder –  
  
    -   Führen Sie an der Eingabeaufforderung `runas.exe` aus.  
  
## Siehe auch  
 [Domänenübergreifendes Remotedebuggen](../Topic/Remote%20Debugging%20Across%20Domains.md)   
 [Remotedebuggen – Fehler und Problembehandlung](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remotedebugging](../debugger/remote-debugging.md)