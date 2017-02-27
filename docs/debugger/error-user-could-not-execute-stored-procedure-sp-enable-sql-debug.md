---
title: "Fehler: Der Benutzer konnte die gespeicherte Prozedur &quot;sp_enable_sql_debug&quot; nicht ausf&#252;hren | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.sqlde_accessdenied"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 11957495-c238-4cc5-8937-e4026f5e10e1
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Fehler: Der Benutzer konnte die gespeicherte Prozedur &quot;sp_enable_sql_debug&quot; nicht ausf&#252;hren
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die gespeicherte Prozedur "sp\_enable\_sql\_debug" konnte auf dem Server nicht ausgeführt werden.  Mögliche Ursachen:  
  
-   Ein Verbindungsproblem.  Es muss eine stabile Verbindung mit dem Server bestehen.  
  
-   Fehlende erforderliche Berechtigungen für den Server.  Zum Debuggen auf SQL Server 2005 müssen sowohl das Konto, unter dem Visual Studio ausgeführt wird, als auch das Konto, unter dem die Verbindung mit SQL Server hergestellt wird, Mitglieder der Systemadministratoren\-Rolle sein.  Das Konto, mit dem die Verbindung mit SQL Server hergestellt wird, ist entweder das Windows\-Benutzerkonto \(bei Windows\-Authentifizierung\) oder ein Konto mit Benutzer\-ID und Kennwort \(bei SQL\-Authentifizierung\).  
  
 Weitere Informationen finden Sie unter [How to: Set SQL Server Permissions for Debugging](http://msdn.microsoft.com/de-de/84e088d0-0409-41d4-841b-f5d4b0fda414).  
  
## Siehe auch  
 [How to: Set SQL Server Permissions for Debugging](http://msdn.microsoft.com/de-de/84e088d0-0409-41d4-841b-f5d4b0fda414)   
 [Setting Up SQL Debugging](http://msdn.microsoft.com/de-de/3db09e68-edcc-42de-9c22-4e97cfd55ab3)