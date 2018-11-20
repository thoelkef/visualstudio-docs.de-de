---
title: 'Fehler: Timeout während des Debuggens von Webdiensten | Microsoft-Dokumentation'
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
helpviewer_keywords:
- debugger, Web application errors
- XML Web services, timeout while debugging
ms.assetid: 4b7df112-788a-4429-9a0c-4c6dac4fb609
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 985082d675da2a56d9880414809d91e92cb1fe0d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51736348"
---
# <a name="error-timeout-while-debugging-web-services"></a>Fehler: Timeout während des Debuggens von Webdiensten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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



