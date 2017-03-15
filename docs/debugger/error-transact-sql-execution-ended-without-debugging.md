---
title: "Fehler: Das Ausf&#252;hren von Transact-SQL wurde ohne Debuggen beendet | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.sqlde_sql_executed_but_not_debugged"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "SQL"
ms.assetid: 7a4d4999-3973-4339-ba6a-f0d19bcb1d4a
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Fehler: Das Ausf&#252;hren von Transact-SQL wurde ohne Debuggen beendet
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dieser Fehler tritt auf, wenn Sie versuchen, eine Transact\-SQL\- oder SQL\/CLR\-Prozedur zu debuggen und der Debugger keine Debugmeldungen vom SQL\-Server erhält.  
  
 Dies kann durch Netzwerkprobleme oder Probleme auf dem SQL\-Server verursacht worden sein, aber die wahrscheinlichste Ursache ist ein Berechtigungsproblem.  
  
 Zwei Konten sind beteiligt:  
  
-   Das Anwendungskonto ist das Benutzerkonto, unter dem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ausgeführt wird.  
  
-   Das Verbindungskonto ist die Identität, mit der die Verbindung zu SQL Server hergestellt wird.  Dies ist nicht notwendigerweise die gleiche Identität, unter der Visual Studio ausgeführt wird, wenn die Verbindung SQL\-Authentifizierung verwendet.  
  
 SQL\-Debuggen erfordert, dass das Anwendungskonto mit dem Verbindungskonto übereinstimmen muss oder Systemadministratorrechte hat.  
  
 Wenn Sie einen SQL\-Benutzernamen wie sa verwenden, muss das Anwendungskonto auf dem SQL\-Server als Systemadministrator eingerichtet sein.  Standardmäßig sind Administratoren auf dem Computer, auf dem SQL Server ausgeführt wird, SQL Server\-Systemadministratoren.  
  
 So können Sie diesen Fehler korrigieren:  
  
-   Überprüfen Sie die Berechtigungseinstellungen.  Weitere Informationen finden Sie unter [How to: Set SQL Server Permissions for Debugging](http://msdn.microsoft.com/de-de/84e088d0-0409-41d4-841b-f5d4b0fda414).  
  
-   Stellen Sie sicher, dass SQL\-Debuggen ordnungsgemäß eingerichtet ist.  
  
-   Weitere Informationen erhalten Sie vom Netzwerk\- oder Datenbankadministrator.  
  
## Siehe auch  
 [Setting Up SQL Debugging](http://msdn.microsoft.com/de-de/3db09e68-edcc-42de-9c22-4e97cfd55ab3)   
 [How to: Set SQL Server Permissions for Debugging](http://msdn.microsoft.com/de-de/84e088d0-0409-41d4-841b-f5d4b0fda414)   
 [Einstellungen und Vorbereitung für das Debuggen](../debugger/debugger-settings-and-preparation.md)   
 [Remotedebugging](../debugger/remote-debugging.md)