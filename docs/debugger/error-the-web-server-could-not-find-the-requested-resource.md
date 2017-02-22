---
title: "Fehler: Der Webserver konnte die angeforderte Ressource nicht finden | Microsoft Docs"
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
ms.assetid: 1ceeaf30-918c-42bb-ace1-96944530fef3
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Fehler: Der Webserver konnte die angeforderte Ressource nicht finden
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Aufgrund von Sicherheitsüberlegungen wurde von IIS ein generischer Fehler zurückgegeben.  
  
 Eine mögliche Ursache ist die Sicherheitskonfiguration des Servers.  In IIS 6.0 und früheren Versionen wurde ein Zusatzhardwareprogramm, das als URLScan bekannt ist, zum Herausfiltern verdächtiger und fehlerhafter Anforderungen verwendet.  Bei IIS 7.0 ist zu diesem Zweck die Anforderungsfilterung integriert.  In beiden Fällen kann übermäßig einschränkende Anforderungsfilterung Visual Studio am Debuggen des Servers hindern.  
  
 Für diesen Fehler sind viele Ursachen möglich.  Einige der häufigsten Ursachen schließen ein Problem mit der IIS\-Installation oder der Konfigurationsroutine, der Websitekonfiguration oder den Berechtigungen im Dateisystem ein.  Sie können versuchen, mit einem Browser auf die Ressource zuzugreifen.  Abhängig von der IIS\-Konfiguration müssen Sie möglicherweise einen lokalen Browser auf dem Server verwenden oder das IIS\-Fehlerprotokoll überprüfen, um eine ausführliche Fehlermeldung zu erhalten.  
  
 Weitere Informationen über die Problembehandlung bei IIS finden Sie unter [IIS\-Verwaltung](http://go.microsoft.com/fwlink/?LinkId=255872).  
  
## Siehe auch  
 [UrlScan\-Sicherheitstool](http://www.microsoft.com/technet/security/tools/urlscan.mspx)   
 [Fehler: Der Webserver wurde gesperrt und blockiert das DEBUG\-Verb](../debugger/error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb.md)