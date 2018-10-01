---
title: 'Fehler: Timeout während des Debuggens von Webdiensten | Microsoft-Dokumentation'
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
helpviewer_keywords:
- debugger, Web application errors
- XML Web services, timeout while debugging
ms.assetid: 4b7df112-788a-4429-9a0c-4c6dac4fb609
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dee3017114c645c5bc3c2001e0cb2cafda48ef53
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47516174"
---
# <a name="error-timeout-while-debugging-web-services"></a>Fehler: Timeout während des Debuggens von Webdiensten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Fehler: Timeout While Debugging Web Services](https://docs.microsoft.com/visualstudio/debugger/error-timeout-while-debugging-web-services).  
  
Wenn Sie über den Aufrufcode schrittweise einen XML-Webdienst ausführen, kommt es in einigen Situationen zum Timeout des Aufrufs. Im Anschluss daran kann das Debuggen nicht fortgesetzt werden. Möglicherweise wird die folgende Fehlermeldung angezeigt.  
  
```  
An unhandled exception of type 'System.Net.WebException' occurred in   
system.Web.services.dll  
Additional information: The operation has timed-out.  
```  
  
## <a name="solution"></a>Lösung  
 Sie können dieses Problem umgehen, indem Sie den Timeoutwert des XML-Webdienstaufrufs auf unendlich festlegen, wie im folgenden Beispiel gezeigt:  
  
```  
Service1 obj = new Service1();  
obj.TimeOut = -1; // infinite time out.  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von Webanwendungen: Fehler und Problembehandlung](../debugger/debugging-web-applications-errors-and-troubleshooting.md)



