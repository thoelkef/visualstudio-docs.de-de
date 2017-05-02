---
title: "Zugriff verweigert | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT5"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 8a512060-d744-47af-a83e-4ba42ea2c5b2
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
caps.handback.revision: 2
---
# Zugriff verweigert
Ein Skript hat versucht, auf Daten aus einer anderen Quelle als dem Host der aktuellen Seite zuzugreifen.  Mit der Richtlinieneinschränkung der gleichen Quelle gefolgt vom Internet Explorer und anderen Browsern können Skripts nur auf Daten aus Quellen mit demselben Schema, Host und Port der URL der aktuellen Seite zugreifen.  
  
 Wenn die aktuelle Seite https:\/\/employees.mycompany.com lautet, können Sie nicht auf Daten aus den folgenden URLs zugreifen:  
  
-   http:\/\/data.contoso.com, da sie HTTP statt HTTPS vewendet.  
  
-   https:\/\/somedatasource.com, da es sich um eine andere Domäne handelt.  
  
-   https:\/\/Employees.mycompany.com:8888, da sie einen anderen Port verwendet.  
  
### So beheben Sie diesen Fehler  
  
-   Überprüfen Sie, ob die API, die Sie aufrufen möchten, JSONP oder CORS unterstützt, d. h. zwei Ansätze, die Cross\-Origin\-Skripting sicher zulassen.  
  
-   Wenn Sie versuchen, eine REST\-API aufzurufen, gestalten Sie diesen Aufruf für Ihren serverseitigen Code um, und machen Sie dann den neuen REST\-Endpunkt für Ihre clientseitigen Skripts verfügbar.  
  
     Weitere Informationen im Zusammenhang mit den Richtlinieneinschränkungen der gleichen Quelle, JSONP und CORS finden Sie in der Onlinedokumentation.