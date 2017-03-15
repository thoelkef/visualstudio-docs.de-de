---
title: "Fehler: Fehler bei einer Sicherheits&#252;berpr&#252;fung, weil der IIS-Verwaltungsdienst nicht reagiert hat | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.iis_not_responding"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Debugger, Webanwendungsfehler"
ms.assetid: 6060e94e-71dc-49f2-bb59-2584216eadbf
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Fehler: Fehler bei einer Sicherheits&#252;berpr&#252;fung, weil der IIS-Verwaltungsdienst nicht reagiert hat
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dieser Fehler tritt auf, wenn der IIS\-Verwaltungsdienst nicht reagiert.  Normalerweise weist dies auf ein Problem mit der IIS\-Installation hin.  Stellen Sie zunächst in der **Verwaltung** unter **Dienste** sicher, dass der Dienst ausgeführt wird.  
  
### So beheben Sie diesen Fehler  
  
-   IIS in der Systemsteuerung über die Option **Software** erneut installieren.  
  
-   \- oder \-  
  
-   IIS in der Systemsteuerung über die Option Software vom Computer entfernen.  Wenn Sie IIS entfernt haben und die Probleme weiterhin auftreten, vergewissern Sie sich in der Registrierung, dass der folgende Schlüssel nicht mehr existiert:  
  
    ```  
    HKEY_CLASSES_ROOT\CLSID\{A9E69610-B80D-11D0-B9B9-00A0C922E750}  
    ```  
  
     \- oder \-  
  
-   Deaktivieren Sie den IIS\-Verwaltungsdienst in der Systemsteuerung über die Option Verwaltung.  Dadurch wird IIS auf dem Computer deaktiviert.  
  
     Sie müssen den Computer nach jedem dieser drei Schritte neu starten.  
  
     Weitere Informationen finden Sie in der IIS\-Dokumentation.  
  
## Siehe auch  
 [Debuggen von Webanwendungen: Fehler und Problembehandlung](../debugger/debugging-web-applications-errors-and-troubleshooting.md)