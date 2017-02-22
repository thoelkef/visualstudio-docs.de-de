---
title: "Fehler: Timeout w&#228;hrend des Debuggens von Webdiensten | Microsoft Docs"
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
helpviewer_keywords: 
  - "Debugger, Webanwendungsfehler"
  - "XML-Webdienste, Zeitüberschreitung beim Debuggen"
ms.assetid: 4b7df112-788a-4429-9a0c-4c6dac4fb609
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Fehler: Timeout w&#228;hrend des Debuggens von Webdiensten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn Sie über den Aufrufcode schrittweise einen XML\-Webdienst ausführen, kommt es in einigen Situationen zum Timeout des Aufrufs. Im Anschluss daran kann das Debuggen nicht fortgesetzt werden.  Möglicherweise wird die folgende Fehlermeldung angezeigt.  
  
```  
An unhandled exception of type 'System.Net.WebException' occurred in   
system.Web.services.dll  
Additional information: The operation has timed-out.  
```  
  
## Lösung  
 Sie können dieses Problem umgehen, indem Sie den Timeoutwert des XML\-Webdienstaufrufs auf unendlich festlegen, wie im folgenden Beispiel gezeigt:  
  
```  
Service1 obj = new Service1();  
obj.TimeOut = -1; // infinite time out.  
```  
  
## Siehe auch  
 [Debuggen von Webanwendungen: Fehler und Problembehandlung](../debugger/debugging-web-applications-errors-and-troubleshooting.md)